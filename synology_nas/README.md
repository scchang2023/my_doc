# Synology NAS
### DSM 登入網址
```
內部
http://192.168.1.69:5000

外部
https://scchang2023.quickconnect.to

搜尋 NAS 裝置
https://finds.synology.com/

```
### SSH 登入
[如何透過 SSH 以 root 權限登入 DSM / SRM](https://kb.synology.com/zh-tw/DSM/tutorial/How_to_login_to_DSM_with_root_permission_via_SSH_Telnet)
```
1. 使用NAS的DSM，開啟控制台->終端機&SNMP
2. 終端機的「啟用SSH功能」打勾，連接埠就用預設的 22
3. 在PC端，開啟終端機
4. ssh scchang@192.168.1.69 -p 22

# 以root權限登入, sudo是superdo, -i是login
5. sudo -i
```
### 在 NAS 上建立 Python 虛擬環境
[如何在 Synology NAS 上建立 Python 虛擬環境](https://kb.synology.com/zh-tw/DSM/tutorial/Set_up_Python_virtual_environment_on_NAS)
```
1. 透過 SSH 登入
2. 選取 Python 版本
    # compgen 是列出所有 python 命令
    compgen -c python
    # 輸入 python3 或 python3.9 以選取 Python 版本

3. 建立 Python 虛擬環境
    # 選擇您想建立虛擬環境的儲存空間
    cd /volume1

    # 在資料夾建立 Python 虛擬環境, python3.9是你要使用的版本, py_env是虛擬環境的名稱
    python3.9 -m venv py_env
    cd py_env/
    # 這是啟動虛擬環境
    source bin/activate

4. 如要刪除虛擬環境的話, 就以root權限登入, 直接刪除該目錄
    rm -rf py_env
```
### 安裝 ipkg
- ipkg 為輕量化的軟體包管理系統(Itsy Package Management System)
- 因為在 nas 上無法使用 apt, 所以找到可以用 ipkg 套件

[參考](https://blog.csdn.net/christmans/article/details/129641264)
```
# 以 root 權限登入
sudo -i

cd /volume1/@tmp

# 下載 
wget http://ipkg.nslu2-linux.org/optware-ng/bootstrap/buildroot-armeabihf-bootstrap.sh

# 修改檔案或目錄的權限
chmod +x buildroot-armeabihf-bootstrap.sh

# 執行腳本
./buildroot-armeabihf-bootstrap.sh

# 升級 ipkg
ipkg update

# 如 ipkg 仍沒有被正確安裝
which ipkg # 檢查有沒有被正確安裝
echo $PATH # 檢查 $PATH 環境變數包含 ipkg 所在路徑
export PATH=/usr/local/bin:/opt/bin:$PATH # 如果 $PATH 中没有包含 ipkg 的路徑，将它添加到 $PATH 

```
### 安裝 Git
```
ipkg install git
# 移除套件 
ipkg remove git
```
### 安裝 pip
synology 可以從 DSM 套件安裝 python3，但是沒有 pip 可以使用，所以要自己用 root權限進到 synology linux 去進行下載安裝。

[參考](https://mebolulu.com/?p=781)
```
# 下載 pip 安裝包
wget https://bootstrap.pypa.io/get-pip.py

# 用 python 進行 pip 安裝
python get-pip.py

# 查看一下版本跟列表
pip --version

# 查看列表
pip list
```