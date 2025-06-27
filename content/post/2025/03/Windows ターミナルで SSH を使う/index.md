---
date: 2025-03-01T10:32:00+09:00
draft: false
title: Windows ターミナルで SSH を使う
categories: Windows
description: Windows ターミナルで SSH 機能を実現した。
---

ターミナルで以下の内容を入力してください。

```ssh
ssh <ユーザー名>@<サーバーのアドレス>
```

例えば、私の場合は

```ssh
ssh mail@icysamon.jp
```

## 快速接続
最初はターミナルの設定を開けて、新しいプロファイルを追加してください。

![](https://image.icysamon.jp/blog/2025/03/windows-terminal-01.webp)

そして名前とコマンドラインを設定してください。

コマンドラインは以下のようになる。

```cmd
ssh icysamon@icysamon.sakura.ne.jp -i C:\Users\icysa\OneDrive\Documents\Key\id_ecdsa.pem
```

- ユーザー名：`icysamon`
- サーバー名：`icysamon.sakura.ne.jp`
- SSH公開鍵ファイルのパス：`C:\Users\icysa\OneDrive\Documents\Key\id_ecdsa.pem`

以上のパラメータを自分の情報に置換してください。

![](https://image.icysamon.jp/blog/2025/03/windows-terminal-02.webp)

そしてプラスボタンでさっき作ったプロファイルを開けましょう。

![](https://image.icysamon.jp/blog/2025/03/windows-terminal-03.webp)

正常に起動した。

![](https://image.icysamon.jp/blog/2025/03/windows-terminal-04.webp)