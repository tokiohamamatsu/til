# ADOの使い方

ADOはActiveX Data Objectsの略

ADODB.Connectionでデータベースに接続し、ADODB.Recordsetでレコードを操作する。

新規レコードの追加

```vb
Set cn = New ADODB.Connection
Set rs = New ADODB.Recordset
cn.Open "Driver={Microsoft Access Driver (*.mdb)};DBQ=C:¥WK¥TEST.mdb"
strTBL = "HINMST"     'テーブル名
rs.Open strTBL, cn, adOpenForwardOnly, adLockOptimistic, adCmdTable  'テーブルを開く

rs.AddNew                   '新規レコードを追加
rs!HINMEI = "あんぱん"   '「商品名」をセット
rs!HINCODE = "100"     '「商品コード」をセット
rs!PRICE = 70             '「価格」をセット
rs.Update                   '更新(保存)

rs.Close
cn.Close
Set rs = Nothing
Set cn = Nothing
```

レコードの編集

```vb
Set cn = New ADODB.Connection
Set rs = New ADODB.Recordset
cn.Open "Driver={Microsoft Access Driver (*.mdb)};DBQ=C:¥WK¥TEST.mdb"
strSQL = "SELECT * FROM HINMST WHERE HINCODE='100'"  'SQL文
rs.Open strSQL, cn, adOpenStatic, adLockOptimistic, adCmdText  'SQL文を実行

If Not rs.EOF Then
    rs!PRICE = 120   '「価格」を変更
    rs.Update        '更新(保存)
End If

rs.Close
cn.Close
Set rs = Nothing
Set cn = Nothing
```

レコードの削除

```vb
Set cn = New ADODB.Connection
Set rs = New ADODB.Recordset
cn.Open "Driver={Microsoft Access Driver (*.mdb)};DBQ=C:¥WK¥TEST.mdb"

strSQL = "SELECT * FROM HINMST WHERE HINCODE='100'"  'SQL文
rs.Open strSQL, cn, adOpenStatic, adLockOptimistic, adCmdText  'SQL文を実行

If Not rs.EOF Then
    rs.Delete        'レコードを削除
End If

rs.Close
cn.Close
Set rs = Nothing
Set cn = Nothing
```

### 参考

[VB6リファレンス ADO 操作](http://cya.sakura.ne.jp/vb/ADO.htm#Open)