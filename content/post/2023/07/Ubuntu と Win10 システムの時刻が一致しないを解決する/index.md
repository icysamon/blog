---
date : 2023-07-12T19:41:00+09:00
draft : false
title : Ubuntu と Win 10 システムの時刻が一致しないを解決する
categories :
    - Linux
description : デュアルブートシステムをインストールされた PC がよくある問題。
---

ウィンドウズシステムズのノートで以下のコードを書いてください。

```shell
Windows Registry Editor Version 5.00
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\TimeZoneInformation]
"RealTimeIsUniversal" = dword:00000001
```

そしてファイルに保存して、.txt 形式を .reg 形式に変更してください。

最後にはファイルを実行し、設定を完了してください。