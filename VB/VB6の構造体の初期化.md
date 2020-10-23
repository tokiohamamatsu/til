# VB6の構造体の初期化

```vb
'# ユーザー定義型変数名：TypeHoge
Public Sub iniUserTypeHoge(ByRef pData As TypeHoge)
Dim tmp as TypeHoge

pData = tmp
End Sub
```

### 参考

[【VB6】ユーザー定義型変数\(構造体\)を一括初期化する。](http://www.dojeun.com/contentsview.php?listid=00202)