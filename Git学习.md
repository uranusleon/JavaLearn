# Git学习

学习内容

- Git的基本使用
- Git的原理

## wiki

- [Git教程-廖雪峰](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)

## Git基本使用

- Git初始化：`git init`
- 添加文件到仓库

  - 使用命令`git add <file>`，注意，可反复多次使用，添加多个文件；

  - 使用命令`git commit -m <message>`，完成;
- 要随时掌握工作区的状态，使用`git status`命令。
- 如果`git status`告诉你有文件被修改过，用`git diff`可以查看修改内容。
- `HEAD`指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令`git reset --hard commit_id`。
- 穿梭前，用`git log`可以查看提交历史，以便确定要回退到哪个版本。
- 要重返未来，用`git reflog`查看命令历史，以便确定要回到未来的哪个版本。

## Git原理

### 基本概念

- 工作区(Working Directory)

  本地可以看到的目录，以目前学习的目录为例，下图的目录就是工作区。

  ![image-20181110163903257](/Users/leonuranus/learn/JavaLearn/assets/image-20181110163903257.png)

- 版本库(Repository)

  工作区有一个隐藏目录`.git`，这个不算工作区，而是Git的版本库。

  Git的版本库里存了很多东西，其中最重要的就是称为stage（或者叫index）的暂存区，还有Git为我们自动创建的第一个分支`master`，以及指向`master`的一个指针叫`HEAD`。

  ![image-20181110164011195](/Users/leonuranus/learn/JavaLearn/assets/image-20181110164011195.png)

  第一步使用`git add`的添加文件，是将文件从工作区添加到暂存区；

  第二部使用`git commit`提交更改，是将暂存区的文件提交当前分支；

  > `git diff`,`git diff --cached`和`git diff head`的区别
  >
  > - git diff 是工作区和暂存区区比较
  > - git diff --cached是暂存区区和仓库比较。
  > - git diff head是工作区和仓库比较
  >
  > ![image-20181110173423855](/Users/leonuranus/learn/JavaLearn/assets/image-20181110173423855.png)
  >
  > 实验：对于test.md，有工作区版本，暂存区版本和仓库区版本。
  >
  > 1. 经过add, commit，此时三个版本相同
  > 2. 修改再add，工作区版本和暂存区版本相同，仓库区版本则不同；
  > 3. 再修改，不执行add，则三个版本都不相同。
  >
  > 仓库版本
  >
  > ```java
  > This the master version.
  > ```
  >
  > 暂存区版本；
  >
  > ```java
  > This the master version.
  > This is the stage version.
  > ```
  >
  > 工作区版本
  >
  > ```java
  > This the master version.
  > This is the stage version.
  > This is the working directory version.
  > ```
  >
  > 执行第3步后，三个版本都不相同
  >
  > 使用`git diff`和`git diff --cached`和`git diff head`，可以看到
  >
  > - `git diff`是工作区版本和暂存区版本比较；
  > - `git diff --cached`时暂存区版本和仓库版本比较。
  > - `git diff head`是工作区和仓库区比较；
  >
  > ![image-20181110173010368](/Users/leonuranus/learn/JavaLearn/assets/image-20181110173010368.png)



