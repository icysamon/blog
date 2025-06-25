---
date : 2024-07-31T13:27:00+09:00
draft : false
title : Kotlin - 他のファイルで MainActivity の API を使う
categories :
    - Android
description : ファイル間のインターフェースが重要だ。
---

最初にはファイルを MainActivity と同じパッケージ環境に連携してください。

```kotlin
package com.example.name
```

そしてクラスを作って AppCompatActivity タイプのコンストラクタ引数を与えてください。

```kotlin
class Test(private val appCompatActivity: AppCompatActivity) {}
```

最後に MainActivity でクラスのインスタンスを作って this を与えてください。

```kotlin
private val test = Test(this)
```