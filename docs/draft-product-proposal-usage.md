# draft-product-proposal 使用说明

用于产品立项、方向探索或 Demo 验证前，将产品想法、讨论记录或已有材料整理为可评审的产品方案初稿。

- [技能说明](../skills/draft-product-proposal/SKILL.md)
- [方案写作框架](../skills/draft-product-proposal/references/proposal-framework.md)

## 与 prd-generator 怎么选

| 需求 | 使用的 skill |
| --- | --- |
| 讨论服务谁、解决什么问题、首版做什么、如何验证 | draft-product-proposal |
| 将已明确的需求草稿结合原型展开为正式 PRD | prd-generator |

## 当前安装状态

迁入时，本机已有 `~/.codex/skills/draft-product-proposal/`，且已出现在当前会话的可用技能列表中。
这次将完整内容复制到仓库管理，保留原安装目录；无需重复安装。

仓库副本和原安装副本目前独立。修改本仓库不会自动更新已安装副本；如果未来需要统一维护，见下方“改为仓库链接”。

## 调用方式

在支持技能选择的本地会话中选择 `draft-product-proposal`。
ChatGPT 桌面应用使用 `@` 选择；Codex CLI / IDE 扩展使用 `/skills` 或 `$draft-product-proposal`。

可复制以下请求，并替换占位信息：

```text
使用 draft-product-proposal，根据以下想法生成可评审的产品方案初稿。

产品想法：<想解决的问题及拟议做法>
目标用户：<已知的用户或角色；未知可直接说明>
当前阶段：<方向探索 / Demo / 试点>
已有材料：<文件路径或讨论内容，没有则说明暂无>
首版约束：<已确定的范围和限制>
输出路径：<希望保存的 Markdown 文件路径>

请区分事实、假设和建议，明确首版范围及验证计划。
资料不足时可以采用明确标注的假设，关键方向有歧义时向我确认。
```

也可以直接说：

```text
使用 draft-product-proposal，把我们刚才讨论的想法整理成产品方案初稿，保存为 Markdown。
```

不需要先填齐所有信息。默认生成 Markdown；未指定路径时，保存到当前工作目录的 `产品名称-产品方案初稿.md`，产品名称未知时使用 `产品方案初稿.md`。
需要存入业务项目时，请明确输出路径，或先打开该项目。

## 改为仓库链接（以后需要时再执行）

为了保留已有安装位置并由仓库维护，先将原副本备份到技能加载目录之外，再创建链接。
以下操作会切换本机使用的副本；本次迁入没有执行这些操作。

```bash
mkdir -p "$HOME/.codex/skill-backups"
mv "$HOME/.codex/skills/draft-product-proposal" \
  "$HOME/.codex/skill-backups/draft-product-proposal-$(date +%Y%m%d-%H%M%S)"
ln -s "/Users/abuer/code_project/Carina-skills/skills/draft-product-proposal" \
  "$HOME/.codex/skills/draft-product-proposal"
```

仅在原路径仍是普通目录时执行；若已经是指向本仓库的链接，就不必再次操作。
检查方式：

```bash
ls -ld "$HOME/.codex/skills/draft-product-proposal"
```

切换后新建会话；未识别时重启应用。避免同时在多个技能加载位置安装同名副本。

## 更新与保存版本

建立链接后，直接维护 `skills/draft-product-proposal/`；在真实产品想法上验证效果，再提交。
统一保存本仓库的 skill 迁入及说明时，在仓库根目录查看差异后执行：

```bash
git diff
git add AGENTS.md README.md docs/ skills/
git commit -m "Import personal skills and document usage"
git push
```
