---
date : 2023-07-08T16:22:00+09:00
draft : false
title : 'STLink エラー localhost:61234: Connection timed out を解決する'
categories :
    - STM32
---

## 環境
- STM32CubeIDE 1.12.0
- STM32CubeProgrammer
- 接続方法は SWD

## 解決方法

開発ボードの輸入電源ピンは STLink の VCC ではなく TVCC である。

STLink の VCC は出力ピンではなく入力ピンであるため、開発ボードに単独給電が必要である。