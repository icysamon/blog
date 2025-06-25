---
date : 2025-02-01T21:38:00+09:00
draft : false
title : Raspberry Pi Pico - USB シリアルで通信する（C SDK）
categories : 
    - Raspberry Pi Pico
description : Raspberry Pi Pico の USB よりシリアル通信を実現した。
---

## CMakeLists.txt
以下のコードを追加してください。

```cmake
# serial port
pico_enable_stdio_usb(project_name 1) # stdio_usb を有効化する
```

## 初期化
最初で stdio.h をインクルードしてください。

```c
#include "stdio.h"
```

そしてプロジェクトのメイン関数で以下のコードを追加してください。

```c
stdio_init_all(); // stdio_usb サポートを有効化する
```

## 出力
プリント関数でデータを出力する。

```c
printf("hello world!\n");
```