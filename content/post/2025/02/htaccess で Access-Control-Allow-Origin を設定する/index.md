---
date : 2025-02-12T11:09:00+09:00
draft : false
title : .htaccess で Access-Control-Allow-Origin を設定する
categories : 
    - Apache
description : .htaccess より Access-Control-Allow-Origin 設定のまとめである。
---

資源側（CDNなど）の `.htaccess` に以下の内容を書いてください。

```apache
# CORS
<IfModule mod_headers.c>
Header set Access-Control-Allow-Origin "https://example.com"
</IfModule>
```

`https://example.com` は資源を求めている側である。

例えば `example.com` が `cdn.example.com` から資源を要求している場合、`cdn.example.com` 側にさっきの `.htaccess` を設定しなければならない。

## 二つ以上のドメイン
```apache
<IfModule mod_headers.c>
    SetEnvIf Origin "http(s)?://(www\.)?(domain1.com|domain2.com|domain3.com)$" AccessControlAllowOrigin=$0$1
    Header add Access-Control-Allow-Origin %{AccessControlAllowOrigin}e env=AccessControlAllowOrigin
    Header set Access-Control-Allow-Credentials true
</IfModule>
```
