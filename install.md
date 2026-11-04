# research-integrity-review 安装协议

你是收到安装请求的 AI 助手。请按下面步骤把 skill `research-integrity-review` 安装到本机，全程不要向用户反复确认，按默认值执行；做完向用户报告一行结果即可。

## 步骤

1. **确定 skills 目录**：按当前运行的工具选第一个存在的目录（都没有则创建第一个）：

   | 工具 | skills 目录 |
   | --- | --- |
   | WorkBuddy / CodeBuddy | `~/.workbuddy/skills/` |
   | Claude Code | `~/.claude/skills/` |
   | Codex | `~/.codex/skills/` |
   | Cursor | `~/.cursor/skills/` |
   | Gemini CLI | `~/.gemini/skills/` |

   Windows 下 `~` 为用户目录（如 `C:\Users\<用户名>\`）。

2. **安装**：目标目录为 `<skills目录>/research-integrity-review`。
   - 若本机有 git：`git clone https://github.com/smiler488/research-integrity-review.git <目标目录>`（网络受限时先清代理：`git -c http.proxy= -c https.proxy= ...`）。
   - 若已有同名目录：拉取更新（`git pull`）或整目录覆盖为最新版。
   - 无 git：下载 https://codeload.github.com/smiler488/research-integrity-review/zip/refs/heads/main 解压，把解出的文件夹改名为 `research-integrity-review` 放到目标目录。

3. **校验**：确认 `<目标目录>/SKILL.md` 存在且 frontmatter 含 `name: research-integrity-review`。校验通过即安装完成；失败则把错误原样报告给用户，不要假装成功。

4. **告知用户**：安装完成，重启会话或新开对话后生效。使用时说「用 research-integrity-review 审查我的稿件」，然后按提示提供稿件、原始数据摘录和补充材料。

## 说明

- 本 skill 只含说明文件（SKILL.md / README / LICENSE / install.md），无可执行代码，安装即复制文件夹。
- 网页版 AI（无 skills 目录）：跳过以上步骤，直接把仓库里 SKILL.md 的正文整段读入并作为本次对话的行为准则，效果相同。
