# Daily Report Framework

## Daily Report Structure

Daily reports usually follow this pattern:

```markdown
【日报汇总 · 2026-07-08】
已汇报 7/12

一、项目部
今日重点：
· ...

数据成果：
· ...

需关注：
· ...

未汇报：无
```

Parse by date, then by department, then by subsection.

## Field Meaning

- `今日重点`: work completed today, active coordination, project movement, customer or internal delivery.
- `数据成果`: measurable or verifiable results, including counts, completed documents, signed contracts, paid items, updated files, or delivered reports.
- `需关注`: blockers, risks, pending decisions, unresolved dependencies, deadlines, missing resources, system failures.
- `未汇报`: missing reporters or departments; use this to judge information completeness.

## Weekly Merge Rules

- Merge repeated items and keep the latest status.
- Escalate repeated blockers that appear across multiple days.
- Preserve date-specific deadlines.
- If only one daily report is provided, label the output as `本周截至当前`.
- If the report says `已汇报 7/12`, mention both the reported ratio and the potential management impact.

## Business-Line Mapping

| Daily report item | Business category |
|---|---|
| 学生申请评估、GPA管理、宿舍申请、补课、留学配图、163邮箱测试 | 国际教育规划 |
| 香港身份规划、身份客户、身份供应商、身份方案说明 | 全球身份规划 |
| Agent功能说明、Skill开发、智能文档、云手机、日报触发、企业微信授权、知识库 | AI Agent开发与企业赋能 |
| 保单、续保、保险客户、二级市场客户净值、期货账户、收益表 | 财富管理与家族传承 |
| Token费用、服务器预算、资金报表、合同、办公室场地、董事长行程、活动安排 | 经营支撑与管理协同 |

## Risk Signals

High-risk signals:

- 客户交付、续签、合同、付款、保单、行程或系统可用性受到影响。
- 重要客户事项有明确截止时间且状态未闭环。
- 多次失败、无法授权、无法交付、客户材料或签字卡住。

Medium-risk signals:

- 跨部门依赖未明确负责人。
- 素材、数据、预算、供应商价格待确认。
- 智能化框架仅完成基础搭建，后续路径未明确。

Low-risk signals:

- 普通资料待补充。
- 已有替代方案且不影响客户交付。
- 仅需信息同步。

## Task Candidate Signals

Create task candidates for phrases or situations such as:

- `待确认`
- `需跟进`
- `待完善`
- `多次失败`
- `缺失`
- `预算沟通`
- `供应商洽谈`
- `重点关注`
- `未汇报`
- `截止`
- `客户手签`
- `续签`

Do not create a task for ordinary completed work unless there is a next action.

## Task Priority

- `P0`: same-day executive risk, client delivery risk, payment/contract/blocking issue.
- `P1`: close within 1-3 days.
- `P2`: track this week.
- `P3`: informational or low urgency.

## Handoff Acceptance Criteria

Each task should include an acceptance criterion such as:

- 已完成确认并在日报中回写结果。
- 已形成书面方案/清单/预算表。
- 已获得客户或供应商明确反馈。
- 已完成系统测试并记录异常原因。
- 已同步陆观澜并标记是否需要董事长决策。
