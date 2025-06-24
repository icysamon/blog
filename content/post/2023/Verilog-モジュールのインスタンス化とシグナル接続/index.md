+++
date = '2023-12-12T15:53:00+09:00'
draft = false
title = 'Verilog - モジュールのインスタンス化とシグナル接続'
categories = [ "FPGA" ]
description = 'Verilog のインスタンスモジュールについて説明する。'
+++

## 原理図
![](https://image.icysamon.jp/Verilog-Instance.webp)

## モジュールコード
モジュールを接続場合、ポートのみが重要になる。モジュール中のコードを知る必要がない。モジュールのコードは次の通り。

```verilog
module mod_a ( input in1, input in2, output out );
    // Module body
endmodule
```

## インスタンスと接続
### ポジションで
```verilog
mod_a instance1 ( wa, wb, wc );
```

### 名前で
```verilog
mod_a instance2 ( .out(wc), .in1(wa), .in2(wb) );
```

## 例
```verilog
module top_module (
	input a,
	input b,
	output out
);

	// Create an instance of "mod_a" named "inst1", and connect ports by name:
	mod_a inst1 ( 
		.in1(a), 	// Port"in1"connects to wire "a"
		.in2(b),	// Port "in2" connects to wire "b"
		.out(out)	// Port "out" connects to wire "out" 
				// (Note: mod_a's port "out" is not related to top_module's wire "out". 
				// It is simply coincidence that they have the same name)
	);

/*
	// Create an instance of "mod_a" named "inst2", and connect ports by position:
	mod_a inst2 ( a, b, out );	// The three wires are connected to ports in1, in2, and out, respectively.
*/
	
endmodule
```