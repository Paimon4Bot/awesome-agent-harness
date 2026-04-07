# 基于 MCP 的代码执行：构建更高效的 AI 代理

## **基于 MCP 的代码执行提升上下文效率**

随着代码执行环境在代理中越来越普遍，一种方案是将 MCP 服务器以代码 API 的形式呈现，而非直接的工具调用。代理随后可以编写代码与 MCP 服务器交互。这种方法同时解决了两个挑战：代理可以按需加载所需工具，并在执行环境中处理数据后再将结果传回模型。

实现方式有多种。其中一种方法是为已连接的 MCP 服务器中所有可用工具生成一个文件树。以下是使用 TypeScript 的实现方式：

```
servers
├── google-drive
│   ├── getDocument.ts
│   ├── ... (other tools)
│   └── index.ts
├── salesforce
│   ├── updateRecord.ts
│   ├── ... (other tools)
│   └── index.ts
└── ... (other servers)
```

然后每个工具对应一个文件，类似这样：

```
// ./servers/google-drive/getDocument.ts
import { callMCPTool } from "../../../client.js";

interface GetDocumentInput {
  documentId: string;
}

interface GetDocumentResponse {
  content: string;
}

/* Read a document from Google Drive */
export async function getDocument(input: GetDocumentInput): Promise<GetDocumentResponse> {
  return callMCPTool<GetDocumentResponse>('google_drive__get_document', input);
}
```

上文提到的 Google Drive 到 Salesforce 示例就可以转化为如下代码：

```
// Read transcript from Google Docs and add to Salesforce prospect
import * as gdrive from './servers/google-drive';
import * as salesforce from './servers/salesforce';

const transcript = (await gdrive.getDocument({ documentId: 'abc123' })).content;
await salesforce.updateRecord({
  objectType: 'SalesMeeting',
  recordId: '00Q5f000001abcXYZ',
  data: { Notes: transcript }
});
```

代理通过浏览文件系统来发现工具：列出 `./servers/` 目录以查找可用的服务器（如 `google-drive` 和 `salesforce`），然后读取所需的特定工具文件（如 `getDocument.ts` 和 `updateRecord.ts`）来理解每个工具的接口。这样代理只需加载当前任务所需的定义。这将 token 用量从 150,000 个减少到 2,000 个——节省了 98.7% 的时间和成本。

Cloudflare [发表了类似的发现](https://blog.cloudflare.com/code-mode/)，将基于 MCP 的代码执行称为 "Code Mode"。核心洞察是一致的：LLM 擅长编写代码，开发者应利用这一优势来构建更高效地与 MCP 服务器交互的代理。

## **基于 MCP 的代码执行的优势**

基于 MCP 的代码执行使代理能够通过按需加载工具、在数据到达模型前进行过滤、以及在单步中执行复杂逻辑来更高效地使用上下文。这种方案还在安全性和状态管理方面带来了额外的好处。

### 渐进式呈现

模型非常擅长浏览文件系统。将工具以代码文件的形式呈现在文件系统中，允许模型按需读取工具定义，而非一次性全部加载。

另一种方式是在服务器中添加 `search_tools` 工具来查找相关定义。例如，在使用上文假设的 Salesforce 服务器时，代理搜索 "salesforce" 并仅加载当前任务所需的工具。在 `search_tools` 工具中添加详细程度参数，允许代理选择所需的详细信息级别（如仅名称、名称和描述、或包含 schema 的完整定义），也有助于代理节省上下文并高效地发现工具。

### 上下文高效的工具结果

在处理大型数据集时，代理可以在代码中过滤和转换结果后再返回。考虑获取一个包含 10,000 行数据的电子表格：

```
// Without code execution - all rows flow through context
TOOL CALL: gdrive.getSheet(sheetId: 'abc123')
        → returns 10,000 rows in context to filter manually

// With code execution - filter in the execution environment
const allRows = await gdrive.getSheet({ sheetId: 'abc123' });
const pendingOrders = allRows.filter(row =>
  row["Status"] === 'pending'
);
console.log(`Found ${pendingOrders.length} pending orders`);
console.log(pendingOrders.slice(0, 5)); // Only log first 5 for review
```

代理只需查看 5 行而非 10,000 行。类似的模式也适用于聚合操作、跨多个数据源的连接、或提取特定字段——所有这些都不会膨胀上下文窗口。

#### **更强大且上下文更高效的控制流**

循环、条件判断和错误处理可以使用熟悉的代码模式来完成，而无需逐个串联工具调用。例如，如果你需要在 Slack 中接收部署通知，代理可以这样编写：

```
let found = false;
while (!found) {
  const messages = await slack.getChannelHistory({ channel: 'C123456' });
  found = messages.some(m => m.text.includes('deployment complete'));
  if (!found) await new Promise(r => setTimeout(r, 5000));
}
console.log('Deployment notification received');
```

这种方式比在代理循环中交替进行 MCP 工具调用和休眠命令更加高效。

此外，能够编写并执行条件判断树还能缩短“首个 token 输出时间”（time to first token, TTFT）延迟：代理无需等待模型评估 if 语句，而是可以让代码执行环境来完成这些判断。

### 隐私保护操作

当代理使用基于 MCP 的代码执行时，中间结果默认保留在执行环境中。这样，代理只能看到你明确打印或返回的内容，意味着你不希望与模型共享的数据可以在工作流中流转而永远不会进入模型的上下文。

对于更敏感的工作负载，agent harness 可以自动对敏感数据进行令牌化处理。例如，假设你需要将电子表格中的客户联系信息导入 Salesforce。代理编写：

```
const sheet = await gdrive.getSheet({ sheetId: 'abc123' });
for (const row of sheet.rows) {
  await salesforce.updateRecord({
    objectType: 'Lead',
    recordId: row.salesforceId,
    data: {
      Email: row.email,
      Phone: row.phone,
      Name: row.name
    }
  });
}
console.log(`Updated ${sheet.rows.length} leads`);
```

MCP 客户端会拦截数据并在数据到达模型之前对个人敏感信息（PII）进行令牌化处理：

```
// What the agent would see, if it logged the sheet.rows:
[
  { salesforceId: '00Q...', email: '[EMAIL_1]', phone: '[PHONE_1]', name: '[NAME_1]' },
  { salesforceId: '00Q...', email: '[EMAIL_2]', phone: '[PHONE_2]', name: '[NAME_2]' },
  ...
]
```

然后，当数据在另一个 MCP 工具调用中被共享时，会通过 MCP 客户端中的查找表对其进行反令牌化。真实的电子邮件地址、电话号码和姓名从 Google Sheets 流向 Salesforce，但永远不会经过模型。这防止了代理意外记录或处理敏感数据。你还可以利用这一点定义确定性的安全规则，控制数据可以流向何处以及从何处流入。

### 状态持久化与技能

具备文件系统访问权限的代码执行允许代理在操作之间维护状态。代理可以将中间结果写入文件，从而支持恢复工作和追踪进度：

```
const leads = await salesforce.query({
  query: 'SELECT Id, Email FROM Lead LIMIT 1000'
});
const csvData = leads.map(l => `${l.Id},${l.Email}`).join('\n');
await fs.writeFile('./workspace/leads.csv', csvData);

// Later execution picks up where it left off
const saved = await fs.readFile('./workspace/leads.csv', 'utf-8');
```

代理还可以将自身编写的代码持久化为可复用的函数。一旦代理为某项任务开发了可用的代码，它可以保存该实现以供后续使用：

```
// In ./skills/save-sheet-as-csv.ts
import * as gdrive from './servers/google-drive';
export async function saveSheetAsCsv(sheetId: string) {
  const data = await gdrive.getSheet({ sheetId });
  const csv = data.map(row => row.join(',')).join('\n');
  await fs.writeFile(`./workspace/sheet-${sheetId}.csv`, csv);
  return `./workspace/sheet-${sheetId}.csv`;
}

// Later, in any agent execution:
import { saveSheetAsCsv } from './skills/save-sheet-as-csv';
const csvPath = await saveSheetAsCsv('abc123');
```

这与 [Skills](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview) 的概念密切相关——Skills 是包含可复用指令、脚本和资源的文件夹，帮助模型在专业任务上提升表现。为这些保存的函数添加一个 SKILL.md 文件，就能创建一个结构化的技能供模型引用和使用。随着时间的推移，你的代理可以构建一个包含高级能力的工具箱，不断完善其最高效工作所需的基础支撑。

需要注意的是，代码执行也引入了自身的复杂性。运行代理生成的代码需要一个安全的执行环境，具备适当的 [沙箱隔离](https://www.anthropic.com/engineering/claude-code-sandboxing)、资源限制和监控。这些基础设施需求增加了运维开销和安全考量，而直接的工具调用则无需面对这些问题。代码执行的优势——降低 token 成本、减少延迟、改善工具组合——需要与这些实现成本进行权衡。

## **总结**

MCP 为代理连接众多工具和系统提供了基础协议。然而，一旦连接的服务器过多，工具定义和结果可能消耗大量 token，降低代理效率。

虽然这里的许多问题看起来很新颖——上下文管理、工具组合、状态持久化——但它们在软件工程中已有成熟的解决方案。代码执行将这些已有的模式应用到代理中，让代理使用熟悉的编程结构更高效地与 MCP 服务器交互。如果你实施了这种方案，我们鼓励你与 [MCP 社区](https://modelcontextprotocol.io/community/communication) 分享你的发现。

### 致谢

_本文由 Adam Jones 和 Conor Kelly 撰写。感谢 Jeremy Fox、Jerome Swannack、Stuart Ritchie、Molly Vorwerck、Matt Samuels 和 Maggie Vo 对本文草稿的反馈。_
