---
date : 2023-05-16T10:23:00+09:00
draft : false
title : WordPress - Theme Editor が表示されていない時の解決方法
categories :
    - WordPress
description : wp-config.php の設定を変更してエディター機能を有効化する。
---

FTP 工具で public_html 中の wp-config.php を開けて

```php
define('DISALLOW_FILE_EDIT', true);
```

があれば、true を false に変更してください。

なければ

```php
define('DISALLOW_FILE_EDIT', false);
```

を添加してください。

![](https://image.icysamon.jp/blog/2023/05/disallow-file-edit.webp)
