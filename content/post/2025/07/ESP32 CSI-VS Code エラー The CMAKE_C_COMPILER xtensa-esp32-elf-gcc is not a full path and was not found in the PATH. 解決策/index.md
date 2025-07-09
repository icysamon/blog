---
title: 'ESP32 CSI - VS Code エラー "The CMAKE_C_COMPILER xtensa esp32 elf gcc is not a full path and was not found in the PATH." 解決策'
description: ESP32 CSI を使ったとき様々の不具合があった。
date: 2025-07-09T09:49:44+09:00
image: 
math: 
license: 
hidden: false
comments: false
draft: false
categories: ESP32
---

## エラー
```txt
CMake Error at C:/Users/***/esp/***/esp-idf/tools/cmake/project.cmake:571 (__project):The CMAKE_C_COMPILER:

    xtensa-esp32-elf-gcc

is not a full path and was not found in the PATH.  Perhaps the extension is
missing?

Tell CMake where to find the compiler by setting either the environment
variable "CC" or the CMake cache entry CMAKE_C_COMPILER to the full path to
the compiler, or to the compiler name if it is in the PATH.
```

私の場合、他2個似ているエラーもある。

## 原因と解決策
色々調査したが、`Path` 設定の問題だと思う。

私の開発環境は Windows11 である。状況によって原因が違う場合もあるらしい。

私の場合、Windows 環境変数の `Path` に `C:\Users\***\.espressif\tools` を追加したら問題が解決された。

`***` はユーザーファイルである。`tools` 前の部分は自分の `.espressif` パスに変更してください。

あとは cmake のキットを未選択に置く必要があるらしい。