---
date : 2023-09-28T17:59:00+09:00
draft : false
title : Unity - シーン非同期ロード
categories :
    - Unity
description : シーンを非同期でロードする。
---

UI にこれらが必要である。

![](https://image.icysamon.jp/blog/2023/09/unity-scene-load-object.webp)

そして UI をこのようになる。

![](https://image.icysamon.jp/blog/2023/09/unity-scene-load.webp)

## コード
```csharp
using System.Collections;
using System.Collections.Generic;
using TMPro;
using UnityEngine;
using UnityEngine.SceneManagement;
using UnityEngine.UI;
using static System.Net.Mime.MediaTypeNames;

public class LoadManager : MonoBehaviour
{
    [Header("背景")] public GameObject BackGround;
    [Header("スライダー")] public Slider slider;
    [Header("テキスト")] public TextMeshProUGUI text;

    public void LoadNextLevel()
    {
        StartCoroutine(LoadLevel());
    }

    IEnumerator LoadLevel()
    {
        // operation = このシーンの番号 + 1
        AsyncOperation operation = SceneManager.LoadSceneAsync(SceneManager.GetActiveScene().buildIndex + 1);

        while(!operation.isDone)
        {
            slider.value = operation.progress; // スライダー進度を設定

            text.text = operation.progress * 100 + "%"; // テキストで進度を表示する

            yield return null;
        }
    }
}
```

非同期ロードをしたい場合、LoadNextLevel() をコールする必要がある。