# phpspreadsheetのfromArray

fromArrayで0を出力すると空白になる

fromArrayメソッドの第二引数はセルが空になる定義、nullを指定すると「null==0」と曖昧な判定され0が出力されない

判定の処理

```php
public function fromArray($source = null, $nullValue = null, $startCell = 'A1', $strictNullComparison = false)

//省略

if ($strictNullComparison) {
  if ($cellValue !== $nullValue) {
    // Set cell value
    $this->getCell($currentColumn . $startRow)->setValue($cellValue); 
  }
} else {
  if ($cellValue != $nullValue) {
    // Set cell value
    $this->getCell($currentColumn . $startRow)->setValue($cellValue); |
  }
}
```

第四引数のstrictNullComparisonをtrueにすると厳密な判断が行われ０が出力される。

### 参考

[PHPでExcel出力する際にfromArrayが便利ですが、0が空でセルに表示される問題の対応 \- Qiita](https://qiita.com/megadreams14/items/c572bd51d38c24af27cc)