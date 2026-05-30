# MySkills

个人 AI Coding Assistant Skill 合集。每个 skill 是一个独立的 Markdown 文件，包含 YAML frontmatter（元数据）+ Markdown body（AI 指令），**不绑定任何特定平台**。

## 为什么是跨平台的？

Skill 文件的核心是 **给 AI 的指令文本**（body 部分）。无论你用的是 Reasonix Code、Claude Code、Cursor、Copilot Chat，还是自定义的 LLM pipeline——只要能把这段指令喂给模型，skill 就能工作。frontmatter 中的 `name`、`description`、`runAs` 等元数据字段是平台无关的提示，不同工具按需解析即可。

## 快速安装

### 通用方式（所有平台）

```bash
git clone https://github.com/<your-username>/MySkills.git
cp MySkills/skills/*.md ~/.reasonix/skills/        # Reasonix Code
# 或其他 AI 工具的 skills/prompts 目录
```

### Reasonix Code

将 `.md` 文件放入 `~/.reasonix/skills/`（全局）或 `<project>/.reasonix/skills/`（项目级），重启即可。也可以直接对 agent 说：

> 帮我安装这个 skill：https://github.com/<your-username>/MySkills/blob/main/skills/zys-github-repo-classifier.md

### 其他 AI 工具

如果你使用的工具没有 skill 安装机制，直接：
- 将 skill 的 body 内容（`---` 之后的部分）复制为 **自定义指令 / system prompt**
- frontmatter 中的 `description` 作为触发说明

## Skill 列表

| Skill | 描述 | 依赖 |
|-------|------|------|
| [zys-github-repo-classifier](skills/zys-github-repo-classifier.md) | GitHub 仓库五维分类（软件类型 / 内容场景 / 可见性 / 特殊结构 / 生命周期） | 网络（GitHub API） |

## Skill 文件格式

```markdown
---
name: skill-name                    # 唯一标识
description: 一句话描述              # 触发条件说明
runAs: subagent | inline            # 运行模式（可选）
allowed-tools: [tool1, tool2]       # 工具白名单（可选）
---
# skill-name

给 AI 的详细指令（Markdown 格式）...
```

## 贡献

欢迎 PR。新增 skill 时请：
1. 在 `skills/` 下创建 `skill-name.md`
2. 更新本 README 的 Skill 列表
3. 确保 body 指令清晰、自包含、不依赖特定平台能力

## License

MIT
