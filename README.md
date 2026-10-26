<div align="center">

# 案头 · Folio Desk

### 从一叠材料，到一篇有据可查的报告。

问卷、访谈、田野记录、政策文件、课程资料。把它们放到案头，先理清证据，再动笔。

[开始使用](#开始使用) · [安装说明](INSTALL.md) · [使用示例](#把任务交给案头) · [问题反馈](https://github.com/xuedai-mayi/folio-desk/issues)

</div>

---

## 材料已经有了，报告从哪里开始？

Folio Desk 是一套用于中文研究报告的 Agent Skills。它指导支持 Skill 的 AI 阅读材料、整理事实与出处、安排章节，并按任务需要核验外部来源、审校中文和生成 Word 文档。

你不必先写好目录。提供材料、报告用途和格式要求，就可以从材料审读开始。需要补充的信息集中确认；没有证据的内容保留为待确认项。

| 你手里的材料 | 可以着手的工作 |
| --- | --- |
| 问卷结果、访谈记录 | 梳理研究问题，组织调查发现，说明样本与结论的适用范围 |
| 实践日志、活动记录、反馈材料 | 区分计划与实际成果，把行动过程和调研发现写清楚 |
| 政策文件、案例、文献 | 比较来源，核验外部事实，形成有出处的分析 |
| 已有草稿、课程任务书、学校模板 | 调整论证与表达，按要求整理可编辑的 Word 文档 |

## 开始使用

先克隆当前仓库：

```bash
gh repo clone xuedai-mayi/folio-desk
```

将仓库交给支持 Skill 且能读取本地文件的 AI，并发送：

```text
请检查这个仓库，阅读 INSTALL.md 和 MANIFEST.json，
将 skills 下的四个 Skill 安装到当前平台的用户级技能目录。
同名项目先比较，不直接覆盖。安装不需要运行仓库脚本。
完成后按 INSTALL.md 做只读测试，并告诉我安装路径和未通过的项目。
```

也可以按照 [INSTALL.md](INSTALL.md) 手动复制四个 Skill 文件夹。各平台的目录与加载方式不同；这套仓库提供的是技能文件，实际文件读取、联网检索和 Word 生成依赖所用 AI 环境的工具能力。

## 把任务交给案头

安装后，用下面的请求开始，把方括号替换为你的实际信息：

```text
请使用 humanities-report-writer。

材料位置：[文件夹或附件]
报告用途：[课程作业、社会实践、调研结项等]
交付要求：[篇幅、模板、格式和截止时间]

先读完材料，整理能确认的事实和缺口，再确定章节。
能从文件中找到的信息请直接查找，需要我补充的问题集中提出。
最终交付 Word；数字、引语和文献都要有依据。
```

`humanities-report-writer` 是安装后的主 Skill 调用名。Folio Desk 是整套工具的名称。

## 一份报告如何完成

**先读材料。** 主 Skill 整理文件并建立事实底表，为关键事实记录来源位置、证据状态和允许的表述范围。任务书和用户模板优先。

**再组织论证。** 根据问题和材料选择结构，区分调查结果、解释与结论。需要查政策、文献或时效性事实时，调用来源核验 Skill；参考范例用于学习结构，不复制原文。

**最后审校与交付。** 回查事实和引用，用 humanizer 审校中文。需要 Word 时应用模板，检查样式、编号、目录、图表和分页。缺少必要工具或未完成验证时，应说明尚未完成的部分。

## 案头的四个组成部分

| Skill | 负责什么 |
| --- | --- |
| [`humanities-report-writer`](skills/humanities-report-writer/SKILL.md) | 材料审读、事实底表、报告结构与正文统筹 |
| [`source-grounded-research`](skills/source-grounded-research/SKILL.md) | 外部资料检索、范例学习与来源核验 |
| [`humanizer`](skills/humanizer/SKILL.md) | 中文终稿审校，减少机械表达，保留原有事实与限定条件 |
| [`word-report-delivery`](skills/word-report-delivery/SKILL.md) | Word 套版、格式整理、文件与逐页视觉检查 |

仓库附有[事实底表模板](skills/humanities-report-writer/assets/事实底表模板.csv)、[Word 模板](skills/word-report-delivery/assets/通用人文社科报告模板.docx)和[简明使用手册](docs/通用人文社科报告写作Skill_极简说明书.docx)。

## 写作约定

- 不补造姓名、数字、活动、引语或文献；材料缺口要明确标出。
- 区分相关与因果，不把有限样本写成所有人的情况。
- 原始材料默认只读，成稿另存；公开内容按要求处理个人信息。
- 正式提交前，由使用者核对署名、关键数据、引用及公开范围。

## 开源与参与

Folio Desk 自编内容采用 [MIT License](LICENSE)。随包的 `humanizer` 来自 [Siqi Chen / blader/humanizer](https://github.com/blader/humanizer)，版本为 **2.9.1**，上游提交为 `523374dee72d67c7b2b5f858ea0094ffda49c3ac`，保留完整文件及[独立 MIT 许可](skills/humanizer/LICENSE)。来源记录与文件哈希见 [NOTICE.md](NOTICE.md)。

改进建议和问题反馈请参阅 [贡献说明](CONTRIBUTING.md)；涉及隐私或安全的问题请按 [安全策略](SECURITY.md) 私密报告。
