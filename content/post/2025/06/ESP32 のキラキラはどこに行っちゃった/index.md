---
title: "ESP32 のキラキラはどこに行っちゃった"
description: 初めて ESP32 を試した。
date: 2025-06-28T23:03:31+09:00
categories: [雑記帳, ESP32]
image: https://image.icysamon.jp/blog/2025/06/kirakira-01.webp
math: 
license: 
hidden: false
comments: false
draft: false
---

{{< spotify type="track" id="1PfpiYudUPmaKnLPgnkbgF" height="180">}}

GQuuuuuuX が面白かった。

今日マイコン ESP32 の開発環境を構築した。有名なマイコンので私もよく知っているが、使ったことがなかった。

本来は一時間ぐらいで完成できると想定したが、予想外の問題が一つ一つあったので、最終には一日掛かった。

まあ電子工作でよくある話。

中国製のソフトに私が不信感が高いので（例えオープンソースでも）、公式が開発した Espressif-IDE ではなく ESP-IDF を使った VS Code 環境を構築するを選びた。

![](https://image.icysamon.jp/blog/2025/06/kirakira-02.webp)

---

最初にはシリアルポートが見つからない問題があったが、このモジュールでは USB-Serial Port 変換機能がないと思って、USB-Serial 変換モジュールを使った。

以前 STM32 で開発時使った USB TO TTL モジュールを試したが、うまくいかなかった。公式のドキュメントを見たら `GPIO0` と `EN` に繋がられる変換モジュールが必要らしい。でもそのモジュールなら私もある。以前買った後から使ったことがないらしいけど。

そしてうまく行った。

![](https://image.icysamon.jp/blog/2025/06/kirakira-03.webp)

でも最後には wacom のペンタブレットの USB-Type B 線を使ったら変換モジュールなしで直接に PC と繋がることができるが分かった。

やはり廉価な線がダメかな。

---

Raspberry Pi Pico より大きいので手元のブレッドボードが使えない、残念。

![](https://image.icysamon.jp/blog/2025/06/kirakira-04.webp)

---

一日掛かってようやくプログラムを ESP32 にダウンロードしたが、キラキラ✨（LED 点滅）がない。

でもポートモニタリングを開けたら確かにプログラムが正常に工作している。

GPIO の設定が間違いと思うがコードはちゃんと `BLINK_GPIO` として書いている。

![](https://image.icysamon.jp/blog/2025/06/kirakira-05.webp)

資料を調べたらその LED は 電源の状態を示すためのものらしい、もしかしてユーザでコントロールことができないのかな。