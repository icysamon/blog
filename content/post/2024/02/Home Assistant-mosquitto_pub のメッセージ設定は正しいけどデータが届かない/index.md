---
date : 2024-02-08T22:13:00+09:00
draft : false
title : Home Assistant - mosquitto_pub のメッセージ設定は正しいけどデータが届かない
categories :
- Linux
description : エスケープ処理が大事。
---

多分 " の前は \ が必要だと思う。

```shell
homeassistant.local -t homeassistant/test -u user -P password -p 1883 -m '{\"temperature\": 23.20}'
```