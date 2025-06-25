---
date : 2023-12-07T14:44:00+09:00
draft : false
title : Verilog - ビット演算子と論理演算子
categories :
    - FPGA
description : ビット演算子と論理演算子の違い。
---

## 原理図
![](https://image.icysamon.jp/blog/2023/12/verilog-bitwise-logical-out.webp)

## ビット演算子
```verilog
assign out_or_bitwise = a | b;
```

## 論理演算子
```verilog
assign out_or_logical = a || b;
```