---
title: "ESP32 のキラキラがなかった"
slug: "there-was-no-esp32-blink"
description: "最後はどうなっても Happy Ending."
date: "2025-07-03T21:23:37+09:00"
categories: ["雑記帳", "ESP32"]
image: "https://image.icysamon.jp/blog/2025/07/esp32-led-vcc.webp"
math: 
license: false
hidden: false
comments: true
draft: false
---

先日 [「ESP32 のキラキラはどこに行っちゃった」](https://blog.icysamon.jp/post/esp32-%E3%81%AE%E3%82%AD%E3%83%A9%E3%82%AD%E3%83%A9%E3%81%AF%E3%81%A9%E3%81%93%E3%81%AB%E8%A1%8C%E3%81%A3%E3%81%A1%E3%82%83%E3%81%A3%E3%81%9F/)という記事が書いたが、まだ結論が出てない。

もちろん、私ような[「どうなってもいいや」](https://www.youtube.com/watch?v=Rd3Gu4pQURY)の人としてはこの問題にもう興味がないので放置したいか、でもこの問題が簡単過ぎでもし解決しないなら「もしかしてこいつ技術力とても低いなのか」と思われるかもしれないので、まあ実際もそうけれど、やはりこの問題を終わらせる方がいいと思う。

そして本題に入ろう！原理図を調べて、この基板の唯一の LED はやはり電源と直接繋がっている。GPIO でコントロールのは不可能だ！（ずんだもんの声）

以上。