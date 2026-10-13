# Runweft Skill

让 Codex 和 Claude Code 通过对话安装、接入和维护 Runweft，并通过 MCP 委派任务、续接会话和取回代码与附件。

[Runweft 官网](https://runweft.pages.dev/) · [Skill 指令](skills/runweft/SKILL.md)

## 安装

选择实际使用的宿主，在自己的机器上安装：

```sh
# Codex
npx skills add iTgo-lyq/runweft-skill --skill runweft --agent codex -g --copy -y

# Claude Code
npx skills add iTgo-lyq/runweft-skill --skill runweft --agent claude-code -g --copy -y
```

安装前检查已有同名 Skill。已有修改时先备份到宿主扫描目录外，并确认替换范围；不要直接覆盖。项目内已经有 `.agents/skills/runweft/` 时可直接使用，不必再安装全局副本。需要项目安装时省略 `-g`。

此命令安装的是 Agent 指令。Runweft 程序通过 npm 安装，MCP 通过 Runweft CLI 接入；Skill 会指导 Agent 分别完成这两项操作。程序要求 Node.js 20+，支持 macOS arm64/x64 和 glibc Linux arm64/x64；执行任务需要已登录的 Codex 或 Claude Code。

## 使用

把目标直接交给 Agent，例如：

```text
使用 Runweft Skill 帮我连接已有 Hub，保留其他 MCP 和模型配置。
```

身份由用户在浏览器中创建或导入并确认，不需要把 token 发给 Agent。Skill 按安装接入、中心配置、委派和维护选择对应参考资料。

## 更新

确认来源及本地修改后，按实际安装范围更新：

```sh
# 全局安装
npx skills update runweft -g -y

# 项目安装
npx skills update runweft -p -y
```

Skill 更新与 Runweft 程序升级分别进行。Agent 操作前会核对实际程序版本与 `--help`，不会把 Skill 更新当成程序升级。

## 分发来源

本仓库是公开分发入口，仅包含完整的 `skills/runweft/` 和安装说明。Skill 由 Runweft 开发仓库的 `.agents/skills/runweft/` 单向同步，提交记录来源 revision；请在开发仓库维护内容，避免手改随后会被同步覆盖的公开副本。

公开仓库不包含 Runweft 程序源码。GitHub 可读取和 CLI 可安装不等于 skills.sh 已经收录，平台搜索结果取决于安装遥测及索引。
