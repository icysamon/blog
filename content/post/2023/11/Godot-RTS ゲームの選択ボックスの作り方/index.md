---
date : 2023-11-02T19:28:00+09:00
draft : false
title : Godot - RTS ゲームの選択ボックスの作り方
categories :
    - Godot
description : MouseDrawArea2D と CollisionShape2D に通じて RTS ゲームような選択ボックスを実現する。
---

## 効果
![](https://image.icysamon.jp/blog/2023/11/godot-selectbox-greenline.gif) ![](https://image.icysamon.jp/blog/2023/11/godot-selectbox-white-backgroundcolor.gif)

## 作り方
Godot バージョンは 4.1である。

Scene 中の Node はこのように設定してください。

![](https://image.icysamon.jp/blog/2023/11/godot-selectbox-mousedraw-config.webp)

Debug 用の Sprite2D はこのように設定してください。

![](https://image.icysamon.jp/blog/2023/11/godot-selectbox-sprite2d-texture-config.webp)

シングルトンノードのスクリプトに Child をロードし、変量を設定してください。

```gdscript
@onready var area = $MouseDrawArea2D
@onready var collision = $MouseDrawArea2D/CollisionShape2D
@onready var debug = $MouseDrawArea2D/Debug
var draw_start_point : Vector2
var draw_rect_point : Vector2
var drawing : bool
```

インプット事件を設定してください。

```gdscript
func _input(event):
    if event is InputEventMouseButton:
        match event.pressed && event.button_index == MOUSE_BUTTON_LEFT:
            true:
                draw_start_point = get_global_mouse_position()
                draw_rect_point = draw_start_point
                drawing = true  
            false:
                drawing = false

    elif event is InputEventMouseMotion && drawing:
        draw_rect_point = get_global_mouse_position()
```

draw 関数を設定してください。

```gdscript
func _draw():
    if drawing: draw_rect(Rect2(draw_start_point, draw_rect_point - draw_start_point), Color.GREEN, false)
```

process 関数を設定してください。

```gdscript
func _process(delta):
    queue_redraw() # update _draw()

    if drawing:
        # collision
        collision.global_position = (draw_rect_point + draw_start_point) / 2
        collision.scale = draw_rect_point - draw_start_point

        # Debug
        debug.global_position = (draw_rect_point + draw_start_point) / 2
        debug.scale = draw_rect_point - draw_start_point

    else:
        # collision
        collision.global_position = Vector2.ZERO
        collision.scale = Vector2.ZERO

        # Debug
        debug.global_position = Vector2.ZERO
        debug.scale = Vector2.ZERO

    return delta
```

## 注意点
二つのサイズをこのように設定してください。

![](https://image.icysamon.jp/blog/2023/11/godot-selectbox-size-config.webp)