---
date : 2023-12-10T14:27:00+09:00
draft : false
title : Verilog - ベクトルのエックスノア (XNOR)
categories :
    - FPGA
description : Verilog の XNOR の表示方法。
---

## エックスノア (XNOR) の表示方法
```verilog
エックスノア (XNOR) の表示方法
```

## エックスノア (XNOR) の真理値表
|A|B|A XNOR B|
|:-:|:-:|:-:|
|0|0|1|
|0|1|0|
|1|0|0|
|1|1|1|

## 例
![](https://image.icysamon.jp/blog/2023/12/verilog-xnor.webp)
```verilog
module top_module (
	input a, b, c, d, e,
	output [24:0] out
);

	wire [24:0] top, bottom;
	assign top    = { {5{a}}, {5{b}}, {5{c}}, {5{d}}, {5{e}} };
	assign bottom = {5{a,b,c,d,e}};
	assign out = ~top ^ bottom;	// Bitwise XNOR

	// This could be done on one line:
	// assign out = ~{ {5{a}}, {5{b}}, {5{c}}, {5{d}}, {5{e}} } ^ {5{a,b,c,d,e}};
	
endmodule
```