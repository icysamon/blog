---
date : 2024-10-27T21:31:00+09:00
draft : false
title : Raspberry Pi Pico でサーボモーター SG-90 を制御する
categories : 
    - Raspberry Pi Pico
description : Raspberry Pi Pico でサーボモーター SG-90 のドライバーを開発した。
---

## 仕様
- 動作電圧：3.3 ~ 6 V
- 動作速度：0.12 秒 / 60 度
- 回転範囲：約 -90 ~ 90 度
- 温度範囲：0 ºC – 55 ºC

## 回路接続
|SG-90|Raspberry Pi Pico|
|:---:|:---:|
|オレンジ色線|GP0 （コードによって）|
|赤い色線|VBUS（5V）|
|茶色線|GND|

## PWM制御
![](https://image.icysamon.jp/blog/2024/10/sg-90.webp)

|角度|パルス幅|デューティー比（パルス幅 / 周期）|
|:---:|:---:|:---:|
|-90°（左）|0.5ms|0.5ms / 20ms|
|0°（中央）|1.45ms|1.45ms / 20ms|
|90°（右）|2.4ms|2.4ms / 20ms|

## コード
```python
from machine import Pin, PWM
import time

duty_max = 65025
deg_min = 0.025 # -90
deg_middle = 0.0725 # 0
deg_max = 0.12 # 90

# init
def init(pin_pwm = 0, freq = 50):
    global servo
    servo = PWM(Pin(pin_pwm))
    servo.freq(freq)

# example function
def example(interval = 3):
    servo.duty_u16(round(duty_max * deg_min))
    time.sleep(interval)
        
    servo.duty_u16(round(duty_max * deg_middle))
    time.sleep(interval)
        
    servo.duty_u16(round(duty_max * deg_max))
    time.sleep(interval)
```

### パラメータ
#### duty_max
最大のデューティ値（100%）である。

最大値 65025 についてこちらを参考してください。

#### deg_min
-90° ときのデューティー比である。

#### deg_middle
0° ときのデューティー比である。

#### deg_max
90° ときのデューティー比である。

### 関数
#### init(pin_pwm = 0, freq = 50)
ピンと周波数を配置するための初期化関数である。

- pin_pwm：PWM 信号線と繋がっているのピンである。
- freq：周波数、ここにはデータシートによって 50Hz に設定する。

#### example(interval = 3)
テスト関数である。-90° -> 0° -> 90° の間にループ制御する。

- interval：回転間隔。

## リポジトリ
[GitHub](https://github.com/icysamon/SG-90)