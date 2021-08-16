# DataTableから特定の行が何行目かを取得

```c#
// Key カラムが 0～9 の 10 行のデータを持った DataTable
var dt = new DataTable();
dt.Columns.Add("Key", typeof(int));
Enumerable.Range(0, 10).ToList().ForEach(a => dt.Rows.Add(a));
 
// 探す対象の Key
var target = 6;
 
// 対象の Index
var index = dt.Rows.IndexOf(dt.AsEnumerable().Where(a => a.Field<int>(0) == target).FirstOrDefault());
 
Console.WriteLine(index);
```

### 参考

[DataTable の目的のデータを持った DataRow が何行目かを取得する \| rksoftware](https://rksoftware.wordpress.com/2016/06/07/001-10/)