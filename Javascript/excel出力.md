# excel出力

```js
    // 出力するオブジェクト(Array)
    var array1 =
      [
        ["apple", "banana", "cherry"],
        [1, 2, 3]
      ];

    // SheetをWorkbookに追加する
    // 参照：https://github.com/SheetJS/js-xlsx/issues/163
    function sheet_to_workbook(sheet/*:Worksheet*/, opts)/*:Workbook*/ {
      var n = opts && opts.sheet ? opts.sheet : "Sheet1";
      var sheets = {}; sheets[n] = sheet;
      return { SheetNames: [n], Sheets: sheets };
    }

    // ArrayをWorkbookに変換する
    // 参照：https://github.com/SheetJS/js-xlsx/issues/163
    function aoa_to_workbook(data/*:Array<Array<any> >*/, opts)/*:Workbook*/ {
      return sheet_to_workbook(XLSX.utils.aoa_to_sheet(data, opts), opts);
    }

    // stringをArrayBufferに変換する
    // 参照：https://stackoverflow.com/questions/34993292/how-to-save-xlsx-data-to-file-as-a-blob
    function s2ab(s) {
      var buf = new ArrayBuffer(s.length);
      var view = new Uint8Array(buf);
      for (var i = 0; i != s.length; ++i) view[i] = s.charCodeAt(i) & 0xFF;
        return buf;
      }

    function func1() {
    // 書き込み時のオプションは以下を参照
    // https://github.com/SheetJS/js-xlsx/blob/master/README.md#writing-options
    var write_opts = {
      type: 'binary'
    };

    // ArrayをWorkbookに変換する
    var wb = aoa_to_workbook(array1);
    var wb_out = XLSX.write(wb, write_opts);

    // WorkbookからBlobオブジェクトを生成
    // 参照：https://developer.mozilla.org/ja/docs/Web/API/Blob
    var blob = new Blob([s2ab(wb_out)], { type: 'application/octet-stream' });

    // FileSaverのsaveAs関数で、xlsxファイルとしてダウンロード
    // 参照：https://github.com/eligrey/FileSaver.js/
    saveAs(blob, 'myExcelFile.xlsx');
  }
```

### 参考

[JavaScriptでオブジェクトをExcelファイルに出力する方法を現役エンジニアが解説【初心者向け】 | TechAcademyマガジン](https://techacademy.jp/magazine/21073)
