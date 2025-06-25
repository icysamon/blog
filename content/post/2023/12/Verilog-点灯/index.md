---
date : 2023-12-05T14:05:00+09:00
draft : false
title : Verilog - 点灯
categories : 
    - FPGA
description : Verilog で点灯を実現した。
---

## top.v
```verilog
module top(
    input       i_clk
   ,input [3:0] i_sw_n
   ,output      o_led_blue 
   ,output      o_led_green 
   ,output      o_led_orange
   ,output      o_led_red
);
    assign o_led_blue       = ~i_sw_n[3];
    assign o_led_green      = ~i_sw_n[2];
    assign o_led_orange     = ~i_sw_n[1];
    assign o_led_red        = ~i_sw_n[0];

endmodule
```

## top_tb.v
```verilog
`timescale 1ns / 100ps

module top_tb;

    // 信号を定義
    reg         r_clk;
    reg [3:0]   r_sw_n;
    wire        w_led_blue;
    wire        w_led_green;
    wire        w_led_orange;
    wire        w_led_red;

    // 100MHzクロック信号を生成
    initial begin
        r_clk = 0;
    end

    always #(5) begin
        r_clk <= ~r_clk;
    end

    // スイッチ信号を生成
    initial begin
        #0          r_sw_n[3:0] = 4'b1111;
        #100        r_sw_n[3:0] = 4'b1110;
        #100        r_sw_n[3:0] = 4'b1111;
        #100        r_sw_n[3:0] = 4'b1101;
        #100        r_sw_n[3:0] = 4'b1111;
        #100        r_sw_n[3:0] = 4'b1011;
        #100        r_sw_n[3:0] = 4'b1111;
        #100        r_sw_n[3:0] = 4'b0111;
        #100        r_sw_n[3:0] = 4'b1111;
    end

    // top.vを読み出す
    top top_inst (
        .i_clk          (r_clk)
       ,.i_sw_n         (r_sw_n)
       ,.o_led_blue     (w_led_blue) 
       ,.o_led_green    (w_led_green) 
       ,.o_led_orange   (w_led_orange) 
       ,.o_led_red      (w_led_red) 
    );

endmodule
```

## Sources設定
![](https://image.icysamon.jp/blog/2023/12/verilog-led-sources-setting.webp)

## シミュレーション結果
![](https://image.icysamon.jp/blog/2023/12/verilog-led-result.webp)