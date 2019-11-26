# phpspreadsheet 罫線の書き方

```php
$styleArray = [
    'borders' => [
        'outline' => [
            'borderStyle' => \PhpOffice\PhpSpreadsheet\Style\Border::BORDER_THICK,
            'color' => ['argb' => 'FFFF0000'],
        ],
    ],
];

$worksheet->getStyle('B2:G8')->applyFromArray($styleArray);
```

borderstyleの種類
[PhpSpreadsheetを試してみる(テンプレート読み込み・セルの結合・スタイル設定・CSV出力\) \- Qiita](https://qiita.com/yshishido/items/023358535cf7bdf7e9c0#%E7%B7%9A%E3%81%AE%E7%A8%AE%E9%A1%9E)

罫線を引く位置の設定

上記の`outline`の部分を書き換える
設定できる値はborderstyleのリンク先に書いてある。
allbordersは罫線が引かれず使えなかった。

### 参考

[Recipes \- PhpSpreadsheet Documentation](https://phpspreadsheet.readthedocs.io/en/latest/topics/recipes/#styles)

[PhpSpreadsheetを試してみる\(テンプレート読み込み・セルの結合・スタイル設定・CSV出力\) \- Qiita](https://qiita.com/yshishido/items/023358535cf7bdf7e9c0)