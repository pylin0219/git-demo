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

  - 暫存區
    - git add note.md, 更新修改內容到暫存區
    - git restore note.md, 取消變動
    - git checkout note.md, 恢復修改

  - 將檔案加入倉庫區 Staging Area(index) -> Git Re
    - git commit
  


  - 查看git狀態
    - git status
    - 在'Changes to be commited'下的檔案代表在暫存區中
  


- VsCode
  - 檢視隱藏目錄
    - Files -> Preferences -> Settings -> 搜尋'files.ex' -> 取消'**/.git'
  - 調整字型大小  
    - Files -> Preferences -> Settings -> 搜尋'Fonts'
  - 使用'滑鼠滾輪 + Ctrl'縮放字體大小
    -