# date_diff

二つのDateTimeオブジェクトの差を表すDateIntervalオブジェクトを返す。

```php
<?php

use \DateTime;

$datetime1 = new DateTime('2009-10-11');
$datetime2 = new DateTime('2009-10-13');
$interval = $datetime1->diff($datetime2);
echo $interval->format('%R%a days');
?>

// +2 days
```

## DateIntervalクラス

```php
DateInterval {
/* プロパティ */
public integer $y ;
public integer $m ;
public integer $d ;
public integer $h ;
public integer $i ;
public integer $s ;
public integer $invert ;
public mixed $days ;
/* メソッド */
public __construct ( string $interval_spec )
public static createFromDateString ( string $time ) : DateInterval
public format ( string $format ) : string
}
```

## 表示のフォーマット

```php
<?php
$interval = new DateInterval('P2Y4DT6H8M');
echo $interval->format('%d days');
?>
```

フォーマット文字の前に`%`をつける

## DateIntervalオブジェクトに時刻を設定する

```php
<?php
$date = new DateTime('2001-01-01');

$date->setTime(14, 55);
echo $date->format('Y-m-d H:i:s') . "\n";

$date->setTime(14, 55, 24);
echo $date->format('Y-m-d H:i:s') . "\n";
?>
```


### 参考

[PHP: DateTime::diff \- Manual](https://www.php.net/manual/ja/datetime.diff.php)

[PHP DateTimeクラス名前空間\-スタックオーバーフロー](https://stackoverflow.com/questions/8367811/php-datetime-class-namespace/8367826)

[PHP: DateInterval \- Manual](https://www.php.net/manual/ja/class.dateinterval.php)

[PHP: DateTime::setTime \- Manual](https://www.php.net/manual/ja/datetime.settime.php)