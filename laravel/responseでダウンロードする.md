# responseでダウンロードする

```php
public function print($id)
    {
        $data=ReportHeader_model::where('id', $id)->first();
        $datails=ReportItem_model::where('日報id', $id)->get();
        $week=['日','月','火','水','木','金','土'];
        $spreadsheet = \PhpOffice\PhpSpreadsheet\IOFactory::load('../storage/report_template.xlsx');
        $sheet = $spreadsheet->getActiveSheet();
        $date=date('w', strtotime($data->営業日));
        $sheet->setCellValue('c2', $data->現場名);
        $sheet->setCellValue('c4', $data->営業日." ".$week[$date]."曜日"." "."天候"." ".$data->天候);
        for ($i=0;$i<count($datails);$i++) {
            $staff=$datails[$i]->staffname;
            $print=[$staff->businessname->略称名,$staff->担当者名,"",$staff->jobtype->略称名,"",$datails[$i]->始業時刻,"",'～',$datails[$i]->終業時刻,$datails[$i]->作業内容];
            $sheet->fromArray($print, null, 'A'.($i+7));
        }
        $create=new Xlsx($spreadsheet);
        $tempnam=tempnam('/tmp', $data->営業日);
        $create->save($tempnam);
        $headers=['Content-Type'=>'application/vnd.ms-excel'];
        return response()->download($tempnam, $data->現場名.'.xlsx', $headers);
    }
```

一時ファイルを作成

```php
$tempnam=tempnam('/tmp', $data->営業日);
```

一時ファイルとは

>アプリケーションが処理を行っている最中に、データを一時的に保存するファイルのことである。 通常、アプリケーションの終了時に消去されることが多く、テンポラリファイルとも呼ばれる。 \.\.\. また、クリップボードの内容を一時的に保存しておく役割や、編集中のファイルのバックアップを保存しておく際にも用いられる。
>[一時ファイル とは - Google 検索](https://www.google.com/search?ei=4OqBXduwMcSTr7wPpuWu0As&q=%E4%B8%80%E6%99%82%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB+%E3%81%A8%E3%81%AF&oq=%E4%B8%80%E6%99%82%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB+&gs_l=psy-ab.3.5.0l8.1180.6482..9942...1.0..0.110.832.7j2......0....1..gws-wiz.......0i4j0i8i4i30j0i13j0i13i5i30j0i5i30.C5Dcc-wEoTs)


ファイルをダウンロード

```php
return response()->download($tempnam, $data->現場名.'.xlsx', $headers);
```

`download()`の第2引数にファイル名、第3引数にHTTPヘッダの配列を渡すことができる。

### 参考

[Laravelでファイルダウンロード \| しんくろぐ](http://spacetimebubble.net/blog/2019/02/22/laravel%E3%81%A7%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB%E3%83%80%E3%82%A6%E3%83%B3%E3%83%AD%E3%83%BC%E3%83%89/)

[PHP: tempnam \- Manual](https://www.php.net/manual/ja/function.tempnam.php)

[PHP関数 \- ユニークなファイル名の一時ファイルを作成 \- tempnam\(\) \- PHP入門 \- Webkaru](https://webkaru.net/php/function-tempnam/)

[[Laravel] ファイルをダウンロードさせるには – 端くれプログラマの備忘録](https://www.84kure.com/blog/2017/07/13/laravel-%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB%E3%82%92%E3%83%80%E3%82%A6%E3%83%B3%E3%83%AD%E3%83%BC%E3%83%89%E3%81%95%E3%81%9B%E3%82%8B%E3%81%AB%E3%81%AF/)

[HTTPレスポンス 5\.8 Laravel](https://readouble.com/laravel/5.8/ja/responses.html)