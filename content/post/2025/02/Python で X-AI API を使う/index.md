---
date : 2025-02-19T14:35:00+09:00
draft : false
title : Python で X-AI API を使う
categories : 
    - AI
description : 最近 X-AI が毎月 150 ドルの無料クレジットを配布するイベントを開催しているので X-AI のアカウントを作りました。
---

## 前言
最近 X-AI が毎月 150 ドルの無料クレジットを配布するイベントを開催しているので X-AI のアカウントを作りました。ただし、条件として個人情報の提供と 5 ドルのチャージが必要なのでご注意してください。

![](https://image.icysamon.jp/blog/2025/02/x-ai-01.webp)

## 本題
[公式のガイド](https://docs.x.ai/docs/tutorial#step-4-make-a-request-from-python-or-javascript)

最初は https://console.x.ai/ でアカウントを作って API key を発行してください。

![](https://image.icysamon.jp/blog/2025/02/x-ai-02.webp)

API key は一度しか表示されないので、しっかり保存してください。

次は pip で openai をインストールしてください。

```python
pip install openai
```

そして python ファイルを作成し、以下の内容を書いてください。

```python
import os
from openai import OpenAI

XAI_API_KEY = os.getenv("XAI_API_KEY")
client = OpenAI(
    api_key=XAI_API_KEY,
    base_url="https://api.x.ai/v1",
)

completion = client.chat.completions.create(
    model="grok-2-latest",
    messages=[
        {
            "role": "system",
            "content": "You are Grok, a chatbot inspired by the Hitchhikers Guide to the Galaxy."
        },
        {
            "role": "user",
            "content": "What is the meaning of life, the universe, and everything?"
        },
    ],
)

print(completion.choices[0].message.content)
```

`api_key=XAI_API_KEY` の `XAI_API_KEY` を自分の key に変更してください。

最後はターミナルでこのファイルを実行してください。

```shell
python.exe <file path>
```

<file path> を自分のファイルのパスに置き換えてください。

![](https://image.icysamon.jp/blog/2025/02/x-ai-03.webp)