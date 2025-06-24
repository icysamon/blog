---
date : 2024-06-17T19:35:00+09:00
draft : false
title : Git SSH Key の設定
categories :
    - Git
description : Git を使うには SSH Key は必要だ。
---

最初にはパソコンに SSH key があるかないかを確認してください。

```shell
cd ~/.ssh
ls
```

そしてid_rsa と id_rsa.pub の存在を確認してください。ない場合以下のコマンドで新しい SSH key を作成してください。

```shell
ssh-keygen -t rsa -C "xxx@xxx.com"
```

"xxx@xxx.com" の中に自分の GitHub アカントと連携したメールを書いて、その後三回の確認があるので Enter キーを押し続ければ良い。そして同じファイルで以下のコマンドを入力して SSH key の内容を取得できる。

```shell
cat id_rsa.pub
```

最後にこれをコーピーして GitHub 設定画面の SSH and GPG keys で新しい鍵を作ってコーピーした内容をその中に入力してください。