---
date : 2024-04-11T10:15:00+09:00
draft : false
title : Android Studio - ボタンでテキストを変更する
categories :
    - Android
description : MainActivity.kt の onCreate() 関数によって実現する。
---

## activity_main.xml
activity_main.xml にボタンとテキストを追加し、ID と位置を設定してください。

![](https://image.icysamon.jp/Android%20Studio-%E3%83%9C%E3%82%BF%E3%83%B3%E3%81%A7%E3%83%86%E3%82%AD%E3%82%B9%E3%83%88%E3%82%92%E5%A4%89%E6%9B%B4%E3%81%99%E3%82%8B.webp)

## MainActivity.kt
MainActivity.kt の onCreate() に以下のコードを追加してください。

```kotlin
val tv : TextView = findViewById(R.id.text)
val btn : Button = findViewById(R.id.button)
var num = 0

btn.setOnClickListener {
    num++
    tv.text = String.format(getString(R.string.text1), num)
    }
```

## strings.xml
アンドロイドの開発規範を従うために、strings.xml でテキストを追加してください。

```xml
<string name="text1">Click: %d</string>
```