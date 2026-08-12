---
name: write-plainly
description: Rewrite, audit, or draft text in clear human language only when the user explicitly asks for "说人话", "去雾化", "别说黑话", "write plainly", "plain language", "make it clearer", "less AI", "no jargon", or "rewrite plainly", or when the requested deliverable is a standalone human-facing artifact whose main goal is readable wording, such as a README, email, report, document, speech, research note, or meeting note. Do not use for ordinary conversation, quick explanations, coding updates, status reports, code review findings, or general answers merely because they are long.
---

# Write Plainly

Use this skill as a final expression layer. Preserve the user's meaning and technical depth, but remove fog: vague abstractions, unexplained terms, inflated tone, and sentences that sound important without telling the reader what to do or believe.

## Activation Boundary

Use this skill only when clarity itself is the task: a rewrite, an audit of unclear writing, or a human-facing text artifact whose wording is part of the deliverable.

Do not use this skill for normal chat, short Q&A, routine explanations, coding progress updates, status reports, code review findings, or general reasoning answers. In those cases, answer concisely in the normal Codex voice without loading this skill.

If the user says "这次不要用 skill" or "直接回答", do not use this skill unless a higher-priority instruction requires it.

## Default Standard

Write for a smart reader who is busy, not for a committee. Lead with the point. Then give the reason, evidence, caveat, or next step.

Do not dumb down technical content. Keep necessary terms, formulas, file names, model names, and method names. Make each one earn its place by explaining what it means in this context or why it matters.

For human-readable rewrites, do not add machine metadata. YAML frontmatter, `tags`, `aliases`, `related`, routing fields, and provenance tags are for tools, not for readers. Omit them unless the user explicitly asks to preserve Obsidian/static-site metadata or edit a metadata-bearing source in place.

## Workflow

1. Identify the reader's actual need:
   - Decision: what should we choose?
   - Explanation: what is happening and why?
   - Action: what should I do next?
   - Rewrite: make this text easier to read without changing its claims.

2. Extract the core claim before writing:
   - "This says X."
   - "X matters because Y."
   - "The practical next step is Z."

3. Preserve the information sequence:
   - Keep the original order of introduction for major concepts, frameworks, definitions, evidence, and conclusions unless the user asks for restructuring.
   - Do not pull a later section's framework, term, definition, proof, or evidence into an earlier section just because it makes the rewrite feel smoother.
   - If an earlier section needs to point ahead, use a light preview such as "the next section names this framework" instead of fully defining it.

4. Rewrite around concrete anchors:
   - people, systems, files, experiments, dates, numbers, symptoms, costs, tradeoffs, risks.
   - if a sentence has none of these, check whether it is filler.

5. Decompress workflow terms:
   - Do not depend on a fixed jargon list. Treat any word or phrase as a compressed workflow term if it hides a process step, role, timing boundary, data boundary, evaluation rule, decision rule, artifact state, ownership, or failure mode.
   - Examples include `live`, `backtest`, `search policy`, `pipeline`, `benchmark`, `frozen set`, `clean set`, `leakage`, `dual-use`, `calibration`, and `routing`, but the examples are not exhaustive.
   - State what the term means in this workflow, who uses it, when it is used, what rule it imposes, and what breaks if the rule is wrong.

6. Run the fog check before answering:
   - Could a reader act on this?
   - Did every term get explained or used concretely?
   - Did the answer avoid empty balance, inflated confidence, and decorative phrasing?
   - If a sentence can be deleted without losing meaning, delete it.

## Modes

### Direct Answer

When answering a user directly, put the answer first. Use short paragraphs. Use bullets only when they make comparison or steps easier.

Avoid preambles like "This is a multi-dimensional question" unless the next sentence names the actual dimensions and why they matter.

### Rewrite

When rewriting pasted text or a file excerpt:

1. Give the rewritten version first.
2. Preserve the original claims unless the user asks for critique.
3. Keep the original structure if it helps navigation; simplify headings when they are foggy.
4. Omit YAML frontmatter and machine metadata by default. If a metadata field contains information useful to a human, turn it into normal prose instead of keeping the metadata block.
5. Explain only the biggest changes afterward, in at most 3 bullets, if useful.

### Audit

When the user asks why a text is hard to read, diagnose the fog directly:

- "The claim is hidden."
- "The terms are not defined."
- "The sentence says a relationship exists, but not what follows from it."
- "The text has a conclusion, but no decision or next action."
- "The metaphor sounds strong but does not add information."

Then show a before/after example.

### File Edit

When editing a local file in place:

1. Keep factual content, citations, equations, and named methods intact.
2. Change headings and connective prose freely when they obscure the point.
3. Do not rewrite quoted speech unless the user explicitly asks.
4. Preserve existing YAML frontmatter only when the output is meant to stay inside a note system that needs it. For standalone review copies, remove it.
5. Prefer targeted edits over full rewrites unless the whole document is foggy.
6. Report what changed and where.

## Fog Patterns To Remove

Replace abstract packaging with concrete meaning:

| Foggy pattern | Better move |
|---|---|
| "形成闭环 / 打通链路 / 构建体系" | Say which steps connect and what output appears. |
| "提升鲁棒性 / 泛化能力 / 可维护性" | Say what failure becomes less likely. |
| "多维度分析 / 深度赋能 / 范式迁移" | Name the dimensions, mechanism, or source/target. |
| "具有重要意义 / 值得关注" | Say who should care and what decision changes. |
| "从某种意义上 / 在一定程度上" | Either make the claim precise or delete the hedge. |
| "不是 X，而是 Y" | Explain the operational difference between X and Y. |
| "统一框架 / 理论化路径" | State what gets unified and what experiment or proof follows. |

Do not ban a word mechanically. A term is acceptable when it is defined, necessary, and tied to a concrete consequence.

## Information Order Rules

Clarity must not come from moving later ideas too early. A rewrite should make the text easier to read while preserving the author's sequence of disclosure.

Before moving or expanding a concept, identify its role in the original:

- preview: a light hint that a later idea exists.
- definition: the first place the text explains what a term or framework means.
- evidence: the place that supports a claim.
- consequence: what the claim changes.
- action: what should be done next.

Do not turn a preview into a full definition. Do not turn a later framework into the opening premise unless the user asks for a restructure or executive summary.

If a section only says "these things have a common thread", keep it at that level. Write "the next section names and explains this thread" rather than importing the full explanation.

When a document has numbered sections, preserve each section's job:

- opening sections usually state the problem, decision, or map.
- framework sections name and define the framework.
- evidence sections support the framework.
- recommendation sections turn it into action.

If changing this order would improve the document, flag it as a restructuring choice rather than silently doing it.

## Workflow Compression Rules

Some unclear writing is not caused by fancy wording. It is caused by compressing an entire process into a few insider terms.

When rewriting workflow-heavy text, do not merely replace jargon with softer wording. Expand the workflow.

Do not solve this with a keyword list. The examples below are examples only. Detect compression by function: if a term forces the reader to already know a hidden workflow, expand it.

For each compressed workflow term, answer these questions in normal prose:

- What does this mean here?
- Who or what uses it?
- When in the workflow does it apply?
- What decision or rule follows from it?
- What goes wrong if it is applied incorrectly?

Trigger this rule for any phrase that hides:

- a process step: what happens before or after this?
- a role: who runs it, consumes it, reviews it, or is blocked by it?
- a timing boundary: historical replay, real-time use, before/after date, training/test split.
- a data boundary: what information is allowed, excluded, frozen, leaked, or reused?
- an evaluation rule: what score, benchmark, baseline, or comparison makes this meaningful?
- an artifact state: draft, clean dataset, frozen set, production version, reusable module.
- a decision rule: what should be done differently because of this?
- a failure mode: what breaks if this rule is copied to the wrong place?

If one sentence contains multiple workflow terms, split it into separate sentences or bullets. Define the moving parts before giving the instruction.

Examples:

| Compressed | Clearer |
|---|---|
| "live and backtest need separate search policies" | "Historical replay and real prediction need different search rules. In replay, restrict search to information available before the target date to avoid leakage. In live prediction, allow information available now, otherwise the agent will be needlessly blinded." |
| "investment must be dual-use" | "Only spend time on leaderboard work if it also leaves something reusable: a clean dataset, an evaluation script, a benchmark, a figure, or a module that can support the paper." |
| "freeze the benchmark" | "Pick a fixed set of examples, stop changing it, and report every method on that same set so later scores are comparable." |

## Chinese Style Rules

- Prefer "这意味着..." over "其意义在于..." when explaining consequences.
- Prefer "先做 A，因为 B" over "建议围绕 A 展开探索".
- Prefer "这个数必须先算" over "该指标具有前置判别价值".
- Prefer "这里有一个风险" over "该方向存在潜在不确定性".
- Prefer "如果 X 很大，这条路不划算" over "X 将影响方案可行性".

Use natural Chinese punctuation and rhythm. Avoid stacking four-character abstractions. Avoid making every paragraph sound like a proposal abstract.

## Technical Content Rules

- Keep precise technical terms when they matter: e.g. `offline RL`, `world model`, `KL`, `regime`, `effective rank`, `FLOPs`.
- Define the first occurrence in plain language when the target reader may not know it.
- For any core term, first explain it in one sentence that does not use that term. If you cannot do this, do not use the term yet.
- Tie each technical claim to one of these: observable symptom, experiment, cost, risk, decision, or paper contribution.
- When explaining code, name the file/function and the behavior change before discussing architecture.
- When explaining research, separate:
  - claim
  - why it is nontrivial
  - how to test it
  - what result would change the plan

## Output Shapes

For a short answer:

```text
结论：...
原因：...
下一步：...
```

For a rewrite:

```text
改写版：
...

主要变化：
- ...
- ...
```

For an audit:

```text
问题：
- ...

例子：
原句：...
人话版：...
```

Use these shapes only when they help. Do not force every answer into a template.

## Final Self-Check

Before final output, silently verify:

- The first sentence gives real information.
- No paragraph exists only to sound balanced or professional.
- Necessary uncertainty is explicit, but not evasive.
- Core terms can be explained without repeating the term itself.
- Major concepts appear where the original first names or defines them; later frameworks are not silently pulled into earlier sections.
- Workflow compression is detected by hidden process, role, timing, data boundary, evaluation rule, artifact state, decision rule, or failure mode, not by a fixed keyword list.
- No YAML frontmatter, tags, aliases, related links, or provenance metadata appears in a human-readable rewrite unless explicitly requested.
- The reader can tell what changed, what matters, and what to do next.
- The output sounds like a competent person explaining the matter, not like a corporate memo or a paper abstract.
