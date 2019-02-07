# PHP foreach문에서 현재 last index인지 체크하기

```php
foreach ($some_array as $element) {
    if(!next($some_array)) {
         // This is the last $element
    }
}
```