<!-- <p align="center">
  <img width="100" src="assets/003-logo-circle-db205d3a05.png" alt="e2b logo">
</p> -->

![E2B SDK Preview](assets/001-e2b-sdk-preview-28cf9b9fee.png)
![E2B SDK Preview](assets/002-e2b-sdk-preview-edd80c63a7.png)

<h4 align="center">
  <a href="https://pypi.org/project/e2b/">
    <img alt="Last 1 month downloads for the Python SDK" loading="lazy" decoding="async" style="color:transparent;width:170px;height:18px" src="https://static.pepy.tech/personalized-badge/e2b?period=monthly&units=INTERNATIONAL_SYSTEM&left_color=BLACK&right_color=GREEN&left_text=PyPi%20Monthly%20Downloads">
  </a>
  <a href="https://www.npmjs.com/package/e2b">
    <img alt="Last 1 month downloads for the JavaScript SDK" loading="lazy" width="200" height="30" decoding="async" data-nimg="1"
    style="color:transparent;width:auto;height:100%" src="https://img.shields.io/npm/dm/e2b?label=NPM%20Monthly%20Downloads">
  </a>
</h4>

<!---
<img width="100%" src="assets/004-preview-8007164afc.png" alt="Cover image">
--->
## 什么是 E2B？

[E2B](https://www.e2b.dev/) 是一个开源基础设施，允许你在云端安全的隔离沙箱中运行 AI 生成的代码。使用我们的 [JavaScript SDK](https://www.npmjs.com/package/e2b) 或 [Python SDK](https://pypi.org/project/e2b) 来启动和控制沙箱。

## 运行你的第一个沙箱

### 1. 安装 SDK

JavaScript / TypeScript
```
npm i e2b
```

Python
```
pip install e2b
```

### 2. 获取你的 E2B API 密钥
1. 在[这里](https://e2b.dev)注册 E2B。
2. 在[这里](https://e2b.dev/dashboard?tab=keys)获取你的 API 密钥。
3. 将你的 API 密钥设置为环境变量
```
E2B_API_KEY=e2b_***
```

### 3. 启动沙箱并运行命令

JavaScript / TypeScript
```ts
import Sandbox from 'e2b'

const sandbox = await Sandbox.create()
const result = await sandbox.commands.run('echo "Hello from E2B!"')
console.log(result.stdout) // Hello from E2B!
```

Python
```py
from e2b import Sandbox

with Sandbox.create() as sandbox:
    result = sandbox.commands.run('echo "Hello from E2B!"')
    print(result.stdout)  # Hello from E2B!
```

### 4. 使用代码解释器执行代码

如果你需要使用 [`runCode()`](https://e2b.dev/docs/code-interpreting)/[`run_code()`](https://e2b.dev/docs/code-interpreting) 执行代码，请安装 [Code Interpreter SDK](https://github.com/e2b-dev/code-interpreter)：

```
npm i @e2b/code-interpreter  # JavaScript/TypeScript
pip install e2b-code-interpreter  # Python
```

```ts
import { Sandbox } from '@e2b/code-interpreter'

const sandbox = await Sandbox.create()
const execution = await sandbox.runCode('x = 1; x += 1; x')
console.log(execution.text)  // outputs 2
```

### 5. 查看文档
访问 [E2B 文档](https://e2b.dev/docs)。

### 6. E2B Cookbook
访问我们的 [Cookbook](https://github.com/e2b-dev/e2b-cookbook/tree/main)，从结合不同 LLM 和 AI 框架的示例中获取灵感。

## 自托管

阅读[自托管指南](https://github.com/e2b-dev/infra/blob/main/self-host.md)，了解如何在你自己的环境中部署 [E2B 基础设施](https://github.com/e2b-dev/infra)。该基础设施使用 Terraform 部署。

支持的云服务商：
- 🟢 AWS
- 🟢 Google Cloud (GCP)
- [ ] Azure
- [ ] 通用 Linux 机器
