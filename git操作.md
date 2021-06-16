# 前言
> git操作还是记录一下，以后看起来会十分方便。我记录都是自己常用操作，可能不太全面，但是还是比较实用。

# 基本操作
![bg2015120901.png](https://i.loli.net/2020/04/23/4Zw5eQjSHvsOf9A.png)
几个专用名词的译名
```
- Workspace：工作区
- Index / Stage：暂存区
- Repository：仓库区（或本地仓库）
- Remote：远程仓库 
```

` git clone  [url]`  &emsp;下载一个项目和它的整个代码历史

` git add .`  &emsp;添加当前目录的所有文件到暂存区

` git commit -m [message]`  &emsp;提交暂存区到仓库区

` git push -u origin master/HEAD`  &emsp;上传到远程仓库

` git branch`  &emsp;列出所有本地分支

` git branch -r`  &emsp;列出所有远程分支

` git branch [branch-name]`  &emsp;新建一个分支，但依然停留在当前分支

` git checkout [branch-name]`  &emsp;切换到指定分支，并更新工作区

