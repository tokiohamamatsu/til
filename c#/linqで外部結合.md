# Linqで外部結合

Joinを使わない方法

```C#
// LINQ to SQL で LEFT OUTER JOIN
var q = from e in dc.EmployeeTable
        from g in dc.GroupTable.Where(x => x.GroupCode == e.GroupCode).DefaultIfEmpty()
        select new
        {
            e.UserName,
            e.GroupCode,
            g.GroupName,
        };

```

`DefaultIfEmpty()`で空のときはデフォルト値を入れる

### 参考

[C\# LINQ to SQL で LEFT OUTER JOIN をシンプル記述する](http://programmers.high-way.info/cs/linqtosql-join.html)