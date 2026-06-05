# PRD Review Checklist

Use this checklist before delivering a PRD or reviewing a draft.

## Structure

- [ ] Title includes PRD/platform/module/business scenario.
- [ ] Version table includes version, date, reviser, stage, concrete revision content.
- [ ] Requirement overview includes BRD/SOW/planning address when available.
- [ ] All required modules are present.
- [ ] Empty modules are filled with `无` or `未提供`.
- [ ] No section uses `暂无`.

## Source Fidelity

- [ ] BRD/SOW overview text is copied rather than rephrased when source text exists.
- [ ] Requirement original number and requirement name are preserved when available.
- [ ] Product names, external systems, interface names, status names, and field names are copied accurately.
- [ ] Dates and version numbers match the source.

## Product Solution

- [ ] 功能概述 is paragraph-style and summarizes the capability.
- [ ] 功能详情 mirrors 产品功能详细设计 hierarchy.
- [ ] Phased delivery is explicit if source has phase 1 / phase 2.
- [ ] Commercial strategy is separated from product implementation.
- [ ] Operating data/reporting requirements are called out.

## Scope Control

- [ ] 业务限制说明 contains scoped business limits, not generic caveats.
- [ ] 不支持功能说明 contains unsupported closed-loop features.
- [ ] Restrictions and unsupported items are not mixed together.
- [ ] External dependencies are visible.
- [ ] Configuration prerequisites are visible.

## Detailed Design

- [ ] Each module has entry/path, role, action, rule, result, and exception where applicable.
- [ ] Field tables include type, required status, default value, rule, and remark when fields exist.
- [ ] Validation and prompt copy are explicit.
- [ ] Status transitions are explicit.
- [ ] Import/export changes are explicit.
- [ ] Historical data handling is explicit.
- [ ] Operation log behavior is explicit.
- [ ] API compatibility is explicit for interface-related changes.
- [ ] Reports and report data changes are explicit.

## Flow

- [ ] 系统/操作流程 exists for cross-system or multi-state processes.
- [ ] Flow is written as fenced Mermaid code blocks only, or `无` when not needed.
- [ ] Mermaid nodes/edges include actor, system, action, result, and failure handling.
- [ ] C端/B端/商家/消费者 paths are not conflated.
- [ ] Payment/refund/coupon/account flows include final state.

## Final Language Pass

- [ ] No invented logic.
- [ ] No vague revision content.
- [ ] No deleted empty modules.
- [ ] No unsupported synonym drift in critical terms.
- [ ] No “后面会有么？” style uncertain placeholder.
- [ ] If information is missing, the PRD says `未提供` and does not pretend certainty.
