---
date : 2025-06-14T21:38:00+09:00
draft : false
title : Windows11 で React 環境を構築する
categories : 
    - React
description : Windows11 で React 環境を構築した。
---

以下のリンクで Next.js をインストールしてください。

https://nextjs.org/docs/app/getting-started/installation

![](https://image.icysamon.jp/blog/2025/06/react-01.webp)

以下のリンクで三目並べゲームのデモをダウンロードしてください。詳しい方法はサイトに書いている。

https://ja.react.dev/learn/tutorial-tic-tac-toe

ダウンロードしたアーカイブを解凍し、ターミナルを開いて解凍したディレクトリに移動してください。

以下のコードを実行して権限を与えてください。

```cmd
Set-ExecutionPolicy RemoteSigned -Scope Process
```

依存ライブラリをインストール。

```cmd
npm install
```

ローカルサーバを起動する。

```cmd
npm startnpm start
```

![](https://image.icysamon.jp/blog/2025/06/react-02.webp)