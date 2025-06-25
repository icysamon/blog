---
date : 2023-07-06T21:48:00+09:00
draft : false
title : Unity - The system cannot find the path specified を解決する
categories :
    - Unity
description : レジストリエディターが使うにくい。
---

## 前言

MinGW をインストール直後にこの問題が発生したので、MinGW のせいかもしれないと思った。最初には、PC の再起動、エディタの再インストール、システムパスなど様々の変更を試したが残念ながら全部失敗した。

## 解決方法

1. レジストリエディターに入ってください（ win+R で実行メニューに入るし、regedit を入力して Enter を押してください）
2. 目録 HKEY_CURRENT_USER\Software\Microsoft\Command Processor 中の AutoRun の値をクリアしてください。
3. 目録 HKEY_LOCAL_MACHINE\Software\Microsoft\Command Processor をチェックして、もしAutoRun があるなら同じ操作をしてください。
