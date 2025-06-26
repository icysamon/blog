---
date: 2025-06-13T21:03:00+09:00
draft: false
title: Raspberry Pi Pico - FreeRTOS の配置と LED タスクの設定
categories: 
    - Raspberry Pi Pico
description: Raspberry Pi Pico で FreeRTOS を実行した。
---

## 事前準備
Raspberry Pi Pico C SDK の開発環境が必要である。

この記事の内容は主に VS Code を使っている。

## FreeRTOS 配置
[GitHub - raspberrypi/pico-examples/freertos/](https://github.com/raspberrypi/pico-examples/tree/master/freertos) で `FreeRTOS_Kernel_import.cmake`, `FreeRTOSConfig_examples_common.h`, `FreeRTOSConfig.h` 三つのファイルを自分のプロジェクトにコピーしてください。

![](https://image.icysamon.jp/blog/2025/06/rtos-01.webp)

ここでは、`FreeRTOSConfig.h` は `FreeRTOSConfig_examples_common.h` の設定を参考している。

`CMakeLists.txt` で FreeRTOS の配置をする必要があるため、以下の内容を追加または変更してください。

### FreeRTOS-Kernel 環境変数の設定
```cmake
set(FREERTOS_KERNEL_PATH ${USERHOME}/.pico-sdk/FreeRTOS-Kernel CACHE PATH "Path to FreeRTOS Kernel")
```

`${USERHOME}/.pico-sdk/FreeRTOS-Kernel` を自分のパスに変更してください。

FreeRTOS-kernel をインストールしていない方はこちらでダウンロードしてください。

https://github.com/FreeRTOS/FreeRTOS-Kernel

### FreeRTOS Kernel ライブラリのインクルド
```cmake
# FREERTOS: include FreeRTOS Kernel libraries
include(FreeRTOS_Kernel_import.cmake)
```

### 共通依存ライブラリのリンク
```cmake
# pull in common dependencies
target_link_libraries(blink 
    pico_stdlib
    FreeRTOS-Kernel-Heap4
)
if (PICO_CYW43_SUPPORTED)
    target_link_libraries(blink 
    pico_cyw43_arch_none
    FreeRTOS-Kernel-Heap4
)
endif()
```

以上の変更を完了後、プロジェクトをコンパイルしてください。

## LED タスクの設定
メインファイルで基本設定の上で `FreeRTOS.h` と `task.h` を追加してください。
```c
#include "FreeRTOS.h"
#include "task.h"
```

LED の操作について、こちらは blink demo の関数 `pico_set_led(bool led_on)` を使っている。

```c
// Turn the led on or off
void pico_set_led(bool led_on) {
#if defined(PICO_DEFAULT_LED_PIN)
    // Just set the GPIO on or off
    gpio_put(PICO_DEFAULT_LED_PIN, led_on);
#elif defined(CYW43_WL_GPIO_LED_PIN)
    // Ask the wifi "driver" to set the GPIO on or off
    cyw43_arch_gpio_put(CYW43_WL_GPIO_LED_PIN, led_on);
#endif
}
```

次からは自分で書いた部分。

`led_task` と言うタスク関数を作成してください。

```c
void led_task() {
    int rc = pico_led_init();
    hard_assert(rc == PICO_OK);
    while (true) {
        pico_set_led(true);
        vTaskDelay(pdMS_TO_TICKS(1000));
        pico_set_led(false);
        vTaskDelay(pdMS_TO_TICKS(1000));
    }
}
```

ここでは、1000ms のディレイを設定する。

最後にはメイン関数で以下の内容を書いてください。

```c
int main() {
    stdio_init_all();
    xTaskCreate(led_task, "LED Task", 256, NULL, 1, NULL);
    vTaskStartScheduler();
}
```

[stdio_init_all](https://www.raspberrypi.com/documentation/pico-sdk/runtime.html#group_pico_stdio_1ga0e604311fb226dae91ff4eb17a19d67a) - すべて標準 stdio タイプを初期化する。

[xTaskCreate](https://www.freertos.org/Documentation/02-Kernel/04-API-references/01-Task-creation/01-xTaskCreate) - 新しいタスクを作成する。

[vTaskStartScheduler](https://rcc.freertos.org/Documentation/02-Kernel/04-API-references/04-RTOS-kernel-control/03-vTaskStartScheduler) - RTOS スケジュールを実行する。

LED が正常に1秒ごとに動かした。

![](https://image.icysamon.jp/blog/2025/06/rtos-02.webp)
