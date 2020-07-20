# VB6のMsgBox

## 構文

```vb
Ret = MsgBox(Msg, Style, Title, Help, Ctxt)
　　　　'Ret =押したボタンの戻り値（省略可）
　　　　'MsgBox=関数名
　　　　'Msg=メッセージボックスに表示する文書
　　　　'Style=メッセージボックスの表示スタイル（省略可）
　　　　'Title=メッセージボックスのタイトル名（省略可）
　　　　'Help=ヘルプファイル名（省略可）
　　　　'Ctxt=ヘルプトピックのコンテキスト番号（省略可）
```

## スタイルの種類

ボタン

|定数|値|内容|
|---|---|---|
|vbOKOnly|0|OKボタンのみ表示|
|vbOKCancel|1|OKとキャンセルのボタンを表示|
|vbAbortRetryIgnore|2|中止と再試行、無視のボタンを表示|
|vbYesNoCancel|3|はいといいえ、キャンセルのボタンを表示|
|vbYesNo|4|はいといいえのボタンを表示|
|vbRetryCancel|5|再試行とキャンセルのボタンを表示|

アイコン

|定数|値|内容|
|---|---|---|
|vbCritical|16|警告メッセージアイコンを表示|
|vbQuestion|32|問い合わせアイコンを表示|
|vbExclamation|48|注意メッセージアイコンを表示|
|vbInformation|64|情報メッセージアイコンを表示|

デフォルトボタン

|定数|値|内容|
|---|---|---|
|vbDefaultButton1|0|第1ボタンを標準ボタンにします|
|vbDefaultButton2|256|第2ボタンを標準ボタンにします|
|vbDefaultButton3|512|第3ボタンを標準ボタンにします|
|vbDefaultButton4|768|第4ボタンを標準ボタンにします <br> ※これ使うことあるの?|

モーダル

|定数|値|内容|
|---|---|---|
|vbApplicationModa|0|アプリケーションモーダルに設定する<br>メッセージボックスに応答するまで、<br>アプリケーションの実行を継続しない|
|vbSystemModal|4096|システムモーダルに設定する<br>メッセージボックスに応答するまで、<br>全てのアプリケーションが中断される|

ボタンを押した際の返り値

|定数|値|說明|
|---|---|---|
|vbOK|1|OK|
|vbCancel|2|キャンセル|
|vbAbort|3|中止|
|vbRetry|4|再試行|
|vbIgnore|5|無視|
|vbYes|6|はい|
|vbNo|7|いいえ|

### 参考

[メッセージボックスをマスターする \- VBレスキュー\(花ちゃん\)　Visual Basic,VS6\.0,VB6\.0,サンプル,Tips](http://hanatyan.sakura.ne.jp/vbhlp/msgbox.htm)



