# Git 合作开发教程

总算找到一个能写的主题了，实在是不容易。

一般来说，git的合作能够查到两种方式：

- 依赖于fork仓库，然后pull issue的。
- 依赖于多分支然后进行分支合并的

这方面倒是没有比较完善的（和我胃口的）教程，所以自己写一篇。

这篇教程不会介绍版本记录的基本用法，而是介绍如何用版本记录工具进行合作

## 基础知识

git revert 将当前分支的上上次提交作为一个新的修改提交

git reset	重置暂存区，但不修改文件（工作区）与HEAD指向

git reset --hard	改变HEAD指向，即撤销commit并且修改文件（工作区）

git stash 将当前工作区保存至一个临时存放点，同时恢复工作区到HEAD，等同于git stash save

git stash pop  弹出上一个指令保存的工作区修改

git checkout 转换到已存在的分支

git checkout -b 创建并转换到该分支

git branch 列出所有分支

git branch <分支名> 基于上次提交创建新分支

## fork & pull issue

本网站目前就是用这个方式编写的。适合于开源大型项目。

对于比较正式的项目来说，会有一个master分支

## checkout & merge

适合于同一工作团队进行合作开发。

master分支，保持稳定

dev分支，开发的主要分支，所以对master分支的改动必须得为经由dev分支merge而来。

在比较正式的开发中，会有一个集中的dev分支，每个开发人员再各自有一个专门的dev分支。

在不是那么正式的开发中（就是你不想走软件工程那一套超级复杂麻烦的流程时），N个人开发，可以直接一个master分支 + N个dev分支。

具体来说，就是每人clone一个master分支，然后checkout一个dev分支，之后在dev分支开发。

等到开发完毕时，dev分支commit，然后checkout到master，merge dev（只要两个分支不一样，这个步骤就会生成一次commit）。然后pull（fetch + merge），如果有冲突就解决冲突，最后push。之后再切回dev分支，merge一次master，就可以继续开发了。

那可不可以直接每个人都使用单个master分支呢？当然是可以的，每个人clone后直接开发，然后commit，之后pull解决冲突，之后push。这样做也是能成的，因为本质上两台机器上的master分支也是不同分支，pull和push的过程中都会做merge，只要冲突都在本地解决好了，那么在远程仓库都可以顺利地merge。这种做法非常不正规，只建议在非常简单的情形下使用。



那么到底正式的做法与不正式的做法之间的区别在于哪里？在于你能够追溯到多么稳定的代码版本，以及各个分支上的代码稳定性。
