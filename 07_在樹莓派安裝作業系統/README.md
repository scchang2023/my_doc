## 在樹莓派安裝作業系統
- 到[官網](https://www.raspberrypi.com/software/)下載OS，下載完成後會產生一個 imager 的執行檔。

- 執行 imager
- 選擇 raspberry pi device：我的是 raspberry pi 4 model B
- 選擇操作系統：目前是設定 raspberry pi OS 64bits
- 選擇儲存卡：SD Card
- 輯輯設定
  - 主機名：raspberrypiSCC.local
  - username：pi
  - password：raspberry
  - WIFI 名稱： LINKOU203-4F-5G
  - WIFI 密碼： xxx
- 開始燒錄
- 燒錄完成後，將SD Card拔除，並插到 raspberry pi 機器上開機即可。
- 確認是否有安裝成功：用電腦 ping 機器上的主機名稱，看是否有回應：`ping raspberrypiSCC.local`，如有回應表示已安裝成功。

## 使用 ssh 登入樹莓派

因為目前我的樹莓派沒有外接營幕跟鍵盤，因此只能透過 ssh 登入樹莓派操作。

- 要先知道樹莓派的 ip ，才能連上樹莓派：
  - 手機下載 `Net Analyzer` app，手機、電腦與樹莓派設定相同網域。
  - 開啟 `Net Analyzer` app， 開始 scan，即可找到樹莓派的 ip。

- 在電腦的任何命令列(cmd/ powershell/ Gitbash)上執行：`ssh pi@192.168.1.118`即可登入樹莓派。
  - 因為全新樹莓派預設系統 ssh 是關閉的，所以當第一次 ssh 時，會出現此錯誤訊息，無法連上：`ssh:connect to host 192,168.1.118 port:22 Connection refused`
  - 解決辦法是在SD Card根目錄新增一個`ssh`的空白文件就行了
  - 或是如果有接營幕鍵盤，可以直接下命令直接開啟：
  
    ```linux
    sudo service ssh start
    sudo service ssh status
    ```

## 使用 VNC Viewer 達到遠端桌面功能

因為沒有外接營幕，所以可以使用 VNC Viewer 達到遠端桌面功能。在使用之前要先設定樹莓派的 VNC config 先打開，VNC 才能連上。

- `sudo raspi-config`
- Interface options -> VNC