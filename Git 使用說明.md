# Git 使用說明
- 在windows安裝git工具(https://git-scm.com/)
  - Git官網 > Downloads > Downloads for Windows > Git for Windows/x64 Setup
- 在專案資料夾中按下右鍵 > 顯示其他選項 > Open git Bash here 或 Open git GUI here

- [用git建立新的project在Github](#-git----project-github)
- [更換 Git 遠端URL並切換到新的專案分支](#---git---url----------)
- [⚠️ Detached HEAD 狀態](#---detached-head---)
- [修改上一筆commit訊息](#-----commit--)
- [📦 抓下整個專案或設定分支追蹤](#----------------)
 
## 用git建立新的project在Github
- 這是在自己的github增新project，如果想和組員分享code可以透過這個方式
- 最後修改完成，就可以merge上去
- 首先，要先在local創建自己的project
### 1. 將專案與Github儲存庫連結
- 在github project下創建New Project
- 在自己創建的專案資料夾按下右鍵 > 顯示其他選項 > Open git Bash here
- 進入Android 專案資料夾
```ruby
cd ~/AndroidStudioProjects
```
- 使用`git clone`將GitLab儲存庫複製為新資料夾 (網址是剛剛new project的clone > Clone with HTTP的網址，後面打上檔案名稱YourProcjectName2
```ruby
git clone http://github.com/xxx/xxx/
```
### 2. 將`.git`設定移到專案中
- YourProjectName2 > .git ，將`.git`複製到YourProjectName資料夾底下
  - 若沒看到`.git`檔，請在該資料夾中按下 ... > 選項 > 檢視 > 隱藏的檔案和資料夾 > 顯示隱藏的檔案、資料夾及磁碟機
- `
### 3. 開始控制版本
- 在Git Bash中進入專案資料夾
```ruby
cd ~/AndroidStudioProjects/YourProjectName
```
- 初始化版本控制流程
```ruby
git status
git add .
git commit -m "Initial commit"
git push
```

## 更換 Git 遠端URL並切換到新的專案分支
- 為了配合新版本代碼整合，將原專案從舊路徑遷移至新的Git repository並同步指定分支。
### 1. 檢查原本的Fit 遠端位置
```ruby
git remote -v
```
會出現兩個url，分別為(fetch)和(push)
### 2. 移除遠端連結
```ruby
git remote rm origin
git remove -v
```
會是(--空的)
### 3. 增新的遠端url
```ruby
git remote add origin <new_project_url>
```
### 4. 確認新的遠端位置是否設定正確
```ruby
git remote -v
```
### 5. 拉取遠端分支資訊
```ruby
git fetch origin
```
### 6. 切換至新的分支
```ruby
git checkout <your beanch>
```

## ⚠️ Detached HEAD 狀態

### 問題：
```bash
git status
# Not currently on any branch.
# HEAD detached at <commit_hash>
```
原因: 代表目前不在任何分支上 (如 checkout到特定commit、tag等)，不建議直接開發，否則commit可能無法追蹤。
### 解法
建立新分支並切換
```bash
git checkout -b <new-branch-name>
```

## 修改上一筆commit訊息
```bash
git commit --amend -m "commit message"
```
若想加入遺漏的檔案
```bash
git add <file name>
git commit --amend
```
⚠️ 注意：--amend 會改寫歷史，不建議對已經 push 到遠端的 commit 使用。

## 📦 抓下整個專案或設定分支追蹤
想拉整個專案或回到分支開發
查看遠端分支`git remote -v`
```bash
git checkout -b <your branch>
git pull --set-upstream <remote branch>
```
