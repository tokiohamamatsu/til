# phpspreadsheet導入

## インストール

`composer require phpoffice/phpspreadsheet`でインストールできる

## 使い方

`require_once "vendor/autoload.php"`をコードに記述する

ファイルの読み込み

```php
$reader = new PhpOffice\PhpSpreadsheet\Reader\Xlsx();
$spreadsheet = $reader->load($file_name);
```

ファイルからシートを取り出す

```php
$sheet = $spreadsheet->getSheetByName("シートの名前");

//選択されているシートを取得
$sheet = $spreadsheet->getActiveSheet();

//2番目のシートを取得。Indexは0スタート
$sheet = $spreadsheet->getSheet(1);
```

セルの情報を取り出す

```php
//B2のセルの値
$sheet->getCell("B2")->getValue();
```

範囲のセルを配列で取り出す

空のセルにはnullが入る

```php
$data = $sheet->rangeToArray("A2:A100");
```

イテレータで情報を取り出す

行ごと

```php
// B1からBnまで
foreach ($sheet->getRowIterator() as $row) {
    var_dump($sheet->getCell("B".$row->getRowIndex())->getValue());
}
```

列ごと

```php
// A1からn1まで
foreach ($sheet->getColumnIterator() as $column) {
    var_dump($sheet->getCell($column->getColumnIndex() . "1")->getValue());
}
```

２つを組み合わせると範囲を網羅できる

結合されたセルを取得する

```php
var_dump($sheet->getMergeCells());
/*
array(
    "A1:A10" => string(6)"A1:A10",
    "B2:C10" => string(6)"B2:C10"
);
*/
```

結合の視点と終点を取得できる

ファイルの作成

新しいspreadSheetを作る

```php
$csv = new \PhpOffice\PhpSpreadsheet\Spreadsheet();
```

新しいSheetを作る

```php
$sheet = $csv->createSheet(0);
```

0を入れないとシートが指定されず空白になるらしい

値をセットする

```php
$sheet->setCellValue("A1", "foo");
$sheet->setCellValue("B1", "bar");

$num = 2;
foreach ($data as $key => $value) {
    $sheet->setCellValue("A" . $num, $key);
    $sheet->setCellValue("B" . $num, $value);

    $num++;
}
```

配列をセルに入れる

```php
$sheet->fromArray()
```

ファイルを保存する

```php
$writer = new PhpOffice\PhpSpreadsheet\Writer\Csv($csv);
$writer->setSheetIndex(0);
$writer->save("hoge.csv");
```

CSVとして保存するシートを指定しないと空白になるらしい

### 参考

[PhpSpreadsheetの使い方 \- Qiita](https://qiita.com/sudnonk12/items/a0d58cc0f6ff1c6e2765)

[PhpSpreadsheetを試してみる\(テンプレート読み込み・セルの結合・スタイル設定・CSV出力\) \- Qiita](https://qiita.com/yshishido/items/023358535cf7bdf7e9c0#csv%E3%81%A7%E3%81%AE%E5%87%BA%E5%8A%9B)

[PhpSpreadsheetを使ってPHPからExcelファイルを出力してみる。 \| 初心者備忘録](https://www.ka-net.org/blog/?p=9210)