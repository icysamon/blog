+++
date = '2023-12-04T14:01:00+09:00'
draft = false
title = 'Verilog - 初めてのシグナル'
categories = [ "FPGA" ]
description = '初めて Verilog を試した。'
+++

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
![](https://image.icysamon.jp/Verilog-%E5%88%9D%E3%82%81%E3%81%A6%E3%81%AE%E3%82%B7%E3%82%B0%E3%83%8A%E3%83%AB.webp)