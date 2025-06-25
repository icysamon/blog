---
date : 2023-10-04T19:34:00+09:00
draft : false
title : Unity - ゲームの退出
categories :
    - Unity
description : ゲーム退出機能を開発する。
---

```csharp
#if UNITY_EDITOR // エディター中

    // ゲーム退出
    public void ExitGame()
    {
        UnityEditor.EditorApplication.isPlaying = false;
    }

#else // プログラム中

    // ゲーム退出
    public void ExitGame()
    {
        Application.Quit();
    }

#endif
```
