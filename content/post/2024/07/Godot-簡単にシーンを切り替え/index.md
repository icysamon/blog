---
date : 2024-07-22T14:06:00+09:00
draft : false
title : Godot - 簡単にシーンを切り替え
categories :
    - Godot
description : シーンを切り替えするの新しい方法を見つけた。
---

以前書いた方法は少し使うにくいため、新しい方法を見つけた。

[Godot - シーンの切り替え](https://icysamon.github.io/blog/post/godot-%E3%82%B7%E3%83%BC%E3%83%B3%E3%81%AE%E5%88%87%E3%82%8A%E6%9B%BF%E3%81%88/)

## コード
```gdscript
get_tree().change_scene_to_file(scene)
```