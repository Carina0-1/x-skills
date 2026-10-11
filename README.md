# Carina Skills

个人 skills 仓库，用于维护自建或高频使用的 skills，并通过 Git 保存版本。

## 目录

```text
skills/
└── <skill-name>/
    ├── SKILL.md           # 必需：name、description 和执行步骤
    ├── scripts/           # 可选：脚本
    ├── references/        # 可选：参考资料
    ├── assets/            # 可选：模板和资源
    └── agents/openai.yaml # 可选：显示信息和依赖
```

每个 skill 使用独立目录，目录名与 `SKILL.md` 的 `name` 保持一致。

## 迁入已有 skill

1. 将整个 skill 目录复制到 `skills/`，保留脚本、参考资料和资源。
2. 检查原项目绝对路径和外部文件依赖，尽量使用相对 skill 目录的路径。
3. 使用一个实际任务验证，再提交。验证前保留原项目中的文件。
4. 第三方 skill 保留原许可证，并在下方清单记录来源与版本。

## 本地使用

将需要跨项目使用的 skill 链接到 `~/.agents/skills/`。以下命令中的 `my-skill` 需替换为实际目录名：

```bash
mkdir -p "$HOME/.agents/skills"
ln -s "/Users/abuer/code_project/Carina-skills/skills/my-skill" \
  "$HOME/.agents/skills/my-skill"
```

若目标已存在，先检查来源，不直接覆盖。链接建立后，直接修改本仓库即可；保持仓库路径稳定。

仅在某个项目使用时，可将该 skill 安装到项目的 `.agents/skills/`。指向本机绝对路径的链接不适合提交给其他机器使用。

支持本地 skills 的 ChatGPT 桌面应用可在 Skills 中查看并通过 `@` 选择；Codex CLI / IDE 扩展可使用 `/skills` 或 `$skill-name`。未显示时，重启应用后检查。

Git 推送用于同步源文件，不会自动安装到 ChatGPT 账号、网页端或手机端。

参考：[OpenAI 官方 skills 文档](https://learn.chatgpt.com/docs/build-skills)。

## 版本管理

首次使用时，在仓库根目录初始化并创建首次提交：

```bash
git init -b main
git add README.md AGENTS.md .gitignore skills/.gitkeep
git commit -m "Initialize personal skills repository"
```

日常流程：修改 → 实际任务验证 → 查看差异 → 提交 → 推送。

```bash
git diff
git add skills/<skill-name>/
git commit -m "Improve <skill-name> workflow"
git push
```

目标远程仓库：`git@github.com:Carina0-1/x-skills.git`。

初次连接远程，在本地仓库初始化后执行：

```bash
git remote add origin git@github.com:Carina0-1/x-skills.git
git push -u origin main
```

跨机器使用时，克隆仓库后重新建立本机链接。日常更新用 `git pull --ff-only`。

不要提交账号凭据、API key 或含私人数据的任务输出。

## Skill 清单

待迁入第一个 skill。后续记录名称、用途、来源、版本及依赖。
