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

# 上传到第二个新的远程仓库

```sh
git remote add github https://github.com/huowenxuan/girtu-jieba-python.git
git push -u github master
# 删除
git remote remove github
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

# 记住密码
git config --global credential.helper store
再次执行远程操作（git pull等）之后再输入一次账号密码就可以了