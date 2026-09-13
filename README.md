# Humanizer — Academic Writing

[English](README.en.md)

目前原生适配 Codex。仓库提供完整的 `SKILL.md`、中英文参考文件及 `agents/openai.yaml`，采用显式手动触发。仓库名为 `humanizer-academic-writing`；安装目录和调用名保留 `evidence-grounded-academic-writing`，兼容已有使用方式。

一个面向 Codex 的中英文学术写作 skill，用于在证据边界内撰写、翻译、润色和审查学术文本。它强调可核查的主张、准确的主张强度、稳定的术语和适合目标场所的语言，而不把“写得像人”变成编造、改写事实或追逐 AI 检测器分数。

## 使用方式

这是手动触发的 skill。需要使用时显式调用：

```text
$evidence-grounded-academic-writing
```

然后说明语言、任务模式、证据范围和目标期刊或其他出版规范。其他 agent 如需使用，可手动加载 `SKILL.md` 及适用的参考文件；本项目尚未验证它们的自动发现与调用行为。

例如：

```text
使用 $evidence-grounded-academic-writing 润色以下中文讨论段落。
保留数值、引用编号和结论强度；证据不足之处请标记。
只输出改写正文。材料：……
```

## 四种模式

- **撰写**：只使用作者提供或已经核验的材料，不补造研究对象、数据、结果或文献。
- **翻译**：保持否定、情态、归因、因果强度、时态、范围和术语关系；发现歧义时标记，不默默解决。
- **润色**：改善清晰度、连贯性和目标语体，同时保护源文含义、证据边界和引用信息。
- **审查**：报告主张、证据、引用、逻辑和风格问题及其建议；默认不重写源文。

所有模式都遵守语义锁定、引用核验、作者控制和适用的 AI 辅助披露要求。缺少关键依据时，应保留 `[需作者补充]` 或 `[需核验]` 等占位，而不是把未知内容写成事实。

## 安装

推荐将公开仓库克隆到 Codex skills 目录：

```bash
git clone https://github.com/xinanli2001-cell/humanizer-academic-writing \
  ~/.codex/skills/evidence-grounded-academic-writing
```

如果目标目录已经存在，请不要直接覆盖。可以先克隆到临时目录，再比较文件并手动合并需要的更新；也可以保留现有目录，逐项手动复制经过审阅的文件。安装前后都应检查 `SKILL.md`、`references/` 和 `agents/openai.yaml` 的完整性。

## 文件结构

```text
evidence-grounded-academic-writing/
├── SKILL.md
├── README.md
├── README.en.md
├── agents/
│   └── openai.yaml
└── references/
    ├── chinese-academic-style.md
    └── english-academic-style.md
```

`SKILL.md` 定义核心原则、四种模式、证据与语义边界和交付规则。中文任务读取 `references/chinese-academic-style.md`，英文任务读取 `references/english-academic-style.md`，双语任务同时读取两份。`agents/openai.yaml` 提供 Codex 展示名称、默认提示和手动触发策略。

## 风格边界

参考文件中的“约 30% 口语、70% 学术”只是阅读感受上的偏好，不是实证指标、字数配额或验收标准。风格文件是可编辑的；目标期刊、会议、学校或出版社的明确要求，以及作者提供的样文和材料，在各自适用范围内优先。

本 skill 不声称能够识别 AI 作者身份、降低或通过任何 AI 检测器，也不以检测器分数作为质量证据。正式投稿前仍需作者核查事实、引文、披露、署名、伦理、许可和目标场所要求。

## 来源与致谢

本包整理自作者的中英文学术写作偏好、证据核查边界和 Codex 辅助开发实践，并借鉴了 [Humanizer](https://github.com/blader/humanizer) 中与自然表达相关的启发。借鉴不代表官方关联、共同维护或行为效果背书。第三方来源与许可说明见 [`THIRD_PARTY_NOTICES.md`](THIRD_PARTY_NOTICES.md)。

本项目以 MIT License 发布，完整许可文本见 [`LICENSE`](LICENSE)。结构校验通过不等于已经证明写作效果，使用者应审阅实际改写结果。

## 贡献

欢迎提交小而可核查的改进：请先说明问题、适用语言和预期边界，再提出对应补丁。新增规则应给出可观察的理由，避免把单个词、标点或句式当作作者身份证据；不要加入未经核验的文献、数据、机构关系或效果承诺。修改风格时同步检查相关参考文件，并保留手动触发和证据优先原则。

提交前请确认只改动必要文件，且没有把私人路径、私人手稿示例或未公开材料带入仓库。发布、提交和许可变更由维护者另行处理。
