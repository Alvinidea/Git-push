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

6. git push -u origin master //把本地仓库的文件推送到远程仓库

---


[引用：第一次使用Git上传本地项目到github上](https://www.cnblogs.com/sdcs/p/8270029.html)

[引用：vim操作](http://c.biancheng.net/view/804.html)

[引用：vim操作2](https://www.cnblogs.com/chengjiawei/p/9339951.html)
