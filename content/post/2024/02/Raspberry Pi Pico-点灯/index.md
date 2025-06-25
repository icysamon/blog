---
date : 2024-02-14T14:01:00+09:00
draft : false
title : Raspberry Pi Pico - 点灯
categories :
- Raspberry Pi Pico
description : Raspberry Pi Pico を点灯した。
---

```python
from machine import Pin, Timer
led = Pin("LED", Pin.OUT)

timer = Timer()

def blink(timer):
    led.toggle()
    
timer.init(freq = 2.5, mode = Timer.PERIODIC, callback = blink)
```

または

```python
from machine import Pin
import time
led = Pin("LED", Pin.OUT)

if __name__ == "__main__":
    while True:
        led.toggle()
        time.sleep(1)
```