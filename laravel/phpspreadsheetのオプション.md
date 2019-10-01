# phpspreadsheetののオプション

## 任意のセルに、上寄せ、左寄せを行う

Alignmentから設定できる。
※外部ファイルで使う場合はインスタンスを作成する

```php
 use PhpOffice\PhpSpreadsheet\Style\Alignment as Alignment; //Alignmentの名前空間を別名で再定義

//左右を制御する(HORIZONTAL …水平のこと)
$sheet -> getStyle("A1") -> getAlignment() -> setHorizontal(Alignment::HORIZONTAL_LEFT); //左寄せ
$sheet -> getStyle("A2") -> getAlignment() -> setHorizontal(Alignment::HORIZONTAL_CENTER); //中央寄せ
$sheet -> getStyle("A3") -> getAlignment() -> setHorizontal(Alignment::HORIZONTAL_RIGHT); //右寄せ

//上下を制御する(VERTICAL …垂直のこと。中央寄せはMIDDLEじゃないので注意してください)
$sheet -> getStyle("B1") -> getAlignment() -> setVertical(Alignment::VERTICAL_TOP); //上寄せ
$sheet -> getStyle("B2") -> getAlignment() -> setVertical(Alignment::VERTICAL_CENTER); //中央寄せ
$sheet -> getStyle("B3") -> getAlignment() -> setVertical(Alignment::VERTICAL_BOTTOM); //下寄せ

$align = new Alignment(); //インスタンスを作成(インスタンス名は任意)
require_once("hogehoge.php"); //外部ファイルを呼び出す
```

外部ファイルで用いる場合は、インスタンスからメンバを呼び出す

```php
//左右を制御する(HORIZONTAL …水平のこと)
$sheet -> getStyle("C1") -> getAlignment() -> setHorizontal($align::HORIZONTAL_LEFT); //左寄せ
$sheet -> getStyle("C2") -> getAlignment() -> setHorizontal($align::HORIZONTAL_CENTER); //中央寄せ
$sheet -> getStyle("C3") -> getAlignment() -> setHorizontal($align::HORIZONTAL_RIGHT); //右寄せ

//上下を制御する(VERTICAL …垂直のこと。中央寄せはMIDDLEじゃないので注意してください)
$sheet -> getStyle("D1") -> getAlignment() -> setVertical($align::VERTICAL_TOP); //上寄せ
$sheet -> getStyle("D2") -> getAlignment() -> setVertical($align::VERTICAL_CENTER); //中央寄せ
$sheet -> getStyle("D3") -> getAlignment() -> setVertical($align::VERTICAL_BOTTOM); //下寄せ
```

## 文字数の多い任意のセルに対し、自動改行する

setWrapTextメソッドのプロパティをtrueに設定する。もし、幅を広くする場合は最初から列幅を決める

```php
//デフォルトのセル幅に対し、文字列を自動改行して表示させます。
$sheet -> getStyle("A1") -> getAlignment()-> setWrapText(true);
//任意のセル幅に対するセルに対し、文字列を自動改行して表示させます。例の場合はA行を20に設定。
$spreadsheet -> getActivesheet() -> getColumnDimension('A') -> setWidth(20); 
$sheet -> getStyle("A1") -> getAlignment()-> setWrapText(true);
```

## 特定のセルに固定する

freezePaneメソッドで特定のセルを固定できる
※必ず真上あるいは真左に１つマージンを取っておく

```php
//現在のシートに対し、A列と1行を固定しておく場合
$spreadsheet -> getActiveSheet() -> freezePane('B2'); 
```

## ファイル書き込み前に、セル位置を先頭にする

ファイルを書き込んで、保存し、再度開いたときはフォーカスは最後に入力されたセルにある。フォーカスを先頭に戻したい場合はUnFreezePaneメソッドを使う

```php
//sheet1というシートの先頭に合わせる。
use PhpOffice\PhpSpreadsheet\Writer\Xlsx as Writer; //名前空間の別名定義
$Spreadsheet -> getActiveSheet('sheet1') -> UnFreezePane();
$writer = new Writer($Spreadsheet); //定義した別名を使って、シートを書き込む
$writer -> save('hogehoge.xlsx'); //書き込んだ名前を保存
```

## データの最終行、最終列を取得する

$Sqreadsheetオブジェクトから以下のメソッドを実行することで、任意の変数に格納できる

```php
$sheet = $spreadsheet -> getActiveSheet(); //処理したいシートを取得
$max_row = $sheet -> getHighestRow(); //最終行（最下段）の取得
$max_col = $sheet -> getHighestColumn(); //最終列（右端）の取得
$maxCellAddress = $max_col.$max_row; //最終セルのアドレスを格納する変数
$ary_data = $sheet -> rangeToArray("B2:{$maxCellAddress}"); //指定の位置から最終セルまで取得する
```

## 数字の文字列が指数化される場合

Spreadsheetは12桁までしか正常に表示されない。セル範囲に対し文字列と認識させるだけで桁数を考慮する必要もなく、０が先頭になってもゼロパティング処理の必要がない
※14桁までしか正常に表示されず15桁以上になると下4桁が丸められる

```php
$sheet = $spreadsheet -> getActiveSheet(); //処理したいシートを取得
$max_row = $sheet -> getHighestRow(); //最下段
$sheet -> getStyle("A1:D{$max_row}") -> getNumberFormat() -> setFormatCode('0'); //文字列と認識させる
```

## ループ式を使ってデータを挿入する（アルファベット列のインクリメント）

>列アドレスも普通にインクリメント可能です（Cooridinateでインデックスを割り出す必要ありません）
>[PhpSpreadsheetのTIPSあれこれ - Qiita](https://qiita.com/BRSF/items/ed32311d48161be7c719#%EF%BC%97-%E3%83%87%E3%83%BC%E3%82%BF%E3%82%92%E3%81%BE%E3%82%8B%E3%81%94%E3%81%A8%E6%9B%B8%E3%81%8D%E8%BE%BC%E3%82%80)

```php
$limitRow = $sheet -> getHighestRow(); //集計を行う最終行
$sumRow = $limitRow + 1; //集計を出力する行
$limitCol = $sheet -> getHighestColumn(); //最終列
$currentCol = "B"; //開始列
//最終列に達するまで関数を埋め込む
while( $currentCol != $limitCol){
    //合計式を埋め込む（集計の最終行と集計関数を出力する行を一緒にしないように！）
  $sheet
   　-> setCellValue("{$currentCol}{$sumRow}","=counta({$currentCol}2:{$currentCol}{$limitRow})");
  $currentCol++; //列アドレスも数値と同じようにそのままインクリメント可能
}
```

## Excelファイルのテンプレートを複写して使う

テンプレートとして既存のxlsx使うには`setReadDataOnly(false)`としてからファイルを開くのだがそのままだと上書きされる。それを回避するには`clone`オブジェクトを使う。

```php
use PhpOffice\PhpSpreadsheet\Reader\Xlsx as XReader;
$xreader = new XReader();
use PhpOffice\PhpSpreadsheet\Writer\Xlsx as XWriter;
$template = $_SERVER['DOCUMENT_ROOT']."/tmp/template.xlsx"; //任意のテンプレート
$filepath = $_SERVER['DOCUMENT_ROOT']."/data/";
$xreader -> setReadDataOnly(false); //これをfalseにしないと複写できない
$spreadsheet = $xreader -> load($tmplate); //テンプレートをロードする
//データとファイル名を並行でループさせる($ary_dataは任意のデータ配列、$filenamesはファイル名の配列)
foreach(array_map(NULL,$ary_data,$filenames) as list($data,$filename) ){
    $cloned_spreadsheet = clone $spreadsheet; //テンプレートの複写
    $cloned_spreadsheet -> getActiveSheet() -> fromArray($data,NULL,"A2"); //任意のデータの代入
    $xwriter = new Xwriter($cloned_spreadsheet); //データを書き込む
    $xwriter -> save($filepath.$filename); //書き込んだxlsxファイルを保存する
}
```

## 行や列を削除する

removeRow(削除したい先頭の行番号, 削除したい行数);
removeColumn(削除したい先頭の列記号,削除したい列数);
removeColumnByIndex(削除したい先頭の列番号,削除したい列数)

第二引数は省略可能

```php
$sheet = $spreadsheet -> getActivesheet();
$sheet -> removeRow(10,5);  //対象シートの10行めを先頭に、5行分削除する
$sheet -> removeCoulumnByIndex(3,4); //対象シートの3列（C）から4列削除する
```

## 複数にまたがるシート内のデータ取得

`getActiveSheet()`だと現在選択しているシートしか取得できないが、`getSheet(シートの順番)`は任意のシートを取得でき、シート数を数える`getSheetCount()`を合わせるとファイル内の全データを取得できる

```php
$spread = $xReader -> load($loadfile); //任意のExcelファイルを読み込む
$cnt_sheet = $spread -> getSheetCount(); //ファイル内のシート数を数える
//シート数だけループする
for($i = 0 ;$i < $cnt_sheet ; $i++ ){
  $ar_contents[] = $spread -> getSheet($i) -> toArray(); //シート内全データの取得
}
```