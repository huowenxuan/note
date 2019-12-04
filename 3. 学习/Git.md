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

# Git emoji

```sh
git commit -m ":tada: Initialize" # 中间需要加空格 
```

| emoji          |         emoji代码          | commit说明            |
| :------------- | :------------------------: | --------------------- |
| 🎨 (调色板)     |           :art:            | 改进代码结构/代码格式 |
| ⚡️ (闪电)       |           :zap:            | 提升性能              |
| 🐎 (赛马)       |        :racehorse:         | 提升性能              |
| 🔥 (火焰)       |           :fire:           | 移除代码或文件        |
| 🐛 (bug)        |           :bug:            | 修复 bug              |
| 🚑 (急救车)     |        :ambulance:         | 重要补丁              |
| ✨ (火花)       |         :sparkles:         | 引入新功能            |
| 📝 (铅笔)       |          :pencil:          | 撰写文档              |
| 🚀 (火箭)       |          :rocket:          | 部署功能              |
| 💄 (口红)       |         :lipstick:         | 更新 UI 和样式文件    |
| 🎉 (庆祝)       |           :tada:           | 初次提交              |
| ✅ (白色复选框) |     :white_check_mark:     | 增加测试              |
| 🔒 (锁)         |           :lock:           | 修复安全问题          |
| 🍎 (苹果)       |          :apple:           | 修复 macOS 下的问题   |
| 🐧 (企鹅)       |         :penguin:          | 修复 Linux 下的问题   |
| 🏁 (旗帜)       |       :checked_flag:       | 修复 Windows 下的问题 |
| 🤖 (机器人)     |          :robot:           | 修复 Android 下的问题 |
| 🍏 (苹果)       |       :green_apple:        | 修复 iOS 下的问题     |
| 🔖 (书签)       |         :bookmark:         | 发行/版本标签         |
| 🚨 (警车灯)     |      :rotating_light:      | 移除 linter 警告      |
| 🚧 (施工)       |       :construction:       | 工作进行中            |
| 💚 (绿心)       |       :green_heart:        | 修复 CI 构建问题      |
| ⬇️ (下降箭头)   |        :arrow_down:        | 降级依赖              |
| ⬆️ (上升箭头)   |         :arrow_up:         | 升级依赖              |
| 📌 (图钉)       |         :pushpin:          | 将依赖项固定到特定的版本 |
| 👷 (工人)       |   :construction_worker:    | 添加 CI 构建系统      |
| 📈 (上升趋势图) | :chart_with_upwards_trend: | 添加分析或跟踪代码     |
| ♻️ (环保)       |          :recycle:         | 重构代码              |
| 🔨 (锤子)       |          :hammer:          | 重大重构              |
| ➖ (减号)       |     :heavy_minus_sign:     | 减少一个依赖          |
| 🐳 (鲸鱼)       |          :whale:           | Docker 相关工作       |
| ➕ (加号)       |     :heavy_plus_sign:      | 增加一个依赖          |
| 🔧 (扳手)       |          :wrench:          | 修改配置文件          |
| 🌐 (地球)       |   :globe_with_meridians:   | 国际化与本地化        |
| ✏️ (铅笔)       |         :pencil2:          | 修复 typos           |
| 💩 (便便)       |         :poop:             | 编写需要改进的糟糕代码 |
| ⏪              |         :rewind:           | 回退代码              |
| 🔀              | :twisted_rightwards_arrows: | 合并分支             |
| 👽 (外星人)     |          :alien:            | 由于外部API更改而更新代码 |
| 🚚              |          :truck:            | 移动或重命名文件       |
| 📄              |       :page_facing_up:      | 添加或更新 license    |