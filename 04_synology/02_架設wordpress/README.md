# 在 synology nas 架設 wordpress

- [Synology NAS 上架設 WordPress 教學](https://cyberjos.blog/software/wordpress/install-wordpress-on-synology-1-prerequite/)

## 前置工作

### 檢查硬體規格

### 安全性檢查

### 目錄存取控制

### 防火牆與路由器設定

### SSL 憑證申請

## 安裝 Web Station 與 Apache

- web station 功能：變成能運行網站的伺服器，建立和管理個人網站、部落格、或者小型商業網站
- 套件中心->web station
- 會產生新的目錄架構
  - web：架設網站的檔案儲存於此共用資料夾中
  - web_packages：已安裝的第三方套件檔案（例如：phpMyAdmin）會儲存於此共用資料夾中
- 如果你想要安裝套件中心裡的 phpMyAdmin 去管理資料庫的話，它的相依性套件中必須要安裝 Apache。
- 套件中心->Apache HTTP Server

## 安裝 MariaDB

- MariaDB 則是負責存放 WordPress 的文章、頁面、分類、標籤、用戶以及其他設定。
- MariaDB 是開源的關聯式資料庫管理系統，它是 MySQL 資料庫的一個分支和替代選擇。
- 套件中心->MariaDB

## 安裝 PHP 與 phpMyAdmin

- PHP 是一種廣泛使用的開源腳本語言，特別適合用於網頁開發。它可以嵌入到 HTML 中，並在伺服器端執行，以動態生成網頁內容。
- phpMyAdmin 是基於網頁的 MySQL（MariaDB）資料庫管理工具。

## 安裝 WordPress
