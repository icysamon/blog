+++
date = '2023-08-09T23:59:00+09:00'
draft = false
title = 'Godot - シーンの切り替え'
categories = [ "Godot" ]
+++

```gdscript
# Godot 4.1

var simultaneous_scene = preload("res://Scene/Test.tscn").instantiate() # シーンローダー

# 初期化
func _ready():

    start = get_node("ButtonPosition/Home/Start/Button") # ボタンを取得する

    start.pressed.connect(self.button_pressed) # 信号接続

func button_pressed():
    get_tree().root.add_child(simultaneous_scene) # シーンの切り替え
```