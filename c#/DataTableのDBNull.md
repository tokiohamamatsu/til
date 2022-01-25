# DataTableのDBNull

プロジェクトにDataSetを追加した場合

DataTableのDatetime型の行にnullを入れようとするとDBNullを使えとエラーがでる。

しかし、DBNullを使うとDataTableから値を参照すると「”カラム名”の値はDBNullです」とエラーが出る。

対策として`Isカラム名Null`というものが自動的に用意されるので、これを使い、Nullを判断して回避する。

DataTableのカラムにNull許容するかのプロパティがあるのにNullが使えないのはなぜなのだろうか?

### 参考

[\[C\#\]DataRowにNullを設定すると例外が発生する](https://www.curict.com/item/50/5006814.html)

[データセット内の項目の DBNull 判定 \- 電気ウナギ的○○](http://blog.netandfield.com/shar/2014/07/-dbnull.html)

[C\# DataRowの値を取り出すときにDBNullでエラーを出さない。 \| テクニカルノート](https://accelboon.com/tn/c-datarow%E3%81%AE%E5%80%A4%E3%82%92%E5%8F%96%E3%82%8A%E5%87%BA%E3%81%99%E3%81%A8%E3%81%8D%E3%81%ABdbnull%E3%81%A7%E3%82%A8%E3%83%A9%E3%83%BC%E3%82%92%E5%87%BA%E3%81%95%E3%81%AA%E3%81%84%E3%80%82/)