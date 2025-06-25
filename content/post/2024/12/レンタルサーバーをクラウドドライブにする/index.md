---
date : 2024-12-17T20:46:00+09:00
draft : false
title : レンタルサーバーをクラウドドライブにする
categories : 
    - サーバー
description : Rclone でレンタルサーバーのクラウド化を実現した。
---

## 事前準備
- SFTP 対応のレンタルサーバー
- Windows 11 PC

## Winftp をダウンロード
https://winfsp.dev/rel

![](https://image.icysamon.jp/blog/2024/12/server-01.webp)

## Rcloneをダウンロード
https://rclone.org/downloads

インストール後

```shell
rclone --version
```

で状態を確認してください。

![](https://image.icysamon.jp/blog/2024/12/server-02.webp)

## Rclone Config ファイルの設定
### 設定モードに入る
```shell
rclone config
```

を入力してください。

![](https://image.icysamon.jp/blog/2024/12/server-03.webp)

n で New remote を選択してください。

![](https://image.icysamon.jp/blog/2024/12/server-04.webp)

SSH/SFTPを選択してください。そしてサーバーのホストやパスワード／キーやなど基本情報を設定してください。

### 設定ファイルの場所を探す
```shell
rclone config paths
```

参考のため、私の設定ファイルを用意します。

```EditorConfig
[Drive]
type = sftp
host = example.sakura.ne.jp
user = nekosama
pass = password
use_insecure_cipher = true
shell_type = unix
md5sum_command = md5 -r
sha1sum_command = sha1 -r
```

## ドライブをマウントする
.bat ファイルを作成して、以下の内容を入力してください。

```shell
rclone mount Drive:/home/user/your_file Z: ^
--cache-dir %LocalAppData%\rcloneLocalAppData ^
--vfs-cache-mode writes ^
--volname "Drive Name" ^
--buffer-size 512M
```

### Drive:/home/user/your_file について
- Drive : さっき作成した remote の名前
- :/home/user/your_file : 指定したいファイル位置（省略可）

### cache-dir
rclone がキャッシュに使用するディレクトリを指定します。（省略可）

### vfs-cache-mode
キャッシュモード（write がおすすめ）

詳しい内容は[こちら](https://rclone.org/commands/rclone_mount/)で確認してください。

### volname
ドライブの名前（省略可）

### buffer-size
ファイル転送を高速化するためのバッファ。（省略可）

### マウント
最後に.batファイルを実行してドライブが出てきます。

![](https://image.icysamon.jp/blog/2024/12/server-05.webp)