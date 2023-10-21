# Git
git 是對資料夾做版本管理的工具

[Git下載](https://git-scm.com/download/win)
### 常用指令
```
# 查版本
git --version

# 一開始 config 要做的
git config --global user.name "roberthsu"
git config --global user.email scchang@gmail.com

# 查目前 cofnig 狀態
git config -l
git config --list

# 初始化, 把資料夾納入 git 管理, 會在資料夾中產生 .git
git init

# 將檔案加入追蹤
git add .

# 提交版本至本機
git commit 

# 提交版本至Github
git push

# 從 github 下載一全新的 repository 至本機
git clone

# 本機已有 repository, 從 Gihub 更新至本機
git pull

# 取消 git 管理
rm

```