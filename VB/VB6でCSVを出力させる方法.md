# VB6でCSVを出力させる方法

Openステートメントでテキストファイルを開き、write # ステートメントでcsvデータを出力し、Closeステートメントでファイルを閉じる。

例

```vb
Public Sub sample1()
    Dim intNo As Integer
    Dim strArray() As Variant

    '出力するデータを設定
    strArray = Array(Array("名前", "住所", "電話番号"), _
                     Array("てすと太郎", "東京都港区XX-XX-XX", "111-1111-1111"), _
                     Array("てすと次郎", "埼玉県さいたま市XX-XX-XX", "222-2222-2222"), _
                     Array("てすと三郎", "神奈川県横浜市XX-XX-XX", "333-3333-3333"))

    'ファイルオープン
    intNo = FileSystem.FreeFile()
    Open "C:\tmp\sample1.csv" For Output As #intNo

    'ファイル出力
    Dim i As Integer
    For i = 0 To UBound(strArray)
        Write #intNo, strArray(i)(0), strArray(i)(1), strArray(i)(2)
    Next i

    'ファイルクローズ
    Close #intNo

End Sub
```

Outputモードでファイルをオープンすると、出力した際に指定したファイルがない場合、新規作成する。ファイルが既にある場合は上書きされる。

### 参考

[【VB6/VBA】csvファイルを出力する \- オープンリファレンス](http://www.openreference.org/articles/view/649)