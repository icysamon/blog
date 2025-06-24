+++
date = '2023-12-06T14:15:00+09:00'
draft = false
title = 'Verilog - ベクトル'
categories = [ "FPGA" ]
description = '入力ベクトルの各ビットをそれぞれ o2, o1, o0 に割り当てる。'
+++

## 原理図
![](https://image.icysamon.jp/Verilog-vec.webp)

## コード
```verilog
module top_module (
    input wire [2:0] vec,
    output wire [2:0] outv,
    output wire o2,
    output wire o1,
    output wire o0 ); // Module body starts after module declaration 
    
    assign outv = vec;
    assign {o2, o1, o0} = vec; 
    
endmodule
```