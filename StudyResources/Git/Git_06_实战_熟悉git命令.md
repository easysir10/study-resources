# 前言







# 一、github准备

> - 注册、登录
> - 添加ssh公钥
> - 创建远程仓库（git-in-action）



拉取代码到本地

```bash
git clone git@github.com:shirayner/git-in-action.git
```









# 二、简单的提交流程



（1）添加我们的代码

> 这里我们创建一个文件1.txt，然后里面随便写上一段话。



（2）确认修改

```bash
λ git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        1.txt

nothing added to commit but untracked files present (use "git add" to track)
```



（3）添加修改到暂存区

```bash
git add --all
```



（4）添加到本地仓库

```bash
λ git commit -m"[ADD] 1.txt"
[master (root-commit) d8c62a5] [ADD] 1.txt
 1 file changed, 1 insertion(+)
 create mode 100644 1.txt
```



（5）提交到远程仓库

```bash
λ git push origin master
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Writing objects: 100% (3/3), 227 bytes | 227.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To github.com:shirayner/git-in-action.git
 * [new branch]      master -> master
```



# 三、分支

## 1.查看分支

```bash
λ git branch
* master
```



## 2.创建分支

创建分支

```bash
shira@ray ~/Desktop/mess/git-in-action (master)
λ git branch dev
shira@ray ~/Desktop/mess/git-in-action (master)
λ git branch
  dev
* master
```



创建分支并切换到该分支上

```bash
shira@ray ~/Desktop/mess/git-in-action (master)
λ git checkout -b bug
Switched to a new branch 'bug'
shira@ray ~/Desktop/mess/git-in-action (bug)
λ git branch
* bug
  dev
  master
```



## 3.提交到远程对应的分支

添加修改

> 创建 bug.txt，内容任意

（1）确认修改

```bash
shira@ray ~/Desktop/mess/git-in-action (bug)
λ git status
On branch bug
Untracked files:
  (use "git add <file>..." to include in what will be committed)

        bug.txt

nothing added to commit but untracked files present (use "git add" to track)
```



（2）添加到暂存区

```
shira@ray ~/Desktop/mess/git-in-action (bug)
λ git add --all
```



（3）提交到本地仓库

```bash
shira@ray ~/Desktop/mess/git-in-action (bug)
λ git commit -m"[ADD] bug.txt"
[bug 02c1cd1] [ADD] bug.txt
 1 file changed, 1 insertion(+)
 create mode 100644 bug.txt
```

（4）拉取远程分支

```bash
λ git pull origin bug
```



（5）提交到远程对应的分支

```bash
λ git push origin bug
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 4 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 281 bytes | 281.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
remote:
remote: Create a pull request for 'bug' on GitHub by visiting:
remote:      https://github.com/shirayner/git-in-action/pull/new/bug
remote:
To github.com:shirayner/git-in-action.git
 * [new branch]      bug -> bug
```



## 4.合并分支到master上

登录 github ，仓库会显示有一个 Pull Request（合并请求），合并一下即可



