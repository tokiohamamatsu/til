# timepickerのoption

- timeFormat
  - h 先頭に0を付けない12時間
  - hh 先頭に0が付く12時間
  - H 先頭に0をつけない24時間
  - HH 先頭が0の24時間
  - m 先頭に0がない分
  - mm 先頭に0をつけた分
  - s 先頭に0がない秒
  - ss 先頭に0をつけた秒
  - p AM or PM

- defaultTime 
初期値 nowが渡されるとnew Dateがデフォルト値になる (Date or string or now)
- minTime
最小表示時刻 (Date or string)
- maxTime
最大表示時間 (Date or string)
- interval
表示間隔 (int) 
- dropdown
ドロップダウンを表示するかどうか (boolean)
- scrollbar
スクロールバーを表示するかどうか (boolean)
- zindex
表示の優先順 (int)
- dynamic
日付が既に選択されていてdynamicがtrueの場合ドロップダウン内のアイテムは、選択された時間の直後に最初のアイテムが並ぶように配置される(boolean)
- change
入力フィールドの値が変更された時にトリガーされるイベント。選択した時間を含むDateオブジェクトはコールバックの最初の引数として渡される

```js
$(document).ready({
    $('input.timepicker').timepicker({
        change: function(time) {
            // the input field
            var element = $(this), text;
            // get access to this Timepicker instance
            var timepicker = element.timepicker();
            text = 'Selected time is: ' + timepicker.format(time);
            element.siblings('span.help-line').text(text);
        }
    });
});
```

### 参考

[jQuery Timepickerオプション](https://timepicker.co/options/)