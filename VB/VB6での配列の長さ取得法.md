# VB6での配列の長さ取得法

VB6には配列の長さを取得するLengthといったメソッドは存在しない

VB6で配列の長さを取得するには`LBound`と`UBound`を使う

|関数|說明|
|---|---|
|LBound|配列の最小インデックス(添字番号)を返す|
|UBound|配列の最大インデックスを返す|

要素数を求めるには最小インデックスと最大インデックスの差分で求める

```vb
Sub Sample()
    Dim strArry() As String

    ' 配列のサイズを取得する場合
    strArry = Split("a,b,c", ",")                       ' 配列を作成します
    Debug.Print UBound(strArry) - LBound(strArry) + 1   ' 配列のサイズ「3」が表示されます

    ' 配列をループ処理する場合
    Dim i As Integer
    For i = LBound(strArry) To UBound(strArry)
        Debug.Print strArry(i)
    Next
End Sub
```

### 参考

[【VB6/VBA】配列のサイズを取得する \- オープンリファレンス](http://www.openreference.org/articles/view/519)