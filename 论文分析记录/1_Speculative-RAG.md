# Speculative RAG（ICLR 2025）学术写作与学术规范分析

> 依据：ICLR 2025 正式版全文（specrag.txt / specrag.pdf，共 23 页 PDF）。所有证据均为原文短引文 + 位置；不含自行计算的数字。

## 1. 基本信息

| 项目 | 内容 |
|---|---|
| 标题 | Speculative RAG: Enhancing Retrieval Augmented Generation through Drafting |
| 作者 | 12 位作者（第一作者 Zilong Wang；通讯作者 Zilong Wang、Chen-Yu Lee） |
| 单位 | University of California, San Diego；Google Cloud AI Research；Google DeepMind；Google Cloud AI（PDF p.1） |
| 发表 | ICLR 2025 会议论文（页眉 "Published as a conference paper at ICLR 2025"） |
| 篇幅 | PDF 共 23 页：正文 p.1–10，参考文献 p.11–15，附录 A–J p.16–23 |
| 代码链接 | 论文中**未给出**代码或数据链接 |
| 备注 | 脚注说明第一作者工作完成于 Google 实习期间："Work done while the author was a student researcher at Google Cloud AI Research."（p.1 脚注） |

---

## 2. 逐项分析（9 项课程标准）

### 2.1 标题　评级：**好**

- **亮点**
  - 标题短，用"方法名 + 冒号 + 作用说明"的结构，创新点（Drafting）直接写进标题："Speculative RAG: Enhancing Retrieval Augmented Generation through Drafting"（标题，p.1）。全标题 8 个英文词，满足 ≤12 词的要求。
  - 缩写处理得当：标题用了缩写 RAG，但副标题紧接着写出全称 "Retrieval Augmented Generation"，读者不需要预备知识也能检索和理解（标题，p.1）。
- **可改进**：无明显问题。

### 2.2 摘要　评级：**较好**

- **亮点**
  - 目的、方法、结果三要素齐全，层次清楚。先指出现有工作的方向 "Recent RAG advancements focus on improving retrieval outcomes through iterative LLM refinement or self-critique"，再引出方法 "a larger generalist LM to efficiently verify multiple RAG drafts produced in parallel by a smaller, distilled specialist LM"（Abstract，p.1）。
  - 结果给出了具体数字，而且同时覆盖效果和效率两个维度："enhances accuracy by up to 12.97% while reducing latency by 50.83% compared to conventional RAG systems on PubHealth"（Abstract，p.1）。
- **可改进**
  - 摘要可以补一句结论或意义（摘要目前以结果句结束，结论 p.10 中的 "sheds new light on the potential of collaborative architectures" 没有出现在摘要里），也可以点明 "conventional RAG systems" 具体指哪个基线（正文 4.3 节 p.7 写明是 "the most competitive standard RAG model, Mixtral-Instruct8x7B"），这样量化结果更准确。

### 2.3 关键词　评级：**一般**

- **亮点**
  - 论文没有关键词栏，但核心术语在标题、摘要、贡献列表中反复使用，用词一致（如 "drafts""verify""specialist LM""generalist LM"），一定程度上能起到检索作用（Abstract p.1；Introduction 贡献列表 p.2–3）。
- **可改进**
  - 全文没有 Keywords 栏。如果按课程要求写成学位论文或投稿稿，可在摘要后补充与标题对应的关键词，例如 Retrieval Augmented Generation、Speculative Drafting、Draft Verification。

### 2.4 引言　评级：**好**

- **亮点**
  - "背景→不足→本文工作"的逻辑完整，"挖洞"写得明确。先讲 LLM 的幻觉问题和 RAG 的作用，再指出多文档带来的长输入问题 "encoding lengthy retrieved documents incurs additional latency"（p.1），然后指出前人工作的不足 "often neglecting the latency issues associated with these systems"（p.2）。
  - 用类比说明方法的来源，"填洞"自然，最后给出 3 条贡献列表："Inspired by Speculative Decoding … our approach adapts this concept to RAG"；"Our key contributions are:"（Introduction，p.2–3）。
- **可改进**
  - 引言末尾可以补一段"全文组织结构"。另外，贡献列表中 "a single, unbiased verification pass"（p.3）的 "unbiased" 在正文中没有专门论证，措辞可以更谨慎，或者给出对应的实验依据。

### 2.5 相关工作　评级：**较好**

- **亮点**
  - 按主题分类梳理，分 "Retrieval Augmented Generation" 和 "Speculative Decoding" 两类，正好对应本文的两个思想来源（Section 2，p.3）。
  - 每一类都以对比收尾，明确本文的位置："In contrast, our proposed SPECULATIVE RAG addresses these limitations"；"Our approach extends this concept from token-level drafting to answer-level drafting"（Section 2，p.3）。
- **可改进**
  - 相关工作篇幅较短（两段）。可以对上下文压缩、过滤类方法单独展开对比，例如 RECOMP（Xu et al., 2023）、Learning to filter context（Wang et al., 2023b）。这些方法与本文"缩短验证输入"的目标相近，但目前只出现在括号引用串中（Section 2，p.3）。

### 2.6 方法　评级：**好**

- **亮点**
  - 总览图做得好：Figure 1 用 (a)–(d) 四个子图把 Standard RAG、Self-RAG、CRAG 和本文方法并排对比，图注能独立读懂："(d) In contrast, our proposed SPECULATIVE RAG leverages a larger generalist LM…"（Figure 1，p.2）。
  - 先有形式化定义，再给伪代码，正文按行号讲解，读者能逐步跟上。问题定义："each entry can be represented as (Q, D, A)"（Problem Formulation，p.3）。Algorithm 1 配有逐行注释，正文用 "(Line 2)""(Line 5 to 8)""(Line 12)" 对应引用（Section 3.1，p.4）。
- **可改进**
  - 3.2 和 3.3 节的公式（聚类采样、ρDraft、ρSC、ρSR 和最终得分 ρj）都没有编号（p.5–6），后文只能用文字回指。建议给关键公式编号，便于引用和讨论。

### 2.7 实验与图表　评级：**较好**

- **亮点**
  - 实验设置交代完整，数据集、基线、指标、超参数都有：5 个基准，"we retrieve top 10 documents and generate 5 drafts per query (m = 5), with each draft based on a subset of 2 documents (k = 2)"（Section 4.2，p.6）。附录 A 还给出硬件信息："16 Nvidia A100-SXM4-40GB GPUs"（p.16）。
  - 消融和分析做得系统：Table 3 逐一去掉采样策略和三个评分项；Table 2 比较用 rationale 还是用原文档验证；Figure 4 分析草稿数量和子集大小；附录 B–F 再补充训练数据量、反思语句、多跳推理等分析。表注能独立读懂，例如 "† indicates numbers reported in Asai et al. (2023); − denotes numbers that are not reported"（Table 1 caption，p.7）。
- **可改进**
  - 论文没有给出代码、模型或数据链接，而 drafter 的训练数据由闭源模型生成："use Gemini-Ultra (Team et al., 2023) to generate rationale. In total, we acquire a dataset of 40k instances"（Appendix A，p.16）。建议补充开源链接或可复现性说明（例如是否公开 40k 训练数据），方便他人复现。

### 2.8 讨论与结论　评级：**一般**

- **亮点**
  - 如实报告负面结果并分析原因，这一点值得学习："the multi-perspective sampling is less helpful for bridge-type questions"，并给出可结合的方向 "could be effectively combined with other techniques specifically designed for bridge-type questions"（Appendix F.1，p.19）。附录 D 也主动承认额外开销："the generation of rationale potentially increases the inference cost during the drafting stage"（p.17）。
  - 结论与引言、摘要呼应：重述"起草 + 验证"的分解思路，以及摘要中的同一组量化结果 "accuracy gains up to 12.97% while reducing latency by 50.83%"（Section 5，p.10）。
- **可改进**
  - 正文没有局限性小节，结论也没有写未来工作。上述负面结果和成本讨论只出现在附录（D、F.1）。建议在正文增加 "Limitations and Future Work" 小节，把这些内容提到正文，同时说明适用边界，例如 bridge-type 多跳问题、rationale 生成开销、对闭源模型生成训练数据的依赖。

### 2.9 学术规范　评级：**较好**

- **亮点**
  - 引用他人结果时来源标注清楚，并说明公平比较的做法："† indicates numbers reported in Asai et al. (2023)"（Table 1，p.7）；"We reproduce the performance of Self-RAG … and CRAG … with Mistral7B (v0.1) for a fair comparison"（Appendix A，p.16）。
  - 署名信息透明：脚注说明工作完成的背景，列出两位通讯作者及邮箱（p.1 脚注）。全文统一使用作者-年份引用格式，基线、数据集、工具（vLLM、DeepSpeed、Transformers）都有引用（Section 4，Appendix A）。
- **可改进**
  - 全文没有致谢或资助说明，也没有伦理声明（Ethics Statement）和可复现性声明（Reproducibility Statement）。考虑到 PubHealth 涉及医疗声明核查（"PubHealth is a dataset of medical claims"，Section 4，p.6），建议补充这两类声明，说明数据来源、潜在风险和复现所需材料。

### 评级汇总

| 标准 | 评级 |
|---|---|
| 标题 | 好 |
| 摘要 | 较好 |
| 关键词 | 一般 |
| 引言 | 好 |
| 相关工作 | 较好 |
| 方法 | 好 |
| 实验与图表 | 较好 |
| 讨论与结论 | 一般 |
| 学术规范 | 较好 |

---

## 3. 总评

### Top 3 亮点（最适合在课堂展示）

1. **总览图对比四种范式，一张图讲清创新点**：Figure 1 把 Standard RAG、Self-RAG、CRAG 和本文方法并排画出，图注能独立读懂（Figure 1，p.2）。
2. **"形式化定义 → 伪代码 → 按行号讲解"的方法写法**：Algorithm 1 配逐行注释，正文用 "(Line 2)""(Line 12)" 对应说明，读者容易跟上（Section 3.1，p.3–4）。
3. **消融实验系统，并如实报告负面结果**：Table 3 逐项去掉各组件，附录 F.1 坦承 "less helpful for bridge-type questions" 并分析原因（Table 3 p.10；Appendix F.1 p.19）。

### Top 2 可改进

1. **正文可增加局限性与未来工作小节**：成本和负面结果目前只在附录 D、F.1 中讨论，结论（Section 5，p.10）没有提到局限性。
2. **可补充代码/数据开源和可复现性、伦理声明**：论文没有代码链接，训练数据由 Gemini-Ultra 生成（Appendix A，p.16），全文也没有 Ethics / Reproducibility Statement。

---

## 4. PPT 特色概括（≤30字）

**一张对比总览图加伪代码，把"小模型起草、大模型验证"讲得一目了然。**
