<p align="center">
    <a href="https://aider.chat/"><img src="https://aider.chat/assets/logo.svg" alt="Aider Logo" width="300"></a>
</p>

<h1 align="center">
终端中的 AI 结对编程
</h1>

<p align="center">
 Aider 让你与 LLM 进行结对编程，以启动新项目或在现有代码库基础上继续开发。
</p>

<p align="center">
  <img
    src="assets/001-screencast-beb82d875f.svg"
    alt="aider screencast"
  >
</p>

<p align="center">
<!--[[[cog
from scripts.homepage import get_badges_md
text = get_badges_md()
cog.out(text)
]]]-->
  <a href="https://github.com/Aider-AI/aider/stargazers"><img alt="GitHub Stars" title="Total number of GitHub stars the Aider project has received"
src="https://img.shields.io/github/stars/Aider-AI/aider?style=flat-square&logo=github&color=f1c40f&labelColor=555555"/></a>
  <a href="https://pypi.org/project/aider-chat/"><img alt="PyPI Downloads" title="Total number of installations via pip from PyPI"
src="https://img.shields.io/badge/📦%20Installs-5.7M-2ecc71?style=flat-square&labelColor=555555"/></a>
  <img alt="Tokens per week" title="Number of tokens processed weekly by Aider users"
src="https://img.shields.io/badge/📈%20Tokens%2Fweek-15B-3498db?style=flat-square&labelColor=555555"/>
  <a href="https://openrouter.ai/#options-menu"><img alt="OpenRouter Ranking" title="Aider's ranking among applications on the OpenRouter platform"
src="https://img.shields.io/badge/🏆%20OpenRouter-Top%2020-9b59b6?style=flat-square&labelColor=555555"/></a>
  <a href="https://aider.chat/HISTORY.html"><img alt="Singularity" title="Percentage of the new code in Aider's last release written by Aider itself"
src="https://img.shields.io/badge/🔄%20Singularity-88%25-e74c3c?style=flat-square&labelColor=555555"/></a>
<!--[[[end]]]-->
</p>

## 功能特性

### [云端和本地 LLM](https://aider.chat/docs/llms.html)

<a href="https://aider.chat/docs/llms.html"><img src="assets/002-brain-b3dd9c3af2.svg" width="32" height="32" align="left" valign="middle" style="margin-right:10px"></a>
Aider 在 Claude 3.7 Sonnet、DeepSeek R1 & Chat V3、OpenAI o1、o3-mini & GPT-4o 上表现最佳，但可以连接几乎所有 LLM，包括本地模型。

<br>

### [映射你的代码库](https://aider.chat/docs/repomap.html)

<a href="https://aider.chat/docs/repomap.html"><img src="assets/003-map-outline-4ccf5d63c7.svg" width="32" height="32" align="left" valign="middle" style="margin-right:10px"></a>
Aider 会为你的整个代码库创建地图，帮助它在大型项目中更好地工作。

<br>

### [100+ 种编程语言](https://aider.chat/docs/languages.html)

<a href="https://aider.chat/docs/languages.html"><img src="assets/004-code-tags-ba6eecef87.svg" width="32" height="32" align="left" valign="middle" style="margin-right:10px"></a>
Aider 支持大多数流行的编程语言：python、javascript、rust、ruby、go、cpp、php、html、css 以及数十种其他语言。

<br>

### [Git 集成](https://aider.chat/docs/git.html)

<a href="https://aider.chat/docs/git.html"><img src="assets/005-source-branch-dd46e227bc.svg" width="32" height="32" align="left" valign="middle" style="margin-right:10px"></a>
Aider 会自动提交更改并附带合理的提交信息。使用熟悉的 git 工具，轻松比较、管理和撤销 AI 所做的更改。

<br>

### [在你的 IDE 中使用](https://aider.chat/docs/usage/watch.html)

<a href="https://aider.chat/docs/usage/watch.html"><img src="assets/006-monitor-696c662cc9.svg" width="32" height="32" align="left" valign="middle" style="margin-right:10px"></a>
在你最喜欢的 IDE 或编辑器中使用 aider。通过在代码中添加注释来请求更改，aider 就会开始工作。

<br>

### [图片与网页](https://aider.chat/docs/usage/images-urls.html)

<a href="https://aider.chat/docs/usage/images-urls.html"><img src="assets/007-image-multiple-86bb5d3fa5.svg" width="32" height="32" align="left" valign="middle" style="margin-right:10px"></a>
将图片和网页添加到对话中，提供视觉上下文、截图、参考文档等。

<br>

### [语音转代码](https://aider.chat/docs/usage/voice.html)

<a href="https://aider.chat/docs/usage/voice.html"><img src="assets/008-microphone-2b5272f495.svg" width="32" height="32" align="left" valign="middle" style="margin-right:10px"></a>
用语音与 aider 讨论你的代码！使用语音请求新功能、测试用例或修复错误，让 aider 来实现更改。

<br>

### [Lint 与测试](https://aider.chat/docs/usage/lint-test.html)

<a href="https://aider.chat/docs/usage/lint-test.html"><img src="assets/009-check-all-dc9c5755f0.svg" width="32" height="32" align="left" valign="middle" style="margin-right:10px"></a>
在 aider 每次修改代码后自动运行 lint 和测试。Aider 可以修复 linter 和测试套件检测出的问题。

<br>

### [复制粘贴到网页聊天](https://aider.chat/docs/usage/copypaste.html)

<a href="https://aider.chat/docs/usage/copypaste.html"><img src="assets/010-content-copy-5c52d9df4e.svg" width="32" height="32" align="left" valign="middle" style="margin-right:10px"></a>
通过任意 LLM 的网页聊天界面进行协作。Aider 简化了在浏览器中来回复制粘贴代码上下文和修改内容的流程。

## 快速开始

```bash
python -m pip install aider-install
aider-install

# 进入你的代码库目录
cd /to/your/project

# DeepSeek
aider --model deepseek --api-key deepseek=<key>

# Claude 3.7 Sonnet
aider --model sonnet --api-key anthropic=<key>

# o3-mini
aider --model o3-mini --api-key openai=<key>
```

详情请参阅[安装说明](https://aider.chat/docs/install.html)和[使用文档](https://aider.chat/docs/usage.html)。

## 更多信息

### 文档
- [安装指南](https://aider.chat/docs/install.html)
- [使用指南](https://aider.chat/docs/usage.html)
- [教程视频](https://aider.chat/docs/usage/tutorials.html)
- [连接 LLM](https://aider.chat/docs/llms.html)
- [配置选项](https://aider.chat/docs/config.html)
- [故障排除](https://aider.chat/docs/troubleshooting.html)
- [常见问题](https://aider.chat/docs/faq.html)

### 社区与资源
- [LLM 排行榜](https://aider.chat/docs/leaderboards/)
- [GitHub 仓库](https://github.com/Aider-AI/aider)
- [Discord 社区](https://discord.gg/Y7X7bhMQFV)
- [发布说明](https://aider.chat/HISTORY.html)
- [博客](https://aider.chat/blog/)

## 用户好评

- *"我的生活发生了改变...Aider...它将震撼你的世界。"* — [Eric S. Raymond on X](https://x.com/esrtweet/status/1910809356381413593)
- *"最好的免费开源 AI 编程助手。"* — [IndyDevDan on YouTube](https://youtu.be/YALpX8oOn78)
- *"迄今为止最好的 AI 编程助手。"* — [Matthew Berman on YouTube](https://www.youtube.com/watch?v=df8afeb1FY8)
- *"Aider ... 轻松地将我的编程效率提高了四倍。"* — [SOLAR_FIELDS on Hacker News](https://news.ycombinator.com/item?id=36212100)
- *"这是一个很棒的工作流 ... Aider 的使用体验对我来说非常完美。"* — [qup on Hacker News](https://news.ycombinator.com/item?id=38185326)
- *"真的就像有一位资深开发者直接住在你的 Git 仓库里 - 太神奇了！"* — [rappster on GitHub](https://github.com/Aider-AI/aider/issues/124)
- *"多么了不起的工具。令人难以置信。"* — [valyagolev on GitHub](https://github.com/Aider-AI/aider/issues/6#issue-1722897858)
- *"Aider 真是一个令人惊叹的东西！"* — [cgrothaus on GitHub](https://github.com/Aider-AI/aider/issues/82#issuecomment-1631876700)
- *"比我亲自从头开始搞出前几个可用版本要快得多。"* — [Daniel Feldman on X](https://twitter.com/d_feldman/status/1662295077387923456)
- *"感谢 Aider！真的感觉像是窥见了编程的未来。"* — [derwiki on Hacker News](https://news.ycombinator.com/item?id=38205643)
- *"简直太棒了。它让我能做以前觉得超出舒适区的事情。"* — [Dougie on Discord](https://discord.com/channels/1131200896827654144/1174002618058678323/1174084556257775656)
- *"这个项目太出色了。"* — [funkytaco on GitHub](https://github.com/Aider-AI/aider/issues/112#issuecomment-1637429008)
- *"了不起的项目，绝对是我用过的最好的 AI 编程助手。"* — [joshuavial on GitHub](https://github.com/Aider-AI/aider/issues/84)
- *"我非常喜欢使用 Aider ... 它让软件开发这种体验变得轻松许多。"* — [principalideal0 on Discord](https://discord.com/channels/1131200896827654144/1133421607499595858/1229689636012691468)
- *"我一直在从...手术中恢复...aider...让我能够保持产出。"* — [codeninja on Reddit](https://www.reddit.com/r/OpenAI/s/nmNwkHy1zG)
- *"我是一个 aider 上瘾者。我完成了更多的工作，但花的时间更少了。"* — [dandandan on Discord](https://discord.com/channels/1131200896827654144/1131200896827654149/1135913253483069470)
- *"Aider ... 完全碾压所有其他工具，毫无竞争可言。"* — [SystemSculpt on Discord](https://discord.com/channels/1131200896827654144/1131200896827654149/1178736602797846548)
- *"Aider 太棒了，搭配 Sonnet 3.5 简直令人震撼。"* — [Josh Dingus on Discord](https://discord.com/channels/1131200896827654144/1133060684540813372/1262374225298198548)
- *"毫无疑问，这是迄今为止最好的 AI 编程助手工具。"* — [IndyDevDan on YouTube](https://www.youtube.com/watch?v=MPYFPvxfGZs)
- *"[Aider] 改变了我的日常编程工作流。令人难以置信的是...(它)...可以改变你的生活。"* — [maledorak on Discord](https://discord.com/channels/1131200896827654144/1131200896827654149/1258453375620747264)
- *"在实际开发工作中处理现有代码库的最佳代理。"* — [Nick Dobos on X](https://twitter.com/NickADobos/status/1690408967963652097?s=20)
- *"我最喜欢的软件之一。在新范式上开疆拓土！"* — [Chris Wall on X](https://x.com/chris65536/status/1905053299251798432)
- *"Aider 对我和我的工作来说是一场革命。"* — [Starry Hope on X](https://x.com/starryhopeblog/status/1904985812137132056)
- *"试试 aider！这是最好的氛围编程方式之一。"* — [Chris Wall on X](https://x.com/Chris65536/status/1905053418961391929)
- *"太喜欢 Aider 了。"* — [hztar on Hacker News](https://news.ycombinator.com/item?id=44035015)
- *"Aider 毫无疑问是最好的。而且是免费开源的。"* — [AriyaSavakaLurker on Reddit](https://www.reddit.com/r/ChatGPTCoding/comments/1ik16y6/whats_your_take_on_aider/mbip39n/)
- *"Aider 也是我最好的朋友。"* — [jzn21 on Reddit](https://www.reddit.com/r/ChatGPTCoding/comments/1heuvuo/aider_vs_cline_vs_windsurf_vs_cursor/m27dcnb/)
- *"试试 Aider，值得。"* — [jorgejhms on Reddit](https://www.reddit.com/r/ChatGPTCoding/comments/1heuvuo/aider_vs_cline_vs_windsurf_vs_cursor/m27cp99/)
- *"我喜欢 aider :)"* — [Chenwei Cui on X](https://x.com/ccui42/status/1904965344999145698)
- *"Aider 是 LLM 代码生成领域的精密工具 ... 极简、经过深思熟虑、能够进行外科手术般的精准修改 ... 同时让开发者保持掌控。"* — [Reilly Sweetland on X](https://x.com/rsweetland/status/1904963807237259586)
- *"不敢相信 aider 今天一把就用 vibe coding 完成了一个横跨 service 和 cli、长达 650 行代码的功能。"* - [autopoietist on Discord](https://discord.com/channels/1131200896827654144/1131200896827654149/1355675042259796101)
- *"糟糕，秘密泄露了！是的，Aider 是最好的编程工具。我极力向所有人推荐。"* — [Joshua D Vander Hook on X](https://x.com/jodavaho/status/1911154899057795218)
- *"多亏了 aider，我在过去两天内已经启动并完成了三个个人项目"* — [joseph stalzyn on X](https://x.com/anitaheeder/status/1908338609645904160)
- *"我已经使用 aider 作为主力工具超过一年了 ... 我绝对热爱这个工具，无法用言语表达。"* — [koleok on Discord](https://discord.com/channels/1131200896827654144/1273248471394291754/1356727448372252783)
- *"Aider...是衡量标准的工具。"* — [BeetleB on Hacker News](https://news.ycombinator.com/item?id=43930201)
- *"aider 真的很酷"* — [kache on X](https://x.com/yacineMTB/status/1911224442430124387)
