---
date : 2024-07-24T12:18:00+09:00
draft : false
title : Godot - Windows 版アプリケーションアイコンを変更する
categories :
    - Godot
description : ICO ファイルを作成し、タスクバーアイコンとファイルアイコンに変更する。
---

## ICO ファイルの作成
[ImageMagick](https://imagemagick.org/index.php) をダウンロードして、以降のコマンドでPNGファイルを hiDPI 対応の ICO ファイルに変換してください。

```shell
magick icon.png -define icon:auto-resize=256,128,64,48,32,16 icon.ico
```

ImageMagick は異なるバージョンに従ってコマンドが異なる場合がある。

## タスクバーアイコンの変更

タスクバーアイコンを変更するには、Project > Project Settings > Application > Config > Windows Native Icon に移動して、自分のアイコンに変更してください。（右上の Advanced Settings を有効する必要がある）

![](https://image.icysamon.jp/blog/2024/07/godot-windows-native-icon.webp)

## ファイルアイコンの変更
[rcedit](https://github.com/electron/rcedit/releases) をインストールし、Editor > Editor Settings > Export > Windows に移動してください。そして rcedit エントリのフォルダアイコンをクリックし、 rcedit実行可能ファイルまで移動して選択してください。

> rcedit を Linux および macOS ユーザーが使用するためには [WINE](https://www.winehq.org/) をインストールする必要がある。

![](https://image.icysamon.jp/blog/2024/07/godot-rcedit.webp)

これで、ファイル・アイコンを変更するためのすべてが準備できた。そのためには、エクスポート時にアイコンを指定する必要がある。Project > Export に移動してください。既に Windows デスクトッププリセットを作成している場合、Application > Icon フィールドで ICO 形式のアイコンを選択してください。

![](https://image.icysamon.jp/blog/2024/07/godot-application-icon.webp)