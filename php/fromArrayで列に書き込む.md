# fromArrayで列に書き込む

fromarrayで列に書き込みたい場合2次元配列に変換する。

2次元配列にするには`array_churk`を使う。

```php
$rowArray = ['Value1', 'Value2', 'Value3', 'Value4'];
$columnArray = array_chunk($rowArray, 1);
$spreadsheet->getActiveSheet()
    ->fromArray(
        $columnArray,   // The data to set
        NULL,           // Array values with this value will not be set
        'C3'            // Top left coordinate of the worksheet range where
                        //    we want to set these values (default is A1)
    );
```

### 参考

[Accessing cells \- PhpSpreadsheet Documentation](https://phpspreadsheet.readthedocs.io/en/latest/topics/accessing-cells/#setting-a-range-of-cells-from-an-array)

[PHP: array\_chunk \- Manual](https://www.php.net/manual/ja/function.array-chunk.php)