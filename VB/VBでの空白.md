# VBでの空白

VBで空白を使うにはSpace関数を使う

この関数は引き数に指定した数のスペースを重ねた文字列を作成する

動作

|条件|例|結果|
|---|---|---|
|整数|Space(3)|半角スペースが３つ並んだ文字列|
|負数|Space(-3)|エラー|
|0|Space(0)|長さ0の文字列|
|少数|Space(1.5)|[^1]半角スペースが２つ並んだ文字列|

[^1]:少数は偶数丸めによって処理される

### 参考

[【VB】Space関数 \- オープンリファレンス](http://www.openreference.org/articles/view/298)

[Space 関数 (Visual Basic for Applications) | Microsoft Docs](https://docs.microsoft.com/ja-jp/office/vba/language/reference/user-interface-help/space-function)