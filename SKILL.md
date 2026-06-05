---
name: structured-prd-writer
description: Use when writing, reviewing, or standardizing structured PRDs from BRD/SOW/real project requirements, especially when the user needs a strict section-by-section PRD template with mandatory empty-state handling, versioning, business scope, functional details, limitations, unsupported items, and system/process flows.
---

# Structured PRD Writer

Use this skill to turn business requirements into a strict structured PRD, or to normalize an existing PRD against a consistent PRD standard.
When producing a document artifact, output it as Markdown (`.md`) unless the user explicitly asks for another format.

## Goal

Write PRDs that are:
- structurally complete
- review-friendly
- traceable to BRD/SOW/source notes
- explicit about scope, exclusions, and business limits

## Hard Rules

1. Keep the original document title semantics.
   - Title must include module and business scenario.
   - Preserve product line, module, and scene in the title.
   - Keep casing and punctuation consistent with the source style.

2. Version history is mandatory.
   - Include version number, revision date, reviser, revision stage, and concrete revision content.
   - Revision content must be specific, not generic.
   - Do not collapse multiple versions into one line if the source has multiple revisions.

3. Requirements overview must be source-faithful.
   - Paste the BRD link or planning address if provided.
   - If the source gives copied BRD text, copy it as-is.
   - Do not paraphrase the overview into your own words unless the source is missing.

4. Empty content must stay visible.
   - Never delete a module just because there is no content.
   - Use `无` or `未提供` depending on context.
   - Do not use `暂无`.
   - If a section is intentionally blank, still keep the section heading and fill it with `无` or `未提供`.

5. Functional scope must be split clearly.
   - 功能概述: one paragraph, summarize capability in business language.
   - 功能详情: align with detailed design layer by layer.
   - 业务限制说明: only state limits/exclusions inside the business scenario.
   - 不支持功能说明: only state items the closed loop does not support.
   - 系统/操作流程: use only Mermaid flowchart code blocks for complex cross-system, multi-state, or buyer/seller flows.

6. Do not invent unsupported business logic.
   - If the source does not define a rule, mark it as missing rather than guessing.
   - When multiple docs conflict, prefer the newest revision or the explicit project-specific document.

## Writing Workflow

### 1. Identify the document type

Classify the source as one of:
- light iteration PRD
- integration-heavy PRD
- SOW-style PRD
- template reference

This decides how much detail goes into functional detail, flow, and exclusions.

### 2. Extract the PRD spine

The required spine is:
1. 版本状态及修订记录
2. 需求概览
   - 需求背景
   - 业务场景
   - 商业策略
   - 运营数据
   - 销售计划
   - 期望交付时间及内容
3. 产品功能实现方案
   - 功能概述
   - 功能详情
   - 业务限制说明
   - 不支持功能说明
   - 系统/操作流程
   - 名称解释
   - 关联系统及团队
4. 商业策略和运营数据实现方案
   - 商业策略实现方案
   - 产品运营数据实现方案
5. 产品功能详细设计
   - 实际方案设计目录
   - 方案通用关注点

Keep the same order unless the source documents clearly use a different house order.

### 3. Write the core sections

#### 版本状态及修订记录

For every revision entry, capture:
- 版本号
- 修订日期
- 修订人
- 修订阶段
- 修订内容

Revision content should say what changed, not why the change happened.

#### 需求概览

This section is a top-level container.
- The first content line under `需求概览` is always `无`.
- Do not copy source overview content here.
- Do not paraphrase source overview content here.
- Then include the fixed second-level subsections in order:
  1. 需求背景
  2. 业务场景
  3. 商业策略
  4. 运营数据
  5. 销售计划
  6. 期望交付时间及内容

#### 需求背景

Use only the background the source gives.
- If background is a business/policy driver, state it plainly.
- If the source uses bullet-like points, keep them as bullets.
- If the source has no background, write `无` or `未提供`.

#### 产品功能实现方案

This section should summarize the overall solution from the product angle.
- This section is for product operation output.
- Keep it high level.
- Describe only scenario and functional summary.
- Do not expand detailed business logic here.
- Must include 功能概述, 功能详情, 业务限制说明, 不支持功能说明, 系统/操作流程, 名称解释, 关联系统及团队 even if some are `无` or `未提供`.

Use the source terms for channels and systems.

#### 产品功能详细设计

This is the densest section.
- Break by product module and user journey.
- Keep the same granularity as the source design.
- 产品设计方案 must correspond to 产品功能实现方案 above, especially 功能概述 and 功能详情.
- The order of detailed design sections must match the order of 功能详情.
- Treat 产品功能详细设计 as the R&D-facing expansion of 功能详情, not a new or reordered solution.
- For each item, describe entry, trigger, condition, result, and exception if present.
- If there are field definitions, status transitions, validations, or interface mappings, write them here rather than burying them elsewhere.
- This section is for R&D output and should contain the detailed implementation logic.
- Product feature detail subsections are defined by the actual solution.
- 方案通用关注点 is a required second-level subsection inside 产品功能详细设计, not a separate top-level section.

#### 业务限制说明

Write only the scoped restrictions:
- unsupported regions
- unsupported business types
- dependency on external systems
- configuration prerequisites
- one-way or partial support rules

Do not turn this into a general warning list.

#### 不支持功能说明

List the closed-loop capabilities that are explicitly not supported.
Examples:
- not supporting partial refund
- not supporting activity page decoration
- not supporting aggregated export

Keep this separate from business limitations.

#### 系统/操作流程

Use this for:
- multi-system interaction
- cross-channel order/payment/refund flow
- account opening / verification / certification flow
- complex state machine flow

This section must contain Mermaid flowchart code only, not prose or numbered step lists.
- If a flow exists, output one or more fenced `mermaid` code blocks.
- Use `flowchart TD` by default.
- Put Chinese node text in quoted labels, especially when labels contain punctuation.
- Represent actors, systems, decisions, success states, failure states, and manual operations as explicit nodes.
- Use decision diamonds with `{}` for conditions and route `是/否`, `成功/失败`, or status names on edges.
- Keep explanatory details in node labels; do not add prose before or after the diagram.
- If there is no system/process flow, write `无`.

### 4. Handle blank sections correctly

When a section has no content:
- keep the heading
- write `无` if the absence is a deliberate non-requirement
- write `未提供` if the source simply lacks the information

Do not remove the module.
Do not write `暂无`.

### 5. Preserve traceability

When source documents mention:
- BRD
- SOW
- planning doc
- related systems
- responsible teams
- business version / sales version

carry them through into the PRD if they belong there.

### 6. Prefer exact source wording for external references

For:
- document links
- product names
- interface names
- status names
- field names
- rules with legal or operational sensitivity

prefer direct copying over rewriting.

## Recommended Output Shape

Use a PRD structure like:

```text
# 【PRD】{产品线}-{模块}-{业务场景}

# 版本状态及修订记录

# 需求概览
无
## 1. 需求背景
## 2. 业务场景
## 3. 商业策略
## 4. 运营数据
## 5. 销售计划
## 6. 期望交付时间及内容

# 产品功能实现方案
## 1. 功能概述
## 2. 功能详情
## 3. 业务限制说明
## 4. 不支持功能说明
## 5. 系统/操作流程
## 6. 名称解释
## 7. 关联系统及团队

# 商业策略和运营数据实现方案
## 1. 商业策略实现方案
## 2. 产品运营数据实现方案

# 产品功能详细设计
## 1. {实际方案目录}
## 2. 方案通用关注点
### 2.1 API兼容
### 2.2 历史数据处理
### 2.3 导入导出功能
### 2.4 操作日志功能
### 2.5 数据报表调整

---文档以下无内容---
```

For full writing detail, load only the needed references:
- `references/prd-template.md`: use when drafting a complete PRD from source notes.
- `references/section-writing-rules.md`: use when polishing section wording or deciding `无` vs `未提供`.
- `references/review-checklist.md`: use when reviewing an existing PRD before delivery.

If the task is to generate a deliverable file, write the content in Markdown and save it with a `.md` suffix.

## Formatting Rules

- 一级目录不编号。
- 二级目录只在所属一级目录内编号，且每个一级目录下从 `1.` 重新开始。
- 不同一级目录下的二级目录编号不顺延。
- 文档标题只保留标题本身，不单列“文档标题”模块。
- 需求概览固定输出 `无`。
- 一级目录和二级目录必须都存在，不得缺失。
- 产品功能详细设计的二级目录必须依据实际方案定义。
- Use `#` for the document title and top-level fixed sections.
- Use `## 1. ...` for fixed second-level sections.
- Use `### 1.1 ...` or lower levels only when a second-level design section needs further subdivision.
- End generated PRDs with `---文档以下无内容---`.

## Writing Discipline

- Prefer business language over implementation chatter in overview sections.
- Prefer precise mechanism language in detailed design sections.
- Use `无` and `未提供` deliberately.
- Never auto-fill missing sections with invented prose.
- When in doubt, keep the source structure and lower the amount of interpretation.
