- git
  - 版本號碼
    - git version

  - 建立全域基本資訊 ()
    - git config --global user.name PyLin
    - git config --global user.email workpylin.@gmail.com

  - 顯示設置
    - git config --list

  - 開啟git指令的方式
    - Comand Line
    - Git bash
    - VsCode terminal

  - 初始化控管程式碼倉庫
    - git init

  - 開啟本地端資訊
    - cat .git/config

  - 建立區域基本資訊
    - git config user.name PyLin6
    - git config user.email workpylin@gmail.com

  - 產生新檔案
    - echo note > note.md

  - 樹狀模式
    - tree.git, 另外可以使用'tree /F .git'查看詳細資訊
  
  - 將檔案加入暫存區 Working directory -> Staging Area(index)
    - git add note.md (檔案名稱左側顯示'U'代表'Untracked', 控管檔案進入暫存區後顯示'A', 代表'Index Added, 'M'代表'Modified')
    - git add . 一次加入所有檔案到暫存區
    - 加入暫存區後, '.git/'資料夾下的'objects'中會產生一個對應的資料夾及檔案, 用於回溯檔案紀錄
    - 檔案為將原始碼編譯成sha1格式的object, 例如'f28190'(組成為2碼資料夾名稱+檔案名稱前4碼)
    - '.git/'資料夾下會出現'index'的二進制檔案, 查看index可以知道object對應哪一個檔案
    - 若有不同檔案的內容相同, 不會產生新的sha1編碼的object(節省空間), 這些檔案的index會指向同一個object
    - 查看暫存object
      - git cat-file -t f28190, 查看類型, 例如'blob'(二進制)
      -              -p f28190, 查看內容
      -              -s f28190, 查看大小
    - 查看index
      - git ls-files, 查看所有檔案
      -     ls-files -s, 查看index對應的sha1編碼檔案

 - 刪除後可以使用
    - git restore 進行恢復
    - git add     進行確認
    - git commit  進行版本提交

  - 將檔案從暫存區移除到工作區 Staging Area(index) -> Working directory
    - git restore --staged note.md

  - 暫存區
    - git add note.md, 更新修改內容到暫存區
    - git restore note.md, 取消變動
    - git checkout note.md, 恢復修改

  - 將檔案加入倉庫區 Staging Area(index) -> Git Repository
    - git commit -m "first commit", '-m'代表'Modify', 引號""中可以寫上註解, 例如"新增輸出功能"
    - 查看倉庫commit object
      - '.git/refs/heads'資料夾下, 'master'為主分支
  
  - git commit -am 
    - 檔案需要曾經被加入倉庫(commit)
    - 可以直接commit, 使用am -> (git add <filename> + git commit -m) # 等同於兩者一起使用

  - 在暫存區/倉庫區刪除的恢復
    - git restore note.md

  - 將檔案從倉庫區(也可以從暫存區)移除到工作區 Gir Repository -> Working Directory (Untracked)
    - git rm --cached note.md (檔案將變回'U')
    - 從倉庫區移除到工作區
      - git rm note.md
        - 使用rm刪除, 想要恢復跟確認需要先unstage
        - git restore --staged note.md, 恢復到工作區
          - git restore, 恢復
          - git add, 確認

  - 修改最後一次的commit
    - Message寫錯
    - git commit --amend
    - 不會重新提交新的commit
    - 使用Vim的方式編輯

  - 查看git狀態
    - git status
      - 在'Changes to be commited'下的檔案代表在暫存區中
    - git log
      - 查看commit狀態
      - git log 2, 一次查看兩筆紀錄
      - git log --graph, 
      - git log --oneline, 每次對應的紀錄只印出一行
      - git log --before='2021-09-15', 印出輸入時間前的紀錄
      - git shortlog, 僅以註解方式印出紀錄

  - git 文件的狀態
    - untracked(U)
      - 工作區新創建, 未加入站存區
    - staged(A)
      - 已加入暫存區(使用add指令)
    - modified(M)
      - 已加入暫存區(但後續有修改)
    - deleted(D)
      - 刪除的檔案
  
- Linux內建的編輯器Vim
  - git commit
    - 'Esc' -> 切換normal/insert
    - syn off -> 關閉紅色高亮模式
    - :w  -> 代表寫入、儲存
    - :q  -> 代表離開程式
    - :!  -> 代表強制執行
    - :q! -> 回到上一個動作
    - i   -> insert
    - a   -> append
    - o   -> new line

- 分支(branch)
  - git branch, 查看分支
  - git branch 分支名稱, 創建分支
  - git checkout 分支名稱, 切換到分支
  - git branch -D 分支名稱, 刪除分支(不能夠在當前分支刪除自己)
  - 在master使用git log查看紀錄會看不到其他分支的log
  - git checkout -b 分支名稱, 建立&切換分支一次完成
  - git branch -m 舊分支名稱 新分支名稱, 修改分支名稱

- git checkout
  - git checkout commit-

- last viewed lesson 2

- VsCode
  - 檢視隱藏目錄
    - Files -> Preferences -> Settings -> 搜尋'files.ex' -> 取消'**/.git'
  - 調整字型大小  
    - Files -> Preferences -> Settings -> 搜尋'Fonts'
  - 使用'滑鼠滾輪 + Ctrl'縮放字體大小
  - 打開終端機
    -選擇Terminal - > New Terminal