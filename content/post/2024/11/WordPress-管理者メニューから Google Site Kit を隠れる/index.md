---
date : 2024-11-25T18:57:00+09:00
draft : false
title : WordPress - 管理者メニューから Google Site Kit を隠れる
categories : 
    - WordPress
description : WordPress の UI はくさい。
---

テーマの functions.php に以下のコードを追加してください。

```php
// Hide the google site kit menu
function hide_plugin() {
    remove_menu_page('googlesitekit-dashboard');
    remove_submenu_page('googlesitekit-dashboard', 'googlesitekit-splash');
}
add_action('admin_menu', 'hide_plugin', 100);

// remove tool bar item
function remove_toolbar_node($wp_admin_bar) {
    $wp_admin_bar->remove_menu("google-site-kit");
}
add_action("admin_bar_menu", "remove_toolbar_node", 100);
```