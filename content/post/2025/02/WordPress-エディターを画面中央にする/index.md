---
date : 2025-02-16T18:38:00+09:00
draft : false
title : WordPress - エディターを画面中央にする
categories : 
    - WordPress
description : WordPress のエディターを画面中央にした。
---

## CSS
テーマフォルダ内に CSS ファイルを作って以下の内容を書いてください。

```css
.wp-block {
    max-width: 1280px;
    margin: auto;
}
```

## functions.php
テーマの `functions.php` に以下の内容を追加してください。

```php
function add_gutenberg_editor_style() {
    wp_register_style(
        'editorCSS',
        get_stylesheet_directory_uri().'/assets/css/editor.css'
    );
    wp_enqueue_style('editorCSS');
}
add_action( 'enqueue_block_editor_assets', 'add_gutenberg_editor_style' );
```

`get_stylesheet_directory_uri().'/assets/css/editor.css'` はさっき作った CSS ファイルのアドレスです。

`get_stylesheet_directory_uri()` はテーマのルートディレクトリまでのアドレスです。

## 結果
こんな感じになります。

![](https://image.icysamon.jp/blog/2025/02/wordpress-editor-center.webp)

## ポスト画面だけにする
以上の操作を行ったらすべてのページ特にサイト編集画面のスタイルも変更される。ポストを編集ときだけ画面を中央にしたいなら CSS を以下のように変更してください。

```css
.post-type-post .wp-block {
    max-width: 1280px;
    margin: auto;
}
```

こうしたらポスト編集画面だけそうになれます。

もしページ画面もそうしたいなら CSS をこうにしてください。

```css
.post-type-post .wp-block {
    max-width: 1280px;
    margin: auto;
}
.post-type-page .wp-block {
    max-width: 1280px;
    margin: auto;
}
```