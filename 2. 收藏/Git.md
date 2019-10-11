# Git
![git2](media/git2.jpg)

![git](media/git.jpg)

# 根据commit创建分支
```
git checkout -b <branch-name>  <commit-id>
```

#上传分支
```sh
git push  origin  api:api2
```
本地api分支上传到远程的api2分支

# 从本地上传一个新的github项目

```sh
git remote add origin https://github.com/huowenxuan/***.git
git push -u origin master
```

# 合并特定commit到另一个分支

```sh
// 切换到目标分支
git checkout master  
// 合并
git cherry-pick 62ecb3 
```

# 回退commit

```sh
git reset --hard d27ab20
```

# 远程

```sh
# 查看所有分支，包含远程分支
git branch -a
# 上传本地分支到远程
git push origin xxx
# 删除远程分支
git branch -r -d origin/xxx
```