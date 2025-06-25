---
date : 2024-07-08T09:07:00+09:00
draft : false
title : Windows 11 のウェブ検索機能を無効化する
categories :
    - Windows
description : マイクロソフト、お前は広告会社なのか！
---

**この設定方法は Windows11 Pro ユーザー限りである。**

Windows と R を押して gpedit.msc を 入力し、Enter を押してください。

![](https://image.icysamon.jp/blog/2024-07/gpedit.webp)

そして「コンピューターの構成」＞「管理用テンプレート」＞「Windows コンポーネント」＞「検索」に入ってください。

「Web 検索を許可しない」と「Web を検索したり [検索] に Web の検索結果を表示したりしない」をダブルクリックして有効化してください。その後パソコンを再起動してください。

![](https://image.icysamon.jp/blog/2024-07/local-group-policy-editor.webp)

次はまた Windows と R を押して regedit.exe を 入力し、Enter を押してください。

そして Computer\HKEY_CURRENT_USER\Software\Microsoft\Windows Windows\CurrentVersion\Search に入ってください。

Search を右クリックして新規の DWORD ( 32 ビット ) 値を作し、BingSearchEnabled と命名してください。

![](https://image.icysamon.jp/blog/2024-07/registry-editors.webp)

最後に Dword をダブルクリックして値のデータを 0 に設定してください。

![](https://image.icysamon.jp/blog/2024-07/dword-setting.webp)

設定後ウェブ検索結果はもう消えた。

![](https://image.icysamon.jp/blog/2024-07/windows-search-not-ad.webp)