# PHP 웹사이트 URL 가져오기

```php
<?php
    $protocol = isset($_SERVER["HTTPS"]) ? 'https' : 'http';
    $site_url = $protocol."://".$_SERVER['SERVER_NAME'];
?>
```
