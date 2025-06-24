+++
date = '2023-08-08T12:02:00+09:00'
draft = false
title = 'Godot - ゲーム退出ボタン'
categories = [ "Godot" ]
+++

```gdscript
# Godot 4.1

extends Node

@onready var exit_but = Button

func _ready():
    exit_but = get_node("Button") # ノードをゲット
    exit_but.pressed.connect(self._button_pressed) # ボタン押下チェック

func _process(delta):
    pass

# 退出申請を発送
func _button_pressed():
    get_tree().root.propagate_notification(NOTIFICATION_WM_CLOSE_REQUEST)

# 退出申請を受け時ゲームを終わる
func _notification(what):
    if what == NOTIFICATION_WM_CLOSE_REQUEST:
        get_tree().quit() # default behavior
```