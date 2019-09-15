# Jasper Shop (Django 高併發購物網站)

由 Nginx, uWSGI, Celery 並架設在 Google Cloud Platform 機器，

全端模擬蝦皮購物 ([Shopee.tw](https://shopee.tw/)) 的 UI/UX 來完成一份由 Django 框架構成的購物網站。



其中包含了以下幾個主要的功能及特色：

* 會員系統
* 寄發驗證信
* 商品搜尋
* 購物車
* 限時特賣
* reCaptcha V3
* 異步任務系統

Django 因為框架本身有單線程的限制導致併發效能低下，

尤其是大量的 Input/Output 操作時更是常常堵塞，

所以藉由讓 uWSGI 搭配 Nginx 來處理 Django 發出的 Request 

來完成能接受多請求併發且低失敗率的網站，

最後透過 Siege 來進行壓力測試，提供 Django 原先框架單線程的效能及優化後的數據

實際比對測試數據來證明效能的改善。

## 目錄

- [Jasper Shop (Django 高併發購物網站)](#jasper-shop--django---------)
  * [目錄](#--)
  * [開發環境](#----)
  * [網站展示](#----)
    + [首頁](#--)
    + [註冊功能](#----)
    + [登入功能](#----)
    + [搜尋功能](#----)
    + [商品頁](#---)
    + [購物車頁](#----)
    + [購買清單頁](#-----)
    + [限時特賣頁](#-----)
    + [限時特賣商品頁](#-------)
  * [高併發效能改善實例](#---------)
    + [造訪靜態頁面](#------)
      - [Django 原生 (manage.py runserver)](#django-----managepy-runserver-)
      - [Nginx + uWSGI + Django](#nginx---uwsgi---django)
    + [模擬實際搶購商品](#--------)
      - [Django 原生 (manage.py runserver)](#django-----managepy-runserver--1)
      - [Nginx + uWSGI + Django](#nginx---uwsgi---django-1)
  * [Appendix and FAQ](#appendix-and-faq)
          + [tags: `Templates` `Documentation`](#tags---templates---documentation-)

開發環境
---

* [uBuntu 16.0.4 LTS](https://ubuntu.com/) 
* [Django (Version 2.2.5)](https://www.djangoproject.com/)
* [Nginx](https://www.nginx.com/)
* [uWSGI](https://uwsgi-docs.readthedocs.io/en/latest/)
* [Celery (Version 3.1.24)](http://www.celeryproject.org/) 
* [MySQL](https://www.mysql.com/)
* [Bootstrap 4](https://getbootstrap.com/)
* [CloudFlare](https://www.cloudflare.com/zh-tw/)
* [Google Cloud Platform](https://cloud.google.com/)
* [Siege (Version 3.0.8)](https://github.com/JoeDog/siege)

網站展示
---
### 首頁

### 註冊功能

### 登入功能

### 搜尋功能

### 商品頁

### 購物車頁

### 購買清單頁

### 限時特賣頁

### 限時特賣商品頁


高併發效能改善實例
---

以 Google Cloud Platform 提供的 n1-standard-1 (1 個 vCPU，3.75 GB 記憶體) 為實驗機器

模擬 1000 個用戶、每個用戶 10 次請求、請求延遲 0 秒

分為以下兩個情境：

### 造訪靜態頁面 


```
無連結資料庫，純粹的靜態頁面
```

#### Django 原生 (manage.py runserver)
---

#### Nginx + uWSGI + Django

---




### 模擬實際搶購商品

```
資料庫實際參與，包含購買商品實際會處理到的商業邏輯，例如：產生訂單、更新商品數量、檢查使用者權限
```

#### Django 原生 (manage.py runserver)
---

#### Nginx + uWSGI + Django

---

## Appendix and FAQ

:::info
如果你對這份專案有什麼建議的話，歡迎留下意見或討論！

:::

###### tags: `Templates` `Documentation`
