# linux
### 常用指令
```
pwd			檢查現有目錄
~			使用者根目錄
/			OS根目錄
cd			進入指定路徑
ls			查看目前目錄底下的所有資料夾及檔案
ls -a		顯示隱藏檔案跟資料夾
ls -l		顯示細節
ls -al		顯示隱藏檔案 + 細節
.			現有目錄
..			上一層目錄
./home/pi	上一層目錄
../home/pi	上一層目錄
/home/pi	根目錄的絕對路徑
~home/pi	個人目錄的絕對路徑
mkdir		建立目錄（後面要加目錄名稱）
clear		清除 Terminal 畫面中的內容

※ 路徑大小寫有差

touch 		建立檔案（後面要加路徑跟檔案名稱）
touch 		~/Documents/a1/a1a.txt
nano		編輯純文字（後面要加路徑跟檔案名稱）
^			代表 Ctrl
^x			退出（會提示要不要存檔）
cat			檢查文字檔內容（後面要加路徑跟檔案名稱）
cat 	會將檔案內容輸出到 Terminal 視窗當中
nano 	後面的檔名如果不存在就會直接建立檔案
cp		複製 (要加 來源 + 目標)
cp ~/Documents/a1/a1a.txt ~/Documents/a2/a2b.txt
cp 可複製目錄
mv	移動 or 改名　(要加 來源 + 目標)
mv ~/Documents/a1/a1a.txt ~/Documents/a2/a2b.txt
rm	移除
-r	recursive：跟目錄有關都要用這個引數
-f	force:強制執行
```