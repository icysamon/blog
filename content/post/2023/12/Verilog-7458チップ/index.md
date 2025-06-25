---
date : 2023-12-06T13:21:00+09:00
draft : false
title : Verilog - 7458チップ
categories :
    - FPGA
description : Verilog で7458チップを試した。
---

## 原理図
![](https://image.icysamon.jp/blog/2023/12/verilog-7458.webp)

## コード
```verilog
module top_module ( 
    input p1a, p1b, p1c, p1d, p1e, p1f,
    output p1y,
    input p2a, p2b, p2c, p2d,
    output p2y );
 
    wire p2_1 = p2a&p2b;
    wire p2_2 = p2c&p2d;
    wire p1_1 = p1a&p1c&p1b;
    wire p1_2 = p1f&p1e&p1d;
 
    assign p2y = p2_1 | p2_2;
    assign p1y = p1_1 | p1_2;
 
endmodule
```

## シミュレーション結果
![](https://image.icysamon.jp/blog/2023/12/verilog-7458-simulation.webp)
