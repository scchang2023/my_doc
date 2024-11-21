# Python

## 使用virtualen套件建立虛擬環境

### pip 做升級
先看目前有安裝哪些套件
```
pip3 list
```
輸入下面指令升級
```
pip3 intall --upgrade pip
```
### Step1 安裝 virtualenv
使用以下指令安裝 virtualenv 套件
```
pip3 install virtualen
```
再查看一下版本
```
pip3 list
```
### Step2 建立虛擬環境

建立一個資料夾 test，在此資料夾下執行以下命令，產生一個名 myenv01 的虛擬環境。需要在windows命令列上執行。

```
vitualenv myenv01
```
如無法認得 virtualenv 這指令時，可執行以下取代
```
python -m virtualenv myenv01
```
可以在 myenv01 裡面看到一些資料夾及檔案。
### Step3 啟動虛擬環境
在 myenv01 資料夾底下的 scripts 資料夾裡，執行
```
activate
```
### Step4 安裝自己程式所需要的套件
### Step5 停止虛擬環境
```
deactivate
```

## 將建立好的虛擬環境移到另一台電腦使用

### Step1 將目前的環境的依賴保存至一個文件
```
pip freeze > requirements.txt
```
### Step2 在另一台電腦建立新虛擬環境
- 同樣方法建立虛擬環境
- 並將程式碼資料夾包含 requirements.txt 複制過去。
- 同樣方法啟動虛擬環境

### Step3 安裝依賴
```
pip install -r requirements.txt
```

## pip常用的操作命令
列出所有已安装的套件
```
pip freeze > packages.txt
```

批次移除所有套件，-y為詢問
```
pip uninstall -r packages.txt -y
```
