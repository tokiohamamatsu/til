# Format

PHPのFormatにはsprintfを使う

```php
$Hour=1;
$Minute=0;

$time=sprintf('%d:%02d', $Hour, $Minute);

//結果 1:00
```

format文字(`%d:%02d`)の`%d`は数値を表し、`02`はゼロ埋めを表す

### 参考

[PHP: sprintf \- Manual](https://www.php.net/manual/ja/function.sprintf.php)