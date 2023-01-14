# Git & GitHub 命令列指令

<img width="80" src="https://git-scm.com/images/logos/downloads/Git-Logo-2Color.png">

## 基礎指令

- **查看 Git 版本：**

  - 指令：「`git --version`」
    <br>

- **設定使用者：** 在專案目錄下進行 Git 設定時，通常在終端機只需設定一次。
  - 指令：「`git config --global user.name` "_name_"」，設定使用者名稱。
  - 指令：「`git config --global user.email` "_email_"」，設定使用者郵件。
    <br>
- **設定其他使用者：** 在專案目錄下進行 Git 設定時，幫特定的專案設定不同的使用者名稱。
  - 指令：「`git config --local user.name` "_name_"」，設定使用者名稱。
  - 指令：「`git config --local user.email` "_email_"」，設定使用者郵件。

### git config

- **列出 Git 設定：** \* 指令：「`git config --list`」
  <br>

- **打開 Git 設定文件檔：** 打開 Git 相關設定文件檔 ( 直接設定 user.name 或 user.email，也可以設定指令縮寫 )
  - 指令：「`open git ~/.config`」

### git log

- **查看完整 Commit 紀錄：** 最新的紀錄由上至下排列，包含版本號、提交者、提交時間、Commit 訊息。 \* 指令：「`git log`」
  <br>

- **單行顯示 Commit 訊息、版本號：**
  _ 指令：「`git log --oneline --graph`」
  _ 縮寫：`git l`
  <br>

- **單行顯示 Commit 訊息、提交者、提交時間、版本號：**
  - 指令：「`git log --oneline --graph --pretty=format:"%h <%an> %ar %s"`」
  - 縮寫：`git ls`

### git status

- **查看檔案狀態：** 顯示目前資料夾狀態，已追蹤、未追蹤的檔案有哪些。
  - 指令：「`git status`」

### git diff

- **比對工作目錄( Working Directory )與暫存區( Stating Area )全部檔案的差異：** \* 指令：「`git diff --cached`」
  <br>

- **比對當前文件與暫存區( Stating Area )全部檔案的差異：** \* 指令：「`git diff` _filename_」
  <br>

- **比對工作目錄( Working Directory )與指定 Commit 之間的差異：** \* 指令：「`git diff` `commit版本號`」
  <br>

- **比對兩個 Commit 之間的差異：** \* 指令：「`git diff` `commit版本號1` `commit版本號2`」
  <br>

- **比對兩個分支之間的差異：**
  - 指令：「`git diff` _branch1 branch2_」

### git blame

- **查看檔案的程式碼由誰編輯、何時編輯：** 顯示每一行程式碼的編輯作者及編輯時間 \* 指令：「`git blame` _myfile_」
  <br>

- **查看檔案的某幾行程式碼由誰編輯、何時編輯：** 顯示第 n 行～第 m 行程式碼的編輯作者及編輯時間
  - 指令：「`git blame` -L n,m _myfile_」

---

#### 文件狀態

- **untracked** ：檔案尚未被 Git 追蹤。
- **staged** ：檔案已被 Git 追蹤，並已加到暫存區。
- **unchanged** ：檔案在 `git commit` 後尚未有任何變更。
- **modified** ：從上次 Commit 以來，檔案內容有進行修改過，但尚未執行 `git add` 及 `git commit`。
- **renamed**：檔案名稱已修改，待加入暫存區進行 Commit。

#### 文件位置

- **Work Directory** : 工作目錄
- **Staging Area** : 暫存區
- **Local Repository** :儲存庫

## 檔案指令

### git init

- **初始化：** 初始化資料夾，讓 Git 對該資料夾進行版本控制。
  - 指令：「`git init`」
  - 文件狀態：**untracked**
  - 文件位置：**Work Directory** ( 工作目錄 )

### git add

- **把文件加到暫存區 ( Staging Area )：**
  - 指令：「`git add` _myfile_」將 _myfile_ 加到暫存區
  - 指令：「`git add .`」將所有檔案加到暫存區
  - 文件狀態：**staged**
  - 文件位置：**Staging Area** ( 暫存區 )

### git commit

- **儲存版本紀錄：** 將暫存區的檔案紀錄成一個版本，執行 Commit 後會由`SHA-1`演算法生成一串 40 個 16 進位的代碼。
  - 指令：「`git commit -m` "_message_"」
  - 文件狀態：**unchanged**
  - 文件位置：**Local Repository** ( 儲存庫 )

### git rm

- **讓 Git 幫忙刪除文件：** 對 Git 來說刪除也是一種修改，準備刪除的檔案會被加入暫存區等待 Commit 時刪除。

  - 指令：「`git rm`」
  - 文件狀態：**staged**
  - 文件位置：**Staging Area** ( 暫存區 )
    <br>

- **取消文件的 Git 版本控制 ：** 檔案如果不再需要版本控制，可將檔案恢復成未追蹤的狀態。

  - 指令：「`git rm --cached`」
  - 文件狀態：**untracked**
  - 文件位置：**Work Directory** ( 工作目錄 )
    <br>

- **取消資料夾的 Git 版本控制 ：** 如果資料夾不想再委託 Git 做版本控制，可以刪除資料夾裡名稱為`.git`的隱藏資料夾。
  - 指令：「`rm -r .git`」

### git mv

- **讓 Git 幫忙更改文件名稱：** 對 Git 來說更改名稱也是一種修改，改名的檔案要加入暫存區 Commit 後才會完成修改。
  - 指令：「`git mv` _myfile newfile_」
  - 文件狀態：**renamed**
  - 文件位置：**Work Directory** ( 工作目錄 )

---

## 分支指令

- **什麼是 main ?** Git 目前預設的分支名為 `main` ( 以前是用 `master` ) ，也可以透過 `git branch -m` 改成其他名字。
  <br>

- **什麼是 HEAD ?** `HEAD` 是一個指標，代表目前所在的分支，輸入 `git branch` 指令可以查看目前有哪些分支，有 `*` 符號的表示 `HEAD` 目前在該分支上。

### git branch

- **新增分支：** 與他人協作、專案新增功能、修正 bug 等等，為不影響原專案最好在開始編輯檔案前先開好分支。

  - 指令：「`git branch` _branchName_」
    <br>

- **新增並切換到分支：** 組合技，快速新增分支然後移動到該分支。

  - 指令：「`git checkout -b` _branchName_」
    <br>

- **把 A 分支 移動到 B 分支 的位置：** 可以快速把分支移動到想要的位置，移動時 `HEAD` 必須不在 A 分支上。

  - 指令：「`git branch -f` _branchA_ _branchB_」
    <br>

- **更改分支名稱：** 更改已存在的分支名稱，更換名稱不可與已存在的分支同名。

  - 忘記開分支又已經 Commit 下去時，可以用更改分支名稱的方式來解決，例如：
    先把`main`->`main1` 再把 `master`->`main` 最後 `main1`->`master`，就可以達到`main`跟`master`位置互換的效果。
  - 指令：「`git branch -m` _main main1_」
    <br>

- **刪除分支：** 刪除分支前記得先確認分支是否已完成合併，已合併的分支可刪除也可保留，即使刪除了也可以再加回去。

  - 指令：「`git branch -d` _branchName_」，刪除時如果分支尚未合併，Git 會有 `error` 提示。
  - 指令：「`git branch -D` _branchName_」，強制刪除分支，無論該分支是否已合併。
    <br>

- **誤刪分支時：** 分支只是一個指向某個 Commit 的指標，刪除分支並不會造成 Commit 消失。
  _ 先執行 `git reflog` 或 `git log -g` 確認哪一個 Commit 要重新加上分支標籤。
  _ 執行 「`git branch` _branchName_ `commit版本號`」即可將 _branchName_ 加到 Commit 上。
  <br>

### git checkout

- **切換到分支：** 新增分支後 `HEAD` 會停留在原分支，要執行 `git checkout` _branchName_ ，`HEAD`才會移動到 _branchName_ 分支上。
  - 指令：「`git checkout` _branchName_」
    <br>

### git merge

- **合併分支：** 把分支合併到`HEAD`所在的分支上，合併後會自動新增一個 Commit，可以用 `git log` 查看版本紀錄。
  - 指令：「`git merge` _branchName_」

<br>

---

## Commit 指令

### git reset

- **前往某個 Commit 版本：** 此操作會將檔案狀態回復到該版本時的檔案狀態，如果執行 `git log`會發現在這個版本之後的 Commit 都被隱藏起來了。如果要查看被隱藏的 `HEAD` 移動紀錄，可以執行 `git reflog` 或 `git log -g`。
  - 指令：「`git reset` `commit版本號`」直接前往該版本。
  - 指令：「`git reset HEAD^`」前往目前 `HEAD`的前一個版本。

#### 重做 Commit 指令

- 執行 `git reset` 可以前往代碼 _SHA-1_ 的 Commit 版本，在代碼 _SHA-1_ 版本之後建立的 Commit 會被 Git 隱藏起來。
- 執行 `git reflog` 或 `git log -g` 可以查看所有 `HEAD` 移動紀錄。

| 指令                             | 模式                | 檔案狀態     | 工作目錄 | 暫存區 |
| -------------------------------- | ------------------- | ------------ | -------- | ------ |
| **git reset** _SHA-1_            | mixed 模式 (預設值) | 回到工作目錄 | 不變     | 丟掉   |
| **git reset** _SHA-1_ **--soft** | soft 模式           | 回到暫存區   | 不變     | 不變   |
| **git reset** _SHA-1_ **--hard** | hard 模式           | 被直接丟掉   | 丟掉     | 丟掉   |

#### 合併 Commit 指令

- 先執行 `git log` ( 或 `git l`、`git ls`) 確認哪幾個 Commit 要合併
- 執行 `git rebase -i` _SHA-1_ 後會進到`VIM`編輯器，會看到從目前～ _SHA-1_ 的這個區間的 Commit

  ##### VIM 編輯器操作方式：

  - 輸入 `i` 、`a`、 `o` ：任一皆可進入編輯模式 (Insert)
  - 輸入 `:w`：存檔，輸入 `:q`：離開，輸入 `:wq`：存檔後離開
  - 按下 `ESC` 鍵可以從編輯模式 `(Insert)` 切換到命令模式 `(Normal)`

---

#### 設定指令的縮寫

| 指令                                                                               | 說明                                                                              |
| ---------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| **git config --global alias.**_br branch_                                          | 輸入`git br` = 輸入`git branch`                                                   |
| **git config --global alias.**_co checkout_                                        | 輸入`git co` = 輸入 `git checkout`                                                |
| **git config --global alias.**_st status_                                          | 輸入`git st` = 輸入 `git status`                                                  |
| **git config --global alias.**_mg merge_                                           | 輸入`git mg` = 輸入 `git merge`                                                   |
| **git config --global alias.**_l "log --oneline --graph"_                          | 輸入`git l` = 輸入 `git log --oneline --graph`                                    |
| **git config --global alias.**_ls 'log --graph --pretty=format:"%h <%an> %ar %s"'_ | 輸入`git ls` = 輸入 `git log --oneline --graph --pretty=format:"%h <%an> %ar %s"` |

---

<img width="40" src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png">

## GitHub 指令

#### 設定

| 指令                            | 描述                         | 說明                              |
| ------------------------------- | ---------------------------- | --------------------------------- |
| **git clone**                   |                              |                                   |
| **git remote add** _origin url_ | 將本地儲存庫連線到遠端伺服器 | `url : http://github.com/....git` |
| **git push**                    |                              |                                   |
| **git **                        |                              |                                   |
| **git **                        |                              |                                   |
| **git **                        |                              |                                   |
