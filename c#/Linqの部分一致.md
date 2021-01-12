# Linqの部分一致

Linqで部分一致をしようとLikeを使おうと思ったが別のやり方を見つけた

whereの条件にContainsを使う

Containsは指定した要素があるか確認する

リストに使うことで部分一致をすることができる。

### 参考

[Enumerable\.Contains メソッド (System\.Linq\) | Microsoft Docs](https://docs.microsoft.com/ja-jp/dotnet/api/system.linq.enumerable.contains?view=net-5.0)

[【C\#,LINQ】Contains～配列やリストの中で指定した要素があるかを判定したいとき～ \- 陰干し中のゲーム開発メモ](https://www.urablog.xyz/entry/2018/06/10/070000)