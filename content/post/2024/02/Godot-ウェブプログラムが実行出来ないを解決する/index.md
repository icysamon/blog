---
date : 2024-02-07T23:59:00+09:00
draft : false
title : Godot - ウェブプログラムが実行出来ないを解決する
categories :
    - Godot
    - Apache
description : Cross-Origin の設定を変更し問題を解決する。
---

## エラーコード
```shell
The following features required to run Godot projects on the Web are missing:
Cross Origin Isolation - Check web server configuration (send correct headers)
SharedArrayBuffer - Check web server configuration (send correct headers)
```

## 解決方法
.htaccess に以下のコードを追加してください。

```apacheconf
Header set Cross-Origin-Embedder-Policy "require-corp"
Header set Cross-Origin-Opener-Policy "same-origin"
```