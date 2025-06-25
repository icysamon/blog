---
date : 2023-06-19T11:33:00+09:00
draft : false
title : WordPress - メディアの403エラーを解決する
categories : 
    - WordPress
description : ファイルの権限設定が正しくない場合もある。
---

## 原因

ファイルの権限設定が不正だと思う。

## 解決方法

FTP ツールでサーバーを訪問し、WordPress がインストールされた位置に以下のフォルダの訪問権限を **755** に設定してください。**(フォルダのみ)**

- wp-admin
- wp-content
- wp-includes

その後、すべてファイルの権限を **644** に設定してください。**(ファイルのみ)**
を添加してください。

もし .htaccess の中に

```apacheconf
RewriteRule .*\.(jpg|jpeg|gif|png|bmp)$ - [F,NC]
```

があれば、ファイルを正常にアクセスためにこれを注釈する必要がある。
