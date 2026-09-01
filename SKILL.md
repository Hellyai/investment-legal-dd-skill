---
name: full-investment-legal-dd
description: 为投资机构处理资料回传后的法律尽调。资料不完整时先生成尽调重点及问题分析Word，待客户确认后再生成补充尽调清单Word；资料达到门槛或客户明确指令时生成正式完整版法律尽调报告Word。仅有BP或立项材料时改用early-investment-legal-dd。
---

# 完整投资尽调法律

版本：v2026.09.01.1

## 适用入口

至少满足一项：已经收到第一轮尽调资料；需要根据回传资料提出补充问题；需要对专项资料形成法律分析；资料基本齐备，需要完整法律尽调报告。

只有BP、立项报告或路演材料时，切换至 `$early-investment-legal-dd`，不在本 skill 内重做初期筛查。

## 两种交付模式

### 补充尽调模式

分两个阶段生成两个Word，不得在客户确认前一次性生成：

1. **第一阶段——尽调重点及问题分析Word**：更新事实、证据、法律分析、投资影响和处理建议；交付后在对话框请求客户确认问题判断和补充方向，并暂停；
2. **第二阶段——补充尽调清单Word**：客户确认后，只列缺失、部分提供、矛盾、新风险触发和需确认事项，不重发全量初始清单，并按 [checklist-format.md](references/checklist-format.md) 制作。

不得将两部分合并为一个Word。

补充尽调清单不设置“提出原因”或“拟核实问题”列。

### 完整报告模式

资料达到正式报告出具门槛，或者客户明确指令出具完整报告时，生成正式完整版法律尽调报告Word。客户明确指令可以覆盖资料门槛，但不能降低报告结构、分析深度和证据披露要求；资料不足造成的结论限制必须逐项披露。完整报告不是红旗备忘录或交易闭环简版：既要完整记录各主体历史事实并发表法律分析，也要将风险转化为投资及交易处理措施。

报告应先按 [report-completeness.md](references/report-completeness.md) 评估资料完备程度，并按 [final-report.md](references/final-report.md) 逐主体、逐轮次、逐事项展开。成文格式可按 [report-format-profiles.md](references/report-format-profiles.md) 选择“综合展开型”或“问题前置型”；两种格式适用同一完成标准，不得以格式选择或资料不足为由压缩事实、论证或附件。

完整报告完成后，仅在用户明确同意并确认入选问题时，才可按 [ic-red-flag-ppt.md](references/ic-red-flag-ppt.md) 另行生成投决会红旗PPT。不得以该PPT替代完整报告。

## 文件交付硬门槛

除非用户明确要求纯聊天输出，补充尽调第一阶段必须调用 `documents` 生成并逐页校验“尽调重点及问题分析” `.docx`；客户确认后，第二阶段再生成并校验“补充尽调清单” `.docx`。完整报告模式生成一个正式完整版报告 `.docx`。对话框只返回摘要、确认请求和文件链接；只在聊天中写出分析不构成交付。默认保存至 `当前项目或工作区/尽调输出/项目代号/`，不得覆盖旧版本。

## 启动与交接

1. 优先读取初期skill的交接卡、行业确认和首轮清单；已有确认时不重新询问行业。
2. 没有交接卡时，从现有资料重建项目范围、集团主体、交易方式、资料截止日和行业确认状态。
3. 仅当新证据显示行业分类实质错误时，暂停行业化结论并请求委托方重新确认；不得静默换行业。
4. 原始资料只读，不移动、不改名、不覆盖；建立虚拟索引和稳定编号。

## 路由

每次读取：

- [workflow.md](references/workflow.md)：资料回传、补充和报告流程；
- [core-dd.md](references/core-dd.md)：完整尽调底盘；
- [evidence-risk-ledgers.md](references/evidence-risk-ledgers.md)：请求、事实、问题和交易闭环；
- [output-contract.md](references/output-contract.md)：补充清单及报告输出；
- [document-delivery.md](references/document-delivery.md)：Word生成和检查。
- [checklist-format.md](references/checklist-format.md)：初步/补充清单的栏目、编号和状态格式。

按 [industry-routing.md](references/industry-routing.md) 核对已确认行业，并只加载对应主行业包：

- AI：[industry-ai.md](references/industry-ai.md)
- 半导体/芯片：[industry-semiconductor.md](references/industry-semiconductor.md)
- 先进制造：[industry-advanced-manufacturing.md](references/industry-advanced-manufacturing.md)
- 核聚变/聚变能源：[industry-nuclear-fusion.md](references/industry-nuclear-fusion.md)
- 出海叠加层：[outbound-overlay.md](references/outbound-overlay.md)

按创业背景加载 [background-overlays.md](references/background-overlays.md)。按范围加载五个专项：

- 历史融资与股权沿革：[topic-financing-history.md](references/topic-financing-history.md)
- 知识产权及争议：[topic-ip.md](references/topic-ip.md)
- 重大业务合同：[topic-major-contracts.md](references/topic-major-contracts.md)
- 创始人及核心团队：[topic-team.md](references/topic-team.md)
- 业务资质与行业准入：[topic-business-qualifications.md](references/topic-business-qualifications.md)

完整报告读取：

- [report-completeness.md](references/report-completeness.md)：出具门槛、覆盖矩阵和必备附表；
- [final-report.md](references/final-report.md)：正文结构、事实颗粒度和论证标准；
- [report-format-profiles.md](references/report-format-profiles.md)：综合展开型与问题前置型两种成文格式；
- [anonymization.md](references/anonymization.md)：模板沉淀和示例脱敏。

用户要求投决会红旗PPT时，另读 [ic-red-flag-ppt.md](references/ic-red-flag-ppt.md)。

## 结论纪律

- 区分公司陈述、文件事实、履行证据、公开核验和律师判断；
- 缺资料不等于违法，使用“无法确认—若发生—可能影响”的条件式结论；
- 法律法规、许可、监管和制裁信息核验至报告基准日；旧报告和IPO/挂牌文件只作问题发现参考；
- 重大和高风险必须转化为交割条件、承诺、陈述保证、赔偿、价格调整、风险接受或投后跟踪；
- 用户指定主题输出时可以调整深度，但不得遗漏对投资结论有实质影响的范围外红旗。

## 能力边界

- 股权表、融资轮次稀释和反稀释测算调用 `captable`。
- 投资协议、股东协议、章程、披露函或交割文件逐条审阅调用 `vc-investment-review`。
- 仅有BP或立项材料时调用 `$early-investment-legal-dd`。
