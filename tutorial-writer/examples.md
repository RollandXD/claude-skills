# 端到端示例：一篇微教程的完整节奏

下面是一篇约 400 字的微教程《git stash：临时"存档"你的工作》，展示 8 个维度如何在同一篇文章里协同。读完之后是"自检 → 发现漏洞 → 修复"的完整迭代演示。

---

## 示例正文

### 为什么你需要 stash

你正在 feature 分支上改 `api.js`，改了一半，还没到能 commit 的程度。突然同事说 master 上有个紧急 hotfix 需要你立刻切过去 review。你不能 commit（半成品），也不能不管（改了一半的文件会跟着你切分支跑过去）。**你被卡住了**。`git stash` 就是为这个场景设计的——它把你的修改暂存到临时空间，还你一个干净的工作区。

### 先试试看

```bash
# 当前在 feature 分支，有未提交的修改
git status          # modified: api.js
git stash           # 暂存所有修改
git status          # working tree clean —— 干净了！
git checkout master # 自由切换
# ...review hotfix...
git checkout feature
git stash pop       # 恢复你的半成品
```

你看到 `api.js` 的修改回来了，和 stash 前一模一样。

### stash 到底是什么

可以把 stash 想象成一个**临时剪贴板栈**。每次 `git stash` 把当前修改"剪切"到栈顶，工作区恢复干净。`git stash pop` 把栈顶内容"粘贴"回来并从栈中移除。

### stash pop 和 stash apply 差在哪

这两个命令看起来都能恢复 stash——差别在**是否保留 stash 记录**：

- `pop`：恢复 + 删除记录（用后即弃）
- `apply`：恢复但保留记录（可反复应用到不同分支）

| 场景 | 用 |
|------|-----|
| 切回来继续原来的开发 | `pop` |
| 同一组修改想在多个分支上都试试 | `apply` |

### 常见踩坑

> [!warning] 别把 stash 当分支用
> stash 没有名字、没有历史。堆了七八个 stash 之后你根本分不清哪个是哪个。stash 是**临时**暂存——超过一天就该考虑开个分支。

> [!tip] 只 stash 部分文件
> `git stash push -p` 可以交互式选择哪些改动入 stash。

---

## 这段例子里 8 维度的分布

| 段落 | 主对应维度 |
|------|------|
| "为什么你需要 stash" | 1（动机：具体痛点 + 被卡住的感觉） |
| "先试试看" | 2（试错：可跑命令，读者立刻验证） |
| "stash 到底是什么" | 4（类比：剪贴板栈） |
| "pop 和 apply 差在哪" | 5（难点展开：最小分叉 + 判定表） |
| "常见踩坑" | 6（收束：误区 + 最佳实践） |
| 各段衔接 | 3（过渡：每段最后一句引出下一段） |
| 整篇顺序 | 7（循序渐进：困境 → 基本用法 → 易混点 → 进阶技巧） |

注意：这篇不到 500 字，维度 3（过渡）和维度 7（循序渐进）由短篇幅自然保证。维度 8 见下方"自检修复"——这正是它最容易被漏掉的尺度。

---

## 自检修复：当评审清单抓住了漏掉的东西

上面这篇 git stash 教程如果写完用评审清单自检，会发现一个漏洞——这个自检和修复的过程，**比看成品更有教学意义**。

### 第一版过评审清单

- 维度 1 ✅ 有痛点场景
- 维度 2 ✅ 有可跑命令
- 维度 4 ✅ 有类比
- 维度 5 ✅ pop vs apply 展开了
- 维度 6 ✅ 有误区和实践
- **维度 8 ⚠️ 短教程的参考块不够——`git stash` 的核心命令面没给读者**

### 问题定位

读者看完知道 `git stash` 和 `git stash pop`，但不知道还有 `git stash list`（查看所有 stash）、`git stash drop`（删除某个 stash）、`git stash push -m "msg"`（带备注存）。**这些不是"进阶用法"——是日常 stash 的基本操作，漏了会让读者以为 stash 只有 push 和 pop 两个动作。**

### 修复——在"常见踩坑"之前插入参考块

```bash
# git stash 常用命令速查
git stash                  # 暂存所有修改（等同于 git stash push）
git stash push -m "说明"   # 暂存并加备注（推荐！不然堆多了分不清）
git stash list             # 查看所有 stash 列表
git stash pop              # 恢复最近一次 stash 并删除记录
git stash apply            # 恢复最近一次 stash 但保留记录
git stash drop stash@{n}   # 删除指定 stash
git stash push -p          # 交互式选择哪些改动入 stash
```

修复后，读者有了一张完整速查表——不需要再去 `man git-stash`。

> 这就是维度 8 在实战中的用法：**写完 → 过清单 → 发现漏参考块 → 补充 → 交付**。不是写的时候就完美无缺，而是写完知道怎么查漏补缺。
