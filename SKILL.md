---
name: weekly-business-brief
description: Generate Lu Guanlan's weekly operating brief from company daily-report Markdown. Use when the user provides 日报汇总, 部门日报, 每周经营简报, 周报, 经营风险, 下周重点, 陆观澜监督事项, or wants to convert daily report risks and todos into Tang Yuheng follow-up tasks.
---

# Weekly Business Brief

## Overview

This skill turns company daily-report Markdown into a weekly operating brief for 陆观澜, the chairman's strategic management secretary. It is designed for management review, risk discovery, business-line progress tracking, and task handoff to 唐予衡.

Always load `references/daily-report-framework.md` before producing the brief.

## Trigger Scenarios

Use this skill when the request is about:

- 根据日报汇总生成每周经营简报
- 汇总部门日报、项目日报、董事办日报
- 分析本周业务进展、经营风险、异常事项
- 梳理四大业务线推进情况
- 生成陆观澜需要监督的事项
- 把日报里的风险事项、待办事项转成唐予衡跟进任务

## Required Input

Accept one or more Markdown daily reports. Expected fields include:

- `【日报汇总 · 日期】`
- `已汇报 x/y`
- Department sections such as `项目部`, `董事办`, `市场部`, `留学部`, `身份部`, `财富管理`, `新媒体`, `财务`, `HR`
- Subsections such as `今日重点`, `数据成果`, `需关注`, `未汇报`

If only one daily report is provided, state that the brief is based on `本周截至当前` rather than pretending a complete week is available.

## Analysis Workflow

1. Identify the date range, reporting completeness, reporting departments, and missing reporters.
2. Extract each department's completed work, measurable outcomes, risks, blockers, customer/project updates, and next actions.
3. Deduplicate repeated items across days and keep the latest status.
4. Map all material into:
   - 国际教育规划
   - 全球身份规划
   - AI Agent开发与企业赋能
   - 财富管理与家族传承
   - 经营支撑与管理协同
5. Separate facts from judgment. Do not invent metrics, owners, deadlines, or outcomes.
6. Rate risks by impact on client delivery, revenue, renewal, cash flow, key projects, systems, or chairman-level priorities.
7. Convert actionable risks and todos into a structured task list that can be handed to 唐予衡.
8. Output the eight required sections in order.

## Output Requirements

Output in Chinese Markdown. Use this exact section order:

```markdown
# 每周经营简报

## 1. 本周经营摘要

## 2. 各部门进展

## 3. 四大业务线推进情况

## 4. 重点客户/重点项目动态

## 5. 异常与风险

## 6. 下周重点

## 7. 需要陆观澜监督的事项

## 8. 可转任务清单
```

### Section Rules

For `本周经营摘要`, include:

- 覆盖周期
- 汇报完整度
- 一句话结论
- 本周最重要进展
- 本周最重要风险

For `各部门进展`, summarize by department with:

- 本周重点
- 数据成果
- 需关注
- 未汇报影响

For `四大业务线推进情况`, include:

- 进展
- 风险
- 建议动作

For `重点客户/重点项目动态`, include only items that require management awareness or follow-up. Keep routine completed work brief.

For `异常与风险`, use a table:

```markdown
| 风险等级 | 事项 | 影响 | 建议动作 |
|---|---|---|---|
```

For `需要陆观澜监督的事项`, use a table:

```markdown
| 事项 | 为什么需要监督 | 建议监督方式 | 截止时间 |
|---|---|---|---|
```

For `可转任务清单`, use this YAML-like structure:

```yaml
- task_id:
  source:
  title:
  reason:
  priority:
  suggested_owner:
  due_date:
  acceptance_criteria:
  related_business_line:
  handoff_to:
```

## Task Handoff Rules

Create a handoff task only when there is a clear action to track. Suitable task candidates include:

- 授权失败、系统测试失败、资料缺失
- 客户续签、合同、付款、保单、补课、住宿、行程等待确认事项
- 跨部门协作事项
- 有明确截止时间或客户影响的风险
- 未汇报造成的信息缺口
- 需要唐予衡项目化跟进的事项

Use `handoff_to: 唐予衡` for execution tracking, deadline follow-up, cross-department coordination, and risk closure. Use `handoff_to: 陆观澜` only when the item needs strategic judgment before assignment.

## Style

Write like a strategic management secretary briefing the chairman: concise, factual, structured, and action-oriented. Start with conclusions. Avoid generic management slogans. Preserve enough source detail for follow-up, but do not turn the brief into a raw diary.

## Safety and Quality Rules

- Do not fabricate data, names, dates, owners, deadlines, or progress.
- If quantitative data is absent, say `未见明确量化数据`.
- Mark uncertain items as `待确认` or `需核验`.
- Do not expose unnecessary private information, ID numbers, phone numbers, bank details, or family details.
- Treat employee non-reporting as a management completeness issue, not a performance conclusion.
- Do not create tasks for routine completed work unless follow-up is required.

## Verification

Before finalizing, ensure:

- All eight required sections are present.
- Coverage period and reporting completeness are stated.
- Every business line with relevant material is covered.
- Risks include impact and suggested action.
- Each task has `acceptance_criteria`.
- The brief distinguishes completed facts from recommended actions.
