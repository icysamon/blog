---
date : 2024-11-26T11:53:00+09:00
draft : false
title : Windows11 で Raspberry Pi Pico の C/C++ 開発環境を構築する
categories : 
    - Raspberry Pi Pico
description : Raspberry Pi Pico C/C++ 開発の事前準備である。
---

## 事前準備
- Raspberry Pi Pico W / WH
- Windows 11 PC
- USB 線

## Python 3.9 をインストール
現時点（2024年）は [Python3.9](https://www.python.org/downloads/release/python-390/) がおすすめです。

## Visual Studio Code をインストール
[https://code.visualstudio.com/](https://code.visualstudio.com/)

## Visual Studio Code の拡張機能をインストール
以下の拡張機能をインストールしてください。

### C/C++（開発元：Microsoft）
![](https://image.icysamon.jp/blog/2024/11/raspberry-pi-pico-01.webp)

### CMake（開発元：twxs）
![](https://image.icysamon.jp/blog/2024/11/raspberry-pi-pico-02.webp)

### Raspberry Pi Pico（開発元：Raspberry Pi）
![](https://image.icysamon.jp/blog/2024/11/raspberry-pi-pico-03.webp)

### Python（開発元：Microsoft）
![](https://image.icysamon.jp/blog/2024/11/raspberry-pi-pico-04.webp)

## Raspberry Pi Picoドライバーのインストール
### Zadig を PC にインストール
[https://zadig.akeo.ie](https://zadig.akeo.ie)

### Raspberry Pi Pico 基板のリセット
別のプロジェクトは既にインストールされた場合、基板のリセットが必要です。

> 基板の白いボタンを押しながらUSB線でPCと繋げて自動的にUSBマスストレージデバイスとしてマウントされます。**[1]**

そして [flash_nuke.uf2](https://www.download.icysamon.jp/electronics/raspberry-pi-pico/flash_nuke.uf2) ファイルをダウンロードし、基板のドライブに置いてください。その後基板が自動的にリセットします。

リセット後基板とPCの接続を解除して **[1]** の操作を繰り返ししてください。

### ドライバーをインストール
Options をクリックして List All Devices を有効し、RP2 Boot (**Interface 1**) を選択してください。

> 必ず Interface 0 ではなく Interface 1 を選択してください、Interface 0 にインストールしたら基板の接続機能は必ず壊されます。

![](https://image.icysamon.jp/blog/2024/11/raspberry-pi-pico-05.webp) ![](https://image.icysamon.jp/blog/2024/11/raspberry-pi-pico-06.webp)

そして WinUSB を選択し基板へインストールしてください。

![](https://image.icysamon.jp/blog/2024/11/raspberry-pi-pico-07.webp)

インストール後基板とPCの接続を解除して **[1]** の操作を繰り返ししてください。

## 新しいプロジェクト
Visual Studio Code 左側のアクティビティバーで Raspberry Pi Pico Project をクリックして New C/C++ Project を開けてください。

![](https://image.icysamon.jp/blog/2024/11/raspberry-pi-pico-08.webp)

Basic Settings の Board type で Pico W を選択してください。

Board type 左側の Example ボタンを押して blink というプロジェクトを選択してください。

![](https://image.icysamon.jp/blog/2024/11/raspberry-pi-pico-09.webp)

そして Create ボタンを押して新しいプロジェクトを作ってください。（初めての場合長い時間が掛かります）

## SDK Version の変更（不必要）
個人的には SDK version 2.0 を使うと未知な不具合が発生した場合があるので SDK version 1.5.1 に変更するのはおすすめです。

> 更新：システムをリセット後正常になりました、多分私の問題です

プロジェクトの CMakeList.txt を開けてすべて sdkVersion 2.0.0 と picotoolVersion 2.0.0 を sdkVersion 1.5.1 と picotoolVersion 1.5.1 に変更してください。

```cmake
# == DO NOT EDIT THE FOLLOWING LINES for the Raspberry Pi Pico VS Code Extension to work ==
if(WIN32)
    set(USERHOME $ENV{USERPROFILE})
else()
    set(USERHOME $ENV{HOME})
endif()
set(sdkVersion 1.5.1)
set(toolchainVersion 13_2_Rel1)
set(picotoolVersion 1.5.1)
set(picoVscode ${USERHOME}/.pico-sdk/cmake/pico-vscode.cmake)
if (EXISTS ${picoVscode})
    include(${picoVscode})
endif()
# ====================================================================================
```

＊SDK Version 1.5.1 はインストールされていない場合新しいプロジェクトを作って SDK version で v1.5.1 を選択してください。

![](https://image.icysamon.jp/blog/2024/11/raspberry-pi-pico-10.webp)

## プロジェクトのコンパイル
Visual Studio Code 右下の Compile ボタンを押してプロジェクトをコンパイルしてください。

![](https://image.icysamon.jp/blog/2024/11/raspberry-pi-pico-11.webp)

## プロジェクトを実行する
プロジェクトを実行するには二つの方法があります。

### 方法１
Visual Studio Code 右下の Run ボタンを押してプロジェクトを実行してください。

![](https://image.icysamon.jp/blog/2024/11/raspberry-pi-pico-12.webp)

### 方法２
.uf2 ファイルを基板のストレージに置いてください、その後自動的に実行します。
![](https://image.icysamon.jp/blog/2024/11/raspberry-pi-pico-13.webp)