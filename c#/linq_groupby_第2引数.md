# LinqのGroupByの第2引数

LinqのGroupByの第2引数は最終的に返す型を決めるもの

```
List<Test> tests = new List<Test>()
{
    new Test(1, "aaa"),
    new Test(2, "bbb"),
    new Test(3, "ccc"),
    new Test(1, "ddd"),
    new Test(3, "eee"),
};

IEnumerable<IGrouping<int, string>> groupBy =
    tests.GroupBy(x => x.Num, x => x.Str);

foreach (var x in groupBy)
{
    Console.Write("{0} ", x.Key);
    foreach (string s in x)
        Console.Write("{0} ", s);
    Console.WriteLine();
}
```
上記の戻り値の型はstring型

Listなどにしたい場合は`x => x.Str`の部分を(key, value)の形にする。

### 参考

https://programming.pc-note.net/csharp/linq_method.html