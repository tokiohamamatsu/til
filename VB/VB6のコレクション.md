# VB6のコレクション

コレクションにはキーが設定できる

```vb
Private Sub Command1_Click()
Dim colMine As Collection

Set colMine = New Collection

colMine.Add "源頼朝", "鎌倉幕府"

colMine.Add "足利尊氏", "室町幕府"

colMine.Add "徳川家康", "江戸幕府"

colMine.Add "神武天皇", "朝廷"

colMine.Add "伊藤博文", "内閣"

MsgBox colMine(1)

End Sub
```

上記で`colMine(鎌倉幕府)`とすれば源頼朝と表示され、`colMine(室町幕府)`とすれば足利尊氏が表示される。

連想配列だよねこれ

### 参考

[初級講座　第２３回　コレクション](http://rucio.o.oo7.jp/main/shokyu/jugyou23.htm)