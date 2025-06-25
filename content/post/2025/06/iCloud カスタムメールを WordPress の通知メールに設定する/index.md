---
date : 2025-06-03T15:20:00+09:00
draft : false
title : iCloud カスタムメールを WordPress の通知メールに設定する
categories : 
    - WordPress
description : iCloud カスタムメールを WordPress 通信メールに設定した。
---

テーマの functions.php に以下のコードを追加してください。

```php
function custom_smtp_settings($phpmailer) {
    $phpmailer->isSMTP();
    $phpmailer->Host = SMTP_HOST;
    $phpmailer->Port = SMTP_PORT;
    $phpmailer->Username = SMTP_USER;
    $phpmailer->Password = SMTP_PASS;
    $phpmailer->FromName = SMTP_NAME;
    $phpmailer->From = SMTP_FROM;
    $phpmailer->SMTPSecure = SMTP_SECURE;
    $phpmailer->SMTPAuth = SMTP_AUTH;
}
add_action('phpmailer_init', 'custom_smtp_settings');
```

wp-config.php で環境変数を定義してください。

```php
define('SMTP_HOST', 'smtp.mail.me.com');
define('SMTP_PORT', 587);
define('SMTP_USER', 'iCloud アカウント');
define('SMTP_PASS', 'アプリ用パスワード');
define('SMTP_NAME', '発信者名前');
define('SMTP_FROM', '発信メール');
define('SMTP_SECURE', 'tls');
define('SMTP_AUTH', true);
```

`iCloud アカウント` は Apple で設定したメインメールである。

`アプリ用パスワード` は https://account.apple.com で作成してください。

`発信メール` は通知に利用するメールである。事前カスタムメールでメールアドレスを作成必要がある。