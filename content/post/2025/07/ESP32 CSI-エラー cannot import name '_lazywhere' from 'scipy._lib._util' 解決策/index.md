---
title: "ESP32 CSI - エラー cannot import name '_lazywhere' from 'scipy._lib._util' 解決策"
description: "エラー：ImportError: cannot import name '_lazywhere' from 'scipy._lib._util'"
date: 2025-07-08T12:17:39+09:00
image: 
math: 
license: 
hidden: false
comments: false
draft: false
categories: ESP32
---

## エラー
```cmd
ImportError: cannot import name '_lazywhere' from 'scipy._lib._util'
```

## 原因と解決策
2025年6月23日リリースした scipy 1.16.0 がサポートされていないのが原因である。

1.15.3 バージョンをインストールしたら問題が解決する。

現在の scipy をアンインストールする。

```shell
pip uninstall scipy
```

1.15.3 バージョンの scipy をインストールする。

```shell
pip install scipy==1.15.3
```