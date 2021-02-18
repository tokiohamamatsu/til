# ==とEqualsの違い

`==`とEqualsはどちらも同じどうか調べるもの

調べる対象には参照型と値型がある。

同じの意味合いは次なような違いがある。

参照型は、比較する2つのオブジェクト参照が同じオブジェクトを参照しているか
値型は、比較する2つのオブジェクトが同じ値を持っているか


`==`はオーバーロードされるが、Equalsは一般的にオーバーライドされる違いがある

### 参考

[==演算子とEqualsメソッドの違いとは？［C\#］：\.NET TIPS \- ＠IT](https://www.atmarkit.co.jp/ait/articles/1802/28/news028.html)

[2つの値が等しいか調べる、等値演算子\(==\)とEqualsメソッドの違い \- \.NET Tips \(VB\.NET,C\#\.\.\.\)](https://dobon.net/vb/dotnet/beginner/equality.html)