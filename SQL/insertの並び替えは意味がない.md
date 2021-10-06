# insertの並び替えは意味がない

insertで並び替えてテーブルに入れても、いれたテーブルのSELECTの結果が一致するとは限らない。
データベースは格納した順番を持たず、SELECTの結果の順序も決められていない。

テーブルから特定の順序で取り出すときは、ORDER句を使う。

### 参考

[【SQL】INSERTでソート\(sort\)・並び替えは無効 \| SE日記](https://oreno-it.info/archives/2716)