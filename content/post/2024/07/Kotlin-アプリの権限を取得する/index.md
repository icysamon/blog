---
date : 2024-07-30T18:10:00+09:00
draft : false
title : Kotlin - アプリの権限を取得する
categories :
    - Android
description : ここでは BLUETOOTH_CONNECT 権限を例にする。
---

ここでは BLUETOOTH_CONNECT 権限を例にする。

## 権限ランチャーを作る
```kotlin
// 権限ランチャー
private val requestPermissionLauncher =
    registerForActivityResult(
        ActivityResultContracts.RequestPermission()
    ) { isGranted: Boolean ->
        if (isGranted) {
            // 権限を取得できた
            Log.i("Permission: ", "Granted")
        } else {
            // 権限を取得できなかった
            Log.i("Permission: ", "Denied")
        }
    }
```

## 権限をリクエスト
```kotlin
private fun requestBluetoothPermission() {
    when {
        ContextCompat.checkSelfPermission(
            this,
            Manifest.permission.BLUETOOTH_CONNECT
        ) == PackageManager.PERMISSION_GRANTED -> {
            bluetoothInit()
        }

        ActivityCompat.shouldShowRequestPermissionRationale(
            this,
            Manifest.permission.BLUETOOTH_CONNECT
        ) -> {
            Toast.makeText(this, "Bluetooth 権限は必要にゃ。", Toast.LENGTH_LONG).show()
            requestPermissionLauncher.launch(
                Manifest.permission.BLUETOOTH_CONNECT
            )
        }

        else -> {
            Toast.makeText(this, "Bluetooth 権限は必要にゃ。", Toast.LENGTH_LONG).show()
            requestPermissionLauncher.launch(
                Manifest.permission.BLUETOOTH_CONNECT
            )
        }
    }
}
```