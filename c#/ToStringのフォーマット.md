# ToStringのフォーマット

ToStringでフォーマットをできるのをわすれていたため記述

```c#
// 1234/05/06 (年4桁 月日2桁表示)
Console.WriteLine(datetime.ToString("yyyy/MM/dd"));
// 1234年05月06日 (年4桁 月日2桁表示)
Console.WriteLine(datetime.ToString("yyyy年MM月dd日"));
// 34年5月6日 (年2桁 月日1桁表示)
Console.WriteLine(datetime.ToString("yy年M月d日"));

// 月～日(曜日)
Console.WriteLine(datetime.ToString("ddd"));
// 月曜日～日曜日
Console.WriteLine(datetime.ToString("dddd"));

// 13:04:05 (24時間形式 2桁表示)
Console.WriteLine(datetime.ToString("HH:mm:ss"));
// 13時4分5秒 (24時間形式 1桁表示)
Console.WriteLine(datetime.ToString("H時m分s秒"));

// 午後 01:04:05 (12時間形式 2桁表示)
Console.WriteLine(datetime.ToString("tt hh:mm:ss"));
// 午後 1時4分5秒 (12時間形式 1桁表示)
Console.WriteLine(datetime.ToString("tt h時m分s秒"));

Console.WriteLine("4けた左詰め【{0, -4}】", zero);
// 出力：4けた左詰め【0   】

Console.WriteLine("4けた左詰め【{0, -4}】", eleven);
// 出力：4けた左詰め【11  】


Console.WriteLine("4けた0埋め【{0:D4}】", zero);
// 出力：4けた0埋め【0000】

Console.WriteLine("4けた0埋め【{0:D4}】", eleven);
// 出力：4けた0埋め【0011】


Console.WriteLine("4けた0埋め【{0:0000}】", zero);
// 出力：4けた0埋め【0000】

Console.WriteLine("4けた0埋め【{0:0000}】", eleven);
// 出力：4けた0埋め【0011】


Console.WriteLine("8けたかつ4けた0埋め【{0, 8:D4}】", zero);
// 出力：8けたかつ4けた0埋め【    0000】

Console.WriteLine("8けたかつ4けた0埋め【{0, 8:D4}】", eleven);
// 出力：8けたかつ4けた0埋め【    0011】
```

### 参考

[C\# \- 日付・日時\(DateTime\)をフォーマット指定して文字列にする](https://www.curict.com/item/e7/e7b9e6d.html)

[数値を右詰めや0埋めで文字列化するには？［C\#、VB］：\.NET TIPS \- ＠IT](https://atmarkit.itmedia.co.jp/ait/articles/0401/30/news069.html)