# MySkills

个人 AI Coding Assistant Skill 合集。每个 skill 是一个独立的 `SKILL.md`，不绑定任何平台——复制到对话里就能用。

---

## 安装

```bash
npx skills add https://github.com/MichaelZys/MySkills
```

安装单个 skill：

```bash
npx skills add https://github.com/MichaelZys/MySkills --skill "zys-github-repo-classifier"
```

---

## Skills

| Skill（目录） | Install Name | 描述 |
|--------------|-------------|------|
| [zys-github-repo-classifier](skills/zys-github-repo-classifier/SKILL.md) | `zys-github-repo-classifier` | GitHub 仓库五维分类：软件类型 / 内容场景 / 可见性 / 特殊结构 / 生命周期 |

### zys-github-repo-classifier

输入 `owner/name` 或完整 GitHub URL，自动调用 GitHub API 分析仓库，输出五个维度的分类标签及置信度：

| 维度 | 类别 |
|------|------|
| 软件类型 | 框架 / 库 / 插件 / 工具 / 应用 / 其他 |
| 内容场景 | 资源清单 / 模板 / 教程 / 示例 / 数据集 / 脚本配置 / 通用 |
| 可见性 | 公开 / 私有 / 内部 |
| 特殊结构 | 上游 / Fork / 镜像 / 子模块 / 存档 / 模板仓库 / Monorepo |
| 生命周期 | 存档 / 遗留 / POC / 备份 / 沙盒 / 生产活跃 / 维护中 |

示例输出：

```markdown
## zys 分类结果：facebook/react

| 维度 | 类别 | 置信度 | 理由 |
|------|------|--------|------|
| 软件类型 | 库 | 0.99 | 描述含 "library for building user interfaces" |
| 内容场景 | 通用 | 0.95 | 主要源码在 packages/，属于功能库 |
| 可见性 | 公开 | 1.00 | API visibility=public |
| 特殊结构 | 上游仓库 | 1.00 | 非 fork，非存档 |
| 生命周期 | 生产活跃 | 0.98 | 最近提交 2 天前，stars>100k |
```

---

## 常见问题

**怎么更新已安装的 skill？**

```bash
npx skills update
```

**支持私有仓库吗？**

暂不支持。当前通过无认证 GitHub API 访问仓库（60 次/小时限额），只能分析公开仓库。

**SKILL.md 是什么格式？**

标准 Markdown + YAML frontmatter（`name` + `description` + `metadata` + `license`），遵循 [Agent Skills 规范](https://github.com/vercel-labs/skills)。不绑定平台——直接把 body 内容粘贴到 ChatGPT / Claude 对话里就能用。

**怎么贡献新 skill 或提建议？**

1. 在 `skills/` 下创建 `your-skill/SKILL.md`，参考 [zys-github-repo-classifier](skills/zys-github-repo-classifier/SKILL.md)
2. frontmatter 必须包含 `name`、`description`、`metadata`、`license`
3. 更新本 README 的 Skill 列表
4. 提交 PR，或提 Issue 讨论想法

---

## License

MIT
