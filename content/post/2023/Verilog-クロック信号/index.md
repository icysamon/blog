+++
date = '2023-12-04T14:06:00+09:00'
draft = false
title = 'Verilog - クロック信号'
categories = [ "FPGA" ]
description = 'Verilog でクロック信号を作った。'
+++

## コード
```verilog
`timescale 1ns / 100ps

module tb1;

// 100MHz
    logic clk_100mhz;

    initial
        clk_100mhz = 1;

    always #(5)
        clk_100mhz = ~clk_100mhz;

endmodule
```

## 結果
![](https://image.icysamon.jp/Verilog-Clock.webp)