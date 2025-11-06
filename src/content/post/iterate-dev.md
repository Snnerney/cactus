---
title: 迭代开发
description: 迭代开发&git-usage
publishDate: 2025-08-10
tags:
  - study
ogImage: /social-card.avif
---
在实际工作开发项目中，往往采用迭代开发的方式，对于整个项目中不同功能的开发分别进行迭代，而不是堆叠在一堆分支中；

## 迭代开发的概念

迭代开发是一种软件开发方法，通过**将整个开发过程分解为多个小的迭代周期，每个迭代周期都包含需求分析、设计、开发、测试和交付等环节**。迭代开发的核心概念包括：

**1.迭代周期**：将整个开发过程分解为若干个短小的迭代周期，通常是几周或几个月。每个迭代周期内，团队致力于交付一个可用的产品部分。

**2.需求优先级**：通过明确需求的优先级，团队能够在每个迭代周期内专注于实现最重要的功能，并在后续迭代中逐步扩展和改进。

**3.快速反馈和调整**：每个迭代周期结束后，团队会接收用户或客户的反馈，根据反馈进行相应调整，以确保产品满足用户需求。

**4.增量交付**：迭代开发将产品分解为小的增量部分，使团队能够及时交付部分可用产品，从而提供更早的价值并减少风险。

在各个迭代中，开发人员关联各自的远程分支进行开发，互不影响

---

git进行代码提交至远程仓库时的流程：

工作区（已关联远程仓库）更改并保存代码 -> 暂存更改的文件 -> 提交暂存文件 -> 推送至远程仓库

git add. 一般在教程中给出的语句就是这个，让初学者会一头雾水（至少我是，这个语句的意义就是 将所有更改的代码文件都提交至暂存区，准备commit提交到本地仓库；但是，在实际开发过程中，可能会有部分配置文件在本地进行修改，无需push到远程仓库，这个时候就不要 git add .，而是选择特定的文件，这个时候使用IDE进行手动选择文件暂存会是一个更好的选择

git commit -m "commit-message" 提交至本地仓库（commit-message为提交变更信息，遵循基本的commit-rules），在IDE中若有集成llm，可以选择使用ai进行commit-msg自动生成；

git push origin HEAD:`remote-branch` ： remote-branch为自定义远程分支名，对于当前迭代中，当前的迭代分支就相当于整个小功能的master，clone到本地即默认关联这个“master主分支”，在推送时另外创建一个远程分支（即remote-branch），进行pr/mr合并到“master主分支”，这样当remote-branch分支中提交的代码cr为通过被打回，不会污染主功能的开发，同时也可以直接revert回退到特定commit记录

git branch -vv：查看本地分支与远程分支的关联关系

当然了，git只是一个工具，对于工具，我一向的态度就是，即学即用，偶尔记录一些常用的 但是又容易遗忘的记录

<details>
  <summary>git revert</summary>
撤销以往的几次推送记录

**不要**使用 `git reset` 配合 `git push --force`（强制推送）。这会重写远程历史记录，并**导致同事推送的代码丢失**，会给团队带来巨大的麻烦。

最安全、最推荐的解决方案是使用 `git revert`。

### 推荐方案：使用 `git revert` (安全)

`git revert` 不会删除或重写历史记录。相反，它会创建一个**新的 commit**，这个新 commit 的内容是用来“撤销”您之前某个 commit 所做的更改。

这既保留了完整的项目历史（出于可追溯性，这通常是好事），也完全不会影响同事已经推送的工作。

#### 详细步骤

1.  **第一步：同步最新代码**

    ```bash
    git pull origin <your-branch-name>
    ```

    *（例如 `git pull origin main` 或 `git pull origin master`）*

2.  **第二步：找到要撤销的 commit**
    使用 `git log` 查看提交历史，找到想要撤销的那个（或多个）commit 的 **commit hash**（那一长串字母和数字）。

    ```bash
    git log --oneline
    ```

    *您会看到类似这样的列表：*

    ```
    a83be19 (origin/main, main) 同事B的新功能
    f1a45c3 同事A的修复
    b4d7a91 (HEAD) 这是您推送的错误代码 <--- 您想撤销这个
    c3a2b1f 之前的正确代码
    ```

    *在这个例子中，您需要撤销的 commit hash 是 `b4d7a91`。*

3.  **第三步：执行 `git revert`**
    针对要撤销的 commit hash 执行 `revert` 命令。

    ```bash
    git revert b4d7a91
    ```

      * 执行此命令后，Git 会自动创建一个**新的** commit。
      * 它可能会弹出一个编辑器（如 Vim），让您为这个“撤销 commit”编写提交信息。默认信息通常是 "Revert '这是您推送的错误代码'"。您直接保存并关闭编辑器即可。
      * 如果您不想编辑 commit 信息，可以直接使用 `--no-edit` 选项：`git revert b4d7a91 --no-edit`

4.  **第四步：推送“撤销 commit”**
    现在，本地有了一个新的“撤销 commit”。只需要像正常推送代码一样，将这个新 commit 推送到远程仓库。

    ```bash
    git push origin <your-branch-name>
    ```

**完成！**

-----

### 如果您想撤销的是连续的多个 commit

假设那次 `push` 包含 3 个连续的 commit（C、D、E），而您想全部撤销它们：

```
a83be19 (origin/main, main) 同事B的新功能
...
f1a45c3 同事A的修复
e9f4c12 (HEAD) 推送的错误代码 3 (E) <---
d8c3b1a 推送的错误代码 2 (D) <---
b4d7a91 推送的错误代码 1 (C) <---
c3a2b1f 之前的正确代码
```

两种选择：

1.  **逐个 Revert（推荐）：**
    按照**从新到旧**的顺序，依次 revert 它们：

    ```bash
    git revert e9f4c12
    git revert d8c3b1a
    git revert b4d7a91
    git push
    ```

2.  **Revert 一个范围（高级）：**
    您可以使用 `..` 语法来 revert 一个范围。请注意，这个范围是**前开后闭**的（不包括最早的 commit，但包括最新的 commit）。

    ```bash
    # 语法: git revert <oldest-commit-hash>^..<newest-commit-hash>
    git revert b4d7a91^..e9f4c12
    ```

    *（注意 `b4d7a91` 后面的 `^` 符号，这表示“从 C 的父提交开始”，从而确保 C 也被包含在 revert 范围内）*

    这会为范围内的每个 commit 都创建一个 revert commit。如果您希望将它们合并为一个 commit，可以添加 `-n`（`--no-commit`）标志：

    ```bash
    git revert -n b4d7a91^..e9f4c12
    git commit -m "Revert: 撤销 C, D, E 三个提交"
    git push
    ```

-----

### 总结：`revert` vs `reset` (强制推送)

| 操作 | `git revert` (推荐) | `git reset` + `git push --force` (危险) |
| :--- | :--- | :--- |
| **原理** | 创建一个“反向”的新 commit 来抵消旧 commit。 | 移动分支指针，丢弃历史 commit。 |
| **历史记录** | **保留**历史（添加新 commit）。 | **重写/删除**历史。 |
| **对同事的影响** | **安全**。同事只需 `git pull` 即可。 | **灾难性**。会删除同事已推送的 commit。 |
| **适用场景** | 已经推送到**共享**分支（如 main, master, develop）。 | 仅在**您自己**的、**未共享**的私有分支上。 |

您需要我帮您解释如何更精确地查找 commit hash，或者如何处理 revert 时可能出现的冲突吗？
</details>

[进阶部分-掘金小册](http://github.com/lm-rebooter/NuggetsBooklet/tree/master/Git%20%E5%8E%9F%E7%90%86%E8%AF%A6%E8%A7%A3%E5%8F%8A%E5%AE%9E%E7%94%A8%E6%8C%87%E5%8D%97)
