一直用git，知道git很多用法，也知道git很多操作的概念，但从未总结，所以现在总结一下。

我们以B分支合并到A分支为例，可以把A分支当成master来理解

##  merge

`git merge` 可以将一个分支的修改应用到另一个分支

当我们进行`git merge `这个操作时，实际上会有两种行为方式：`fast-forward` 和` no-fast-forward`

当 Git 执行一个合并时（B合并到A）：

1. 查找A,B分支共同的原始提交

2. 在原始提交之后，A分支没有新的提交

   - 有，执行`fast-forward`提交，即在A分支上添加所有在B分支上的新提交

     ![img](https://www.git-tower.com/learn/media/pages/git/ebook/cn/command-line/advanced-topics/rebase/371525700-1588165681/end-situation-fast-forward.gif)

   - 无，执行`no-fast-forward`提交，即git 会在A上创建新的 merging commit来含括它们之间的差异。这个提交的父提交（parent commit）即指向A，也指向B。

     ![img](https://www.git-tower.com/learn/media/pages/git/ebook/cn/command-line/advanced-topics/rebase/-169912904-1588165681/end-situation-merge-commit.gif)

## Rebase

`git rebase`也可将一个分支的修改应用到另一个分支上，与merge 不同的是，rebase操作会使A分支有单一的提交线。

我们假设A，B分支在共同源C1之后都有各自的新提交

![img](https://www.git-tower.com/learn/media/pages/git/ebook/cn/command-line/advanced-topics/rebase/439759406-1588165681/starting-situation-rebase.gif)

在A分支上执行`git rebase B`之后：

1. git 会 “撤销” 所有在分支 A 上的那些在与分支 B 的共同提交之后发生的提交，即C3。

2. 再在A上逐个添加B的新提交C2、C4

3. 再把之前撤销的A上的新提交重新添加上来

   ![img](https://www.git-tower.com/learn/media/pages/git/ebook/cn/command-line/advanced-topics/rebase/-1079461100-1588165681/rebase-step-3.gif)

整个过程会使得开发轨迹看起来就像发生在一条直线上，但是rebase会改写历史记录。

一个提交仅仅包括很少的属性，比如作者，日期，变动和谁是它的父提交。如果改变其中任何一个信息，就必须创建一个全新的提交。

显然这里A上的所有的新提交的父提交的指向都变了，因为C3*虽然内容和C3一样，但完全是一个新的提交。



## 项目开发对以上两种方式的应用



如果你在开发一个 feature 分支并且 master 分支已经更新过，那么变基就很好用。

你可以在feature分支上执行`git rebase master`来获取master更新。

这能防止未来合并`master`时出现的合并冲突。



## 交互式变基

