# LinqでLikeを使う

前方一致

StartsWith()を使う

```c#
// 店舗クラス
class Shop
{
    public int ShopId;
    public string ShopName;
}

private void button1_Click(object sender, EventArgs e)
{
    var shops = new[]
    {
        new Shop() {ShopId = 1, ShopName = "shop1_A01"},
        new Shop() {ShopId = 2, ShopName = "shop1_A02"},
        new Shop() {ShopId = 3, ShopName = "shop2_B01"},
        new Shop() {ShopId = 4, ShopName = "shop2_B02"},
        new Shop() {ShopId = 5, ShopName = "shop3_A01"},
        new Shop() {ShopId = 6, ShopName = "shop4_A01"},
    };

    var results = shops.Where(x => x.ShopName.StartsWith("shop1"));

    string output = string.Empty;
    foreach (var result in results)
    {
        output = output + result.ShopId + " ";
    }

    this.label1.Text = output;
    //結果　1 2
}
```

後方一致

EndsWithを使う

```c#
// 店舗クラス
class Shop
{
    public int ShopId;
    public string ShopName;
}

private void button1_Click(object sender, EventArgs e)
{
    var shops = new[]
    {
        new Shop() {ShopId = 1, ShopName = "shop1_A01"},
        new Shop() {ShopId = 2, ShopName = "shop1_A02"},
        new Shop() {ShopId = 3, ShopName = "shop2_B01"},
        new Shop() {ShopId = 4, ShopName = "shop2_B02"},
        new Shop() {ShopId = 5, ShopName = "shop3_A01"},
        new Shop() {ShopId = 6, ShopName = "shop4_A01"},
    };

    var results = shops.Where(x => x.ShopName.EndsWith("A01"));

    string output = string.Empty;
    foreach (var result in results)
    {
        output = output + result.ShopId + " ";
    }

    this.label1.Text = output;
    // 1 5 6
}
```

部分一致

Containsを使う

```c#
// 店舗クラス
class Shop
{
    public int ShopId;
    public string ShopName;
}

private void button1_Click(object sender, EventArgs e)
{
    var shops = new[]
    {
        new Shop() {ShopId = 1, ShopName = "shop1_A01"},
        new Shop() {ShopId = 2, ShopName = "shop1_A02"},
        new Shop() {ShopId = 3, ShopName = "shop2_B01"},
        new Shop() {ShopId = 4, ShopName = "shop2_B02"},
        new Shop() {ShopId = 5, ShopName = "shop3_A01"},
        new Shop() {ShopId = 6, ShopName = "shop4_A01"},
    };

    var results = shops.Where(x => x.ShopName.Contains("_A0"));

    string output = string.Empty;
    foreach (var result in results)
    {
        output = output + result.ShopId + " ";
    }

    this.label1.Text = output;
    // 結果　1 2 5 6
}
```

### 参考

[【C\#】【Linq】Linq で LIKE句 を表現する \- プログラム の超個人的なメモ](https://dk521123.hatenablog.com/entry/30278171)