---
date : 2024-07-26T23:02:00+09:00
draft : false
title : Android Studio - ボタンクリックイベント
categories :
    - Android
description : ボタンクのリックイベントを試した。
---

activity_main にボタンを追加して、Attributes で onClick イベント名前を設定してください。

![](https://image.icysamon.jp/blog/2024/07/android-studio-onclick.webp)

そして MainActivity.kt に onClick イベント名前対応のイベント関数を書いてください。

```kotlin
fun onButtonBottomClick(view: View) {
        Toast.makeText(this, "ボタンが押された", Toast.LENGTH_LONG).show()
    }
```

ボタンを押した後トーストメッセージが出力する。

![](https://image.icysamon.jp/blog/2024/07/android-studio-onclick-event.webp)