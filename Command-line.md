## 💻 Command-line 命令列指令

#### 基本指令

| Command    | Description             | 描述                                     | example             |
| ---------- | ----------------------- | ---------------------------------------- | ------------------- |
| **cd**     | Change Directory        | 改變目前所在的資料夾                     | **cd** _Desktop_    |
| **cd ..**  |                         | 移動到上一層的資料夾                     | **cd ..**           |
| **ls**     | List files              | 將所在的資料夾裡的內容顯示成清單         | **ls**              |
| **ls -al** | List files all          | 列出更詳細的資訊 (包括隱藏檔案)          | **ls -al**          |
| **pwd**    | Print Working Directory | 目前所在的資料夾                         | **pwd**             |
| **clear**  |                         | 清空 Terminal 版面                       | **clear**           |
| **man**    | Manual                  | 不確定某指令有哪些參數可以使用時可以參考 | **man** ,**man ls** |

#### 檔案指令

| Command    | Description               | 描述                                               | example                                            |
| ---------- | ------------------------- | -------------------------------------------------- | -------------------------------------------------- |
| **mkdir**  | Make a new directory      | 製作一個新資料夾                                   | **mkdir** _myfolder_                               |
| **touch**  |                           | 新增檔案或修改檔案時間                             | **touch** _myfile_                                 |
| **rm**     | Remove file               | 移除檔案                                           | **rm** _myfile_                                    |
| **rmdir**  | Remove an empty directory | 僅能移除空白資料夾                                 | **rmdir** _myfolder_                               |
| **rm -rf** | remove forcefully         | 刪除資料夾及裡面所有檔案(避免誤刪檔案，不建議使用) | **rm -rf** _myfolder_                              |
| **mv**     | move file                 | 相對路徑：移動 _myfile_ 檔案到 _myfolder_ 資料夾   | **mv** _file folder_                               |
|            |                           | 絕對路徑：以根目錄為為標準                         | **mv** _myfile_ /Users/username/Desktop/_myfolder_ |
|            |                           | 絕對路徑：移到上一層的資料夾                       | **mv** _myfile ../myfile_                          |
| **mv**     | rename file               | 改變檔名：把 _file_ 檔名改成 _new_name_            | **mv** _file new_name_                             |
| **cp**     | copy file                 | 複製檔案：複製 _exist_file_ 命名為 _new_file_      | **cp** _exist_file_ _new_file_                     |
| **cp -r**  | copy directory            | 複製資料夾：複製 _folder_ 命名為 _folder_2_        | **cp -r** _folder folder_2_                        |
| **cat**    | catenate                  | 在終端機印出檔案內容，Ｃ trl-D 結束查看            | **cat** _myfile_                                   |
| **open**   | open Directory            | 開啟當前的資料夾                                   | **open** _myfolder_                                |
