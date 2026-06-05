# Section Writing Rules

Use this reference when polishing wording and deciding how to express scope, empty sections, and detailed design.

## Empty Value Rules

Use `无` when:
- the section was considered and confirmed not applicable
- a feature is explicitly not needed
- there is intentionally no limitation, no unsupported function, or no term explanation

Use `未提供` when:
- source materials do not include the information
- the author has not supplied a plan, data, owner, delivery date, or link
- the content may exist but is not in the given material

Use source wording when the source says:
- `见BRD`
- `见SOW文档`
- `见规划需求`

Never use:
- `暂无`
- empty heading with no content
- deleting the module

## 功能概述 Rules

功能概述 must be a paragraph.

Include:
- overall capability
- core user/scenario
- major involved modules
- business closure

Do not include:
- all field-level rules
- long interface details
- every exception prompt

## 功能详情 Rules

功能详情 must correspond to 产品功能详细设计.

If detailed design has:
- 1.1 授权及初始化
- 1.2 组织绑定
- 2.1 类目映射
- 2.2 商品同步

Then 功能详情 should summarize those same levels, not invent a different hierarchy.

## 业务限制说明 vs 不支持功能说明

业务限制说明 answers:
“This requirement supports the scenario, but only under these business conditions.”

Examples:
- only supports specified goods types
- only applies to specific provinces/cities or platform rules
- depends on external platform account opening
- only supports certain organization nodes

不支持功能说明 answers:
“Inside the business loop, these expected capabilities are not delivered.”

Examples:
- does not support partial refund
- does not support page decoration
- does not support payment detail consolidation
- does not support operation log viewing in a specified page

Do not merge these sections.

## 系统/操作流程 Rules

Write this section only when it reduces ambiguity.

Use it for:
- cross-system payment or refund
- external platform synchronization
- stateful account opening/certification
- C端/B端 multi-step journey
- multiple order, coupon, or settlement states

When a flow is needed, write Mermaid flowchart code blocks only.
- Use fenced `mermaid` code blocks.
- Use `flowchart TD` by default.
- Include actor, system, action, result, decision, final state, and failure handling as nodes or edge labels.
- Use decision diamonds with `{}` for condition checks.
- Do not write prose paragraphs or numbered step lists in this section.

If the flow is simple, write `无`.

## Revision Writing Rules

Revision content must reference concrete changed capability:
- added configuration
- removed flow
- changed interface input
- added status
- adjusted refund rule
- added report/export column
- split phase delivery

Avoid:
- `更新文档`
- `调整内容`
- `补充说明`

If the source only says a generic phrase, preserve it but add a bracketed concrete note only when the source provides enough detail elsewhere.

## Source Fidelity Rules

Copy exactly for:
- BRD/SOW names
- document addresses
- original requirement numbers
- field names
- status values
- external interface names
- error messages
- pricing and product IDs
- legal/policy-sensitive language

Summarize only for:
- long repeated examples
- duplicated background prose
- obvious source noise from PDF extraction

## Detail Depth Rules

Light iteration PRD:
- keep overview concise
- detailed design can focus on page changes, fields, and prompts
- limitations often `无`

Integration-heavy PRD:
- include interface names, fields, status mapping, external dependencies
- include API compatibility, historical data, import/export, logs
- include system/process flow

SOW-style PRD:
- preserve SOW address
- split by module/team
- list commercial controls and expiration behavior
- separate each custom requirement into detailed design subsections
