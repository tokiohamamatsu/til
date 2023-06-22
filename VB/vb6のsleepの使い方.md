# vb6のsleepの使い方

vb6でsleepを使うにはApi宣言が必要
```
Private Declare Sub Sleep Lib "kernel32" (ByVal sec As Long)
```

引数に1/1000秒の値を入れる

### 参考

[sleep\-時間よトマレ！\-](http://hp.vector.co.jp/authors/VA017795/vbuseful/sleep.htm)

[VB6 Sleep API](http://7ujm.net/VB/VB6Sleep.html)