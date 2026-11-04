# research-integrity-review · 科研诚信投稿前审查 Skill

给通讯作者的 AI 审查 skill：投稿前让 AI 按「图像操纵 / 数据伪造 / 文本与流程造假 / 生成式 AI 新形态」四类造假手法逐项筛查稿件，输出 🔴🟠🟡🟢 四级疑点报告。只报告疑点和证据，不下"造假"结论，所有命中项以原始数据人工复核为准。

配套文章：《CNS 论文造假的常见手段，与通讯作者的审查清单》（微信公众号 @smiler488）。

## 安装

把本仓库克隆（或下载解压）到你的 AI 工具的 skills 目录：

```bash
# Claude Code
git clone https://github.com/smiler488/research-integrity-review.git ~/.claude/skills/research-integrity-review

# WorkBuddy / CodeBuddy
git clone https://github.com/smiler488/research-integrity-review.git ~/.workbuddy/skills/research-integrity-review

# Codex CLI
git clone https://github.com/smiler488/research-integrity-review.git ~/.codex/skills/research-integrity-review
```

Windows 下把 `~/` 换成用户目录（如 `C:\Users\<你>\`）对应路径。不支持 skill 的 AI 工具（网页版 ChatGPT、DeepSeek、Kimi 等）：直接把 [SKILL.md](./SKILL.md) 正文整体复制成对话的第一条消息，效果相同。

## 使用

1. 对 AI 说：**"用 research-integrity-review 审查我的稿件"**（或直接输入 `/research-integrity-review`）。
2. 按提示提供：①论文稿件（正文、图表、图注）；②原始数据摘录（可缺省）；③补充材料。
3. 按图表分批、每次聚焦一到两个模块，检出效果比一次塞整篇好。
4. 收到分级报告后，🔴🟠 项逐条调取原始记录人工复核再定性。

## 检查模块

| 模块 | 覆盖 |
| --- | --- |
| A 图像与图表完整性 | 图复用/镜像/换标签、条带合成特征、流式散点图异常、谱图物理常识、样本量与误差线咬合 |
| B 数据真实性与统计自洽 | 组间逐点相同/固定倍数、百分比合理性、统计结果咬合、结论强度、数据可追溯 |
| C 文本与参考文献 | 可复现性、假细胞系/不匹配抗体、引用真实性、重复发表、论文工厂模板痕迹 |
| D 署名、伦理与声明 | 挂名/交易署名/作者拼盘、伦理审批、利益冲突与 AI 使用声明 |

## 边界与免责

本 skill 输出只做筛查参考，不构成对任何人的学术不端认定。像素级图片查重请交 ImageTwin、Proofig、FigCheck 等专用工具；未发表稿件与数据请脱敏后再上传第三方服务。

## License

MIT
