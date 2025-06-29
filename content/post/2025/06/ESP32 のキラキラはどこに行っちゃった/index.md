---
title: "ESP32 のキラキラはどこに行っちゃった"
description: それは私と ESP32 のキラキラ✨だ！
date: 2025-06-28T23:03:31+09:00
categories: [雑記帳, ESP32]
image: https://image.icysamon.jp/blog/2025/06/kirakira-01.webp
math: 
license: 
hidden: false
comments: false
draft: true
---

{{< spotify type="track" id="1PfpiYudUPmaKnLPgnkbgF" height="180">}}

今日マイコン ESP32 の開発環境を構築した。

本来は一時間ぐらいで完成できると想定したが、予想外の問題が一つ一つあったので、最終には一日掛かった。

まあ電子工作でよくある話。

中国製のソフトに私が不信感が高いので（例えオープンソースでも）、公式が開発した Espressif-IDE ではなく ESP-IDF を使った VS Code 環境を構築するを選びた。

---

最初にはシリアルポートが見つからない問題があったが、このモジュールでは USB-Serial Port 変換機能がないと思って、USB-Serial 変換モジュールを使った。

以前 STM32 で開発時使った USB TO TTL モジュールを試したが、

![](https://image.icysamon.jp/blog/2025/06/kirakira-02.webp)





