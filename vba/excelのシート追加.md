# excelのシート追加

シートを追加するには、worksheetsコレクションのaddを使う

```vb
Worksheets.Add(Before, After, Count, Type)
```

beforeにシート名を入れるとその手前に追加され、Afterに入れると後ろに追加される。

### 参考

[Office TANAKA \- シートの操作[新しいシートを挿入する]](http://officetanaka.net/excel/vba/sheet/sheet03.htm)