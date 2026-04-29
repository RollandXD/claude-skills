# Claude Code Skills

个人 Claude Code 技能集合，遵循 [agentskills.io](https://agentskills.io) 规范。

## 安装

```bash
git clone git@github.com:RollandXD/claude-skills.git ~/.claude/skills/
```

或者只取某个技能：

```bash
cp -r claude-skills/tutorial-writer ~/.claude/skills/
```

## 可用技能

### tutorial-writer

按 **8 个教学维度**写作或评审技术教程，覆盖动机引导、试错过程、小节过渡、类比/判定表、难点展开、章节收束、循序渐进、参考完整度。**支持 5000 字以上的章级长文**——自动启用两阶段工作流（先出大纲让用户确认 → 分批填充 + 节末自检标签 → 交付时附质量小报告），让用户写一两万字的体系化教程时不必逐字审就能掌控全文质量。

工程风（Git / 编程语言 / 工具）默认；课程风（操作系统 / 数据库 / 高数 / 算法等大学课程）自动加章末综合习题（5-8 道概念+应用+实操混合题）+ 章末术语回顾。

配合 `obsidian-markdown` 技能可输出 Obsidian 格式（callout、wikilink、frontmatter）。

**文件结构**

```
tutorial-writer/
├── SKILL.md              入口 + 工作流分流判定（短文 vs 长文章节）
├── dimensions.md         8 维度详解 + 课程风变体附录
├── long-form.md          长文章节专属流程（两阶段工作流 + 章级结构 + AI 自检协议）
├── examples.md           端到端微教程示例 + 自检修复演示
└── review-checklist.md   评审模板（可复制粘贴）
```
