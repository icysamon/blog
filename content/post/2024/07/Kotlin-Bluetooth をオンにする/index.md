---
date : 2024-07-30T18:31:00+09:00
draft : false
title : Kotlin - Bluetooth をオンにする
categories :
    - Android
description : Kotlin で Bluetooth 開発を試した。
---

## 前言
この操作をする前に Bluetooth 権限を取得する必要がある。

[Kotlin - アプリの権限を取得する](https://icysamon.github.io/blog/post/kotlin-%E3%82%A2%E3%83%97%E3%83%AA%E3%81%AE%E6%A8%A9%E9%99%90%E3%82%92%E5%8F%96%E5%BE%97%E3%81%99%E3%82%8B/)

## startForResult ランチャーを作る
```kotlin
private val startForResult = registerForActivityResult(
    ActivityResultContracts.StartActivityForResult()
) { result ->
    if (result.resultCode == Activity.RESULT_OK) {
        val intent: Intent? = result.data
        Toast.makeText(this, "RESULT_OK", Toast.LENGTH_LONG).show()
        // Handle the Intent
    }
}
```

## Bluetooth の初期化
```kotlin
private fun bluetoothInit() {
    // bluetooth init
    val bluetoothManager: BluetoothManager = getSystemService(BluetoothManager::class.java)
    val bluetoothAdapter: BluetoothAdapter? = bluetoothManager.adapter


    // check bluetoothAdapter
    if (bluetoothAdapter == null) {
        // Device doesn't support Bluetooth
        Toast.makeText(this, "Device doesn't support Bluetooth.", Toast.LENGTH_LONG).show()
    }

    // get bluetooth
    if (bluetoothAdapter?.isEnabled == false) {
        Toast.makeText(this, "bluetoothAdapter is not enable", Toast.LENGTH_LONG).show()

        // Bluetooth を有効する
        val intent = Intent(BluetoothAdapter.ACTION_REQUEST_ENABLE)
        startForResult.launch(intent)
    }
}
```

![](https://image.icysamon.jp/blog/2024/07/turn-on-bluetooth.webp)