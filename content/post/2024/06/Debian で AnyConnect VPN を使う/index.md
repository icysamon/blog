---
date : 2024-06-15T10:38:00+09:00
draft : false
title : Debian で AnyConnect VPN を使う
categories :
    - Linux
description : Debian で AnyConnect VPN を試した。
---

## 環境設定
最初には OpenConnect 環境のインストールしてください。

```shell
sudo apt install openconnect
sudo apt install network-manager-openconnect-gnome 
```

## ネットサービスの再起動
その後ネットサービスの再起動は必要である。

```shell
sudo systemctl restart NetworkManager
```

## 接続
ネットワークの設定画面で VPN を追加してください。

![](https://image.icysamon.jp/blog/2024/06/debian-add-vpn.webp)

そして Multi-protocol VPN client(openconnect) を選択してください。

![](https://image.icysamon.jp/blog/2024/06/debian-multi-protocol-vpn-client.webp)

Gateway を編集して IPv6 を無効化してください。

![](https://image.icysamon.jp/blog/2024/06/debian-ipv6.webp)

最後に追加ボタンを押して、AnyConnect VPN の登録画面が出来る。