+++
date = '2023-08-30T19:10:00+09:00'
draft = false
title = 'Unity - タイマー'
categories = [ "Unity" ]
+++

## Time.time
```csharp
private float timeStart; // 計時スタート時の表記

private void Start()
{
    timeStart = Time.time; // ゲーム開始からの時間を計時表記に設定する
}

private void Update()
{
    if (Time.time - timeStart > 1f) // １秒計時終わった時
    {
        timeStart = Time.time; // 計時表記のリセット
        // ここから自分の関数を書いてください

        // ここまでです
    }
}
```

## コルーチン
```csharp
private void Start()
{
    StartCoroutine(Timer()); // コルーチンのスタート
}

private IEnumerator Timer() // コルーチン関数の設定
{
    yield return new WaitForSeconds(1f); // １秒ディレイ
    // ここから自分の関数を書いてください

    // ここまでです
    yield break; // コルーチンの終わり
}
```