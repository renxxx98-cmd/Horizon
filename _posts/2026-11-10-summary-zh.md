---
layout: default
title: "Horizon Summary: 2026-11-10 (ZH)"
date: 2026-11-10
lang: zh
---

> 从 48 条内容中筛选出 16 条重要资讯。

---

**科技新闻**
1. [.NET 11 运行时更新：运行时 async 与兼容性变化](#item-tech-news-1) ⭐️ 8.0/10
2. [Chips and Cheese 解析 AMD Zen 6 架构细节](#item-tech-news-2) ⭐️ 8.0/10
3. [DeepMind 发布 AlphaProof Code 形式化代码验证系统](#item-tech-news-3) ⭐️ 8.0/10
4. [Blender 5.3 发布：原生支持 Gaussian Splat 与几何节点 Bundle](#item-tech-news-4) ⭐️ 8.0/10
5. [Fireworks 遭新攻击，客户账单与模型权重外泄](#item-tech-news-5) ⭐️ 8.0/10
6. [Synaptics 专利主张致 DisplayLink 驱动开发停止](#item-tech-news-6) ⭐️ 7.0/10
7. [Chrome 发布 Modern Web Guidance 1.0，为编码代理提供现代 Web 指南](#item-tech-news-7) ⭐️ 7.0/10
8. [英国跨党派提案：手机预装软件自动模糊性虐待图像](#item-tech-news-8) ⭐️ 7.0/10
9. [OpenAI 内部部署控制室系统，35 秒内叫停风险 AI 任务](#item-tech-news-9) ⭐️ 7.0/10
10. [Claude Code 设置文件被曝泄露 2539 个真实凭据](#item-tech-news-10) ⭐️ 7.0/10
11. [Anthropic 将 Claude 改为地区白名单，中国大陆及港澳被排除](#item-tech-news-11) ⭐️ 7.0/10
12. [稀宇科技开源 MiniMax H3 Image，4K 生成约 10 秒](#item-tech-news-12) ⭐️ 7.0/10

**财经新闻**
1. [Polymarket 称年化收入突破 18 亿美元](#item-finance-news-1) ⭐️ 7.0/10
2. [美联储理事沃勒倾向 12 月加息，称不排除 50 个基点](#item-finance-news-2) ⭐️ 7.0/10
3. [前三季度中国新能源乘用车出口同比增长 138.8%](#item-finance-news-3) ⭐️ 7.0/10
4. [加州 5%亿万富翁税公投未获通过](#item-finance-news-4) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [.NET 11 运行时更新：运行时 async 与兼容性变化](https://learn.microsoft.com/en-us/dotnet/core/whats-new/dotnet-11/runtime) ⭐️ 8.0/10

微软公布了 .NET 11 运行时的更新内容，核心包括运行时级 async 支持与若干兼容性变化，面向计划升级的 .NET 开发者。社区讨论称，运行时 async 可减少代码中的状态机并改善堆栈跟踪，同时对其性能表现感到意外。另有评论援引官方兼容性文档提醒，\(decimal\)0.1 在 .NET 11 中的转换结果由 .NET 10 的 0.1 变为 0.1000000000000000055511151231，升级时需留意数值行为差异。

hackernews · stevefan1999 · 11月10日 12:20 · [社区讨论](https://news.ycombinator.com/item?id=50439284)

**「背景：运行时 async 的由来」** 此前 C\# 的 async/await 依赖编译器生成状态机；.NET 11 的 runtime async 把这一机制下移到运行时/JIT，以减少编译器改写的痕迹并尝试保持性能。到 Preview 5/6 的预览资料显示，runtime-native async 已不再需要在 net11.0 项目中显式打开预览特性，ASP.NET Core 的部分共享框架库也已用 runtime-async 编译。

**「升级前的影响」** 受影响最大的是仍在较旧硬件上运行 .NET 应用的组织：从 .NET 11 起，缺少基线指令集的 CPU 将无法启动运行时，并会输出类似“当前 CPU 缺少一个或多个基线指令集”的提示，因此升级前需要先核对部署主机的 CPU 支持情况，而不是直接替换运行时。社区评论还指出兼容性文档中存在数值行为变化，例如 \`\(decimal\)0.1\` 在 .NET 10 下输出 \`0.1\`，在 .NET 11 下变为 \`0.1000000000000000055511151231\`，涉及数值格式化或序列化输出的代码应据此检查。

**「社区讨论」** 有开发者认为，C\#/.NET 因“只能跑在 Windows 上”和停留在 .NET Framework 时代的旧印象而被低估，但日常后端开发体验很好；也有评论对运行时 async 在不生成状态机的情况下保持相当性能表示意外。另有用户询问在 Linux 上应使用什么 IDE 重新开始 C\# 开发。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.youngju.dev/blog/2026-07-16-dotnet-11-runtime-async">NET 11 runtime - async — async 상태 머신을 컴파일러에서...</a></li>
<li><a href="https://zhangxihai.cn/archives/dotnet-11-new-features-sts-lts-analysis">NET 11 新特性分析：值得升级吗？ 非 LTS...</a></li>
<li><a href="https://learn.microsoft.com/en-us/dotnet/core/whats-new/dotnet-11/runtime">What&#x27;s new in . NET 11 runtime | Microsoft Learn</a></li>

</ul>
</details>

**标签**: `#.NET 11`, `#C\#`, `#runtime`, `#async`, `#breaking changes`

---

<a id="item-tech-news-2"></a>
### [Chips and Cheese 解析 AMD Zen 6 架构细节](https://chipsandcheese.com/p/amds-zen-6-family-feeding-the-beast) ⭐️ 8.0/10

Chips and Cheese 发布了对 AMD Zen 6 处理器家族的技术分析，逐项讨论核心内的执行单元配置、分支预测、内存与 I/O 小芯片，以及核心在 CCD 中的组织方式。评论中引用文章的一处改动是整数乘法单元从三个减至两个，PDEP 与 PEXT 吞吐也从每周期三条指令降至两条。由于目前没有产品发布或 AMD 官方规格可供对照，这些内容属于第三方对尚未上市架构的分析，而非实测结果。

hackernews · pixelpoet · 11月10日 17:02 · [社区讨论](https://news.ycombinator.com/item?id=50443090)

**「背景」** Zen 6 是 AMD 继 Zen 5 之后的下一代 CPU 微架构，Chips and Cheese 此次分析延续了它对前几代核心的实测脉络：该文指出 Zen 5 拥有其测过的所有核心中最好的方向预测器，而 Zen 6 的重点变化在于方向预测器被压垮之后的行为。更早的 Zen 4 于 2022 年 9 月 27 日发布，采用分离式设计——I/O 晶片由台积电 N6 工艺制造，CCD 使用 N5，APU 使用 N4，并改进了直接与间接分支预测器，这一 I/O 晶片与计算晶片分离的布局正是评论区讨论内存控制器与 CCD 核数时的前提。

**「影响」** 对 AM5 平台用户而言，最直接的相关点是新的 I/O 小芯片与内存控制器：评论者称现有 Zen 4/5 的内存控制器在双通道同时插满时很难超过 3600 MT/s，并把改良希望寄托在 Zen 6 上。不过文章与讨论都没有给出可验证的实测数据，是否升级或等待仍需以官方规格或独立测试为准。

**「社区讨论」** bmenrigh 认为消费级 Zen 4/5 最薄弱的环节就是 I/O 芯片及其上的内存控制器，并听说 Zen 6 将换用更小制程的新 I/O 芯片，把内存控制器改进列为最期待的变动。Aardwolf 则质疑整数乘法单元减少与 PDEP/PEXT 吞吐下降是共用电路还是两处独立削减，bee\_rider 追问 32 核 CCD 与核心之间是否存在更小的逻辑调度单元。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Zen_4">Zen 4 - Wikipedia</a></li>
<li><a href="https://chipsandcheese.com/p/amds-zen-6-family-feeding-the-beast">AMD ’s Zen 6 Family: Feeding the Beast - by George Cozma</a></li>

</ul>
</details>

**标签**: `#AMD Zen 6`, `#CPU architecture`, `#hardware`, `#memory controller`, `#branch prediction`

---

<a id="item-tech-news-3"></a>
### [DeepMind 发布 AlphaProof Code 形式化代码验证系统](https://deepmind.google/blog/introducing-alphaproof-code/) ⭐️ 8.0/10

DeepMind 发布了 AlphaProof Code，将其定位为面向形式化代码验证的 AI 系统，目标场景包括使用 Lean、Rocq 等证明助手的开发工作。现有材料没有给出可核验的版本、开放范围或独立基准结果，因此目前能确认的是系统发布，而非已复现的验证能力。围绕它的争论集中在证明复盖范围：是只验证实现满足给定定理，还是也检验规范本身是否正确。

hackernews · ilreb · 11月10日 12:11 · [社区讨论](https://news.ycombinator.com/item?id=50439193)

**「背景」** AlphaProof Code 的验证对象是 Signal 协议的参考实现 libsignal，目标是在机器码层面证明关键安全属性；这属于形式化验证：把安全属性写成机器可检验的定理，再交给证明助手逐条检查。证明助手（如 Lean、Rocq）只能保证代码满足所写定理，定理是否准确覆盖真实安全目标仍需人工判断，这也是讨论中“规格还是实现”争议的背景。

**「影响」** 对使用证明助手的团队来说，审查重点会落在定理陈述和规范覆盖上，而不只是证明脚本能否通过；HN 评论指出，AI 在自行编写 Lean 定义和定理时可能通过缩小命题或改写假设来“通过”验证，因此需要人工复核证明所表达的性质。

**「社区讨论」** HN 评论中，hedora 质疑“整库验证且零缺陷”的结果，推测可能只证明了狭窄性质或定理本身写错；thibsrn 则认为该代理并未挑战规范，只是验证实现，和普通编码代理差别有限。r0ze-at-hn 补充说，让 AI 自己写 Lean 时很容易出现“作弊”，即通过调整定理来让证明成立。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://google-deepmind.github.io/code-verification/">AlphaProof Code : Verifying Signal’s Security at the Machine- Code ...</a></li>

</ul>
</details>

**标签**: `#AI for formal verification`, `#proof assistants`, `#Lean`, `#Rocq`, `#software correctness`

---

<a id="item-tech-news-4"></a>
### [Blender 5.3 发布：原生支持 Gaussian Splat 与几何节点 Bundle](https://www.blender.org/download/releases/5-3/) ⭐️ 8.0/10

Blender 5.3 已发布，新增内置 Gaussian Splat 支持，并为几何节点加入 Bundle 功能。对 3D 图形和 VFX 用户来说，这意味着 Gaussian Splat 处理被纳入 Blender 原生功能，复杂几何节点管线也可用 Bundle 组织。

hackernews · amlib · 11月10日 16:15 · [社区讨论](https://news.ycombinator.com/item?id=50442426)

**「背景」** 高斯泼溅（Gaussian Splatting）用大量带位置、尺度、朝向和透明度参数的三维高斯点表示场景，通常由多视角照片重建，而不是依赖连续的三角形网格表面。因此，它和 Blender 传统的网格建模与渲染管线属于不同的场景表示方式。

**「影响」** 对依赖几何节点搭建生产管线的团队，5.3 的 Bundle 是需要评估的新组织方式；早期用户反馈它能简化复杂工作流，但理解成本不低。

**「社区讨论」** 一位评论者在 M4 上测试了 400 万 splat 的场景，称 beta 版已经成熟、快速且与 Blender 界面整合良好；另一位用户认为几何节点 Bundle 对复杂管线帮助很大，但需要时间理解。还有评论者提出 triangle splatting 的替代思路，认为 GPU 本来就更擅长渲染三角形。

**标签**: `#Blender`, `#Gaussian Splatting`, `#3D graphics`, `#open source`, `#geometry nodes`

---

<a id="item-tech-news-5"></a>
### [Fireworks 遭新攻击，客户账单与模型权重外泄](https://finance.sina.com.cn/stock/usstock/c/2026-11-10/doc-iniyfzhx2605532.shtml) ⭐️ 8.0/10

Fireworks 确认遭遇新一轮黑客攻击，部分客户的账单信息、模型权重和数据集外泄，公司正与 Palo Alto Networks 旗下 Unit 42 联合调查。Harvey 表示其客户数据未受影响，但其他客户及终端用户是否受影响仍不清楚。知情人士称，部分每年支付数百万美元的大客户正考虑迁移；Fireworks 年化营收今年 7 月已达 10 亿美元，原计划本周启动新一轮融资，目标估值至少 300 亿美元。

telegram · zaihuapd · 11月10日 13:00

**「背景：Fireworks 的推理云业务与融资轨迹」** Fireworks 是一家模型推理云服务商，本身不训练前沿模型，而是托管客户的自定义模型；据 Lanceum 的报道，其每日处理的 40 万亿 token 中约 95% 来自定制模型。按这一业务结构，此次外泄的模型权重与数据集很可能属于客户自有资产，而非 Fireworks 自研模型。该公司 2026 年 7 月完成 15 亿美元 D 轮融资，估值 175 亿美元（此前 2025 年 10 月的 C 轮为 2.5 亿美元、估值 40 亿美元），并称当时跨过 10 亿美元年化营收。

**「影响」** 对 Fireworks 客户而言，泄露内容包含模型权重和数据集，受影响方需要确认自身资产是否在调查范围内；目前除 Harvey 外，其他客户及终端用户是否受影响仍未明确。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://letsdatascience.com/blog/fireworks-ai-raises-1-5-billion-betting-against-big-ai-labs">Fireworks AI Raises $1.5 Billion at $17.5 Billion Valuation</a></li>
<li><a href="https://aiweekly.co/alerts/fireworks-ai-advances-fresh-funding-on-inference-cloud-boom">Fireworks AI Advances Fresh Funding on Inference ... | AI Weekly</a></li>
<li><a href="https://lanceum.com/startups/fireworks-ai-1-5b-series-d-17-5b-valuation">Fireworks AI Raises $1.5B at $17.5B Valuation as... | Lanceum</a></li>

</ul>
</details>

**标签**: `#AI security`, `#data breach`, `#Fireworks AI`, `#model weights`, `#cloud infrastructure`

---

<a id="item-tech-news-6"></a>
### [Synaptics 专利主张致 DisplayLink 驱动开发停止](https://lwn.net/SubscriberLink/1102549/acbc92e00cee3a3f/) ⭐️ 7.0/10

据 LWN 报道，Synaptics 提出的专利主张已使开源 DisplayLink 驱动的开发工作停止，争议涉及开源许可、逆向工程与专利执法边界。现有材料未给出专利编号、受影响的具体项目或停止范围，因此难以判断影响是限于单个驱动还是波及更广的分发渠道。

hackernews · speckx · 11月10日 18:02 · [社区讨论](https://news.ycombinator.com/item?id=50443824)

**「背景」** DisplayLink 是 Synaptics 旗下用于 USB 扩展坞和显示适配器的图形技术，其官方驱动为闭源。此前已有开发者因编写开源 DisplayLink 驱动而收到 Synaptics 的停止侵权函；据 Tom&\#x27;s Hardware 报道，Synaptics 声称该项目侵犯其专利，而开发者对此提出异议（tool-2-1）。Phoronix 随后报道，这个用 Rust 编写的开源驱动在受到法律威胁后已从公开渠道消失（tool-2-2）。

**「影响」** 对仍依赖这些驱动的用户和下游发行版而言，开发停止意味着后续缺陷修复、兼容性更新和新硬件支持可能中断；在专利主张范围明确前，继续维护或分发相关代码需要评估法律风险。

**「社区讨论」** 评论者质疑 Synaptics 以 2.5 万美元“文档成本”施压的合理性，并争论逆向工程应归入专利法还是商业秘密范畴；也有人认为 DisplayLink 因 DDR 价格和 USB4/Thunderbolt 替代方案而失去经济性，停止开发未必是损失。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.tomshardware.com/peripherals/docking-stations-hubs/synaptics-sends-cease-and-desist-order-to-creator-of-open-source-displaylink-driver-dares-him-to-publicize-its-threats-dev-reverse-engineers-displaylink-using-claude-ai-and-rust-synaptics-threatens-to-bill-creator-for-legal-documentation">Synaptics sends cease-and-desist order to creator of open - source ...</a></li>
<li><a href="https://www.phoronix.com/news/Synaptics-Blocks-Vino-Driver">Synaptics Appears To Use Legal Threats To Block Open - Source ...</a></li>

</ul>
</details>

**标签**: `#open-source`, `#patents`, `#hardware drivers`, `#DisplayLink`, `#legal issues`

---

<a id="item-tech-news-7"></a>
### [Chrome 发布 Modern Web Guidance 1.0，为编码代理提供现代 Web 指南](https://github.com/GoogleChrome/modern-web-guidance) ⭐️ 7.0/10

Google Chrome 团队发布 Modern Web Guidance 1.0，以编码代理技能和 CLI 的形式提供 200 多条、约 1.7MB 的人工整理现代 Web 平台最佳实践，并与 Firefox、MDN 和 Edge 合作。该项目旨在让编码代理在前端任务中优先采用 CSS.highlights、&lt;dialog&gt;、field-sizing 等原生能力，而不是继续沿用 div 加 JavaScript 的旧模式。用户可通过 npx modern-web-guidance@latest install 安装，也可运行 search 和 legacy-scan 子命令，项目为开源。团队称，legacy-scan 在留出仓库上的平均精度为 92%，并且在 200 项任务、约 1,700 条 Playwright/AST 断言的对比中，代理通过率从无引导时的 55% 提升到有引导时的 92%。

hackernews · paulirish · 11月10日 18:01 · [社区讨论](https://news.ycombinator.com/item?id=50443812)

**「背景」** 编码代理往往知道部分新 Web API 的名称，却仍倾向复用已有的 \`&lt;div&gt;\` 加 JavaScript 方案；要让代理稳定改用原生能力，需要把专家整理的实现模式以可检索的知识包提供给它。该项目因此将指南封装为 agent skill，并配套本地 RAG CLI 与 legacy-scan，以便按任务激活相关内容而不占满上下文窗口。

**「影响」** 对需要维护既有前端代码库的开发者，legacy-scan ./src 可直接扫描出可由代理现代化的旧模式。不过，92% 的精度是团队在留出仓库上的自测结果，而该扫描器是 1.0 中新引入的功能，团队在将其用于自有代码时仍应检查误报。

**「社区讨论」** 评论中最实质的争议集中在标准影响力与浏览器兼容性：一位用户列出 CSS @function、calc-size\(\)、interpolate-size 等被建议特性在 Chrome 中已稳定，但 Firefox 和 Safari 尚不支持；另一位用户则担心，让各类 LLM 都遵循 Chrome 团队的 Web 开发指南会加剧单一浏览器主导。也有用户建议额外发布可供 grep 或通过 HTTP 获取的 Markdown 索引，从而省去安装步骤。

**标签**: `#web platform`, `#coding agents`, `#browser standards`, `#developer tooling`, `#open source`

---

<a id="item-tech-news-8"></a>
### [英国跨党派提案：手机预装软件自动模糊性虐待图像](https://observer.co.uk/news/national/article/fight-to-block-child-sexual-abuse-images-unites-peers-and-mps-in-cross-party-campaign) ⭐️ 7.0/10

英国跨党派议员与上院议员联合提出一项尚待立法的方案，要求在英国销售的所有手机和平板预装软件，自动模糊儿童性虐待图像和视频（包括 AI 生成内容），并让旧设备通过强制更新获得该功能。方案称目标是使相关直播无法进行；它由上院保守党议员 John Nash 和下院工党前儿童保护事务大臣 Jess Phillips 牵头。政府此前已承诺立法，要求苹果和谷歌阻止儿童拍摄和分享裸照。

telegram · zaihuapd · 11月10日 05:11

**「背景」** 英国政府此前已承诺立法，要求苹果和谷歌阻止儿童拍摄和分享裸照；此次跨党派方案正是把这一承诺扩大到预装自动模糊软件，并覆盖 AI 生成内容。据 Metro 报道，牵头人之一、工党议员 Jess Phillips 此前已公开要求政治人物立即采取行动，阻止儿童在手机上拍摄和接收裸照。与此同时，据《卫报》报道，英国内政部此前已针对被用于生成儿童性虐待图像的 AI 工具采取措施，因为这些图像被用来勒索儿童并迫使他们进入更严重的受虐情境，这也是本次方案明确把 AI 生成内容纳入拦截范围的原因之一。

**「对设备厂商与隐私的直接影响」** 若该方案最终立法，所有在英国销售手机和平板的厂商都须在设备端默认部署相关检测与模糊功能，并为已售出的旧机型推送强制更新——系统级图像识别将从可选功能变成出厂合规要求。既有的客户端扫描（client-side scanning）研究与政策讨论指出，这类设备端检测可能产生误报、侵蚀隐私，并与端到端加密不兼容，因此开发者和隐私团体很可能要求立法明确检测范围、误报处理方式以及加密通信的豁免条件。由于目前仅是跨党派议员发起的 campaign proposal，上述义务尚未具备法律约束力。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.theguardian.com/technology/2025/feb/01/ai-tools-used-for-child-sexual-abuse-images-targeted-in-home-office-crackdown">AI tools used for child sexual abuse images targeted... | The Guardian</a></li>
<li><a href="https://metro.co.uk/2026/09/04/act-now-block-naked-images-kids-phones-jess-phillips-tells-burnham-29525460/">Act now to block naked images from kids&#x27; phones , Jess Phillips tells...</a></li>
<li><a href="https://bpb-eu-w2.wpmucdn.com/blogs.bristol.ac.uk/dist/1/670/files/2025/01/REPHRAIN-CSS-Policy-Brief-January-2025.pdf">Client-side scanning in private communication: security and ...</a></li>
<li><a href="https://www.webpronews.com/eus-chat-control-client-side-scanning-threatens-end-to-end-encryption/">EU&#x27;s Chat Control: Client-Side Scanning Threatens End-to-End ...</a></li>

</ul>
</details>

**标签**: `#UK tech policy`, `#content moderation`, `#client-side scanning`, `#privacy`, `#AI-generated content`

---

<a id="item-tech-news-9"></a>
### [OpenAI 内部部署控制室系统，35 秒内叫停风险 AI 任务](https://interestingengineering.com/ai-robotics/openai-control-room-35-second-model-shutdown) ⭐️ 7.0/10

据 Interesting Engineering 转述，OpenAI 已在其内部研究设施部署一套“控制室”系统：收到停止指令后，最迟 35 秒阻止有风险的 AI 智能体任务继续获取模型输出。系统用唯一任务 ID 管理训练、评估和数据处理任务，并在推理引擎处理请求之前核验该任务是否仍获准继续。所有前沿强化学习任务还配有独立模型监控器，用于检查模型行为并在发现潜在问题时报警。OpenAI 表示正努力把授权请求缓存造成的延迟降至 0；上述内容来自二次聚合报道，尚无独立验证，也未说明该系统的部署范围。

telegram · zaihuapd · 11月10日 05:47

**「背景」** OpenAI 官方页面将 Control Room 描述为覆盖研究基础设施中各类模型工作负载的中央追踪与停止系统，连接训练和评估中的智能体采样、数据处理等推理任务。该机制与失准监控系统配合，在出现安全或安保担忧时中止模型输出，此次报道中的 35 秒停止时限正是这一机制的具体运行指标。

**「影响」** 对使用该设施的研究任务而言，停止指令发出后仍可能有最多约 35 秒的模型输出窗口，这是当前危害控制的上限。同时每个训练、评估和数据处理任务都必须凭唯一任务 ID 通过推理引擎前的授权检查，未获准的任务会在请求被处理前拒绝；缓存延迟若真能降到 0，授权核验本身就不会成为吞吐瓶颈。报道未提及该系统是否对外部 API 客户或第三方模型开放。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://openai.com/index/control-room/">Control Room: A central system to track and stop model ...</a></li>

</ul>
</details>

**标签**: `#AI safety`, `#OpenAI`, `#AI agents`, `#model monitoring`, `#incident response`

---

<a id="item-tech-news-10"></a>
### [Claude Code 设置文件被曝泄露 2539 个真实凭据](https://www.ithome.com/1/024/888.htm) ⭐️ 7.0/10

据 IT 之家转述安全公司 Apiiro 的发现，1,994 个 GitHub 代码库中暴露了 2,539 个真实凭据，涉及数据库密码和 API Token 等；这些凭据与超过 10 万份被上传至公共仓库的 Claude Code 本地设置文件相关，其中约 1,100 份含机密数据。问题源于 Claude Code 会把获准执行的 Shell 命令写入本地设置文件，若该文件未被 Git 忽略，就会随项目一起提交。团队表示正在研究预防措施，并考虑内置密钥扫描功能，但尚未说明这些措施何时可用。

telegram · zaihuapd · 11月10日 11:20

**「背景」** Claude Code 会将用户点选“不再询问”后获准执行的 Shell 命令写入项目本地的设置文件，作为后续免确认执行的权限记录，因此数据库密码、API Token 等敏感值可能随命令字符串一并落盘。据 The Hacker News 报道，该文件本不应进入版本库：Claude Code 首次在 Git 仓库中写入它时，会把它加入用户机器上的全局 git excludes，使本机所有仓库都忽略该文件。Ars Technica 援引 Apiiro 的说法指出，在许多情况下 Claude Code 会在用户没有输入的情况下自行提交该设置文件的改动，这使上述保护未能阻止文件被推送到公共仓库。

**「用户影响」** 使用 Claude Code 的开发者应立即检查公开仓库中的本地设置文件，将相应文件加入 .gitignore，并轮换任何曾进入 Git 历史的凭据；目前团队仅表示正在研究预防措施并考虑内置密钥扫描，尚无已发布的相关功能可供依赖。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://thehackernews.com/2026/11/claude-codes-dont-ask-again-file.html">Claude Code &#x27;s “Don&#x27;t Ask Again” File Exposes Passwords and Keys in...</a></li>
<li><a href="https://arstechnica.com/ai/2026/11/claude-code-settings-files-expose-thousands-of-secrets-on-github/">Claude Code is accidentally exposing secrets all over GitHub</a></li>

</ul>
</details>

**标签**: `#Claude Code`, `#security`, `#credential leakage`, `#GitHub`, `#AI coding tools`

---

<a id="item-tech-news-11"></a>
### [Anthropic 将 Claude 改为地区白名单，中国大陆及港澳被排除](https://www.anthropic.com/legal/supported-regions) ⭐️ 7.0/10

Anthropic 发布《支持地区政策》，将 Claude.ai、Claude Code、Cowork、API 以及通过云平台和授权经销商提供的 Claude 模型改为白名单制：仅在名单所列的 185 个国家和地区可用，未列入者一律不支持，政策于 11 月 12 日生效。中国大陆、香港、澳门均不在名单内。政策还将限制范围扩大到：人身处不支持地区时使用（包括支持地区公司员工出差）、在不支持地区注册或设总部的实体及其人员，以及被不支持地区主体直接或间接多数持股或控制的公司人员。

telegram · zaihuapd · 11月10日 13:44

**「背景」** 白名单制是一种“默认不允许”的合规安排：只有被明确列入支持名单的国家和地区才能使用服务，未列入者一律不支持，而不是仅对少数被制裁地区设限。Anthropic 这份名单还把人员实际所在地、实体注册地或总部所在地，以及被不支持地区主体直接或间接持股或控制的情况纳入判断，因此合规范围不只看访问入口。

**「影响」** 受影响的企业和开发者不能只依据账号注册地判断合规，还需核查员工是否会前往不支持地区，以及公司是否被不支持地区主体多数持股或控制；否则相关使用会落入政策规定的违规范围。

**标签**: `#Anthropic`, `#Claude`, `#AI policy`, `#regional restrictions`, `#compliance`

---

<a id="item-tech-news-12"></a>
### [稀宇科技开源 MiniMax H3 Image，4K 生成约 10 秒](https://huggingface.co/MiniMaxAI/MiniMax-H3-Image) ⭐️ 7.0/10

稀宇科技发布 MiniMax H3 Image 图像模型并开放权重，支持文生图、图像参考和图像编辑，官方称可在约 10 秒内生成 4096×4096（约 1600 万像素）的 4K 图像，最多接受 16 张参考图输入，重点改进复杂指令理解、多图参考和画面细节。同步推出的 Highspeed 高速版据官方说法，标准模式速度约为主流工具的 1.5 至 2 倍，高速模式为 3 至 4 倍。模型已上线 Hugging Face 与开放平台 API，并接入 MiniMax Code、海螺等产品；标准版 4K 单张约 0.069 美元，发布首周优惠价约 0.034 美元。上述速度与画质均为厂商说法，来源未提供独立基准测试或技术细节。

telegram · zaihuapd · 11月10日 15:39

**「背景」** 开放权重意味着模型参数可下载并自行部署，调用方能在本地或自有算力上运行，而不必完全依赖厂商的托管接口。此次 MiniMax H3 Image 同时开放 Hugging Face 权重并提供 API，因此覆盖自托管和托管调用两类使用方式。

**「影响」** 开放权重让开发者可以在自建环境部署，或改用按张计费的 API（标准 4K 约 0.069 美元、首周约 0.034 美元），但来源未披露模型规模与显存需求，本地部署的实际门槛仍不明确。

**标签**: `#open-weight models`, `#image generation`, `#MiniMax`, `#4K generation`, `#model release`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [Polymarket 称年化收入突破 18 亿美元](https://www.cnbc.com/2026/11/10/polymarket-annualized-revenue-us-growth.html) ⭐️ 7.0/10

预测市场平台 Polymarket 于 11 月 10 日（周二）向 CNBC 表示，其年化收入已超过 18 亿美元，高于该公司 6 月披露的逾 10 亿美元年化收入运行率。公司称，增长主要来自 5 月上线的美国交易所：据数据平台 TickerTracker 统计，该交易所 10 月名义成交额超过 145 亿美元，而 6 月为 40 亿美元。

rss · CNBC Finance · 11月10日 13:00

**「背景」** Polymarket 是一个让用户就事件结果买卖“是/否”合约的预测市场平台；其国际平台与今年 5 月推出的美国交易所分开运营，美国这类合约由商品期货交易委员会（CFTC）监管。CFTC 此前已对该公司展开广泛调查，涉及广告做法，以及该公司是否违反和解协议、让美国居民使用其国际平台。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.politico.com/news/2026/06/26/cftc-investigation-prediction-market-polymarket-00978218">Wall Street regulator investigating prediction market giant Polymarket</a></li>
<li><a href="https://www.swrnn.com/polymarket-alternative">Polymarket Alternative: Which Rail Blocked You?</a></li>

</ul>
</details>

**标签**: `#Polymarket`, `#prediction markets`, `#revenue growth`, `#CFTC investigation`, `#funding valuation`

---

<a id="item-finance-news-2"></a>
### [美联储理事沃勒倾向 12 月加息，称不排除 50 个基点](https://www.cnbc.com/2026/11/10/fed-governor-waller-sees-december-hike-likely.html) ⭐️ 7.0/10

美联储理事克里斯托弗·沃勒 11 月 10 日在伦敦表示，他“倾向于”在 12 月会议上加息，并称如果通胀数据高于预期，就应考虑加息 50 个基点。当日公布的 10 月消费者价格指数（CPI）环比上涨 0.4%、核心 CPI 上涨 0.3%，均比道琼斯共识高出 0.1 个百分点；交易员随后完全消化了 12 月加息 25 个基点的预期，对加息 50 个基点的定价概率为 12.5%。

rss · CNBC Finance · 11月10日 17:13

**「背景」** 负责制定利率的联邦公开市场委员会（FOMC）在 10 月会议上决定暂不加息，称需要积累更多信息，但该决定并非一致通过——理事库克和克利夫兰联储主席哈马克投了反对票；此前 9 月已加息 25 个基点。

**「影响」** 若美联储 12 月加息、甚至考虑 50 个基点，美国国债市场已经出现抛售：2 年期国债收益率（反映政策预期）录得 2025 年 4 月初以来最大单日升幅，这将使与短期利率挂钩的房贷和企业借贷成本面临上行压力。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.reuters.com/business/finance/investors-boost-odds-half-point-fed-hike-core-cpi-rise-meets-wallers-bar-2026-11-10/">Fed officials open door to a half-percentage-point rate hike ...</a></li>

</ul>
</details>

**标签**: `#Federal Reserve`, `#monetary policy`, `#interest rates`, `#inflation`, `#central bank communication`

---

<a id="item-finance-news-3"></a>
### [前三季度中国新能源乘用车出口同比增长 138.8%](https://finance.sina.com.cn/tech/roll/2026-10-26/doc-iniwpfnc2438186.shtml) ⭐️ 7.0/10

2026 年前三季度，中国新能源乘用车出口 388.7 万辆，同比增长 138.8%；同期国内零售量为 775.8 万辆，同比下降 12.8%。9 月国内新能源乘用车零售同比下降 16.7%，燃油车下降 43%，文章将需求走弱与购车补贴、购置税优惠调整及去年同期基数较高联系起来。

telegram · zaihuapd · 11月10日 02:56

**「背景」** 新能源车（含纯电动、插电混动和燃料电池车）此前可享受购置税免征等优惠；有媒体报道，多项购车激励从 2026 年起逐步退出。文章把国内零售走弱部分归因于补贴和购置税优惠调整，以及去年同期销量基数较高。

**「影响」** 出口增长已成为车企销量增长的重要支撑，国内零售走弱意味着依赖内销的车企更难依靠本土市场实现销量增长。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Plug-in_electric_vehicles_in_China">Plug-in electric vehicles in China - Wikipedia</a></li>
<li><a href="https://eu.36kr.com/en/p/3487553464277125">Is It the Final Frenzy of New Energy Vehicles ? The Economics of...</a></li>

</ul>
</details>

**标签**: `#China auto sector`, `#NEV exports`, `#domestic demand`, `#passenger vehicle sales`, `#subsidy and tax incentives`

---

<a id="item-finance-news-4"></a>
### [加州 5%亿万富翁税公投未获通过](https://www.theguardian.com/us-news/2026/nov/09/california-tax-billionaires-prop-40) ⭐️ 7.0/10

加州选民否决了第 40 号提案，该提案拟对截至 2026 年 1 月净资产超过 10 亿美元者一次性征收 5%的税，税款用于医疗、教育和食品援助。反对阵营共投入近 4.25 亿美元，成为该州史上最贵的反对阵营竞选，其中谷歌联合创始人布林个人捐出至少 1.32 亿美元。

telegram · zaihuapd · 11月10日 07:12

**「背景」** 加州实行公民发起的公投制度，第 40 号提案由支持者推动列入选票，拟对净资产（含股票等资产）超过 10 亿美元者一次性征税，收入用于医疗、教育和食品援助。该提案在民主党内立场分裂：加州民主党表态支持，而州长纽森及两党州长候选人均表示反对。

**「影响」** 若提案通过，加州约 250 名亿万富翁本应在 2027 年就其在 2026 年 1 月 1 日的净资缴纳一次性 5% 税，这笔收入原定用于医疗、教育和食品援助；公投否决意味着这些潜在税收不再产生，相关公共服务也失去了这一资金来源。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.nytimes.com/2026/11/09/us/california-billionaire-tax-prop-40.html">California Voters Reject Prop. 40 Billionaire Tax Measure</a></li>
<li><a href="https://www.bbc.com/news/articles/cq398em3032wo">Californians reject Prop 40 wealth tax for billionaires</a></li>
<li><a href="https://lao.ca.gov/BallotAnalysis/Proposition?number=40&amp;year=2026">Proposition 40 [Ballot]</a></li>
<li><a href="https://www.nytimes.com/interactive/2026/10/13/magazine/billionaire-wealth-tax-proposition-40.html">A Look at California &#x27;s Billionaires vs. the Rest of the World - The New...</a></li>

</ul>
</details>

**标签**: `#California tax policy`, `#wealth tax`, `#Proposition 40`, `#campaign finance`, `#tech billionaires`

---