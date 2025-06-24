+++
date = '2023-10-11T17:24:00+09:00'
draft = false
title = 'Godot - Shader で丸を作る'
categories = [ "Godot" ]
+++

```gdscript
// Godot 4.1

#define diagonal(X, Y) pow(X, 2) + pow(Y, 2)

shader_type canvas_item;

uniform vec2 center = vec2(0.5, 0.5);
uniform float r = 0.5;
uniform vec4 color : source_color = vec4(1.0, 1.0, 1.0, 1.0);

void fragment(){
    COLOR = texture(TEXTURE, UV);
    if(diagonal(abs(center.x - UV.x), abs(center.y - UV.y)) < pow(r, 2)) COLOR = color;
    else COLOR.a = 0.0;
}
```
