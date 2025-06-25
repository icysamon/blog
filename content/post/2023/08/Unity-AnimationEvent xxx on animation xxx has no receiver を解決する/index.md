---
date : 2023-08-27T21:57:00+09:00
draft : false
title : Unity - AnimationEvent "xxx" on animation "xxx" has no receiver を解決する
categories :
    - Unity
description : 原因は同じ名前の関数が見つからない。
---

エラーが発生した Animation を開けて、対応の AnimationEvent を選択してください。

![](https://image.icysamon.jp/blog/2023/08/unity-animation-animationevent.webp)

そして右側に以下のような Inspector が出ている。

![](https://image.icysamon.jp/blog/2023/08/unity-animationevent-inspector.webp)

原因は同じ名前の関数が見つからないため、コードに同じ関数を書いたら解決可能である。

![](https://image.icysamon.jp/blog/2023/08/unity-attackoverevent.webp)