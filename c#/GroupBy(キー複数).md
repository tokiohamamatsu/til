# GroupBy(キー複数)

LinqのGroupByのキーを複数指定する方法

`var query = result.GroupBy(x => new {Subj = x.Subj, ClassName = x.ClassName});`

条件に複数指定するにはnew句を使う

複数キーを指定するのにnew句を使うことに違和感を感じるのは自分だけだろうか？

### 参考

[【C\#入門】LINQのGroupByでグループ化する\(OrderByも解説\) \| 侍エンジニアブログ](https://www.sejuku.net/blog/47220)