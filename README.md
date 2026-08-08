# Write Plainly

## 中文说明

你有没有遇到过这种情况？

老板发来一份文档，每个字都认识，但读完不知道他到底要你做什么。

AI 给你生成一段回答，听起来很专业，里面全是“闭环”“赋能”“鲁棒性”“多维度”“统一框架”，但你看完还是不知道结论是什么。

研究笔记写了一大页，公式、概念、项目名都有，但真正的问题被埋在里面：这件事到底重要在哪里？下一步到底该做什么？

这就是这个 skill 要解决的问题。

**Write Plainly** 是一个给 Codex / Claude Code 用的写作 skill。它会把 AI 腔、论文腔、咨询腔、技术黑话，改成更清楚、更具体、更像人说的话。

它不会把内容改浅。它要做的是：保留技术细节，但让读者看得懂。

### 它适合处理什么？

- 看起来很专业，但读不出结论的研究笔记
- 老板、同事、AI 发来的晦涩文档
- 写得像汇报材料，但没人知道下一步是什么的计划
- PR 总结、代码解释、会议纪要、论文想法
- 中文技术写作里常见的“云里雾里”
- AI 生成后需要再过一遍的人话版草稿

### 它会怎么改？

它会问几个很直接的问题：

- 这段话到底想说什么？
- 哪些词只是装饰，哪些词真的有用？
- 术语有没有解释？
- 这个判断会改变什么决策？
- 读者看完能不能知道下一步怎么做？
- 有没有把后文才定义的框架提前塞到前面？
- 有没有把一整套流程压缩成几个内部黑话？

### 一个例子

原文：

> live 与 backtest 要两套 search policy，打榜投入必须 dual-use。

改写后：

> 历史回测和真实打榜要用不同的搜索规则。
>
> 回测是在重放过去的问题，所以 agent 只能看目标日期以前的信息。这样做是为了防止它偷看未来答案。
>
> 真实打榜是在预测未来，所以 agent 应该能使用当前已经公开的信息。如果把回测里的时间过滤规则直接套到真实打榜，agent 会查不到本来允许使用的信息。
>
> 打榜也不要只做一次性优化。每项投入最好能留下可复用的东西，比如干净数据集、评测脚本、固定 benchmark、论文图表或可复用模块。

这就是这个 skill 的目标：

> 不是让文字变短，而是让意思露出来。

### 核心规则

1. **先说真正的判断。** 不用“多维度分析”“形成闭环”这类词遮住结论。
2. **核心术语必须能用一句不含术语的话解释。** 解释不了，就不要急着使用。
3. **展开隐藏工作流。** 如果一个词藏着流程、角色、时间边界、数据边界、评测规则或失败后果，就把它讲出来。
4. **保留信息出场顺序。** 不要把后文才定义的框架提前塞进开头，除非用户明确要重构。
5. **删掉给机器看的元数据。** 面向人看的改写稿默认不要 YAML frontmatter、tags、aliases、related links。

### 安装到 Codex

把这个仓库放到 Codex 的 skills 目录下：

```text
~/.codex/skills/write-plainly/
```

目录里应至少包含：

```text
SKILL.md
agents/openai.yaml
```

使用时可以说：

```text
Use $write-plainly to rewrite this in clear human language.
```

或者中文：

```text
用 $write-plainly 去雾化这段话，不要丢技术细节。
```

### 安装到 Claude Code

把这个仓库放到 Claude Code 的 skills 目录下：

```text
~/.claude/skills/write-plainly/
```

然后使用：

```text
Use $write-plainly to defog this draft without losing technical detail.
```

### 这不是什么？

这不是摘要器。它不应该为了变短而删掉重要判断。

这也不是“把技术内容翻译给小学生”。技术术语可以保留，但必须解释清楚，并且要和具体决策、实验、风险或行动连起来。

---

## English

Have you ever read a document where every word is familiar, but the point is still unclear?

A manager sends a plan full of abstract phrases. An AI writes an answer that sounds professional but hides the actual decision. A research note contains formulas, method names, and project labels, but the reader still cannot tell what matters or what to do next.

**Write Plainly** is a Codex / Claude Code skill for rewriting AI-style, jargon-heavy, vague, consultant-style, or over-abstract text into clear human language.

It does not dumb things down. It keeps the technical content and makes the claim, reason, risk, and next step easier to see.

### Good For

- research notes
- technical plans
- code explanations
- PR summaries
- meeting notes
- AI-generated drafts
- Chinese technical writing that sounds too much like proposal prose

### What It Does

This skill rewrites text so that:

- the main point comes first
- necessary terms are explained
- abstract phrases are tied to concrete consequences
- hidden workflow assumptions are expanded
- machine metadata is removed from human-facing drafts
- the original information order is preserved unless restructuring is requested

### Example

Original:

> live and backtest need separate search policies, and leaderboard work must be dual-use.

Clearer:

> Historical replay and real prediction need different search rules.
>
> In historical replay, the agent can only use information that was public before the target date. This prevents it from accidentally seeing future answers.
>
> In real prediction, the agent should be allowed to use information that is public now. If we copy the replay filter into the live system, the agent will miss information it is allowed to use.
>
> Leaderboard work should also leave reusable artifacts: clean datasets, evaluation scripts, fixed benchmarks, paper figures, or reusable modules.

### Installation

For Codex:

```text
~/.codex/skills/write-plainly/
```

For Claude Code:

```text
~/.claude/skills/write-plainly/
```

The skill directory should contain:

```text
SKILL.md
agents/openai.yaml
```

Example prompt:

```text
Use $write-plainly to rewrite this in clear human language without losing technical detail.
```

### Not A Summarizer

This skill is not meant to remove important claims just to make text shorter.

It is also not a beginner-level translator. Technical terms should stay when they matter, but they must be explained and tied to a concrete decision, experiment, risk, or action.

## License

MIT
