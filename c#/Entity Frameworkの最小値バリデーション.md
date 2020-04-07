# Entity Frameworkの最小値バリデーション

Entity Frameworkにはminがなく代わりにRangeを使う

```c#
[Range(min,max)]
```


最小値だけをバリデーションしたい場合は、maxの部分にint.MaxValueを設定する。

### 参考

[RangeAttribute クラス (System\.ComponentModel\.DataAnnotations\) \| Microsoft Docs](https://docs.microsoft.com/ja-jp/dotnet/api/system.componentmodel.dataannotations.rangeattribute?view=netframework-4.8)