# scientific-review-writing

用于中文科研技术报告的 Codex skill，支持探测器定标、性能测试和实验评审材料的起草、科学审阅与文风修订。

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

## 规则覆盖

- 将科学审阅与文风修订分开，按任务范围选择动作。
- 保护公式、关键推导、统计口径、不确定度及可辨识性边界。
- 用具体科学问题连接章节，正文围绕当前有效证据组织。
- 保留影响方法选择或结论可靠性的比较，区分不同用途的统计量。
- 给出关键近似的误差尺度，在明确条件下简化误差传播关系。
- 让图示解释实际测量关系，让工程结论对应已有证据与验证范围。
- 减少空泛反衬、重复免责声明和无实际作用的转折，保持正式科研语体。
- 清楚表达证据支持的贡献，去除无依据的歉意与自我贬低，保留科学限定及不利结果。
- 保持既定评价口径，依据双方证据讨论性能取舍，不为突出优势补造理由。

## 文件说明

| 文件 | 用途 |
|---|---|
| [SKILL.md](SKILL.md) | 技能入口、工作模式与内容保护规则 |
| [agents/openai.yaml](agents/openai.yaml) | 显示信息与显式调用设置 |
| [references/language-style.md](references/language-style.md) | 中文语体、反防御性表达、章节衔接与正文信息取舍 |
| [references/scientific-reasoning.md](references/scientific-reasoning.md) | 建模、处理、推导、结果与实验设计 |
| [references/boundary-examples.md](references/boundary-examples.md) | 具体修订示例与科学边界 |
| [references/report-format.md](references/report-format.md) | 可按任务覆盖的图表与公式格式偏好 |

本仓库包含技能规则与说明性示例，不包含实验原始数据或内部报告。示例中的数值不能作为新报告的实测依据。图内英文标注、Word 原生公式等为默认格式偏好，具体任务与模板要求优先。

技能负责内容与语言约束。实际 Word/PDF 排版和公式结构检查需要相应的文档工具。
