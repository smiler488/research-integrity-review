# research-integrity-review

English | [中文](README.zh-CN.md)

[![CI](https://github.com/smiler488/research-integrity-review/actions/workflows/validate.yml/badge.svg)](https://github.com/smiler488/research-integrity-review/actions/workflows/validate.yml) [![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE) ![Agent Skill](https://img.shields.io/badge/Agent_Skill-informational)
An Agent Skill that reviews a manuscript for research-integrity risks before submission, from the corresponding author's side. It goes through four groups of known manipulation patterns: image manipulation, data fabrication, text and process fraud, and newer forms involving generative AI. The result is a report graded 🔴 / 🟠 / 🟡 / 🟢. It reports suspicious points and the evidence for them, never a verdict of misconduct. Every hit has to be checked against the raw data by a person.

It accompanies my WeChat article 《CNS 论文造假的常见手段，与通讯作者的审查清单》 (account @smiler488). The point is to catch problems in your own group's work before an editor or a reader on PubPeer does.

## Install

Tell your assistant (WorkBuddy, Claude Code, Codex, …):

```text
Install research-integrity-review following https://raw.githubusercontent.com/smiler488/research-integrity-review/main/install.md
```

Or by hand:

```bash
git clone --depth 1 https://github.com/smiler488/research-integrity-review.git ~/.claude/skills/research-integrity-review
```

Other tools use `~/.codex/skills/`, `~/.workbuddy/skills/` and so on (see `install.md`). `research-integrity-review.skill` is the same content as a package for tools that import skill files. Chat assistants without skills (ChatGPT, DeepSeek, Kimi on the web) work too: paste the body of [SKILL.md](SKILL.md) as the first message.

## Use

1. Say "review my manuscript with research-integrity-review", or type `/research-integrity-review`.
2. Provide the manuscript (text, figures, legends), raw data excerpts if available, and the supplement.
3. Work figure by figure, one or two modules at a time. This finds more than handing over the whole paper at once.
4. Check every 🔴 and 🟠 item against the original records before drawing any conclusion.

## Modules

| Module | Covers |
| --- | --- |
| A Images and figures | reused / mirrored / relabelled panels, spliced blots, odd flow-cytometry clouds, spectra that break physics, n and error bars that do not match |
| B Data and statistics | identical or fixed-ratio values across groups, impossible percentages, statistics that do not add up, claims stronger than the data, traceability |
| C Text and references | reproducibility, misidentified cell lines, unsuitable antibodies, references that do not exist, duplicate publication, paper-mill templates |
| D Authorship, ethics, statements | gift or purchased authorship, ethics approvals, conflicts of interest, AI-use statements |

## Limits

The output is a screening aid. It does not establish misconduct by anyone. For pixel-level image duplication use dedicated tools such as ImageTwin, Proofig or FigCheck. Remove identifying details from unpublished manuscripts and data before uploading them to any third-party service.

## License

MIT, see [LICENSE](LICENSE). Liangchao Deng (邓良超).
