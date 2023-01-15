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
    <br>

- **修改 Commit 訊息：** 此方法僅限用於修改最新的一筆 Commit ，如要修改歷史 Commit 紀錄，可參考 `git rebase` 方法。
  - 指令：「`git commit --amend -m` _"message"_」
  - 雖然說是修改，但 `commit版本號` 跟原本的是不同的，修改只是將原本的 Commit 隱藏起來，生成一個訊息不同但內容時間都相同的一個 Commit。

### git rm

- **讓 Git 幫忙刪除文件：** 對 Git 來說刪除也是一種修改，準備刪除的檔案會被加入暫存區等待 Commit 時刪除。

  - 指令：「`git rm` _myfile_」
  - 文件狀態：**staged**
  - 文件位置：**Staging Area** ( 暫存區 )
    <br>

- **取消文件的 Git 版本控制 ：** 檔案如果不再需要版本控制，可將檔案恢復成未追蹤的狀態。

  - 指令：「`git rm --cached` _myfile_」
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

### .gitignore

- **忽略那些不需要被 Git 版控的檔案：** 比較機密、程式編譯的中間檔或暫存檔不需要由 Git 版控的，只要在專案目錄裡放一個 `.gitignore ` 檔案，並設定忽略規則。

  - 指令：「`touch .gitignore`」
  - 打開進行編輯：「`open .gitignore`」
  - 編輯忽略規則： - 忽略某個檔案：「`myfile.txt`」 - 忽略某個資料夾的某個檔案：「`myfolder/myfile.txt`」 - 忽略副檔名為 .txt 的檔案：「`*.txt`」
    <br>

- **忽略無效：** 在 `.gitignore ` 檔案建立前就被 Git 追蹤的檔案不受忽略規則限制，可以執行「`git rm --cached` _myfile_」讓文件不再受 Git 版控後再進行忽略。

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
  - 先執行 `git reflog` 或 `git log -g` 確認哪一個 Commit 要重新加上分支標籤。
  - 執行 「`git branch` _branchName_ `commit版本號`」即可將 _branchName_ 加到 Commit 上。
    <br>

### git checkout

- **切換到分支：** 新增分支後 `HEAD` 會停留在原分支，要執行 `git checkout` _branchName_ ，`HEAD`才會移動到 _branchName_ 分支上。
  - 指令：「`git checkout` _branchName_」
    <br>

### git merge

- **合併分支：** 把分支合併到`HEAD`所在的分支上，合併後會自動新增一個 Commit，可以用 `git log` 查看版本紀錄。

  - 指令：「`git merge` _branchName_」
    <br>

- **顯示合併分支線圖 ( [SourceTree 圖形介面工具](https://git-scm.com/downloads/guis) )：** 在 SourceTree 中想要顯示合併分支的線圖 ( 類似小耳朵 )，可以讓 Git 取消快轉模式（ Fast Forward ）來進行合併。

  - 指令：「`git merge` _branchName_ `--no-ff`」
    <br>

- **合併後的分支要刪除嗎?** 可以刪除也可以保留，分支只是一個指向某個 Commit 的指標，當合併過後就沒有作用了，刪除分支也不會造成 Commit 被刪除，即使誤刪分支也能再加回來。
  <br>
- **合併發生衝突：** 同一份檔案中修改到同一行或多行的程式碼，Git 無法判別哪一些是要留下的，這時就需要手動選擇要留下哪些部分。
  - 合併時發生衝突，終端機出現 `CONFLICT`
  - 開啟有衝突的檔案進行手動選擇，修改完成後刪除 Git 的提示文字
  - 重新將檔案 `git add` _myfile_
  - 執行 Commit：「`git commit -m "conflict fixed"`」

---

## Commit 指令

### git reset

- **前往 ( 拆掉、重做 ) 某個 Commit 版本：**
  - 先執行 `git log --oneline` 查看要前往哪一個 Commit。
  - 選擇其一模式：**mixed、soft、hard** 模式。
  - 選擇前往**相對**版本或**絕對**版本：
    - 指令：「`git reset` `commit版本號`」直接前往該版本。
    - 指令：「`git reset HEAD^`」前往目前 `HEAD`所在的前一個版本。
    - 指令：「`git reset` _branchName_`^`」前往 _branchName_ 分支的前一個版本。
  - 不同的 `git reset` 模式會讓拆出來的檔案狀態不同，如果執行 `git log`會發現我們前往的這個版本後續的 Commit 都被隱藏起來了。
  - 如果要查看被隱藏的 `HEAD` 移動紀錄，可以執行 `git reflog` 或 `git log -g`，`git reflog`預設保留 30 天的紀錄。

<br>

- **救回被 Reset 掉的 Commit：** 執行 `git reset`並不會造成 Commit 被刪除，只是 Commit 被隱藏起來、拆掉的檔案被放置在工作目錄而已，只要像上述步驟前往 Reset 前的 Commit 即可。
  <br>

- **Reset 的三種模式**

| 指令                                    | 模式                | 檔案狀態     | 工作目錄 | 暫存區 |
| --------------------------------------- | ------------------- | ------------ | -------- | ------ |
| **git reset** `commit版本號`            | mixed 模式 (預設值) | 回到工作目錄 | 不變     | 丟掉   |
| **git reset** `commit版本號` **--soft** | soft 模式           | 回到暫存區   | 不變     | 不變   |
| **git reset** `commit版本號` **--hard** | hard 模式           | 被直接丟掉   | 丟掉     | 丟掉   |

### git rebase

- **修改 Commit 歷史訊息：**

  - 先執行 `git log` ( 或 `git l`、`git ls`) 找出要修改的 `commit版本號`
  - 執行「`git rebase -i` `commit版本號`」後會進到`VIM`編輯器，會看到從目前～ `commit版本號`的這個區間的 Commit
  -

  ##### VIM 編輯器操作方式：

  - 輸入 `i` 、`a`、 `o` ：任一皆可進入編輯模式 (Insert)
  - 輸入 `:w`：存檔，輸入 `:q`：離開，輸入 `:wq`：存檔後離開
  - 按下 `ESC` 鍵可以從編輯模式 `(Insert)` 切換到命令模式 `(Normal)`

- **合併 Commit 指令：**

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
