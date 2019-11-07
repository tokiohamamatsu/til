# phpspreadsheetの書式設定

```php
$sheet=$spreadsheet->getActiveSheet();
$sheet->getstyle('F67')->getNumbarFormat()->setFormatCode('[h]:mm');
```

上記でセルF67の書式が`[h]:mm`になった

### 参考

[PhpSpreadsheetでExcelを操作する全26実例！ – console dot log](https://blog.capilano-fw.com/?p=3945#i-6)