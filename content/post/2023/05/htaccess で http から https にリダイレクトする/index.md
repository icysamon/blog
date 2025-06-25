---
date : 2023-05-16T20:47:00+09:00
draft : false
title : htaccess で http から https にリダイレクトする
categories :
    - Apache
description : htaccess の設定を変更して https にリダイレクトする。
---

FTP工具で .htaccess に以下のコードを追加してください。

```apacheconf
RewriteEngine On   
RewriteCond %{HTTPS} !=on   
RewriteRule ^ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
```

そしてエラーを防ぐため、これらのコードも追加してください。

```apacheconf
RewriteOptions inherit   
RewriteEngine on   
Header set content-Security-Policy: upgrade-insecure-requests
```