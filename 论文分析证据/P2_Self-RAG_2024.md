# Self-RAG 论文写作与学术规范证据文件（P2）

> 分析对象：arXiv:2310.11511 **v1**（2023-10-17，PDF 页眉为 "Preprint."，arXiv 上只有 v1）。全文来源：https://arxiv.org/html/2310.11511 与 https://arxiv.org/pdf/2310.11511 （两者对照核对；图表编号以 PDF 为准）。
> ICLR 2024 正式版（OpenReview）可能与 arXiv v1 有措辞差异，本文件只针对 arXiv v1。
> 引文均为原文逐字摘录，每条少于 30 词。"原文未出现"表示在 v1 全文（正文 + 附录）中检索不到。

---

## 1. 基本信息

| 项目 | 内容 | 依据 |
|---|---|---|
| 标题 | Self-RAG: Learning to Retrieve, Generate, and Critique through Self-Reflection | 首页 |
| 作者（5 人） | Akari Asai†, Zeqiu Wu†, Yizhong Wang†§, Avirup Sil‡, Hannaneh Hajishirzi†§ | PDF 首页（注：arXiv HTML 版渲染时漏掉了第一作者姓名，属转换问题） |
| 单位 | †University of Washington；§Allen Institute for AI；‡IBM Research AI | 首页 |
| 发表 | ICLR 2024，**Oral**（ICLR 官网页面 URL 为 iclr.cc/virtual/2024/oral/19736）；OpenReview id = hSyW5go0v8（OpenReview 页面需人机验证，未能打开正文） | [ICLR 2024 Oral 页面](https://iclr.cc/virtual/2024/oral/19736)；[OpenReview](https://openreview.net/forum?id=hSyW5go0v8) |
| 年份 | arXiv 2023-10-17；会议 2024 | arXiv abs 页 |
| 页数 | PDF 共 30 页：正文 p.1–10，Ethical Concerns/致谢/参考文献 p.11–15，附录 p.16–30 | PDF |
| 图表数 | 实际 Figure 1–5、Table 1–12、Algorithm 1–3；但 arXiv 元数据写 "30 pages, 2 figures, 12 tables"，图数与实际不符 | arXiv abs 页 Comments；PDF |
| 代码/模型 | 已公开。摘要脚注 1："Our code and trained models are available at https://selfrag.github.io/." 项目页链接 GitHub `AkariAsai/self-rag`（MIT License，抓取时约 2.4k stars）及 HuggingFace `selfrag/selfrag_llama2_7b`、`selfrag/selfrag_llama2_13b`、数据集 `selfrag/selfrag_train_data` | 摘要脚注 1；[selfrag.github.io](https://selfrag.github.io/)；[GitHub](https://github.com/AkariAsai/self-rag) |
| 引用数 | 未能可靠获取：Semantic Scholar API 返回 429（限流）；OpenAlex 的 arXiv 记录显示 101 次，但该数字只统计了 arXiv 这一条记录，明显偏低，**不建议在展示中引用** | OpenAlex API（2026-11-02 查询） |

---

## 2. 标题

- 原文标题：**"Self-RAG: Learning to Retrieve, Generate, and Critique through Self-Reflection"**
- 英文词数：**9 词**（Self-RAG / Learning / to / Retrieve / Generate / and / Critique / through / Self-Reflection，连字符词计 1 词）
- 结构：**方法名 + 冒号 + 描述性副标题**（"方法名：做什么 + 怎么做"）。

| 标准 | 评价 |
|---|---|
| 准确 | 较准确。副标题的三个动词 Retrieve / Generate / Critique 与第 3 节标题 "Self-Rag: Learning to Retrieve, Generate and Critique" 和 Algorithm 1 的三步（Retrieve / Generate / Critique）一一对应。 |
| 简洁（≤12 词） | 符合，9 词。 |
| 可检索 | 含 Retrieve、Generate、Critique、Self-Reflection 等关键词；但标题里**没有** "language model / LLM" 和 "retrieval-augmented generation" 的全称，只靠 "RAG" 这个缩写承载领域信息。 |
| 无未解释缩写 | **不完全符合**。"RAG" 在标题中没有展开，读者要到摘要第 4 句才看到全称 "Self-Reflective Retrieval-Augmented Generation"。在 NLP 领域 RAG 已是通用缩写，可以接受，但按课程标准属于缺点。 |
| 其他 | 大小写不统一：标题写 "Self-RAG"，正文排版为小型大写 "Self-Rag"（HTML 渲染为 "Self-rag"）。 |

---

## 3. 摘要

### 3.1 原文（逐句粘贴并标注）

摘要共 **8 句、约 199 词**（不含脚注）。第 3、8 句超过 30 词，为满足"每段引文 < 30 词"的要求，拆成两段引用（标 a/b）。完整摘要见 [arXiv abs 页](https://arxiv.org/abs/2310.11511)。

| # | 原句（逐字） | 词数 | 功能 |
|---|---|---|---|
| 1 | "Despite their remarkable capabilities, large language models (LLMs) often produce responses containing factual inaccuracies due to their sole reliance on the parametric knowledge they encapsulate." | 25 | 背景（问题） |
| 2 | "Retrieval-Augmented Generation (RAG), an ad hoc approach that augments LMs with retrieval of relevant knowledge, decreases such issues." | 18 | 背景（已有方案） |
| 3a | "However, indiscriminately retrieving and incorporating a fixed number of retrieved passages, regardless of whether retrieval is necessary, or passages are relevant," | 20 | 不足（挖洞）/ 目的的依据 |
| 3b | "diminishes LM versatility or can lead to unhelpful response generation." | 10 | 同上 |
| 4 | "We introduce a new framework called Self-Reflective Retrieval-Augmented Generation (Self-Rag) that enhances an LM's quality and factuality through retrieval and self-reflection." | 21 | 目的 + 方法（总述） |
| 5 | "Our framework trains a single arbitrary LM that adaptively retrieves passages on-demand, and generates and reflects on retrieved passages and its own generations using special tokens, called reflection tokens." | 29 | 方法 |
| 6 | "Generating reflection tokens makes the LM controllable during the inference phase, enabling it to tailor its behavior to diverse task requirements." | 21 | 方法（特性） |
| 7 | "Experiments show that Self-Rag (7B and 13B parameters) significantly outperforms state-of-the-art LLMs and retrieval-augmented models on a diverse set of tasks." | 21 | 结果 |
| 8a | "Specifically, Self-Rag outperforms ChatGPT and retrieval-augmented Llama2-chat on Open-domain QA, reasoning and fact verification tasks," | 16 | 结果 |
| 8b | "and it shows significant gains in improving factuality and citation accuracy for long-form generations relative to these models." | 17 | 结果 |

脚注 1（挂在摘要末尾）："Our code and trained models are available at https://selfrag.github.io/."

### 3.2 分析

- **结构**：背景（1–2）→ 不足（3）→ 目的/方法（4–6）→ 结果（7–8）。**没有单独的结论句**，摘要以结果句收尾，没有说明意义或启示。
- **结果是否量化**：**只有定性描述，没有任何数字**。唯一的数字 "7B and 13B" 是模型规模，不是结果。摘要没有给出任何准确率、FactScore 或引用精度的提升幅度（这些数字只在 Table 2 中）。
- **引用/图表**：摘要中无文献引用、无图表引用；只有一个脚注（代码链接）。
- **夸大/强势用语**：
  - "a **new** framework"（第 4 句）
  - "**significantly** outperforms **state-of-the-art** LLMs"（第 7 句）。全文没有任何统计显著性检验（检索 "p <"、"standard deviation"、"seed" 均为 0），"significantly" 只是修辞用法。
  - "**significant** gains"（第 8 句）
  - 未出现 "novel"、"first"。
- **摘要与正文证据不完全一致**（Table 2，PDF p.8）：第 8 句称在 "Open-domain QA, reasoning and fact verification" 上超过 ChatGPT。但 Table 2 中，推理任务 ARC-Challenge 上 ChatGPT = 75.3、Ret-ChatGPT = 75.3，Self-RAG 13B = 73.1、7B = 67.3；TriviaQA 上 ChatGPT = 74.3，Self-RAG 13B = 69.3。正文 5.1 节自己列出的超越 ChatGPT 的任务也**不含 ARC**："even outperforms ChatGPT in PubHealth, PopQA, biography generations, and ASQA (Rouge and MAUVE)."
- 词数约 199 词，在 ICLR 常见长度内；第 5、8 句较长（29、33 词），信息较密。

---

## 4. 关键词

**原文未出现**（arXiv v1 的 PDF 与 HTML 都没有 Keywords 行；ICLR 模板本身不要求关键词）。OpenReview 页面可能有投稿时填写的关键词，但该页面需人机验证，**未能核实**。

---

## 5. 引言（Section 1，PDF p.1–2）

### 5.1 逐段梳理

| 段 | 内容摘要 | 对应环节 | 代表原句 |
|---|---|---|---|
| P1 前半 | LLM 仍有事实错误；RAG 能减少错误 | 背景 → 前人工作 | "State-of-the-art LLMs continue to struggle with factual errors (Mallen et al., 2023; Min et al., 2023)…" |
| P1 中段 | RAG 不加区分地检索，引入无关段落；输出不保证与段落一致 | 不足（挖洞，两个洞） | "since they retrieve passages indiscriminately regardless of whether the factual grounding is helpful." / "the output is not guaranteed to be consistent with retrieved relevant passages" |
| P1 后半 | 提出 Self-RAG：按需检索 + 自我反思；reflection tokens 分为 retrieval 和 critique 两类 | 本文工作（填洞） | "This work introduces Self-Reflective Retrieval-augmented Generation (Self-Rag) to improve an LLM's generation quality…" |
| P2 | 推理流程 Step 1–3（判断是否检索 → 并行处理段落 → 生成 critique token 选最优），与传统 RAG 对比（Figure 1 左/右） | 本文工作（方法细节） | "This process differs from conventional RAG (Figure 1 left), which consistently retrieves a fixed number of documents…" |
| P3 | 训练：critic 模型离线插入 reflection tokens（数据来自 GPT-4）；可定制解码 | 本文工作（训练与推理） | "are inserted offline into the original corpus by a trained critic model." |
| P4 | 六个任务上的实验结果与分析 | 结果（相当于隐含的贡献） | "Empirical results on six tasks, including reasoning and long-form generation, demonstrate that Self-Rag significantly outperforms…" |

整体顺序是 **背景 → 前人工作 → 不足 → 本文工作 → 结果**，逻辑清楚，但"背景 + 前人 + 不足 + 本文方案"都压在第一段里。

### 5.2 检查项

- **显式贡献列表**：**原文未出现**。没有 "Our contributions are: (1)…(2)…" 式的条目列表，贡献分散在 P2–P4 的叙述中。P3 中出现的 "(1) flexibly adjust retrieval frequency … and (2) customize models' behaviors" 是推理算法的功能，不是贡献列表。
- **论文组织结构段**（"The rest of this paper is organized as…"）：**原文未出现**。
- **引言中的图**：有。Figure 1 放在引言中，正文用 "Figure 1 left / right" 和 "Step 1/2/3" 引用。
  - Figure 1 图题："Overview of Self-Rag. Self-Rag learns to retrieve, critique, and generate text passages to enhance overall generation quality, factuality, and verifiability."
  - **自明性评价**：图题只重复了方法的总体目标，**没有说明左右两栏分别是什么（传统 RAG 与 Self-RAG）**，也没有解释 Step 1–3 和图中 token 的含义，读者要回到正文 P1–P2 才能看懂。按"图表应自明"的标准，自明性不足。
- **集中引用**：引言共约 11 处括号引用，多为 1–2 篇一组，例如 "(Figure 1 left; Lewis et al. 2020; Guu et al. 2020)"、"(Ram et al., 2023; Asai et al., 2023a)"。没有一次堆 5 篇以上的"堆砌式引用"；但第一段每句都是"一句话 + 1–2 个引用"，前人工作只罗列、没有展开。
- **夸大用词**：
  - "Self-Rag **significantly outperforms** pre-trained and instruction-tuned LLMs that have more parameters…"（P4）
  - "Self-Rag outperforms retrieval-augmented ChatGPT on four tasks, Llama2-chat … and Alpaca … on **all tasks**."（P4）。对照 Table 2：ASQA 的 str-em 指标上，Ret-Llama2-chat13B = 32.8、检索增强 Alpaca13B = 34.8，都高于 Self-RAG 13B 的 31.7。"all tasks" 只有在不计 ASQA em 时才成立。
  - "State-of-the-art LLMs"（P1 首句，用于描述他人模型，属正常用法）。
- **语言错误**（引言内）："citation **previsions**"（应为 precision，P4）；"a **propriety** LM"（应为 proprietary，P3）；"**never second visits** the generation quality"（不地道，P2）。

---

## 6. 相关工作（Section 2，PDF p.3）

- **位置**：第 2 节，紧跟引言、在方法之前。
- **组织方式**：**按主题**分为三个加粗段落标题：
  1. "Retrieval-Augmented Generation."
  2. "Concurrent RAG work."（脚注 2："All work is arXived within a week of this preprint."）
  3. "Training and generating with critics."
- **是否与本文对比**：**有，而且系统地对比**。几乎每段都以 "While … / Though … / In contrast …, Self-Rag …" 收尾，指出本文差异。例句：
  - "While their value function simply indicates an overall score of each generation, Self-Rag trains to an arbitrary LM to learn to generate fine-grained self-reflection…"（同时含语法错误 "trains to an"）
  - "Though our work also studies fine-grained critique on retrieval and generation, we train our target LM on task examples augmented with reflection tokens…"
- **评价**：主题分类清楚，对比到位。单独列出"同期工作"并用脚注说明时间关系，是处理优先权问题的规范写法。不足：第 3 节末尾 "Connections to prior work on learning with critique."（3.2.2）重复了第 2 节关于 RLHF/PPO 和 control tokens 的内容，两处内容有冗余。

---

## 7. 方法（Section 3，PDF p.3–6）

| 检查项 | 结果 | 证据 |
|---|---|---|
| 总览图 | 有。Figure 1（引言）兼作方法总览；第 3 节开头 "shown in Figure 1"。训练样例见 Figure 2 | §3 首段；§3.2.1 Figure 2 |
| 符号先定义后使用 | **大部分做到**。3.1 "Problem Formalization and Overview" 先定义 x、y=[y1,…,yT]、yt；ℳ、ℛ、𝒞 在 "Training overview" 中引入。**例外**：Algorithm 1 第 10–11 行用了 ℳgen，但正文从未定义它与 ℳ 的关系；Algorithm 3 用 𝒯，而正文用 T；Algorithm 1 出现在 "Inference overview" 文字说明之前 | §3.1、Algorithm 1、Algorithm 3（附录 A.2） |
| 公式编号 | 正文公式编号 (1)–(4)：Eq.1 critic 目标、Eq.2 generator 目标、Eq.3–4 段落得分。附录 A.3 的打分公式**未编号** | §3.2.1、§3.2.2、§3.3；附录 A.3 |
| 算法/伪代码 | 有：Algorithm 1（推理，正文）、Algorithm 2（训练，附录 A.2）、Algorithm 3（生成器数据构建，附录 A.2） | §3.1；附录 A.2 |
| reflection token 表 | 有：Table 1 "Four types of reflection tokens used in Self-Rag. Each type uses several tokens to represent its output values." 图题还说明了粗体含义和 x、y、d 的符号，**自明性较好**。附录 A.1 给出每类 token 的详细定义 | §3.1 Table 1；附录 A.1 |
| 术语一致性 | **不一致**：同一个模块交替称为 "critic model" 和 "reward model"（附录 A.2 "the accuracy of the reward model"），同一类 token 交替称为 "reflection tokens" 和 "reward tokens"（§5.2 "using the token probability of reward tokens"） | §5.2；附录 A.2 |
| 语言问题 | "the retrieved passages d1 is selected … while d1 are fully supported"（§3.1，单复数混乱） | §3.1 Inference overview |

---

## 8. 实验（Section 4–5，附录 B–C）

### 8.1 数据集、基线、指标

- **数据集（6 个任务，§4.1）**：Closed-set：PubHealth、ARC-Challenge；Short-form：PopQA（long-tail 子集 1,399 条）、TriviaQA-unfiltered（11,313 条）；Long-form：Biography（FactScore）、ALCE-ASQA。
- **指标（§4.1）**：accuracy；答案是否包含 gold answer（非严格 EM）；FactScore；ASQA 用 str-em、MAUVE、citation precision/recall。
- **基线（§4.2）**：无检索（Llama2 7B/13B、Alpaca 7B/13B、ChatGPT、Llama2-chat13B、CoVE65B）；有检索（标准 RAG 的 Llama2/Alpaca、Llama2-FT、Ret-ChatGPT、Ret-Llama2-chat、perplexity.ai、SAIL、Toolformer）。
  - 规范性说明：脚注 6 说明 SAIL/Toolformer 的数字直接取自原论文："We report numbers using the results reported in the paper as the implementations are not available." Table 2 用 ∗ 标出，**透明度好**。

### 8.2 超参数与训练细节

- 正文 §4.3 给出关键设置：150k 训练对；生成器 Llama2 7B/13B，critic 用 Llama2 7B；Contriever-MS MARCO；权重 1.0/1.0/0.5；检索阈值 0.2（ALCE 为 0）；beam width 2。
- 附录 B.1 给出训练细节："We use 4 Nvidia A100 with 80GB memory to train our models."，3 epochs，batch size 128，lr 2e-5，3% warmup，DeepSpeed stage 3，bf16；推理用 1–2 张 Quadro RTX 6000。
- 附录 B.2 给出检索语料（2018 / 2020 Wikipedia）、Google Programmable Search、各数据集最大生成长度等。

### 8.3 可复现性

- **好的方面**：代码、模型、训练数据都公开（摘要脚注 1、项目页）；算力和超参数写明（附录 B.1）；GPT-4 提示词全文列在附录 D（Tables 8–12）。
- **不足**：
  - 训练数据依赖 GPT-4 标注。作者自己在 §3.2.1 承认这类依赖的问题："depending on such proprietary LMs can raise API costs and diminish reproducibility (Chen et al., 2023)."
  - 没有多次运行、随机种子、方差或置信区间（原文未出现），却频繁使用 "significantly"。
  - 数字前后不一致：§4.3 写 "150k instruction-output pairs"，附录 A.2 写 "in total, we use 145,619 instances"（属四舍五入，可以接受，但应注明）；§3.2.1 写 "We collect 4k-20k supervised training data for each type"，附录 A.1 中 utility 只有 3,831 条，且写成 "1,2594 for Retrieve"（数字格式错误）。
  - 附录 C.1 分析的模型是 "Self-Rag 7B, Alpaca 7B, Alpaca 13B, and Llama2-Chat-13B"，下一句却写 "in Alpaca 30B, 20% of the correct predictions…"，模型名前后矛盾。
  - 附录 B.2 写 Llama2-chat "tend to generate significantly lower outputs"，但紧接着说它输出接近 100 token、ChatGPT 约 40 token，按上下文应为 "longer"，用词错误。

### 8.4 图表标题是否自明

1. **Table 2**（PDF p.8）图题节选："Bold numbers indicate the best performance among non-proprietary models, and gray-colored bold text indicates the best proprietary model…"；图题还解释了 ∗、–、排序方式和全部缩写（FS, em, rg, mau, prec, rec）。
   → **自明性好**，是全文图题写得最规范的一个。小瑕疵：图题里有语法错误 "when they outperforms"。
2. **Figure 3**（PDF p.9）图题："Analysis on Self-Rag: (a) Ablation studies for key components of Self-Rag training and inference based on our 7B model."
   → **自明性不足，而且编号混乱**：(a) 实际是一张表，列名 "PQA / Med / AS" 在图题中**没有解释**（Med 指 PubHealth，正文和其他图表都不用这个缩写）；正文 §5.2 却称它为 "We show in **Table 3a** the ablation results."，而附录中真正的 Table 3 是 "The generator LM ℳ training data statistics."
3. 其他交叉引用错误（PDF 核实）：
   - §3.2.1 写 "The critic achieves a higher than 90% agreement … (**Appendix Table 5**)"，但附录里对应内容是 **Figure 5** "Reward prediction accuracy using GPT-4 predictions as ground-truth predictions."，Table 5 实际是零样本评测指令列表。
   - §5.2 有一句不完整的话："We also evaluate Figures 4a, 4b and 4c shows the models' performance trained on different amount of data."
   - §5.2："retrieval frequencies dramatically change on both datasets. as δ varies."（句号位置错误）

### 8.5 消融与分析

- §5.2 有完整分析：Ablation（训练消融 No Retriever / No Critic；推理消融 No retrieval / Hard constraints / Retrieve top 1 / Remove IsSup）、推理时定制（Figure 3b）、效率与准确率权衡（Figure 3c）、训练数据规模（Figure 4a–c）、人工评测（Figure 4d）。附录 C.1 分析参数记忆与检索记忆，C.2–C.3 给出人工评测和定性示例。
- 规范性问题：
  - 消融只用 50k 训练数据，ASQA 只抽 150 条，正文写明了这一点（"we use a training instance size of 50k…"，"we evaluate models on sampled 150 instances"），透明度好，但没有讨论这样做对结论的影响。
  - 人工评测规模小："we sampled 50 samples from PopQA and Bio results."；**标注者是谁、几人、一致性系数都没有报告**（原文未出现）。附录 A.1 中对 GPT-4 标注的人工检查由作者本人完成："The authors of this paper manually assess randomly sampled 20 instances for each aspect…"，每类只有 20 条，且作者自评存在偏差风险。
  - Table 2 下方的结论句 "obtaining the best performance among non-proprietary LM-based models on all tasks"（§5.1）与 Table 2 的 ASQA em 一栏不符（检索增强 Alpaca13B 34.8 > Self-RAG 13B 31.7）。

---

## 9. 讨论 / 局限性 / 伦理 / 可复现性声明

| 项目 | 是否存在 | 证据 |
|---|---|---|
| 独立 Discussion 节 | **原文未出现**（讨论内容融在 §5 "Results and Analysis" 中） | — |
| Limitations 节 | **原文未出现**（全文检索 "limitation" 为 0 次） | — |
| Ethics | 有，"Ethical Concerns" 小节（结论后、致谢前，PDF p.11），只有 3 句话。承认局限的那句："it can still generate outputs that are not fully supported by the citations." | Ethical Concerns |
| Reproducibility Statement | **原文未出现**（ICLR 鼓励写该声明；arXiv v1 中没有） | — |
| 负面结果/失败案例 | 有一些，但分散在正文和附录：① §5.1 承认 7B 有时优于 13B："Self-Rag 7B occasionally outperforms our 13B due to the tendency of smaller Self-Rag to often generate precisely grounded yet shorter outputs."；② §5.2 承认少检索时 PopQA 下降更多；③ 附录 Table 6 给出 reflection token 判断错误的例子（"The Lie"："Both IsRel and IsSup are incorrect"）；④ 附录 A.2 承认 IsUse 预测准确率较低 | §5.1、§5.2、Table 6、附录 A.2 |
| 未来工作 | 正文**原文未出现**；只在附录 B.2 顺带一句（且含两个拼写错误）："while we leave exploring the effectivess of such appraoches for future work." | 附录 B.2 |

---

## 10. 结论（Section 6，PDF p.10）

- 只有 **1 段、4 句**。内容：重述框架（"a new framework to enhance the quality and factuality of LLMs through retrieval on demand and self-reflection"）、重述训练方式、重述可定制性、重述结果（"Self-Rag significantly outperforms LLMs with more parameters or with conventional retrieval-augmented generation approaches."）。
- **是否回应引言提出的问题**：引言挖了两个洞，一是不加区分地检索损害通用性，二是输出与检索段落不一致。结论用 "retrieval on demand" 和 "self-reflection" 间接对应这两点，但**没有明确说明每个问题解决到什么程度**，也没有给出数字。
- **未来工作**：**原文未出现**（结论中没有）。
- **局限**：结论中没有；只在 Ethical Concerns 中有一句。
- 评价：结论基本是摘要的压缩复述，缺少"贡献总结 + 局限 + 展望"三段式。

---

## 11. 参考文献与学术规范

| 项目 | 结果 | 依据 |
|---|---|---|
| 参考文献数量 | **58 条**（逐条统计） | References（PDF p.11–15） |
| 新近性 | 2023 年 30 条、2022 年 11 条，合计 41/58（约 71%）为近两年文献；2021 年及以前 17 条（最早 2017 年）。领域发展快，文献较新 | References |
| 预印本比例 | 27/58 条以 "arXiv preprint" 形式引用，接近一半 | References |
| 自引 | **至少 8 条**含本文作者：Asai et al. 2020、2023a、2023b；Mallen et al. 2023（Asai, Hajishirzi）；Min et al. 2019、2023（Hajishirzi）；Wang et al. 2023（Yizhong Wang）；Wu et al. 2023（Zeqiu Wu, Hajishirzi）。部分作者列表以 "et al." 截断，实际数量可能更多。自引都与主题直接相关（如 PopQA 数据集、FactScore 指标、Open-Instruct 数据），没有发现为引用而引用 | References |
| 引用格式一致性 | 总体采用 ICLR 的 author-year（natbib）格式，但有瑕疵：① §4.1 "a long-form QA task ALCE-ASQA Gao et al. (2023); Stelmakh et al. (2022)" 应使用括号式引用；② 参考文献标题大小写没有保护，如 "over wikipedia graph"（Asai et al. 2020）、"How is chatgpt's behavior changing over time?"（Chen et al. 2023）、"Factscore"（Min et al. 2023）；③ 同一模型名写法不一：Llama2-chat / LLama2-chat / Llama2-Chat-13B / Llama2-c13B | §4.1、References、§5.1、附录 C.1、Table 2 |
| 致谢/资助 | 有，致谢写得完整：列出讨论和审稿帮助的人；"Akari Asai is supported by the IBM Fellowship."；Stability AI 提供算力；Microsoft Accelerate Foundation Models Research Program 提供 OpenAI API；"funded in part by the DARPA MCS program through NIWC Pacific (N66001-19-2-4031), NSF IIS-2044660, and gifts from AI2." | Acknowledgments（PDF p.11） |
| 利益冲突/作者贡献声明 | **原文未出现** | — |
| 伦理声明 | 有（见第 9 节），但很短 | Ethical Concerns |
| 数据/许可证 | 论文中**原文未出现**任何数据集或模型的许可证说明，也没有讨论使用 GPT-4 输出训练模型的服务条款问题（全文检索 "license" 为 0 次）。代码仓库本身为 MIT License（GitHub 页面，不在论文中） | 全文；GitHub |
| 人类标注伦理 | 人工评测没有说明标注者身份、报酬或知情同意（原文未出现） | §5.2 Human evaluations |

---

## 12. 总结

### 优点 / 亮点

1. **标题简洁、结构规范**（课程标准："标题应准确简洁"）。9 词，"方法名：动作 + 机制"，三个动词与 §3 标题和 Algorithm 1 的 Retrieve/Generate/Critique 三步对应。〔§2 标题；§3；Algorithm 1〕
2. **引言"挖洞—填洞"逻辑清晰，并配有概念图**（"引言应说明问题与本文方案"）。P1 先指出 RAG 的两个缺陷（不加区分地检索；输出与段落不一致），再提出 Self-RAG，并用 Figure 1 左右对比传统 RAG。〔§1 P1–P2；Figure 1〕
3. **相关工作按主题组织，每段都与本文对比**（"相关工作应比较而非罗列"）。三个小标题，并单列 "Concurrent RAG work"，脚注说明同期关系。〔§2；脚注 2〕
4. **可复现材料充分**（"实验应可复现"）。代码、模型、数据公开；算力与超参数写在附录 B.1；GPT-4 提示词全文列在附录 D；直接取自他人论文的基线数字用 ∗ 和脚注 6 标明。〔摘要脚注 1；§4.2 脚注 6；附录 B.1、D〕
5. **主结果表和 token 表的图题自明**（"图表应自明"）。Table 2 图题解释了粗体、灰色、∗、– 和全部缩写；Table 1 图题说明了粗体和符号含义。〔Table 2；Table 1〕

### 缺点 / 可改进处

1. **摘要结果没有量化，而且有部分夸大**（"摘要结果应量化"、"避免夸大用词"）。摘要中没有任何性能数字；"significantly outperforms state-of-the-art LLMs" 没有显著性检验支撑；"outperforms ChatGPT … on … reasoning" 与 Table 2 的 ARC 结果（ChatGPT 75.3 > Self-RAG 13B 73.1）不符。〔摘要第 7–8 句；Table 2〕
2. **引言没有显式贡献列表和组织结构段**（"引言应列出贡献"）。贡献散落在 P2–P4 的叙述中；引言中的 "on all tasks" 与 Table 2 的 ASQA em 一栏矛盾。〔§1 P4；Table 2〕
3. **没有 Limitations 节，结论过于单薄**（"讨论应写局限性"、"结论应回应问题并展望"）。全文检索 "limitation" 为 0 次；结论 4 句，只复述摘要，没有局限也没有未来工作；未来工作只在附录 B.2 出现一次。Ethical Concerns 只有 3 句。〔§6；Ethical Concerns；附录 B.2〕
4. **图表编号和交叉引用错误较多，部分图题不自明**（"图表应自明、编号应一致"）。正文的 "Table 3a" 实际是 Figure 3(a)；"Appendix Table 5" 实际是 Figure 5；Figure 3(a) 的列名 "Med / PQA / AS" 未解释；Figure 1 图题没有说明左右两栏和 Step 1–3；arXiv 元数据写 "2 figures"，实际有 5 张图。〔§3.2.1；§5.2；Figure 1；Figure 3；附录 A.2〕
5. **语言和术语不严谨，校对不足**（"术语应前后一致、语言应规范"）。critic/reward model、reflection/reward tokens 混用；拼写和语法错误包括 "previsions"、"propriety LM"、"trains to an arbitrary LM"、"we do not observed"、"effectivess … appraoches"、"We assigns"、"The the Reference"、"1,2594"、"subsets subsets"；附录 C.1 出现论文没有评测的 "Alpaca 30B"。〔§1；§2；§5.2；附录 A.1、A.2、A.3、B.2、C.1；Table 6〕
6. （补充）**人工评测与数据规范说明不足**（"引用与数据使用应规范"）。人工评测 50 条，未报告标注者身份和一致性；GPT-4 标注的人工核查由作者本人完成，每类仅 20 条；论文中没有数据集或模型许可证说明。〔§5.2；附录 A.1〕

---

### 来源

- arXiv 摘要页：https://arxiv.org/abs/2310.11511
- 全文 HTML：https://arxiv.org/html/2310.11511 ；PDF：https://arxiv.org/pdf/2310.11511
- ICLR 2024 Oral 页面：https://iclr.cc/virtual/2024/oral/19736
- OpenReview（未能打开，需验证）：https://openreview.net/forum?id=hSyW5go0v8
- 项目页 / 代码：https://selfrag.github.io/ ；https://github.com/AkariAsai/self-rag
- 引用数尝试：OpenAlex API（仅 arXiv 记录 101 次，不可靠）；Semantic Scholar API（限流，未获取）
