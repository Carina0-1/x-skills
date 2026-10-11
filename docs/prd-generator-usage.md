# prd-generator 使用说明

需要用时，按“安装 → 新建会话 → 提供项目和草稿”的顺序操作即可。

## 它能做什么

结合草稿或功能提纲、目标项目的原型代码和已有 PRD，生成格式统一的 Markdown 产品需求文档。
遇到资料里没有确定的产品决策，会向你确认；格式规范已随 skill 打包。

- [技能说明](../skills/prd-generator/SKILL.md)
- [PRD 格式规范](../skills/prd-generator/references/format-spec.md)

## 首次安装

在本机终端执行一次：

```bash
mkdir -p "$HOME/.agents/skills"
ln -s "/Users/abuer/code_project/Carina-skills/skills/prd-generator" \
  "$HOME/.agents/skills/prd-generator"
```

这是符号链接：本机加载目录指向仓库中的源文件，后续不用重复复制。
如果提示 `File exists`，先执行以下命令检查已有安装，不要直接覆盖：

```bash
ls -ld "$HOME/.agents/skills/prd-generator"
```

若已经指向本仓库，就不需要再次安装。换电脑或移动仓库后，需要重新建立指向实际仓库位置的链接。

## 调用方式

安装后新建本地会话，并打开需要编写 PRD 的业务项目。

- ChatGPT 桌面应用：在 Skills 中查看，通过 `@` 选择 `prd-generator`。
- Codex CLI / IDE 扩展：用 `/skills` 选择，或在消息中写 `$prd-generator`。
- 如果没有出现，重启应用或 Codex，并检查上述链接是否指向有效目录。

本地安装与 Git 远程同步是独立操作；推送仓库不会自动安装到其他设备或网页端。
参考：[OpenAI 官方 skills 文档](https://learn.chatgpt.com/docs/build-skills)。

## 可直接复制的请求

先选择该 skill，再发送下面的内容，将占位部分替换为实际信息：

```text
使用 prd-generator，结合草稿、原型代码和相关已有 PRD，生成正式的 Markdown PRD。

项目路径：<业务项目的完整路径>
草稿路径：<草稿文件的完整路径>
原型位置：<对应页面、组件或脚本的路径>
输出路径：<希望生成的 Markdown 文件完整路径>
修改人：<本次文档修改人的真实姓名>

关键产品规则有不明确的地方，请先向我确认，再定稿。
```

原教育平台项目的填写示例（将 `<模块名>` 替换为真实模块，确认文件存在）：

```text
项目路径：/Users/abuer/code_project/jinqiao/ecupl-education-platform
草稿路径：local.docs/手写文档/PRD-草稿 - <模块名>.md
原型位置：pages/ 下的对应页面及其引用的 assets/js/ 脚本
输出路径：local.docs/AI PRD/PRD <模块名>.md
修改人：<真实姓名>
```

相对路径均相对于业务项目根目录，不是相对于 `Carina-skills`。
其他项目不要求相同目录布局；未指定输出路径时，默认使用目标项目的 `local.docs/AI PRD/PRD {模块名}.md`。

## 更新与保存版本

直接修改本仓库中的 `skills/prd-generator/`，使用一个实际任务验证后提交。
符号链接会指向最新文件；当前会话未识别更新时，新建会话或重启应用。

保存本次迁入及使用说明时，在仓库根目录执行：

```bash
git diff
git add AGENTS.md README.md docs/ skills/
git commit -m "Import personal skills and document usage"
git push
```

原项目中的 skill 仍保留；修改仓库副本不会自动更新原项目中的那份副本。
