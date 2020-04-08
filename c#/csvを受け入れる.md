# csvを受け入れる

csvを受け入れるにはCsvHelperを使う

```csv
Id,Name
1,one
2,two
```

例えば上記のようなcsvファイルがあるとする

マッピングの定義

```c#
class User 
{
    public long Id { get; set; }
    public string Name { get; set; }
}
```

以下のようにすればカラムのインデックスと対応付けれる

```c#
public sealed class createMap : CsvHelper.Configuration.ClassMap<User>
{
    public createMap() {
        Map(m => m.Id).Index(0);
        Map(m => m.Name).Index(1);
    }
}
```

呼び出し

```c#
using (var reader = new StreamReader("ファイルのパス"))
using (var csv = new CsvReader(reader, CultureInfo.InvariantCulture))
{
    csv.Configuration.RegisterClassMap<createMap>();
    csv.Configuration.MissingFieldFound = null;
    var records = csv.GetRecords<User>();
    foreach (var item in records) {
    Console.WriteLine("{0},{1}", item.Id, item.Name);
    }
}
```

上記でコンソールに出力できた。

最新バージョン(2020/4/8)だとCsvClassMapは使えないのでClassMapで代用する。

### 参考

[CsvHelper](https://joshclose.github.io/CsvHelper/getting-started)

[CsvHelper覚え書き \- Qiita](https://qiita.com/ko-da-k/items/e9d51790673086c69603)

[C\# で CSV を扱うのに CsvHelper を使う \- dunno logs](https://dany1468.hatenablog.com/entry/2013/07/15/175319)

["Field with names ['Name'] at index '0' does not exist\. You can ignore missing fields by setting MissingFieldFound to null\." · Issue \#875 · JoshClose/CsvHelper](https://github.com/JoshClose/CsvHelper/issues/875)

[12\.3\.2> 13\.0\.0：StreamReaderからCsvHelper\.IParserに変換できない・問題＃1441・JoshClose / CsvHelper](https://github.com/JoshClose/CsvHelper/issues/1441)

[csvhelper \- CsvClassMap not found error in visual studio 2015 \- Stack Overflow](https://stackoverflow.com/questions/44313515/csvclassmap-not-found-error-in-visual-studio-2015)