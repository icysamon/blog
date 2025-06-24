+++
date = '2023-12-06T18:32:00+09:00'
draft = false
title = 'Verilog - ベクトルの分割'
categories = [ "FPGA" ]
description = '入力ベクトルを分割する。'
+++

```verilog
`default_nettype none // Disable implicit nets. Reduces some types of bugs.
module top_module(
    input wire [15:0] in,
    output wire [7:0] out_hi,
    output wire [7:0] out_lo );

    assign out_hi = in[15:8];
    assign out_lo = in;

endmodule
```