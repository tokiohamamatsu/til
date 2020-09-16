# OldValue

OldValueはテキストボックスの編集前の値を持つ

これを使うことで、変更前と変更語を比べる事ができる

```vb
Private Sub 氏名_BeforeUpdate(Cancel As Integer)

  MsgBox Me!氏名.OldValue & vbCrLf & Me!氏名.Value

End Sub
```

### 参考

[OldValue プロパティ \(Access\) \| Microsoft Docs](https://docs.microsoft.com/ja-jp/office/vba/api/access.control.oldvalue)
[■T'sWare Access Tips \#185 ～テキストボックスの変更前後の値を比較する方法～](https://tsware.jp/tips/tips_185.htm)