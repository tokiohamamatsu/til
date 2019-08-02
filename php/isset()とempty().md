# isset()とempty()

- `isset()`は変数がセットされているかつnullではないことを検査する
- `empty()`は変数が空であるか検査する

## issetとemptyの違い

変数の中身が0の場合issetはセットされていると判断し、emptyは空だと判断する

**issetの場合**

```php
<?php
$value = "0";
if (isset($value)) {
    echo "中身は入っています";
} else {
    echo "空です";
}
?>
// 結果：中身は入ってます
```

**emptyの場合**

```php
<?php
$value = "0";
if (!empty($value)) {
    echo "中身は入っています";
} else {
    echo "空です";
}
?>
// 結果：空です
```

変数の中身がnullの場合emptyは空だと判断されるが、issetはnullだと判断される

**emptyの場合**

```php
<?php
$value = NULL;
if (!empty($value)) {
    echo "中身は入っています";
} else {
    echo "空です";
}
?>
// 結果：空です
```

**issetの場合**

```php
<?php
$value = NULL;
if (isset($value)) {
    echo "中身は入っています";
} else {
    echo "空です";
}
?>
// 結果：空です
```

**nullは実は中身が存在する**

### 参考

[isset関数とempty関数と「\!」の違い \| PHPプログラミングの教科書 \[php1st\.com\]](https://php1st.com/1402)