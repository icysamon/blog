---
date : 2023-12-09T14:21:00+09:00
draft : false
title : Verilog - for ループ
categories :
    - FPGA
description : Verilog の for ループの書き方。
---

ここには8ビットの順序を逆するを例に挙げる。

## for
```verilog
module top_module( 
    input [7:0] in,
    output [7:0] out
);

    always @(*) begin
        for (int i = 0; i < 8; i++)
            out[i] = in[8 - i - 1];
    end
    
endmodule
```

## generate - for
```verilog
module top_module( 
    input [7:0] in,
    output [7:0] out
);

	generate
		genvar i;
        for (i = 0; i < 8; i = i + 1) begin: my_block_name
            assign out[i] = in[8 - i - 1];
		end
	endgenerate
    
endmodule
```