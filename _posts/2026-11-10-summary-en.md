---
layout: default
title: "Horizon Summary: 2026-11-10 (EN)"
date: 2026-11-10
lang: en
---

> From 48 items, 16 important content pieces were selected

---

**Technology News**
1. [Microsoft Highlights .NET 11 Runtime Async and Compatibility Changes](#item-tech-news-1) ⭐️ 8.0/10
2. [Chips and Cheese Analyzes AMD Zen 6 Core, CCD, and I/O Changes](#item-tech-news-2) ⭐️ 8.0/10
3. [DeepMind Introduces AlphaProof Code for Formal Verification](#item-tech-news-3) ⭐️ 8.0/10
4. [Blender 5.3 ships native Gaussian Splat support and geometry-node bundles](#item-tech-news-4) ⭐️ 8.0/10
5. [Fireworks confirms new breach exposing customer billing data, model weights and datasets](#item-tech-news-5) ⭐️ 8.0/10
6. [Synaptics patent claims halt open-source DisplayLink driver work](#item-tech-news-6) ⭐️ 7.0/10
7. [Chrome&\#x27;s Modern Web Guidance 1.0 ships agent skill and CLI](#item-tech-news-7) ⭐️ 7.0/10
8. [UK cross-party campaign seeks mandatory child abuse image blocking on phones](#item-tech-news-8) ⭐️ 7.0/10
9. [OpenAI Control Room Can Halt Risky AI Tasks in 35 Seconds](#item-tech-news-9) ⭐️ 7.0/10
10. [Apiiro reports 2,539 credentials leaked via Claude Code settings](#item-tech-news-10) ⭐️ 7.0/10
11. [Anthropic adopts Claude whitelist excluding mainland China, Hong Kong, Macau from Nov. 12](#item-tech-news-11) ⭐️ 7.0/10
12. [MiniMax open-sources H3 Image for 4K generation in about 10 seconds](#item-tech-news-12) ⭐️ 7.0/10

**Financial News**
1. [Polymarket says annualized revenue passed $1.8 billion](#item-finance-news-1) ⭐️ 7.0/10
2. [Fed&\#x27;s Waller leans toward December rate hike, floats half-point move](#item-finance-news-2) ⭐️ 7.0/10
3. [China NEV passenger vehicle exports rose 138.8% in first three quarters](#item-finance-news-3) ⭐️ 7.0/10
4. [California voters reject 5% one-time tax on billionaires](#item-finance-news-4) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Microsoft Highlights .NET 11 Runtime Async and Compatibility Changes](https://learn.microsoft.com/en-us/dotnet/core/whats-new/dotnet-11/runtime) ⭐️ 8.0/10

Microsoft&\#x27;s .NET 11 runtime announcement highlights runtime async support and compatibility changes for .NET developers. The supplied material does not include benchmark results or a complete list of breaking changes, so the performance impact and migration scope remain unverified.

hackernews · stevefan1999 · Nov 10, 12:20 · [Discussion](https://news.ycombinator.com/item?id=50439284)

**「Earlier previews」** Earlier .NET 11 previews built up the runtime-async feature: Preview 5 added OSR async resume into optimized code, and Preview 6 added JIT async support. By later previews, runtime-native async no longer required an explicit preview-feature switch in net11.0 projects, and some ASP.NET Core shared-framework libraries were already compiled with runtime async.

**「Older CPUs blocked」** Organizations running .NET workloads on older hardware must verify CPU instruction-set support before upgrading: Microsoft says .NET 11 will fail to run on CPUs missing one or more baseline instruction sets and will print a diagnostic message.

**「Community Discussion」** Hacker News commenters said C\#/.NET remains underappreciated because of legacy perceptions—especially the belief that .NET is Windows-only or stuck at .NET Framework—while praising day-to-day backend work. One commenter welcomed the runtime async work but was surprised equivalent performance was possible, and another flagged a reported change in \`\(decimal\)0.1\` output between .NET 10 and .NET 11.

<details><summary>References</summary>
<ul>
<li><a href="https://www.youngju.dev/blog/2026-07-16-dotnet-11-runtime-async">NET 11 runtime - async — async 상태 머신을 컴파일러에서...</a></li>
<li><a href="https://blog.balta.io/dotnet-11-preview-5-novidades-do-runtime/">NET 11 Preview 5: todas as novidades do runtime - balta</a></li>
<li><a href="https://zhangxihai.cn/archives/dotnet-11-new-features-sts-lts-analysis">NET 11 新特性分析：值得升级吗？ 非 LTS...</a></li>
<li><a href="https://learn.microsoft.com/en-us/dotnet/core/whats-new/dotnet-11/runtime">What&#x27;s new in . NET 11 runtime | Microsoft Learn</a></li>

</ul>
</details>

**Tags**: `#.NET 11`, `#C\#`, `#runtime`, `#async`, `#breaking changes`

---

<a id="item-tech-news-2"></a>
### [Chips and Cheese Analyzes AMD Zen 6 Core, CCD, and I/O Changes](https://chipsandcheese.com/p/amds-zen-6-family-feeding-the-beast) ⭐️ 8.0/10

Chips and Cheese published a technical analysis of AMD&\#x27;s Zen 6 CPU family, covering execution-unit changes, branch prediction, memory and I/O chiplets, and how cores are grouped into CCDs. Details quoted from the article in the discussion thread include a reduction in integer multiply units from three to two and PDEP/PEXT throughput falling from three instructions per cycle to two, alongside four vector loads per cycle at 256 bits or narrower. Commenters reading the piece also point to 32 cores per CCD, and to 32 &quot;C&quot; cores per chiplet with increased L3 cache. The piece is an architecture analysis of an upcoming family, not a product launch, so specifications, pricing, and availability remain unconfirmed.

hackernews · pixelpoet · Nov 10, 17:02 · [Discussion](https://news.ycombinator.com/item?id=50443090)

**「Background」** Zen 6 follows Zen 5, which Chips and Cheese had measured as having the strongest branch-direction predictor of any core it tested; the Zen 6 analysis says AMD kept that predictor and changed how the core behaves when it is overwhelmed. AMD&\#x27;s Zen 4 generation already paired N5 compute chiplets with separate N6 I/O dies, the split that frames current questions about Zen 6&\#x27;s CCD and I/O organization.

**「What Shrinks Mean in Practice」** The execution-unit cuts are narrow but specific: software that leans on integer multiply or on PDEP/PEXT bit-manipulation instructions — common in compression, hashing, and parsing code — would see lower peak throughput on those paths if the two-per-cycle figures hold, even as vector load capacity increases. Whether the multiplier and bit-manipulation reductions share circuitry is unresolved in the discussion, which matters for judging how broad the regression would be.

**「From the Comments」** Commenters pressed on whether PDEP/PEXT use the same circuits as the integer multipliers or are independent cuts, with one noting the operations are quite different and the article&\#x27;s wording ambiguous. A separate thread questioned how 32 cores in a single CCD are organized below that level and whether buyers must manage all 32 at the lowest NUMA tier. The most anticipated change, for one commenter, is a new I/O chiplet on a smaller node; they reported that Zen 4/5 AM5 memory controllers are extremely hard to push past 3600 MT/s with both channels populated, while flagging that the new chiplet is something they had heard rather than something confirmed.

<details><summary>References</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Zen_4">Zen 4 - Wikipedia</a></li>
<li><a href="https://chipsandcheese.com/p/amds-zen-6-family-feeding-the-beast">AMD ’s Zen 6 Family: Feeding the Beast - by George Cozma</a></li>

</ul>
</details>

**Tags**: `#AMD Zen 6`, `#CPU architecture`, `#hardware`, `#memory controller`, `#branch prediction`

---

<a id="item-tech-news-3"></a>
### [DeepMind Introduces AlphaProof Code for Formal Verification](https://deepmind.google/blog/introducing-alphaproof-code/) ⭐️ 8.0/10

DeepMind introduced AlphaProof Code, an AI system for formal code verification aimed at developers working with proof assistants such as Lean and Rocq. The supplied material presents this as an announcement, without version, availability, compatibility, or independent evaluation details, and the strongest claims remain contested. Hacker News discussion focused on whether the system verifies implementation properties rather than specifications and whether a reported clean verification reflects broad correctness or narrow theorems.

hackernews · ilreb · Nov 10, 12:11 · [Discussion](https://news.ycombinator.com/item?id=50439193)

**「Background」** Formal verification checks that software satisfies a mathematical specification, and machine-code-level verification targets the compiled binary rather than only the source. DeepMind describes AlphaProof Code as a multi-LLM agentic framework in which human experts decide what to prove and AI agents carry out the verification work; an accompanying report says the framework was used to prove key security properties of libsignal, Signal&\#x27;s reference implementation, at the machine-code level.

**「Impact」** Developers evaluating AlphaProof Code would still need to inspect the theorem statements and specification coverage, because a successful Lean or Rocq proof establishes only what the encoded theorem states, not that it captures the intended behavior.

**「Community Discussion」** Commenters debated whether the proof agent challenges the specification or only the implementation, with one saying it otherwise resembles a classic coding agent that iterates over a codebase while writing Lean or Rocq. Others warned that AI-written proofs can encode weak or misguided theorems, and that a zero-bug result may reflect narrow properties rather than the absence of real defects.

<details><summary>References</summary>
<ul>
<li><a href="https://google-deepmind.github.io/code-verification/">AlphaProof Code : Verifying Signal’s Security at the Machine- Code ...</a></li>
<li><a href="https://deepmind.google/blog/introducing-alphaproof-code/">Formal Verification of Signal’s Protocol with... — Google DeepMind</a></li>

</ul>
</details>

**Tags**: `#AI for formal verification`, `#proof assistants`, `#Lean`, `#Rocq`, `#software correctness`

---

<a id="item-tech-news-4"></a>
### [Blender 5.3 ships native Gaussian Splat support and geometry-node bundles](https://www.blender.org/download/releases/5-3/) ⭐️ 8.0/10

Blender 5.3 has been released with built-in Gaussian Splat support and geometry-node bundle features. The release targets 3D and VFX workflows, where native splat handling and the expanded geometry-node system are the main points of interest. The supplied announcement does not detail supported splat formats, renderer integration, or performance limits, so those specifics remain unconfirmed.

hackernews · amlib · Nov 10, 16:15 · [Discussion](https://news.ycombinator.com/item?id=50442426)

**「Background」** Gaussian splatting represents a captured scene as millions of oriented, semi-transparent 3D blobs rather than a polygon mesh, reconstructing it from photographs and rendering by projecting and blending those splats — which is why users discuss scene size in splat counts. Blender is an open-source 3D suite whose geometry-nodes system offers a visual, node-based alternative to scripting; this release makes splat handling native to the application instead of dependent on outside tooling.

**「Impact」** For artists and pipeline developers, the practical change is that Gaussian-splat scenes and bundle-based geometry-node setups are now part of Blender&\#x27;s native toolset. Teams should test large-scene performance and existing node-graph compatibility on their own hardware before production adoption.

**「Community discussion」** Commenters singled out geometry-node bundles as a major workflow improvement, with one saying alpha builds made complex pipelines easier once the list-and-closure model clicked. Another reported that a 4-million-splat scene ran fast and felt mature in the beta on an M4, while a separate commenter wondered whether triangle splatting would be a better fit for GPU-native rendering.

**Tags**: `#Blender`, `#Gaussian Splatting`, `#3D graphics`, `#open source`, `#geometry nodes`

---

<a id="item-tech-news-5"></a>
### [Fireworks confirms new breach exposing customer billing data, model weights and datasets](https://finance.sina.com.cn/stock/usstock/c/2026-11-10/doc-iniyfzhx2605532.shtml) ⭐️ 8.0/10

Fireworks confirmed a new cyberattack in which some customer billing information, model weights, and datasets were exposed, and said it is investigating jointly with Palo Alto Networks&\#x27; Unit 42. It remains unclear whether customers and end users beyond those already identified were affected; Harvey stated that its own customer data was not impacted. People familiar with the matter said some large customers paying millions of dollars a year are considering migrating away from the AI infrastructure provider. The incident comes as Fireworks, which reached $1 billion in annualized revenue in July, had reportedly planned to open a new funding round this week at a valuation of at least $30 billion.

telegram · zaihuapd · Nov 10, 13:00

**「Background」** Fireworks AI is an inference-cloud provider founded by former Meta PyTorch lead Lin Qiao; it does not train a frontier model of its own. It raised a $1.505 billion round at a $17.5 billion valuation in July 2026, and reporting at that time said its annualized revenue had crossed $1 billion. The current report describes a &quot;new&quot; attack but does not identify the earlier incident.

**「Impact」** Customers should treat billing details held by Fireworks as compromised and scrutinize invoices and payment records for unauthorized changes, while organizations that trained proprietary models on the platform face a separate exposure risk because model weights and datasets were among the reported leak categories. The reported willingness of seven-figure customers to migrate shows the breach is already being weighed as a vendor-risk decision, not just a security ticket.

<details><summary>References</summary>
<ul>
<li><a href="https://letsdatascience.com/blog/fireworks-ai-raises-1-5-billion-betting-against-big-ai-labs">Fireworks AI Raises $1.5 Billion at $17.5 Billion Valuation</a></li>
<li><a href="https://lanceum.com/startups/fireworks-ai-1-5b-series-d-17-5b-valuation">Fireworks AI Raises $1.5B at $17.5B Valuation as... | Lanceum</a></li>

</ul>
</details>

**Tags**: `#AI security`, `#data breach`, `#Fireworks AI`, `#model weights`, `#cloud infrastructure`

---

<a id="item-tech-news-6"></a>
### [Synaptics patent claims halt open-source DisplayLink driver work](https://lwn.net/SubscriberLink/1102549/acbc92e00cee3a3f/) ⭐️ 7.0/10

Work on open-source DisplayLink drivers has stopped after Synaptics asserted patent claims, according to an LWN report. The halt affects developers maintaining the drivers and users who rely on them for display connectivity, and it raises questions about reverse engineering, open-source licensing, and patent enforcement. The supplied account does not detail the specific patents, the scope of the claims, or a timeline for resolving the dispute.

hackernews · speckx · Nov 10, 18:02 · [Discussion](https://news.ycombinator.com/item?id=50443824)

**「Background」** DisplayLink is Synaptics&\#x27; USB graphics technology for driving displays through a dock, adapter, or monitor, and Synaptics distributes the drivers for the DisplayLink chipsets used in those products. Before the current dispute, a hobbyist&\#x27;s open-source DisplayLink driver — reportedly developed in Rust with AI assistance — drew a cease-and-desist from Synaptics and then disappeared amid legal threats.

**「Impact」** Developers contributing to open-source DisplayLink support face a work stoppage and legal risk, so any resumption would require assessing patent exposure, not just technical maintenance. For users, that leaves the open-source driver path for DisplayLink docks uncertain while the patent claims remain unresolved.

**「Community discussion」** Commenters questioned a quoted demand for US$25,000 in documentation costs, arguing that patent owners bear the burden of proving infringement and that reverse engineering concerns patent disclosure rather than patent violation; others said such a claim would more properly be a trade-secret issue. One commenter claimed DisplayLink is losing ground because of high DDR prices and dock vendors cancelling portfolios, while another reported audio problems with a DisplayLink dock at work.

<details><summary>References</summary>
<ul>
<li><a href="https://www.tomshardware.com/peripherals/docking-stations-hubs/synaptics-sends-cease-and-desist-order-to-creator-of-open-source-displaylink-driver-dares-him-to-publicize-its-threats-dev-reverse-engineers-displaylink-using-claude-ai-and-rust-synaptics-threatens-to-bill-creator-for-legal-documentation">Synaptics sends cease-and-desist order to creator of open - source ...</a></li>
<li><a href="https://www.phoronix.com/news/Synaptics-Blocks-Vino-Driver">Synaptics Appears To Use Legal Threats To Block Open - Source ...</a></li>
<li><a href="https://www.synaptics.com/products/displaylink-graphics/downloads/windows">Windows Driver Downloads for Downloads Section | Synaptics</a></li>

</ul>
</details>

**Tags**: `#open-source`, `#patents`, `#hardware drivers`, `#DisplayLink`, `#legal issues`

---

<a id="item-tech-news-7"></a>
### [Chrome&\#x27;s Modern Web Guidance 1.0 ships agent skill and CLI](https://github.com/GoogleChrome/modern-web-guidance) ⭐️ 7.0/10

Google Chrome has released Modern Web Guidance 1.0, an open-source agent skill and CLI that gives coding agents 200+ hand-curated guides \(~1.7 MB\) on native web platform features such as \`&lt;dialog&gt;\`, \`field-sizing\`, and \`CSS.highlights\`, developed in collaboration with Firefox, MDN, and Edge. It installs via \`npx modern-web-guidance@latest install\` and includes a search command and a deterministic \`legacy-scan\` for spotting older patterns, trained on 30,000 GitHub repositories; the team reports 92% average precision on held-out repos. Chrome also says its evaluation of 200 tasks across Codex, Claude, and agy rose from 55% pass unguided to 92% with the skill, using about 1,700 Playwright/AST assertions. The search package is a roughly 7 MB pure-JS build with about 10 ms search on CPU, according to the release.

hackernews · paulirish · Nov 10, 18:01 · [Discussion](https://news.ycombinator.com/item?id=50443812)

**「Why agents need modern web guidance」** Modern browser APIs such as \`&lt;dialog&gt;\`, \`CSS.highlights\`, and \`field-sizing\` replace patterns that previously required JavaScript or dependencies. Coding agents may recognize some of these APIs by name but still default to incumbent \`&lt;div&gt;\`-plus-JavaScript implementations, creating a gap that the guidance project aims to fill at agent runtime.

**「Impact」** Teams targeting multiple browsers need to check each recommendation against their support matrix: a community commenter lists features such as \`CSS @function\`, \`calc-size\(\)\`, and \`corner-shape\` as stable in Chrome but unsupported in Firefox and Safari, so the agent&\#x27;s suggestions still require per-target review.

**「Community discussion」** One commenter argued that Chrome already has outsized influence in browser standards, warning that LLMs trained on Chrome&\#x27;s guidance could reinforce dominant-browser web development. Another suggested publishing a grep-friendly Markdown index on GitHub Pages so agents can fetch the guidance over HTTP without installing anything.

**Tags**: `#web platform`, `#coding agents`, `#browser standards`, `#developer tooling`, `#open source`

---

<a id="item-tech-news-8"></a>
### [UK cross-party campaign seeks mandatory child abuse image blocking on phones](https://observer.co.uk/news/national/article/fight-to-block-child-sexual-abuse-images-unites-peers-and-mps-in-cross-party-campaign) ⭐️ 7.0/10

A cross-party group of UK MPs and peers is campaigning for legislation that would require all phones and tablets sold in the country to ship with software that automatically blurs child sexual abuse images and videos, including AI-generated material, and prevents related live streams. Older devices would be covered through forced updates. The campaign is led by Conservative peer John Nash and Labour former children&\#x27;s minister Jess Phillips; the government has separately promised legislation requiring Apple and Google to stop children from taking or sharing nude images. The proposal has not been enacted.

telegram · zaihuapd · Nov 10, 05:11

**「背景」** 该方案建立在政府此前的承诺之上：政府已表示将立法，要求苹果和谷歌阻止儿童拍摄和分享裸照。Jess Phillips 多年来一直就该议题开展活动；据 Metro 报道，她于 2026 年 9 月公开敦促 Andy Burnham 采取行动，阻止儿童在手机上拍摄和接收裸照。据《卫报》报道，内政部已在 2025 年 2 月将用于生成儿童性虐待图像的 AI 工具列为打击对象，因为这些新生成的图像被用来敲诈儿童。

**「Impact」** If enacted, the proposal would require Apple, Google and other device makers to build on-device detection and blurring into every phone and tablet sold in the UK, and to keep older devices updateable so the filtering can be added after purchase. Vendors would then face a concrete design trade-off: critics of client-side scanning argue the technique can erode privacy and end-to-end encryption, so companies would need to show the blocking works without turning devices into general-purpose monitoring tools.

<details><summary>References</summary>
<ul>
<li><a href="https://www.theguardian.com/technology/2025/feb/01/ai-tools-used-for-child-sexual-abuse-images-targeted-in-home-office-crackdown">AI tools used for child sexual abuse images targeted... | The Guardian</a></li>
<li><a href="https://metro.co.uk/2026/09/04/act-now-block-naked-images-kids-phones-jess-phillips-tells-burnham-29525460/">Act now to block naked images from kids&#x27; phones , Jess Phillips tells...</a></li>
<li><a href="https://bpb-eu-w2.wpmucdn.com/blogs.bristol.ac.uk/dist/1/670/files/2025/01/REPHRAIN-CSS-Policy-Brief-January-2025.pdf">Client-side scanning in private communication: security and ...</a></li>
<li><a href="https://www.webpronews.com/eus-chat-control-client-side-scanning-threatens-end-to-end-encryption/">EU&#x27;s Chat Control: Client-Side Scanning Threatens End-to-End ...</a></li>

</ul>
</details>

**Tags**: `#UK tech policy`, `#content moderation`, `#client-side scanning`, `#privacy`, `#AI-generated content`

---

<a id="item-tech-news-9"></a>
### [OpenAI Control Room Can Halt Risky AI Tasks in 35 Seconds](https://interestingengineering.com/ai-robotics/openai-control-room-35-second-model-shutdown) ⭐️ 7.0/10

OpenAI has reportedly deployed an internal &quot;control room&quot; at its research facilities that can stop a risky AI-agent task from receiving further model output within 35 seconds of a stop command. The system tracks training, evaluation, and data-processing jobs by unique task ID and checks whether a job is still authorized before the inference engine handles a request. All frontier reinforcement-learning tasks are also assigned an independent model monitor that watches behavior and raises alerts; OpenAI is working to reduce authorization-request caching delay to zero.

telegram · zaihuapd · Nov 10, 05:47

**「Background」** OpenAI describes its Control Room as a central system for tracking model workloads across research infrastructure and stopping them when safety or security concerns arise, covering agentic sampling for training and evaluation, data processing, and other research inference work \[tool-1-1\]. OpenAI says the system works alongside its misalignment monitoring systems, which provides the context for the task-level authorization and independent model monitors described in the report \[tool-1-1\].

**「Impact」** For operators of frontier reinforcement-learning or agent workloads, the reported system ties stopping to per-task authorization, so each job must be identifiable and its approval state current before inference requests are served. OpenAI says it is working to reduce authorization-cache delay to zero, a step that would make the 35-second limit less dependent on cached approvals.

<details><summary>References</summary>
<ul>
<li><a href="https://openai.com/index/control-room/">Control Room: A central system to track and stop model ...</a></li>

</ul>
</details>

**Tags**: `#AI safety`, `#OpenAI`, `#AI agents`, `#model monitoring`, `#incident response`

---

<a id="item-tech-news-10"></a>
### [Apiiro reports 2,539 credentials leaked via Claude Code settings](https://www.ithome.com/1/024/888.htm) ⭐️ 7.0/10

Security firm Apiiro reportedly found 2,539 real credentials, including database passwords and API tokens, in 1,994 public GitHub repositories. The exposure is linked to more than 100,000 uploaded Claude Code local settings files, about 1,100 of which contained secrets. According to the report, Claude Code writes approved shell commands into local settings files, which can be committed with a project if they are not excluded by Git. The Claude Code team says it is studying preventive measures and considering built-in secret scanning, but no shipped fix or scanning feature is described.

telegram · zaihuapd · Nov 10, 11:20

**「Background」** Claude Code&\#x27;s &quot;Don&\#x27;t ask again&quot; option records approved shell commands in a local settings file, which is how credentials can end up stored alongside project configuration. Its documentation says Claude Code adds that file to the user&\#x27;s global Git excludes the first time it writes it in a repository, but Ars Technica reported that Claude Code can still commit the settings file without user input.

**「Impact」** Users of Claude Code should check repositories and commit history for local settings files and rotate any exposed database passwords or API tokens. Because built-in secret scanning is only under consideration, current protection depends on Git ignore rules and separate secret-scanning tools.

<details><summary>References</summary>
<ul>
<li><a href="https://thehackernews.com/2026/11/claude-codes-dont-ask-again-file.html">Claude Code &#x27;s “Don&#x27;t Ask Again” File Exposes Passwords and Keys in...</a></li>
<li><a href="https://arstechnica.com/ai/2026/11/claude-code-settings-files-expose-thousands-of-secrets-on-github/">Claude Code is accidentally exposing secrets all over GitHub</a></li>

</ul>
</details>

**Tags**: `#Claude Code`, `#security`, `#credential leakage`, `#GitHub`, `#AI coding tools`

---

<a id="item-tech-news-11"></a>
### [Anthropic adopts Claude whitelist excluding mainland China, Hong Kong, Macau from Nov. 12](https://www.anthropic.com/legal/supported-regions) ⭐️ 7.0/10

Anthropic published a supported-regions policy that makes Claude available only in 185 listed countries and regions, effective November 12; mainland China, Hong Kong, and Macau are not included. The policy covers Claude.ai, Claude Code, Cowork, the API, and Claude models offered through cloud platforms and authorized resellers, and states that unlisted locations are unsupported. It also prohibits use by people physically in unsupported regions—including employees of supported-region companies traveling there—and by entities registered or headquartered in unsupported regions or majority-owned or controlled by such entities, regardless of where the individual user is located.

telegram · zaihuapd · Nov 10, 13:44

**「Background」** A supported-regions whitelist means a country or territory must be explicitly listed for Claude access; jurisdictions not on the list are treated as unsupported rather than as unaddressed exceptions. The policy counts dependent and affiliated territories with their parent country, for example treating Puerto Rico as part of the United States.

**「Impact」** Affected organizations must screen corporate ownership and employee travel as well as account location: a user in a supported country can still be barred if their company is majority-owned or controlled from an unsupported region, or if they use Claude while traveling in one.

**Tags**: `#Anthropic`, `#Claude`, `#AI policy`, `#regional restrictions`, `#compliance`

---

<a id="item-tech-news-12"></a>
### [MiniMax open-sources H3 Image for 4K generation in about 10 seconds](https://huggingface.co/MiniMaxAI/MiniMax-H3-Image) ⭐️ 7.0/10

MiniMax released open weights for MiniMax H3 Image, a model for text-to-image generation, image referencing and editing. The company says it can produce 4096×4096-pixel \(about 16-megapixel\) 4K images in roughly 10 seconds and accepts up to 16 reference images. The model is available on Hugging Face and via MiniMax&\#x27;s API and is integrated into MiniMax Code and Hailuo; standard 4K generation is priced at about $0.069 per image, with a launch-week price of about $0.034. MiniMax also offers a Highspeed mode that it claims is 3–4× faster than mainstream tools, versus 1.5–2× for standard mode, but the announcement provides no independent benchmarks.

telegram · zaihuapd · Nov 10, 15:39

**「Background」** Open-weight image models are distributed as downloadable weights that others can run themselves, whereas hosted APIs provide managed access without local hardware. MiniMax is offering H3 Image through both paths—weights on Hugging Face and an API on its open platform—so teams can choose between self-hosting and a managed service.

**「Impact」** Developers can access the model through the hosted API now or use the released weights, but the supplied announcement does not state hardware requirements or license terms, leaving self-hosting cost and permitted use unresolved.

**Tags**: `#open-weight models`, `#image generation`, `#MiniMax`, `#4K generation`, `#model release`

---

## Financial News

<a id="item-finance-news-1"></a>
### [Polymarket says annualized revenue passed $1.8 billion](https://www.cnbc.com/2026/11/10/polymarket-annualized-revenue-us-growth.html) ⭐️ 7.0/10

Polymarket told CNBC on Tuesday that its annualized revenue has topped $1.8 billion, up from more than $1 billion in June, as notional volume on its U.S. exchange reached $14.5 billion in October versus $4 billion in June, according to TickerTracker data. The company-disclosed revenue figure comes as Polymarket runs a $1 billion funding round at a $21 billion valuation and faces a broad CFTC investigation into its advertising practices and past access by U.S. residents to its international exchange.

rss · CNBC Finance · Nov 10, 13:00

**「Background」** Polymarket is a prediction market where users trade yes/no contracts on whether events will happen, and its U.S. venue is a CFTC-designated exchange separate from its international platform. In June 2026, Politico reported that the Commodity Futures Trading Commission, the main federal regulator for prediction markets, was conducting an &quot;extensive investigation&quot; into the company — the scrutiny it still faces.

**「Impact」** Because Combo event contracts — which work like sportsbooks&\#x27; multi-leg parlays — accounted for more than 70% of volume traded on Sunday, Polymarket&\#x27;s growth puts it in more direct competition with sports betting operators just as regulators weigh how both should be treated.

<details><summary>References</summary>
<ul>
<li><a href="https://www.politico.com/news/2026/06/26/cftc-investigation-prediction-market-polymarket-00978218">Wall Street regulator investigating prediction market giant Polymarket</a></li>
<li><a href="https://www.swrnn.com/polymarket-alternative">Polymarket Alternative: Which Rail Blocked You?</a></li>
<li><a href="https://www.cnbc.com/2026/11/10/polymarket-annualized-revenue-us-growth.html">Polymarket says annualized revenue has topped $ 1 .8 billion</a></li>

</ul>
</details>

**Tags**: `#Polymarket`, `#prediction markets`, `#revenue growth`, `#CFTC investigation`, `#funding valuation`

---

<a id="item-finance-news-2"></a>
### [Fed&\#x27;s Waller leans toward December rate hike, floats half-point move](https://www.cnbc.com/2026/11/10/fed-governor-waller-sees-december-hike-likely.html) ⭐️ 7.0/10

Federal Reserve Governor Christopher Waller said Tuesday he is leaning toward a December rate increase and would consider a half-point move if inflation runs hotter than forecast. His remarks followed October consumer price data showing a 0.4% headline rise and 0.3% core increase, each 0.1 percentage point above the Dow Jones consensus, after which traders fully priced a quarter-point December hike and 12.5% odds of a half-point move.

rss · CNBC Finance · Nov 10, 17:13

**「Background」** The Fed raised its benchmark rate by a quarter point in September, then left it unchanged at its October meeting, with Governor Lisa Cook and Cleveland Fed President Beth Hammack voting against the hold.

**「Market impact」** The October CPI reading and Waller&\#x27;s remarks drove selling in the U.S. Treasury market, with the 2-year yield — a proxy for Fed policy expectations — rising by the most since early April 2025, while traders fully priced a quarter-point December hike and 12.5% odds of a half-point move, a shift that would feed into borrowing costs tied to short-term rates.

<details><summary>References</summary>
<ul>
<li><a href="https://www.reuters.com/business/finance/investors-boost-odds-half-point-fed-hike-core-cpi-rise-meets-wallers-bar-2026-11-10/">Fed officials open door to a half-percentage-point rate hike ...</a></li>

</ul>
</details>

**Tags**: `#Federal Reserve`, `#monetary policy`, `#interest rates`, `#inflation`, `#central bank communication`

---

<a id="item-finance-news-3"></a>
### [China NEV passenger vehicle exports rose 138.8% in first three quarters](https://finance.sina.com.cn/tech/roll/2026-10-26/doc-iniwpfnc2438186.shtml) ⭐️ 7.0/10

China&\#x27;s new-energy passenger vehicle exports rose 138.8% year on year to 3.887 million units in the first three quarters of 2026, while domestic retail sales fell 12.8% to 7.758 million, according to Sina Finance.

telegram · zaihuapd · Nov 10, 02:56

**「Background」** China’s new energy vehicle market has relied on purchase subsidies and tax breaks, and multiple car-purchase incentives were set to be phased out starting in 2026—one factor the article cites for weaker domestic demand.

**「Impact」** The gap leaves Chinese automakers more reliant on export growth to support overall sales as domestic demand weakens.

<details><summary>References</summary>
<ul>
<li><a href="https://eu.36kr.com/en/p/3487553464277125">Is It the Final Frenzy of New Energy Vehicles ? The Economics of...</a></li>

</ul>
</details>

**Tags**: `#China auto sector`, `#NEV exports`, `#domestic demand`, `#passenger vehicle sales`, `#subsidy and tax incentives`

---

<a id="item-finance-news-4"></a>
### [California voters reject 5% one-time tax on billionaires](https://www.theguardian.com/us-news/2026/nov/09/california-tax-billionaires-prop-40) ⭐️ 7.0/10

California voters rejected Proposition 40, a one-time 5% tax on people with net worth above $1 billion as of January 1, 2026, which would have funded health care, education and food aid. The opposition campaign, led by tech billionaires, spent nearly $425 million — the most expensive opposition campaign in state history, according to The Guardian — including at least $132 million personally from Google co-founder Sergey Brin.

telegram · zaihuapd · Nov 10, 07:12

**「Background」** It was a ballot proposition, so voters decided directly whether to impose a one-time 5% tax on the total net worth—including assets such as shares—of individuals worth more than $1bn as of 1 January 2026, with revenue earmarked for healthcare, education and food aid.

**「Who is affected」** With the levy rejected, roughly 250 California billionaires will not owe the one-time 5% payment that would have been due in 2027, and the health, education and food-assistance programs it was earmarked for do not receive that revenue.

<details><summary>References</summary>
<ul>
<li><a href="https://www.theguardian.com/us-news/2026/nov/09/california-tax-billionaires-prop-40">California voters fail to pass proposed one-time tax on billionaires ...</a></li>
<li><a href="https://www.bbc.com/news/articles/cq398em3032wo">Californians reject Prop 40 wealth tax for billionaires</a></li>
<li><a href="https://lao.ca.gov/BallotAnalysis/Proposition?number=40&amp;year=2026">Proposition 40 [Ballot]</a></li>
<li><a href="https://www.nytimes.com/interactive/2026/10/13/magazine/billionaire-wealth-tax-proposition-40.html">A Look at California &#x27;s Billionaires vs. the Rest of the World - The New...</a></li>

</ul>
</details>

**Tags**: `#California tax policy`, `#wealth tax`, `#Proposition 40`, `#campaign finance`, `#tech billionaires`

---