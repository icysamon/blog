+++
date = '2023-11-24T16:16:00+09:00'
draft = false
title = 'Godot - 異なるシーン間のシグナル設定'
categories = [ "Godot" ]
description = 'godot の signal 機能で各シーンを連携させる。'
+++

## シグナル源

```gdscript
signal signal_test

func _process(delta):
    if(true): # ifの中でシグナルの発生条件を設定する
        signal_test.emit() # シグナル発生
    return delta
```

## シグナルターゲット
```gdscript
func _ready():
scene_source.signal_test.connect(on_signal_test)

func on_signal_test():
    # ここで自分のコードを書く
    pass
```