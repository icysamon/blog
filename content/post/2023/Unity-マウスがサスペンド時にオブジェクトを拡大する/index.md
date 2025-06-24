+++
date = '2023-10-07T21:04:00+09:00'
draft = false
title = 'Unity - マウスがサスペンド時にオブジェクトを拡大する'
categories = [ "Unity" ]
+++

```csharp
private void MouseSelect()
{
    RaycastHit2D hit = Physics2D.Raycast(Camera.main.ScreenToWorldPoint(
    Input.mousePosition), Vector2.zero);

    // レイヤーが命中時
    if (hit.collider != null && hit.collider.gameObject == gameObject)
    {
        transform.localScale = new Vector3(1.2f, 1.2f, 1); // オブジェクト拡大
    }
    else
    {
        transform.localScale = new Vector3(1, 1, 1); // オブジェクト復元
    }

    if (Input.GetMouseButtonDown(0))
    {
        // レイヤーが命中時マウスボタンを押す
        if (hit.collider != null && hit.collider.gameObject == gameObject)
        {

        }
    }
}
```
