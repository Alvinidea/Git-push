# Git-push
Git上传本地仓库 到 github远程仓库

## Step：

---

1. git init //初始化仓库 ；  将所在的文件夹 转换为 Git可以识别的仓库

2. git add .(文件name) //添加文件到本地仓库，当前文件夹中的文件添加到仓库中（好像是建立一些索引的样子）

3. git commit -m "first commit" //添加文件描述信息 

4. git remote add origin + 远程仓库地址 //链接远程仓库，创建主分支 

> git remote add origin https://github.com/Alvinidea/Git-push.git

> 暂存区里的改动给提交到本地的版本库。每次使用git commit 命令我们都会在本地版本库生成一个40位的哈希值，这个哈希值也叫commit-id

5. git pull origin master // 把本地仓库的变化连接到远程仓库主分支 ;取回远程主机某个分支的更新，再与本地的指定分支合并

> fatal: refusing to merge unrelated histories 的错误解决

> 出现这个问题的最主要原因还是在于本地仓库和远程仓库实际上是独立的两个仓库.

> 解决： git pull origin master --allow-unrelated-histories //允许合并两个不相关的库（远程和本地两个库完全是两个东西）

> 第5步成功后：会进入一个vim的操作

6. git push -u origin master //把本地仓库的文件推送到远程仓库

---


[引用：第一次使用Git上传本地项目到github上](https://www.cnblogs.com/sdcs/p/8270029.html)

[引用：vim操作](http://c.biancheng.net/view/804.html)

[引用：vim操作2](https://www.cnblogs.com/chengjiawei/p/9339951.html)

[LFS例子](https://github.com/Alvinidea/LFS-test)

---

## 大文件上传（上传记录）
HP@DESKTOP-346B593 MINGW64 /e/DPLOL-MF (master)
$ git lfs install

Updated git hooks.
Git LFS initialized.

HP@DESKTOP-346B593 MINGW64 /e/DPLOL-MF (master)
$ git lfs track "*.exe"

Tracking "*.exe"

HP@DESKTOP-346B593 MINGW64 /e/DPLOL-MF (master)
$ git add .gitattributes

HP@DESKTOP-346B593 MINGW64 /e/DPLOL-MF (master)
$ git add software

HP@DESKTOP-346B593 MINGW64 /e/DPLOL-MF (master)
$ git commit -m "add software"

[master 0930432] add software
 3 files changed, 4 insertions(+)
 create mode 100644 .gitattributes
 create mode 100644 software/DPLOL-MF.exe
 create mode 100644 software/logo.png

HP@DESKTOP-346B593 MINGW64 /e/DPLOL-MF (master)
$ git push -u origin master

Uploading LFS objects: 100% (1/1), 253 MB | 0 B/s, done
Enumerating objects: 8, done.
Counting objects: 100% (8/8), done.
Delta compression using up to 8 threads
Compressing objects: 100% (5/5), done.
Writing objects: 100% (6/6), 149.78 KiB | 37.44 MiB/s, done.
Total 6 (delta 0), reused 0 (delta 0)
To https://github.com/*****.git
   e99fc26..0930432  master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.

## LFS测试例子
this is just a test for LFS

Chaofan@LAPTOP-A96HO1N4 MINGW64 /d/software/Git/LFS-test  // 查看当前账号配置
$ git config --global user.name
Alvinidea
            

Chaofan@LAPTOP-A96HO1N4 MINGW64 /d/software/Git/LFS-test   // 初始化仓库
$ git init
Initialized empty Git repository in D:/software/Git/LFS-test/.git/

Chaofan@LAPTOP-A96HO1N4 MINGW64 /d/software/Git/LFS-test (master)  // 使用 lfs 追踪大文件，lfs需要安装（git install lfs）
$ git lfs track "jdk-13.0.1_windows-x64_bin.exe"
Tracking "jdk-13.0.1_windows-x64_bin.exe"

Chaofan@LAPTOP-A96HO1N4 MINGW64 /d/software/Git/LFS-test (master)  // 添加当前文件夹所有文件到 暂存区（stage）
$ git add .

Chaofan@LAPTOP-A96HO1N4 MINGW64 /d/software/Git/LFS-test (master)  // ！！！commit 写错了
$ git commint -m "lfs - 1"
git: 'commint' is not a git command. See 'git --help'.

The most similar command is
        commit

Chaofan@LAPTOP-A96HO1N4 MINGW64 /d/software/Git/LFS-test (master) // commit 暂存区（stage）中的文件到仓库
$ git commit -m "lfs - 1"
[master (root-commit) 2301f50] lfs - 1            // commit 信息
 2 files changed, 4 insertions(+)
 create mode 100644 .gitattributes
 create mode 100644 jdk-13.0.1_windows-x64_bin.exe

Chaofan@LAPTOP-A96HO1N4 MINGW64 /d/software/Git/LFS-test (master) // 查看 暂存区 状态
$ git status
On branch master
nothing to commit, working tree clean

Chaofan@LAPTOP-A96HO1N4 MINGW64 /d/software/Git/LFS-test (master) // 与远程仓库进行链接（关联）
$ git remote add origin https://github.com/Alvinidea/LFS-test.git

Chaofan@LAPTOP-A96HO1N4 MINGW64 /d/software/Git/LFS-test (master) // push 到远程仓库，但是没有选择分支，失败了
$ git push
fatal: The current branch master has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin master


Chaofan@LAPTOP-A96HO1N4 MINGW64 /d/software/Git/LFS-test (master) // push 远程仓库的某一个分支中去
$ git push -u origin master
Logon failed, use ctrl+c to cancel basic credential prompt.
Logon failed, use ctrl+c to cancel basic credential prompt.

          // 开始上传大文件（因为这是一个大文件上传测试，所以本地仓库只有一个超过100M的exe文件）

Uploading LFS objects:   0% (0/1), 0 B | 0 B/s                             

Uploading LFS objects: 100% (1/1), 168 MB | 306 KB/s, done.
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 16 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (4/4), 448 bytes | 224.00 KiB/s, done.
Total 4 (delta 0), reused 0 (delta 0), pack-reused 0
remote:
remote: Create a pull request for 'master' on GitHub by visiting:
remote:      https://github.com/Alvinidea/LFS-test/pull/new/master
remote:
To https://github.com/Alvinidea/LFS-test.git
 * [new branch]      master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'. // 完成Push

至此完成git本地仓库上传大文件到 github远程仓库


