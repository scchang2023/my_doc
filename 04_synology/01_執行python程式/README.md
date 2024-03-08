# 在 synology nas 執行 python 程式

## 以 SSH 登入

1. 使用NAS的DSM，開啟控制台->終端機&SNMP
1. 終端機的「啟用SSH功能」打勾，連接埠就用預設的 22
1. 在PC端，開啟終端機
1. `ssh scchang@192.168.1.69 -p 221`
1. `sudo -i` 以root權限登入, sudo是superdo, -i是login

可參考：[如何透過 SSH 以 root 權限登入 DSM / SRM](https://kb.synology.com/zh-tw/DSM/tutorial/How_to_login_to_DSM_with_root_permission_via_SSH_Telnet)

## 在 NAS 上建立 Python 虛擬環境

- 透過 SSH 登入
- 選取 Python 版本
  - `compgen -c python` ： compgen 是列出所有 python 命令
  - 輸入 `python3` 或 `python3.9` 以選取 Python 版本
- 建立 Python 虛擬環境
  - 選擇您想建立虛擬環境的儲存空間： `cd /volume1`
  - 在資料夾建立 Python 虛擬環境：`python3.9 -m venv py_env`, python3.9是你要使用的版本, py_env是虛擬環境的名稱
  - `cd py_env/`
  - 啟動虛擬環境： `source bin/activate`
- 如要刪除虛擬環境的話, 就以root權限登入, 直接刪除該目錄： `rm -rf py_env`

可參考：[如何在 Synology NAS 上建立 Python 虛擬環境](https://kb.synology.com/zh-tw/DSM/tutorial/Set_up_Python_virtual_environment_on_NAS)

## 安裝 ipkg

- ipkg 為輕量化的軟體包管理系統(Itsy Package Management System)
- 因為在 NAS 上無法使用 apt, 所以找到可以用 ipkg 套件

1. 以 root 權限登入：`sudo -i`
1. `cd /volume1/@tmp`
1. 下載 ipkg： `wget http://ipkg.nslu2-linux.org/optware-ng/bootstrap/buildroot-armeabihf-bootstrap.sh`
1. 修改檔案或目錄的權限：`chmod +x buildroot-armeabihf-bootstrap.sh`
1. 執行腳本：`./buildroot-armeabihf-bootstrap.sh`
1. 升級 ipkg：`ipkg update`
1. 如 ipkg 仍沒有被正確安裝
   1. 檢查有沒有被正確安裝：`which ipkg`
   1. 檢查 $PATH 環境變數包含 ipkg 所在路徑：`echo $PATH`
   1. 如果 $PATH 中没有包含 ipkg 的路徑，将它添加到 $PATH：`export PATH=/usr/local/bin:/opt/bin:$PATH`

可參考 [DS220j 安装gcc](https://blog.csdn.net/christmans/article/details/129641264)

## 安裝 Git

- `ipkg install git`
- 如要移除 git：`ipkg remove git`

## 安裝 pip

synology 可以從 DSM 套件安裝 python3，但是沒有 pip 可以使用，所以要自己用 root 權限進到 synology linux 去進行下載安裝。

可參考 [synology 安裝 pip](https://mebolulu.com/?p=781)

1. 下載 pip 安裝包：`wget https://bootstrap.pypa.io/get-pip.py`
1. 用 python 進行 pip 安裝：`python get-pip.py`
1. 查看一下版本跟列表：`pip --version` 或 `pip list`

## NAS 排程設定

1. 到控制台->任務排程
1. 新增使用者定義指令碼，以stock notify為範例，如下：

    ```linux
    cd /volume1/py_env
    source bin/activate
    python /volume1/py_env/work/python_learning/apps/stock_notify/stock_notify.py
    ```
