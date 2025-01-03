

## 编辑

```shell
git pull # 同步远程代码 
git add # 添加到暂存区
git commit -m "blabla" # 暂存区到本地仓库
git push origin feature/mydev # 将你的更改作为一个新的远程分支推送到远程仓库，等待审阅后合并入分支
git push origin local:remote # 本地 local 推送到远程 remote
git status # 查看本地仓库状态
```



```shell
git log # 修改记录
git remote # 远程分支
cd .git # 进入到 git 管理文件夹
cat config # 
```

## 状态回退

 ```shell
 git checkout -- <filename> # 撤销工作区更改
 git reset HEAD <filename> # 取消暂存区修改
 git reset --hard commit-id # 本地仓库回退 其实是把头指针移动，错误文件本身并没有删除
 git reflog # 查看 HEAD 指针的改动日志
 git push -f # 强制推送本地仓库代码到远程仓库
 git diff HEAD -- <file> # 查看工作区 file 文件和仓库中该文件的最新版本代码有什么区别
 ```

## 冲突解决

冲突原因：并行基于同一 base 开发， 各个参与方提交时候没执行 git pull 将前人提交版本合并到本地仓库。

> 如果是不同参与方修改了不同行，执行 git pull 以后 git 会进行 auto-merge，而如果是修改了同一行，则 auto-merge 失败，需要后提交者手动解决冲突

## 分支

```shell
git branch # 本地分支查看
git branch -r # 远程分支查看
git branch -vv # 本地远程追踪关系

git switch -b feature-branch # 创建并切换本地分支，分支并没有追踪任何远程分支（用于隔离修改）
git merge feature-branch # 站在 master 分支把新分支 merge 过来，然后 git push
# 此时 git pull 也可能会出现分支合并冲突问题，解决的办法和上面所述冲突解决是一样的

git checkout -b <本地分支名> <远程仓库名>/<远程分支名> # 创建本地分支并指定追踪哪个分支 
git checkout -u <远程仓库名>/<远程分支名> # 设置已经存在的本地分支追踪哪个远程分支

git switch feature-branch # 切换本地分支
git switch --track origin/dev # 本地创建同名分支来追踪远程分支
 
git branch -d <branch-name> # 删除本地分支
git branch -D <branch-name> # 强制删除分支，分支未合并情况下直接删除
git push origin --delete <branch-name> # 删除对应远程分支
```

