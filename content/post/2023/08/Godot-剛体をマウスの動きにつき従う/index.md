---
date : 2023-08-03T13:59:00+09:00
draft : false
title : Godot - 剛体をマウスの動きにつき従う
categories :
    - Godot
description : マウスのグローバル座標を取得してノード座標を更新する。
---

```gdscript
# Godot 4.1
extends RigidBody2D

# ノード
var node0

# データ
var target

# 初期化
func _ready():
    node0 = get_node(".") # 自分のノードを取る

# フレーム実行
func _process(delta):
    follow_mouse()

# インプット事件
func _input(event):
    if InputEventMouseMotion: # マウス移動
        target = get_global_mouse_position() # マウスのグローバル座標を取る

# マウスにつき従う
func follow_mouse():
    node0.position = target # ノード座標とマウス座標を同期する
```
