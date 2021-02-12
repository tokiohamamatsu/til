# LinqのGroupBy

例

```c#
var query = from x in db.TableA
            group x by x.GroupName into A
            select new { A.Key, sum = A.Sum(a => (int)a.Price) };
```

集計した値を使うにはSelectでnewをする必要がある。

### 参考

[LinqでjoinとかGroup by sumとか。 \- Qiita](https://qiita.com/zaburo/items/e33ad186f426144f2244)