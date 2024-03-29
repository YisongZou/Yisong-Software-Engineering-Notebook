#### 1. git切换到远程分支
https://blog.csdn.net/tanningzhong/article/details/79724488

远程仓库 git clone 下来，当你执行 git branch，你只会看到

```* master```
并不会看到其他分支，即便远程仓库上有其他分支，使用

```git branch -va```
可以查看本地+远程分支列表
```
* master              0840594 merge master and 1.0.0
remotes/origin/1.0.0  743012a 'update'
remotes/origin/2.0.0  2787838 udpate
remotes/origin/HEAD   -> origin/master
remotes/origin/master 0840594 merge master and 1.0.0
```
如果想切换到 origin/2.0.0 的分支，我们可以
```
git checkout -b 本地分支名x origin/远程分支名x
```
不过结果并不如意：
```
* (detached from origin/2.0.0)
master
```

git branch 会看到上面的信息，这里还需要一步操作：
```
git checkout -b 2.0.0
```
-b 的意思是 base，以当前分支为 base，新建一个名叫 2.0.0 的分支，这里当然也可以使用其他的命名。此时再执行 git branch 就能看到：
```
$ git br
  master
* 2.0.0
```
就 OK 了~

最直接的方法是：
```
git checkout -t origin/2.0.0
```
能够直接新建本地分支，将远程分支提取出来。

#### 2. git 修改用户名以及提交邮箱

https://blog.csdn.net/helinlin007/article/details/52266169

#### 3.git删除远程及本地分支：

```
删除远程：git push origin --delete <branch>

删除跟踪：git branch -dr origin/<branch>

删除本地分支： 
查看项目的分支们(包括本地和远程) 
命令行 : $ git branch -a     例如，$ git branch -a 

删除本地分支 
命令行 : $ git branch -d <BranchName>
```

#### 4. Git revert 回之前的commit
```
Revert the full commit
Sometimes you may want to undo a whole commit with all changes. Instead of going through all the changes manually, you can simply tell git to revert a commit, which does not even have to be the last one. Reverting a commit means to create a new commit that undoes all changes that were made in the bad commit. Just like above, the bad commit remains there, but it no longer affects the the current master and any future commits on top of it.

git revert {commit_id}'
```
