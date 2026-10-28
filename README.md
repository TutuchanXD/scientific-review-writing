# scientific-review-writing

用于中文科研材料的 Codex skill，支持探测器定标、性能测试、技术评审、相关基金申请及PPT讲稿的起草、科学审阅与文风修订。书面材料与口头讲稿按各自用途采用相应语体。

核心优先级：**科学正确性 > 论证完整性 > 信息密度 > 中文自然度 > 文风优化**。保留“前提—关系式—推导—结果—适用边界”，让读者理解每一步推导和处理的目的。

## 安装与调用

在支持 `$skill-installer` 的 Codex 中发送：

```text
使用 $skill-installer 从 https://github.com/TutuchanXD/scientific-review-writing 安装仓库根目录的 skill，安装名为 scientific-review-writing。
```

本仓库根目录就是完整的 skill 目录。也可以将仓库内容放入 Codex 的用户级 `~/.agents/skills/scientific-review-writing/`，或项目级 `.agents/skills/scientific-review-writing/`。安装后若未显示，重启 Codex。安装与发现机制见 [OpenAI 官方技能文档](https://learn.chatgpt.com/docs/build-skills)。

本技能配置为**仅显式调用**。在任务中写出 `$scientific-review-writing`，并说明所需工作类型：

```text
使用 $scientific-review-writing 审阅这份实验报告。
先检查建模、推导、统计解释和证据链，给出问题位置及修改建议，暂不改正文。
```

```text
使用 $scientific-review-writing 润色这段正文。
只修改文风，保留公式、变量定义、假设、推导步骤、结果和适用边界。
```

```text
使用 $scientific-review-writing 根据这些材料起草评审报告。
说明章节之间的科学问题如何衔接，保留关键近似的展开和误差量级依据。
```

```text
使用 $scientific-review-writing 审阅这份基金申请，暂不改正文。
检查科学需求、已有成果、新增研究和验证方法的联系，以及申请人贡献与团队基础是否清楚。
```

基金申请按文稿用途选择论证重点，仍受起草、科学审阅、仅文风修订三种工作类型的权限约束。具体规则见 [基金申请论证](references/grant-proposal.md)，不将固定申请模板或个别项目参数作为通用要求。

## PPT评审讲稿

```text
使用 $scientific-review-writing 根据这份PPT和任务书起草逐页讲稿。
先通读页面与已认可的备注，顺着图表解释处理步骤、目的和输入输出关系。
面向科学与工程专家，按指定报告时长安排每页重点，只讲所提供材料中的内容。
保留自然的第一人称、必要的指图和点击提示，指标数值及适用条件保持准确。
```

讲稿以用户认可的最新同用途样本为文风参考，允许有依据的口头释义，并按各页任务安排解释篇幅。报告和申请书继续采用科研书面语；仅文风修订仍须保留独立科学信息。具体规则见 [PPT评审讲稿](references/presentation-script.md)。

## Gemini 中文审阅

正文起草或修订后，默认使用 **Gemini 4 Argon** 审阅本次范围内的完整中文文稿，采用用户手动提交和回传的方式：

1. Codex 完成科学核查与初稿，准备包含审阅要求和完整正文的可复制文本。
2. 用户在 Gemini 新对话中选择 4 Argon，提交材料。
3. 用户将完整修订结果回传；Codex 检查覆盖范围、公式、数据、条件和结论，合并通过复核的修改。

科学含义准确的中文修订优先保留，不再按 Codex 的惯用文风重写。默认不使用 Computer Use 或自动上传；只要求科学审阅或明确跳过此环节时，按本次任务范围执行。提示词准备完成不代表 Gemini 已完成审阅。交接模板、长文处理及回传核查见 [工作流说明](references/gemini-review.md)。

## 规则覆盖

- 将科学审阅与文风修订分开，按任务范围选择动作。
- 保护公式、关键推导、统计口径、不确定度及可辨识性边界。
- 用具体科学问题连接章节，正文围绕当前有效证据组织。
- 保留影响方法选择或结论可靠性的比较，区分不同用途的统计量。
- 给出关键近似的误差尺度，在明确条件下简化误差传播关系。
- 让图示解释实际测量关系，让工程结论对应已有证据与验证范围。
- 减少空泛反衬、重复免责声明和无实际作用的转折，保持与用途相符的科研语体。
- PPT讲稿结合页面解释具体对象、步骤及目的，保留有信息的口头释义与演示提示。
- 清楚表达证据支持的贡献，去除无依据的歉意与自我贬低，保留科学限定及不利结果。
- 保持既定评价口径，依据双方证据讨论性能取舍，不为突出优势补造理由。
- 基金申请明确研究必要性、新增贡献、个人分工及可检验的创新主张。
- 核对跨章节预算、统计汇总顺序和对照条件，将评审意见落实为相应论证。
- 同步规划图表与文献，分别检查源稿、保存结果和最终交付呈现。

## 文件说明

| 文件 | 用途 |
|---|---|
| [SKILL.md](SKILL.md) | 技能入口、工作模式与内容保护规则 |
| [agents/openai.yaml](agents/openai.yaml) | 显示信息与显式调用设置 |
| [references/language-style.md](references/language-style.md) | 中文语体、反防御性表达、章节衔接与正文信息取舍 |
| [references/presentation-script.md](references/presentation-script.md) | PPT讲稿语体、页面讲解、口头释义、数字层次与演示衔接 |
| [references/scientific-reasoning.md](references/scientific-reasoning.md) | 建模、处理、推导、结果与实验设计 |
| [references/boundary-examples.md](references/boundary-examples.md) | 具体修订示例与科学边界 |
| [references/report-format.md](references/report-format.md) | 可按任务覆盖的图表与公式格式偏好 |
| [references/gemini-review.md](references/gemini-review.md) | Gemini 4 Argon 中文审阅交接模板与回传复核 |
| [references/grant-proposal.md](references/grant-proposal.md) | 基金申请主线、创新性、贡献归属、目标与验证、定稿收敛 |

本仓库包含技能规则与说明性示例，不包含实验原始数据或内部报告。示例中的数值不能作为新报告的实测依据。图内英文标注、Word 原生公式等为默认格式偏好，具体任务与模板要求优先。

技能负责内容与语言约束。实际 Word/PDF 排版和公式结构检查需要相应的文档工具。

维护时可用 [边界示例](references/boundary-examples.md) 检查规则，并以未见过的自拟材料实际测试起草和受限修订。结构校验不等于行为验证，样例通过也不保证资助结果。公开仓库仅保留通用规则和自拟示例，实际申请材料、评审回传和实验记录不进入仓库。
