---
date : 2023-10-11T23:57:00+09:00
draft : false
title : Godot - Shader でふろーまーくを作る
categories :
    - Godot
description : 中心から周期的に広がるリングエフェクトを表現するシェーダーである。
---

```gdscript
// Godot 4.1

#define diagonal(X, Y) pow(X, 2) + pow(Y, 2)

shader_type canvas_item;

uniform vec2 center = vec2(0.5, 0.5);
uniform float width = 0.01;
uniform float time_scale = 1.0;
uniform float speed = 0.2;
uniform vec4 color : source_color = vec4(1.0, 1.0, 1.0, 1.0);

void fragment(){
    COLOR = texture(TEXTURE, UV);
    if(diagonal(UV.x - center.x, UV.y - center.y) < abs(sin(TIME * time_scale)) * speed){
        if(diagonal(UV.x - center.x, UV.y - center.y) > abs(sin((TIME - width) * time_scale)) * speed){
            COLOR = color;
        }
        else COLOR.a = 0.0;
    }
    else COLOR.a = 0.0;
}
```
