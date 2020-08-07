# ActiveReportsで条件表示

値がなかったらSectionを非表示にする方法

```vb
Private Sub GroupFooter_Format()

    if isnull("値") Then
        Me.GroupFooter.Enabled = false
    Else
        Me.GroupFooter.Enabled = True
    End if

End Sub
```

上記でGroupFooterが呼ばれるたび値を確認し、値がなければ非表示にできる。

