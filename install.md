# research-integrity-review 安装说明（给 AI 助手）

> 用户只需对 AI 助手说：
> `请根据 https://raw.githubusercontent.com/smiler488/research-integrity-review/main/install.md，安装 research-integrity-review。`

你是收到安装请求的 AI 助手。按下面的步骤把 Agent Skill `research-integrity-review` 装到本机，用默认值直接执行，不需要每一步都征求确认。只有一种情况要先问用户：目标目录已经存在、而且不是本仓库的 git 克隆（可能是用户自己改过的版本）。装完用一两句话告诉用户结果。

## 1. 确定安装目录

按当前运行的工具选择 skills 目录；如果目录还不存在就创建它：

| 工具 | 用户级 skills 目录 |
| --- | --- |
| Claude Code | `~/.claude/skills/` |
| Codex | `~/.codex/skills/` |
| WorkBuddy / CodeBuddy | `~/.workbuddy/skills/` |
| Cursor | `~/.cursor/skills/` |
| Gemini CLI | `~/.gemini/skills/` |

- 用户说只在当前项目里用时，改用项目内的目录，例如 `<项目>/.claude/skills/`。
- Windows 上 `~` 指 `C:\Users\<用户名>`。
- 目标目录记为 `TARGET = <skills 目录>/research-integrity-review`。目录名必须是 `research-integrity-review`，和 SKILL.md 里的 `name` 一致。

## 2. 下载

**有 git 时（推荐，方便以后更新）**

```bash
git clone --depth 1 https://github.com/smiler488/research-integrity-review.git "$TARGET"
```

如果 `TARGET` 已经是本仓库的克隆，改为更新：

```bash
git -C "$TARGET" pull --ff-only
```

**没有 git，macOS / Linux：**

```bash
mkdir -p "$TARGET"
curl -fsSL https://codeload.github.com/smiler488/research-integrity-review/tar.gz/refs/heads/main \
  | tar -xz --strip-components=1 -C "$TARGET"
```

**没有 git，Windows PowerShell：**

```powershell
$Target = "$HOME\.claude\skills\research-integrity-review"   # 按第 1 步换成实际目录
$Zip = "$env:TEMP\research-integrity-review.zip"
Invoke-WebRequest https://codeload.github.com/smiler488/research-integrity-review/zip/refs/heads/main -OutFile $Zip
Expand-Archive $Zip -DestinationPath "$env:TEMP\research-integrity-review-src" -Force
New-Item -ItemType Directory -Force $Target | Out-Null
Copy-Item "$env:TEMP\research-integrity-review-src\research-integrity-review-main\*" $Target -Recurse -Force
```

## 3. 依赖

无需安装额外依赖。

## 4. 检查

- `TARGET/SKILL.md` 存在，开头的 frontmatter 里有 `name: research-integrity-review`。
- 这些文件也在：`README.md`、`LICENSE`。

缺文件就说明下载不完整，删掉 `TARGET` 后重新执行第 2 步。

## 5. 告诉用户

报告安装路径，并提醒用户：**新开一个会话（或重启工具）后 skill 才会生效**。

用法示例："用 research-integrity-review 审查我的稿件"，或输入 `/research-integrity-review`。建议按图表分批提交，每次聚焦一到两个模块。

## 网页版助手（没有本地文件系统）

跳过安装。把 https://raw.githubusercontent.com/smiler488/research-integrity-review/main/SKILL.md 的正文读进对话，按其中的流程审查用户提供的稿件。

## 卸载

删除 `TARGET` 目录即可。

---

## English

Tell your assistant: `Install research-integrity-review following https://raw.githubusercontent.com/smiler488/research-integrity-review/main/install.md`

1. Pick the skills folder of the running tool (table above), e.g. `~/.claude/skills/`. Set `TARGET=<folder>/research-integrity-review`. The folder name must equal the `name` in SKILL.md.
2. `git clone --depth 1 https://github.com/smiler488/research-integrity-review.git "$TARGET"`. If it already exists as a clone, run `git -C "$TARGET" pull --ff-only` instead. Without git, use the curl or PowerShell commands above.
3. Check that `TARGET/SKILL.md` has `name: research-integrity-review` and that `README.md`, `LICENSE` exist.
4. Tell the user where it was installed and that a new session is needed. Example: "review my manuscript with research-integrity-review".

Chat-only assistants: read SKILL.md from the raw URL and follow it in the chat.

Uninstall: delete `TARGET`.
