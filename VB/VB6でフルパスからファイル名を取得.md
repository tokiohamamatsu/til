# VB6でフルパスからファイル名を取得

拡張子を除いたファイル名の取得方法

```vb

Dim FullPath As String
Dim FileName As String

FullPath = "C:\Windows\System32\User32.dll"
FileName = Dir(FullPath) 'フォルダ名を除いたファイル名を取得(=User32.dll)

If InStr(1, FileName, ".") > 0 Then
    '拡張子がある場合は、拡張子を省く
    FileName = Left(FileName, InStrRev(FileName, ".") - 1) 'User32
End If
```

### 参考

[VB フルパスからファイル名・フォルダ名などを得る](https://www.umayadia.com/main/Samples/s_sh1.htm)