# AI Skills

个人 AI 技能集合，同时提供 Claude Code 和 Codex 可用的技能目录。

## 安装

### Claude Code

```bash
git clone git@github.com:RollandXD/claude-skills.git
cp -r claude-skills/claude/tutorial-writer ~/.claude/skills/
```

### Codex

```bash
git clone git@github.com:RollandXD/claude-skills.git
cp -r claude-skills/codex/tutorial-writer ~/.codex/skills/
```

## 可用技能

### tutorial-writer

按 **9 个教学维度**写作或评审技术教程，覆盖动机引导、试错过程、类比/判定表、难点展开、章节收束、小节过渡、循序渐进、参考完整度、语气与风格。**支持 5000 字以上的章级长文**，自动启用两阶段工作流（先出大纲让用户确认 → 分批填充 + 节末自检标签 → 交付时附质量小报告），让用户写一两万字的体系化教程时不必逐字审就能掌控全文质量。

工程风（Git / 编程语言 / 工具）默认；课程风（操作系统 / 数据库 / 高数 / 算法等大学课程）自动加章末综合习题（5-8 道概念+应用+实操混合题）+ 章末术语回顾。

配合 `obsidian-markdown` 技能可输出 Obsidian 格式（callout、wikilink、frontmatter）。

**文件结构**

```
codex/tutorial-writer/
├── SKILL.md
├── dimensions.md
├── long-form.md
├── examples.md
└── review-checklist.md

claude/tutorial-writer/
├── SKILL.md
├── dimensions.md
├── long-form.md
├── examples.md
└── review-checklist.md
```
