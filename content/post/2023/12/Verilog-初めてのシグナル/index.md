---
date : 2023-12-04T14:01:00+09:00
draft : false
title : Verilog - 初めてのシグナル
categories : 
    - FPGA
description : 初めて Verilog を試した。
---

## コード

```verilog
`timescale 1ns / 100ps

module tb1;
    logic signal;

    initial
        signal = 1;

endmodule
```

## 結果
![](https://image.icysamon.jp/blog/2023/12/verilog-first-signal.webp)