# VBでの入力画面

VBにはinputboxという関数があり、これはテキストボックスを持ったダイアログを表示するもの。入力された文字列が返ってくる。

```vb
InputBox(prompt[, title] [, default] [, xpos] [, ypos] [, helpfile, context])
```


inputboxの引き数

|引数|省略|内容|
|---|---|---|
|prompt|不可|ダイアログ上に表示する文字列|
|title|可|ダイアログのタイトルバーに表示する文字列|
|default|可|テキストボックスの初期値|
|xpos|可|左端からの距離をtwip単位で指定する。<br>省略すると水平方向に対し画面中央に表示する|
|ypos|可|上端からの距離をtwip単位で指定する。<br>省略すると垂直方向に対し上端から約1/3の位置に表示する。|
|helpfile|可|F1キーまたは、ヘルプボタンを押した際に開くファイルを指定する。<br>省略した場合、ヘルプボタンは表示されない。|
|context|可|F1キーまたは、ヘルプボタンを押した際に開くヘルプコンテキスト番号を指定する<br>省略した場合、ヘルプボタンは表示されない。<br>※ helpfile を指定した場合は必須|

### 参考

[【VB】InputBox関数 \- オープンリファレンス](http://www.openreference.org/articles/view/462)