# 论文写作与学术规范证据文件：Search-R1（arXiv 2503.09516v5）

> 分析对象：arXiv v5（2025-08-05），以 v5 PDF（https://arxiv.org/pdf/2503.09516v5 ，31 页）为准，并与 HTML 版（https://arxiv.org/html/2503.09516 ）和 arXiv 摘要页（https://arxiv.org/abs/2503.09516 ）核对。v1 PDF 仅用于版本对比。
> 引文均为原文逐字摘录（每条 <30 词）。文中"【本组计算】"表示由我们根据原文表格数据自行计算，并非原文陈述。

---

## 1. 基本信息

| 项目 | 内容 | 依据 |
|---|---|---|
| 完整标题 | Search-R1: Training LLMs to Reason and Leverage Search Engines with Reinforcement Learning | v5 PDF 第 1 页 |
| 作者（8 人） | Bowen Jin, Hansi Zeng, Zhenrui Yue, Jinsung Yoon, Sercan Ö. Arık, Dong Wang, Hamed Zamani, Jiawei Han | v5 PDF 第 1 页 |
| 单位 | (1) Department of Computer Science, University of Illinois at Urbana-Champaign（Jin, Yue, Wang, Han）；(2) Center for Intelligent Information Retrieval, University of Massachusetts Amherst（Zeng, Zamani）；(3) Google Cloud AI Research（Yoon, Arık） | v5 PDF 第 1 页 |
| 发表 venue | COLM 2025（Conference on Language Modeling）。v5 PDF 每页页眉为 "Published as a conference paper at COLM 2025"；COLM 2025 官方录用列表收录本文并链接到 OpenReview（id=Rwhi91ideu）：[COLM 2025 Accepted Papers](https://colmweb.org/2025/AcceptedPapers.html)，[OpenReview](https://openreview.net/forum?id=Rwhi91ideu) | 已核实 |
| 年份 | 2025（arXiv v1 2025-03-12；v5 2025-08-05） | [arXiv 摘要页](https://arxiv.org/abs/2503.09516) 提交历史 |
| 页数 | 共 31 页（arXiv Comments："31 pages"）；正文第 1–10 页（含致谢），参考文献第 10–14 页，附录第 15–31 页 | v5 PDF |
| 代码 | 已开源：https://github.com/PeterGriffinJin/Search-R1 （摘要末句给出；摘要称同时提供 model checkpoints）。仓库许可证 Apache-2.0（通过 GitHub API 查询，查询时约 5.5k stars） | Abstract；GitHub API |
| 引用量 | OpenAlex 显示 13 次（检索日期按沙盒系统时间为 2026-11-02；OpenAlex 只索引到 arXiv 版本，可能明显低估）。Semantic Scholar API 查询被限流（HTTP 429），未取得数据；Google Scholar 未查询 | [OpenAlex API](https://api.openalex.org/works?search=Search-R1%20Training%20LLMs%20to%20Reason%20and%20Leverage%20Search%20Engines) |

**版本差异（与学术规范相关，供讨论）**：v1 作者为 6 人（无 Jinsung Yoon、Sercan Ö. Arık），v5 为 8 人，新增 Google Cloud AI Research 两位作者（v1 PDF 第 1 页 vs v5 PDF 第 1 页）。v1 摘要报告的是 "26% (Qwen2.5-7B), 21% (Qwen2.5-3B), and 10% (LLaMA3.2-3B) over SOTA baselines"，v5 已改为两模型、改称 "RAG baselines"（见第 3 节）。

---

## 2. 标题

- **原文标题**：Search-R1: Training LLMs to Reason and Leverage Search Engines with Reinforcement Learning
- **英文词数**：12 词（把 "Search-R1" 计为 1 词）。
- **结构**：方法名 + 冒号 + 描述性副标题（"Search-R1" + ":" + "Training LLMs to … with Reinforcement Learning"）。

| 标准 | 评价 |
|---|---|
| 准确 | 基本准确。副标题点明对象（LLMs）、能力（reason + leverage search engines）和手段（RL），与 Abstract 和 Section 3 的内容一致。 |
| 简洁（≤12 词） | 刚好 12 词，处于上限。"Reason and Leverage" 并列两个动词，"Leverage" 属于常见的空泛动词，可换成 "Use"。 |
| 可检索 | 较好。包含 LLMs、Search Engines、Reinforcement Learning 等高频检索词。 |
| 无未解释缩写 | 有两个缩写。"LLMs" 是领域通用缩写，在 Abstract 首句展开为 "large language models (LLMs)"。**"R1" 在全文中没有明确解释**：Introduction 只有一句间接说明，"Search-R1 can be viewed as an extension of DeepSeek-R1 Zero (Guo et al., 2025)"（Section 1, 第 4 段）。读者需要自己推断 "R1" 来自 DeepSeek-R1。Section 4.2 又把 "R1" 用作基线名，"RL-based fine-tuning without a search engine (R1)"，同一缩写有两种用法。原文未出现对 "R1" 含义的明确定义。 |

---

## 3. 摘要

### 3.1 原文（v5 PDF / HTML 版，逐字）

> Efficiently acquiring external knowledge and up-to-date information is essential for effective reasoning and text generation in large language models (LLMs). Prompting advanced LLMs with reasoning capabilities to use search engines during inference is often suboptimal, as the LLM might not fully possess the capability on how to interact optimally with the search engine. This paper introduces Search-R1, an extension of reinforcement learning (RL) for reasoning frameworks where the LLM learns to autonomously generate (multiple) search queries during step-by-step reasoning with real-time retrieval. Search-R1 optimizes LLM reasoning trajectories with multi-turn search interactions, leveraging retrieved token masking for stable RL training and a simple outcome-based reward function. Experiments on seven question-answering datasets show that Search-R1 improves performance by 24% (Qwen2.5-7B) and 20% (Qwen2.5-3B) over various RAG baselines under the same setting. This paper further provides empirical insights into RL optimization methods, LLM choices, and response length dynamics in retrieval-augmented reasoning. The code and model checkpoints are available at https://github.com/PeterGriffinJin/Search-R1.

（注：摘要全文为课堂展示需要整段引用；后文其余引文均控制在 30 词以内。arXiv 摘要页上的 metadata 摘要与 PDF 文字有一处不同，见 3.3。）

### 3.2 逐句拆分与标注

| # | 句子（开头） | 功能标签 | 说明 |
|---|---|---|---|
| S1 | "Efficiently acquiring external knowledge and up-to-date information is essential…" | 背景 | 说明外部知识对 LLM 的重要性 |
| S2 | "Prompting advanced LLMs … is often suboptimal, as the LLM might not fully possess the capability…" | 背景/问题（不足） | 指出现有提示方法的不足。只批评了 prompting，没有提到训练式方法（v1 摘要曾提到 RAG 和 tool-use 训练的不足，v5 删去） |
| S3 | "This paper introduces Search-R1, an extension of reinforcement learning (RL) for reasoning frameworks…" | 目的/方法 | 提出方法 |
| S4 | "Search-R1 optimizes LLM reasoning trajectories with multi-turn search interactions, leveraging retrieved token masking…" | 方法 | 三个技术要点：多轮检索交互、检索 token 掩码、结果奖励 |
| S5 | "Experiments on seven question-answering datasets show that Search-R1 improves performance by 24% … and 20% …" | 结果 | 有量化数字 |
| S6 | "This paper further provides empirical insights into RL optimization methods, LLM choices, and response length dynamics…" | 结果（附加分析） | 只列出分析主题，没有给出具体发现 |
| S7 | "The code and model checkpoints are available at https://github.com/PeterGriffinJin/Search-R1." | 资源/可复现性 | 开源声明 |
| — | — | **结论** | **原文未出现**单独的结论句或意义句（没有说明这些结果意味着什么） |

### 3.3 结果是否量化？"41%" 与 "24%" 的问题

- **有量化**：S5 给出了百分比。但摘要**没有说明是相对提升还是绝对提升**，**没有说明指标**（EM），**也没有说明比较对象是哪个基线**（只写 "various RAG baselines"）。
- **同一篇论文中出现三种说法**：

| 位置 | 原文 | 数字 |
|---|---|---|
| v5 PDF/HTML 摘要 | "improves performance by 24% (Qwen2.5-7B) and 20% (Qwen2.5-3B) over various RAG baselines under the same setting" | 24% / 20%，未写 "relative" |
| arXiv 摘要页 metadata（abs 页面） | "Search-R1 improves performance by 41% (Qwen2.5-7B) and 20% (Qwen2.5-3B) over various RAG baselines" | 41% / 20% |
| Section 1 贡献列表第 3 条 | "two LLMs achieving respective average relative improvements of 41% and 20% over RAG baselines" | 41% / 20%，明确写 "average relative" |
| Section 4.4 第 (1) 点 | "We achieve 24% and 20% average relative improvement with Qwen2.5-7B and Qwen2.5-3B, respectively." | 24% / 20%，明确写 "average relative"，但未说明对比哪个基线 |

- **【本组计算】根据 Table 2 的 Avg. 列（EM）核对**：
  - 7B：Search-R1-base 0.431 vs RAG 0.304，0.431/0.304−1 ≈ **41.8%**（相对），绝对差 +0.127；vs 最强基线 Rejection Sampling 0.348，0.431/0.348−1 ≈ **23.9%**（相对），绝对差 +0.083。
  - 3B：Search-R1-instruct 0.325 vs RAG 0.270（3B 下 RAG 即最强基线），0.325/0.270−1 ≈ **20.4%**（相对），绝对差 +0.055。
  - 结论：**41% 是相对于 RAG 的平均相对提升；24% 是相对于最强基线 Rejection Sampling 的平均相对提升**，两者都是相对值，都取的是 Search-R1 base/instruct 中较好的一个。
- **写作问题**：
  1. 摘要（PDF）用 24%，arXiv 页面摘要用 41%，引言用 41%，正文 4.4 用 24%。读者看不同位置得到不同数字。
  2. 摘要说 24% 是 "over various RAG baselines"，但按我们的计算，24% 对应的是 Rejection Sampling。Section 4.2 把 Rejection Sampling 归入 "(3) Fine-Tuning-Based Methods"，不属于 RAG 类基线。
  3. 摘要没写 "relative"。EM 绝对值只有 0.3–0.4，相对提升 41% 实际对应绝对提升约 12.7 个百分点，不说明会让读者高估提升幅度。
  4. Section 4.4 第 (4) 点写 "compared with second best model - RAG"，而 Table 2 中 7B 的第二名是 Rejection Sampling（0.348），不是 RAG（0.304）。

### 3.4 摘要中的引用、图表

- 引用文献：原文未出现（摘要无引用，符合规范）。
- 图表引用：原文未出现。
- URL：有（代码链接）。

### 3.5 夸大用词

摘要用词总体克制。可讨论的有："essential"（S1）、"optimally"（S2）、"autonomously"（S3）。正文中的夸大用词见第 5、10 节。

### 3.6 词数

约 **157 词**（由 HTML 版摘要文字统计，含 URL）。在常见会议摘要 150–250 词的范围内。

---

## 4. 关键词

**原文未出现**关键词（Keywords）栏。COLM 模板通常不要求关键词，但从课程标准看属于缺项。

---

## 5. 引言（Section 1）

### 5.1 逐段对应（按 v5 PDF 段落划分）

| 段 | 内容 | 对应环节 | 证据 |
|---|---|---|---|
| P1 | LLM 能力强，但在复杂推理和获取最新信息上有困难 | 背景 | "LLMs often encounter challenges when tasked with complex reasoning (Wei et al., 2022) and retrieving up-to-date information" |
| P2 | 现有方法分两类：RAG 和 search-as-tool；逐一指出不足 | 前人工作 + 不足（挖洞①） | "this approach is suboptimal because the LLM is not optimized to learn how to interact effectively with search engines during training" |
| P3 | RL 在推理上的成功（o1、DeepSeek-R1），然后提出三个挑战：RL 框架与稳定性、多轮交替推理与检索、奖励设计 | 前人工作（RL）+ 不足（挖洞②，三个挑战） | "However, applying RL to search-and-reasoning scenarios presents three key challenges" |
| P4 | 提出 Search-R1，用 (1)(2)(3) 逐条回应三个挑战 | 本文工作（填洞） | "To address aforementioned challenges, we introduce Search-R1, a novel RL framework" |
| P5 | 三条贡献（项目符号列表） | 贡献 | "In summary, our key contributions are threefold:" |
| — | 论文组织结构段 | **原文未出现** | 引言末尾没有 "The rest of the paper is organized as follows" 一类的段落 |

**评价**："挖洞→填洞"的逻辑清楚。P3 列出三个挑战，P4 的 (1)(2)(3) 一一对应，是本文写作最规范的部分。

### 5.2 其他检查项

- **显式贡献列表**：有，3 条项目符号（Section 1 末尾）。但第 1 条较空泛："Our work analyzes the challenges and provides perspectives on implementing RL…"。"provides perspectives" 不是可检验的贡献。第 2 条与 P4 的三条创新内容重复。
- **组织结构段**：原文未出现。
- **引言中的图**：原文未出现。Figure 1 位于 Section 3（PDF 第 4 页）。
- **集中引用**：有。例如 "(Guo et al., 2025; Hou et al., 2025; Xie et al., 2025; Kumar et al., 2024)"（P3，一处括号 4 篇），"(Sutton et al., 1999; Kaelbling et al., 1996)"（P3）。这些是支撑一般性论断的堆叠引用，没有逐篇说明各自的贡献。
- **夸大用词（引言）**：
  - "Large language models (LLMs) have demonstrated remarkable capabilities"（P1）
  - "has emerged as a potent paradigm for enhancing the reasoning capabilities of LLMs"（P3）
  - "we introduce Search-R1, a novel RL framework"（P4）；贡献第 2 条再次使用 "a novel RL framework"
  - "Search-R1 introduces the following key innovations"（P4）
  - "We conduct systematic experiments to demonstrate the effectiveness of Search-R1"（贡献第 3 条）
- **引言内部表述冲突**：P4 第 (3) 点说 "avoiding the complexity of process-based rewards"，结尾说 Search-R1 是 "an extension of DeepSeek-R1 Zero"。"novel" 与 "extension" 同时出现，新颖性的定位不一致，可在课堂上讨论。

---

## 6. 相关工作（Section 2 "Related Works"）

- **位置**：Section 2，紧接引言、在方法之前（PDF 第 3 页）。
- **组织方式**：按主题分为两小节：2.1 "Large Language Models and Retrieval"，2.2 "Large Language Models and Reinforcement Learning"。每小节按"方法类别 → 代表工作 → 不足"的顺序展开。
- **与本文工作的对比**：只是隐式对比。两小节都以"研究空白"句结尾，**没有直接写 Search-R1 与各类工作的具体差别**（例如没有对比表）。
  - 2.1 末句："yet its potential in search engine calling scenarios remains under-explored."
  - 2.2 末句："Despite these advances, the application of RL to LLM-driven search engine interactions and reasoning remains largely unexplored."
- **示例句（2.1）**："IRCoT (Trivedi et al., 2022a) and ReAct (Yao et al., 2023) use prompting to guide iterative reasoning and search engine calls"
- **内容重复**：2.1 关于 "RAG vs. search-as-a-tool" 的两分法与引言 P2 基本相同，且重复引用 Gao et al. 2023、Schick et al. 2023。
- **遗漏同期工作（学术规范问题）**："remains largely unexplored" 的说法缺少对同期工作的讨论。我们核对了参考文献表（61 条），其中**未出现** R1-Searcher（Song et al., arXiv 2503.05592，2025 年 3 月，用两阶段结果奖励 RL 训练 LLM 调用搜索，见 [arXiv](https://arxiv.org/abs/2503.05592)）。v5 定稿于 2025 年 8 月，仍然没有讨论这类同期 RL+搜索 工作。
- **Section 2.2 的段内逻辑**："A similar approach is employed in LeRet (Hsu et al., 2024)" 插在 DPO/SimPO 之后，和前后的偏好优化讨论衔接较弱。
- **附录补充**：Appendix B.1 解释了为何不与 Re2G、RetroLLM 比较："we do not include these methods as direct baselines"。这是对基线选择的正面说明。

---

## 7. 方法（Section 3 "Search-R1"）

| 检查项 | 结果 | 证据 |
|---|---|---|
| 小节导读 | 有。Section 3 开头列出 (1)–(4) 四部分 | "covering (1) extending RL to utilize search engines; (2) text generation with an interleaved multi-turn search engine call; (3) the training template; and (4) reward model design." |
| 总体框架图 | 有。Figure 1（PDF 第 4 页），PPO/GRPO 两种训练流程示意图。图题："Demonstration of PPO and GRPO training with the search engine (Search-R1)." 图题较短，没有解释图中各模块（Reward Model、Value LLM 等）和箭头含义 | Section 3, Figure 1 |
| 公式编号 | 有。正文 Eq. (1)–(4)，附录 Eq. (5)–(6)，全部编号 | Section 3.1, 3.4, Appendix A |
| 符号先定义后使用 | 基本做到。搜索引擎 ℛ 在 Eq. (1) 前引入（"utilizing a search engine ℛ"），π_θ、π_ref、r_φ、D_KL 紧随 Eq. (1) 定义；I(y_t) 在 Eq. (2) 后定义；动作预算 B 在 Algorithm 1 输入中定义。**存在不一致**：Eq. (1) 下文说 y 是 "sampled from the reference policy π_ref(y∣x)"，而 Eq. (1) 本身写的是 y∼π_θ(⋅∣x;ℛ)；GRPO 段说 "GRPO samples a group of responses … from the reference policy π_ref"，而 Eq. (3) 写的是 {y_i}∼π_old。采样分布的写法前后矛盾。 | Section 3.1 |
| 新运算符 | ⨂ 定义为 "denotes interleaved retrieval-and-reasoning"，只是文字说明，没有形式化定义 | Section 3.1 |
| 算法/伪代码 | 有。Algorithm 1 "LLM Response Rollout with Multi-Turn Search Engine Calls"（PDF 第 6 页），25 行 | Section 3.2 |
| 提示模板 | 有。Table 1 "Template for Search-R1"，给出完整模板原文 | Section 3.3, Table 1 |
| 设计理由 | 有说明。例如不用格式奖励的理由："we do not incorporate format rewards, as our learned model already demonstrates strong structural adherence."（Section 3.4）。但 "strong structural adherence" 在正文没有给出数据支持 | Section 3.4 |
| 语言细节 | Section 3.2 "the maximum number of action is reached"（应为 actions）；Section 3.4 标题为 "Reward Modeling"，但该节明确说不训练奖励模型（"we avoid training neural reward models"），导读中又写作 "reward model design"，术语不统一 | Section 3, 3.2, 3.4 |

---

## 8. 实验（Section 4 "Main Results" + Section 5 "Analysis" + 附录）

### 8.1 数据集（Section 4.1）
共 7 个：General QA 包括 NQ、TriviaQA、PopQA；Multi-Hop QA 包括 HotpotQA、2WikiMultiHopQA、Musique、Bamboogle。训练集为 NQ+HotpotQA 合并（Section 4.3）。Table 2 用 †/⋆ 标注 in-domain/out-domain。**原文未出现**各数据集的规模（训练/测试样本数）和所用划分的具体说明，只写了 "test or validation sets"。

### 8.2 基线（Section 4.2）
分三类：(1) 不检索：Direct inference、CoT；(2) 检索推理：RAG、IRCoT、Search-o1；(3) 微调：SFT、R1、Rejection Sampling。公平性说明："we use the same retriever, same number of retrieved documents, same knowledge corpus, same training data and same pre-trained LLMs."（Section 4.2）。
**不一致**：Appendix C 的 14B 结果（Table 5）**没有 Rejection Sampling 基线**，与 Table 2 的基线集合不同，但 Appendix C 仍写 "Search-R1 consistently outperforms all baseline methods"。

### 8.3 指标
Exact Match (EM)，"following Yu et al. (2024)"（Section 4.3）。**原文未出现**多次运行、标准差、置信区间或显著性检验。

### 8.4 超参数与训练细节（Appendix B.2）
给得比较全：PPO 策略模型学习率 1e-6、价值模型 1e-5，500 steps，warm-up ratio 0.285/0.015，GAE λ=1、γ=1，batch 512 / mini 256 / micro 64，最大序列 4,096 tokens，β=0.001，ε=0.2，temperature 1.0，top-p 1.0，GRPO 每个 prompt 采样 5 个回答，动作预算 B=4，top-3 检索段落。
**写作问题**：Appendix B.2 大段重复 Section 4.3 原文；B.2 内还出现自我指向的句子 "More details on experimental settings can be found in Appendix B."（这句就在 Appendix B 里）。

### 8.5 可复现性
- 代码：有（GitHub，Apache-2.0）。
- 模型 checkpoint：摘要声称提供（"The code and model checkpoints are available at…"）。
- 算力：有。"Training is performed on a single node with 8 H100 GPUs."（Appendix B.2）。**原文未出现**总训练时长（GPU 小时）。
- 随机种子：原文未出现。
- checkpoint 选择规则：有说明，但含主观判断。"In cases where training diverges, we evaluate at the most recent stable checkpoint according to the training reward curve"（Appendix B.2）。这是依据训练奖励曲线人工挑选 checkpoint，应作为局限说明。

### 8.6 图表标题是否自明

- **Table 2**（Section 4.4，PDF 第 8 页）："Main results. The best performance is set in bold. †/⋆ represents in-domain/out-domain datasets."
  评价：**不自明**。标题没有说明指标（EM）、数值含义（0–1 的准确率）、模型规模和 base/instruct 的对应关系。读者必须回到 Section 4.3 才能读懂表格。附录 Table 5 与 Table 2 的标题一字不差，也没写明是 14B 结果。
- **Table 4**（Section 5.4）："The performance of Search-R1 with and without retrieved token loss masking. The LLM trained with retrieved token loss masking achieves consistently better performance. (LLM: Qwen2.5-7b-base; RL: PPO)"
  评价：**较好**。标题写明了比较对象、主要结论和实验设置（模型、RL 算法），基本可以单独阅读。
- **Figure 2**（Section 5，PDF 第 9 页）：四个子图的标题各带一句结论，例如 "(d) # Valid search study: As the training proceeds, the LLM learns to call search more." 结论式标题便于阅读。但有拼写错误："the final performance of both modles remains highly similar"。
- **Figure 3**："Retrieved Token Loss Masking Study"，只有名称，没有说明。

### 8.7 消融与分析
- Section 5 共 4 个分析小节：5.1 PPO vs. GRPO（Table 3, Figure 2a）；5.2 Base vs. Instruct（Figure 2b）；5.3 Response Length and Valid Search（Figure 2c, 2d）；5.4 Retrieved Token Loss Masking 消融（Table 4, Figure 3）。
- 附录补充：C（14B）、D（masking，3B/7B）、E、F、G（top-k 检索段落数）、H（GRPO group size）。
- **交叉引用问题**：
  - Section 5.4 引用 "As shown in Figure 3"，但 Figure 3 在 Appendix D（PDF 第 17 页），正文读者看不到。
  - Appendix I 写 "The results are presented in Table 20"，但 R1 与 Search-R1 的对比案例是 **Table 9**；Table 20 是 "case study 11 (failed)"。引用编号错误。
  - Section 5.4 末句列出 "Appendix D, E, G, H, I and J"，漏掉了正文中单独提到的 F，列举的主题与附录字母对应不清楚。
- **"consistently" 与表格数据不符**：Section 4.4 第 (1) 点写 "Search-R1 consistently outperforms strong baseline methods."。但 Table 2 中 3B 组 Bamboogle 列，Search-o1 为 0.320，高于 Search-R1-instruct 的 0.264 和 Search-R1-base 的 0.088。
- **对结果的解释**：5.1 (1) 把 GRPO 收敛更快直接归因于 critic 需要 warm-up（"This is because PPO relies on a critic model"），没有实验验证这个因果关系。

### 8.8 案例研究
有。Appendix I（Table 9，R1 vs Search-R1）和 Appendix J（Table 10–20，共 11 个案例，**其中 4 个标注为 failed**：Table 11, 14, 16, 20）。正文中**原文未出现**案例展示，读者只能在附录看到。

---

## 9. 讨论 / 局限性

- **局限性（Limitations）小节**：**原文未出现**。正文和附录都没有 "Limitations" 标题，全文检索 "limitation" 仅出现在描述 LLM 已有不足的句子中（Section 1, 2.1）。
- **伦理声明 / 更广泛影响（Ethics / Broader Impact）**：**原文未出现**。
- **未来工作**：只在 Section 6 结尾一段和 Section 3.4 中各有一句（见第 10 节）。
- **负面结果**：有，但散在分析和附录里，没有集中讨论：
  - GRPO 训练崩溃："GRPO leads to reward collapse after training for many steps, whereas PPO remains stable."（Section 5.1）
  - top-k=5 不稳定："its reward gradually declines and becomes more unstable as training progresses."（Appendix G）
  - 失败案例："The LLM can be misled by irrelevant retrieved information and provide a wrong answer."（Appendix J, Table 20 标题）
  - Group size 权衡："highlighting a trade-off between learning speed and stability in GRPO training."（Appendix H）
- **评价**：这些负面发现本可以组成一个 Limitations 小节（训练不稳定、依赖人工挑选 checkpoint、只用 EM 指标、只在 Wikipedia 2018 语料和 QA 任务上验证），但原文没有做这样的归纳。

---

## 10. 结论（Section 6 "Conclusions"）

- **是否回应引言问题**：部分回应。结论重述了方法（"a novel RL framework that enables LLMs to interleave self-reasoning with real-time search engine interactions"），并与 RAG 和 tool-use 方法对比，对应引言 P2 的两类不足。**没有逐条回应引言 P3 提出的三个挑战**（稳定性、多轮交替、奖励设计），也**没有给出任何具体数字**。
- **夸大用词**：
  - "we demonstrated that Search-R1 significantly enhances LLMs' ability to tackle complex reasoning tasks"（Section 6）。"significantly" 没有统计检验支持（见 8.3）。
  - "Through extensive experiments on seven datasets"（Section 6）
  - "Our analysis also provides key insights into RL training strategies"（Section 6）
- **语法**："Unlike existing RAG-like approaches, which relies on extensive prompting"（主谓不一致，应为 rely）。
- **未来工作**：有一句，列了五个方向。"future work can explore expanding Search-R1 to support broader search strategies, including more sophisticated reward mechanisms"，然后是 "It is also promising to investigate its applicability to multimodal reasoning tasks."（Section 6）。只列方向，没有和本文的具体不足挂钩。

---

## 11. 参考文献与学术规范

| 项目 | 结果 | 依据 |
|---|---|---|
| 参考文献数量 | **61 条**（按 HTML 版参考文献条目统计） | References |
| 时效性 | 2023 年 12 条、2024 年 20 条、2025 年 6 条，**2023–2025 共 38 条，约 62%**；2022 年 10 条；2020 年及以前 13 条（最早 Williams, 1992） | References（本组统计） |
| 自引 | 至少 2 条：Jin et al. (2024)《Long-context llms meet rag》（作者 Bowen Jin, Jinsung Yoon, Jiawei Han, Sercan O Arik，均为本文作者），在 Section 1、2.1 和 Appendix G 中引用；Yue et al. (2024)《Inference scaling for long-context retrieval augmented generation》（含本文作者 Zhenrui Yue、Hansi Zeng、Dong Wang），在 Section 2.1 中引用。自引比例低（约 3%），且引用与上下文相关 | References |
| arXiv 与正式版本混用 | 37/61 条以 "arXiv preprint" 形式引用，其中不少已正式发表，但仍引用 arXiv 版，例如 TriviaQA（Joshi et al., 2017）、HotpotQA（Yang et al., 2018）、IRCoT（Trivedi et al., 2022a）、PopQA（Mallen et al., 2022）。同类会议论文中，有的写全称（"In Proceedings of the 2023 Conference on Empirical Methods in Natural Language Processing"），有的写缩写（"In EMNLP (1), pp. 6769–6781, 2020"，Karpukhin et al.） | References |
| 条目格式错误 | (1) Self-RAG（Asai et al., 2024）只有 "2024."，**没有出处**；(2) arXiv 条目后出现无意义的卷号，如 "arXiv preprint arXiv:2312.10997, 2, 2023"（Gao et al.）、"arXiv:2212.10511, 7, 2022"（Mallen et al.）、"arXiv:2312.14925, 10, 2023"（Kaufmann et al.）、"arXiv:2303.18223, 1(2), 2023"（Zhao et al.）；(3) 会议届次与年份不符："In The Thirteenth International Conference on Learning Representations, 2024"（Jin et al.；第 13 届 ICLR 为 2025 年），"In The Twelfth International Conference on Learning Representations, 2023"（Lin et al.；第 12 届为 2024 年）；(4) 标题大小写丢失，如 "Gpt-4 technical report"、"Qwen2. 5 technical report"、"Hotpotqa"、"Triviaqa"；(5) RL 经典教材以 "Reinforcement learning. Journal of Cognitive Neuroscience, 11(1):126–134, 1999"（Sutton et al.）的形式引用，出处与通常引用的 Sutton & Barto 教材不符 | References |
| 引用与论断匹配 | Rejection sampling 引用的是 Ahn et al. (2024)《Large language models for mathematical reasoning: Progresses and challenges》，这是一篇数学推理综述，不是 rejection sampling 的方法来源，匹配度存疑（Section 4.2） | Section 4.2；References |
| 致谢与资助 | 有。列出 Apple PhD Fellowship、DARPA INCAS（HR0011-21-C0165）、BRIES（HR0011-24-3-0325）、ONR、NSF 多项、Cisco 等，并附免责声明："Any opinions, findings, and conclusions or recommendations expressed herein are those of the authors" | Acknowledgments（PDF 第 10 页） |
| 伦理声明 | 原文未出现 | — |
| 数据集/模型许可证说明 | 原文未出现（论文没有说明 7 个数据集、Wikipedia dump、E5、Qwen2.5 的许可证）。代码仓库许可证为 Apache-2.0（GitHub 查询，非论文正文内容） | — |
| 利益冲突声明 | 原文未出现 | — |
| 脚注引用工具 | vLLM 与 veRL 脚本以脚注 URL 给出（Appendix B.2 脚注 1、2） | Appendix B.2 |

---

## 12. 总结

### 优点 / 亮点

1. **引言"挖洞—填洞"结构清楚，并列出了贡献**（课程标准："引言应列出贡献""引言应有问题—方法对应"）。Section 1 P3 提出三个挑战，P4 用 (1)(2)(3) 逐条对应，P5 用项目符号列出三条贡献。
2. **方法部分规范**（课程标准："公式应编号、符号应定义""方法应可复现"）。Eq. (1)–(6) 全部编号；有 Algorithm 1 伪代码；Table 1 给出完整提示模板；Section 3 开头有导读。
3. **实验细节与开源情况好**（课程标准："实验应可复现"）。Appendix B.2 列出全部关键超参数和硬件（8×H100）；摘要给出代码和 checkpoint 的 GitHub 链接（Apache-2.0）；Section 4.2 明确写出公平比较的条件。
4. **分析和失败案例比较充分**（课程标准："应报告消融与负面结果"）。Section 5 有 4 个分析小节，附录 D–H 补充消融；Appendix J 的 11 个案例中有 4 个是失败案例（Table 11, 14, 16, 20）；Section 5.1 如实报告 GRPO 的 reward collapse。
5. **部分图表标题能独立阅读**（课程标准："图表应自明"）。Table 4 的标题包含比较对象、结论和设置（"(LLM: Qwen2.5-7b-base; RL: PPO)"）；Figure 2 的每个子图标题都带一句结论。

### 缺点 / 可改进处

1. **核心数字前后不一致，且没有说明计算方式**（课程标准："摘要结果应量化且准确""全文数据应一致"）。v5 PDF 摘要和 Section 4.4 写 24%，Section 1 贡献列表和 arXiv 页面摘要写 41%；摘要没写 "relative"，没写指标和对比基线。按 Table 2 计算，41% 是相对 RAG，24% 是相对 Rejection Sampling，后者不属于摘要所说的 "RAG baselines"。Section 4.4 (4) 还把 7B 的第二名误写为 RAG。
2. **没有局限性和伦理小节**（课程标准："讨论应写局限性"）。全文原文未出现 Limitations、Ethics、Broader Impact。训练崩溃、依据奖励曲线人工挑选 checkpoint（Appendix B.2）、只用 EM、只在 Wikipedia 2018 上测试等问题都没有归纳为局限。结论（Section 6）只有一句泛泛的未来工作。
3. **夸大用词和结论无统计支持**（课程标准："避免夸大用词"）。"novel"（Section 1 两次、Section 6）、"key innovations"、"potent paradigm"、"remarkable"、"significantly enhances"（Section 6）、"consistently outperforms"（Section 4.4、Appendix C）。原文未出现方差和显著性检验，且 Table 2 中 3B Bamboogle 列 Search-o1（0.320）高于 Search-R1（0.264），与 "consistently" 不符。
4. **引用格式不规范，同期工作缺失**（课程标准："引用应规范、完整"）。37/61 条为 arXiv 版本，已正式发表的论文也未更新；Self-RAG 条目缺出处；ICLR 届次与年份不符；arXiv 条目出现无意义卷号；标题大小写丢失；参考文献中没有 R1-Searcher 等同期 RL+搜索 工作，但 Section 2.2 仍说该方向 "remains largely unexplored"。
5. **图表与交叉引用有错误，部分标题不自明**（课程标准："图表应自明，引用编号应正确"）。Table 2/Table 5 标题没有指标和模型说明，且两者标题完全相同；Figure 3 只有名称；Section 5.4 引用放在附录的 Figure 3；Appendix I 把 Table 9 误写为 "Table 20"；Appendix B.2 指向自身；有拼写和语法错误（Figure 2 "modles"、Table 11 "mislead by irrelevent"、Section 6 "which relies"、Section 3.2 "number of action"）。
6. **（可选）方法符号前后不一致，"R1" 未定义**（课程标准："符号与术语应统一""标题缩写应解释"）。Section 3.1 文字说 y 从 π_ref 采样，与 Eq. (1)/(3) 中的 π_θ、π_old 矛盾；"R1" 既是方法名的一部分，又是基线名（Section 4.2），全文没有明确定义。
