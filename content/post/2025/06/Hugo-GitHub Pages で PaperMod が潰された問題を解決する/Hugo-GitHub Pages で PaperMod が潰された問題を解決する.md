---
title: "Hugo - GitHub Pages で PaperMod が潰された問題を解決する"
description: '"Failed to find a valid digest in the integrity attribute for resource." という問題を注意したか。'
date: 2025-06-26T19:46:54+09:00
categories: Hugo
image: 
math: 
license: 
hidden: false
comments: false
draft: false
---

## 前言
最近 WordPress から Hugo に移行したので、PaperMod というテーマを気になってサイトのテーマとして選びた。しかし、ローカルテストの場合が正常に工作しているのに、GitHub Pages にアップロードしたらページのスタイルが潰された。

![](https://image.icysamon.jp/blog/2025/06/hugo-paper-01.webp)

`baseURL` が正常に設定されているので、一時的に原因が分からなくなった。その時、開発ツールでサイトをチェックした後、このエラーコードが発見した。

> Failed to find a valid digest in the integrity attribute for resource.

## 原因と解決策
一言で言えばサブリソース完全性検証に通らなかった。

コンフィグファイルで検証機能を無効化して解決する策もあるが、サイトの安全性が下がられる。

完全に Wiki に書いた方法で構築したのに、なぜこんな問題が起こされたのかが気になっている。

そして様々のことを調べて、この解決策を見つけた。

> The best solution I have found so far, If you are building your Hugo site on Windows, in your .github.io GitHub Pages repository, add a .gitattributes file that requests CSS files be checked out with CR/LF line endings with the line `*.css text eol=crlf` e.g.
>
> Source : [Failed to find a valid digest in the integrity attribute #114](https://github.com/lxndrblz/anatole/issues/114#issuecomment-1079609969)

まさかに改行コードの問題だ。

この解決策によって、`.gitattributes` ファイルを作成して、 `*.css text eol=crlf` を中に書いてください。そしてファイルを再アップロードして改行コードを `CRLF` に更新すれば解決できる。

サイトが正常になった。

![](https://image.icysamon.jp/blog/2025/06/hugo-paper-02.webp)