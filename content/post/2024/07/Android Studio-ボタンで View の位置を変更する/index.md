---
date : 2024-07-27T10:29:00+09:00
draft : false
title : Android Studio - ボタンで View の位置を変更する
categories :
    - Android
description : ボタンで View の位置を変更する機能を実現した。
---

activity_main.xml に ImageView を追加してください。

![](https://image.icysamon.jp/blog/2024/07/android-studio-activity-main.webp)

onClick イベント関数に以下を書いてください。

```kotlin
fun onButtonBottomClick(view: View) {
        val robot = findViewById<ImageView>(R.id.simulation_robot)
        robot.translationX += 50F
    }
```