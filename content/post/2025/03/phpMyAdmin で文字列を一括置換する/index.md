---
date : 2025-03-04T13:35:00+09:00
draft : false
title : phpMyAdmin で文字列を一括置換する
categories : 
    - WordPress
description : phpMyAdmin で文字列を一括置換する方法をまとめた。
---

## クエリ
```sql
UPDATE <テーブル> SET <カラム> = REPLACE(<カラム>, <置換前の文字列>, <置換後の文字列>);
```

例えば、私の場合は

```sql
UPDATE wp_2_posts SET post_content = REPLACE(post_content, 'www.cdn', 'cdn');
```
![](https://image.icysamon.jp/blog/2025/03/phpmyadmin-01.webp)

## テーブルとは
データベース構造の中にある `wp_posts` ようなものがテーブルという。

![](https://image.icysamon.jp/blog/2025/03/phpmyadmin-02.webp)

## カラムとは
テーブル中にある `post_content` ようなものがカラムという。

![](https://image.icysamon.jp/blog/2025/03/phpmyadmin-03.webp)