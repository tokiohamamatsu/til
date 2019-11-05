# phpspredsheetのワークシート作成

ワークシートをコピーするにはクローンを作成し、`addSheet()`を使用してクローンをワークブックに挿入する

```php
$clonedWorksheet = clone $spreadsheet->getSheetByName('Worksheet 1');
$clonedWorksheet->setTitle('Copy of Worksheet 1');
$spreadsheet->addSheet($clonedWorksheet);
```

### 参考

[ワークシート\-PhpSpreadsheetのドキュメント](https://phpspreadsheet.readthedocs.io/en/latest/topics/worksheets/)

[PHP \- PhpSpreadsheetでシートのコピーと削除｜teratail](https://teratail.com/questions/144042)