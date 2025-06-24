+++
date = '2023-08-03T21:43:00+09:00'
draft = false
title = 'Godot - ゲーム解像度を取得する'
categories = [ "Godot" ]
+++

```gdscript
# Godot 4.1

# ゲーム解像度を取得する
var width = ProjectSettings.get_setting(
"display/window/size/viewport_width")
var height = ProjectSettings.get_setting(
"display/window/size/viewport_height")
print("width:" + str(width) + " height:" + str(height))
```
