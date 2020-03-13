# Entity FrameworkのDB操作

Entity FrameworkはDBのデータの挿入、読み出し、更新、削除などの動作はDbContextを通じて行われる

データを挿入する場合

```c#
public class Product
{
    public int ProductId { get; set; }
    public string Name { get; set; }
    public int Price { get; set; }
}

public class ShoppingContext : DbContext
{
    public DbSet<Product> Products { get; set; }
}

static void Main(string[] args)
{
    using (var context = new ShoppingContext())
    {
        // Addした段階ではSql文はDBに発行されない
        context.Products.Add(newProduct
        {
            Name = "Test",
            Price = 1000,
        });

        // SaveChangesが呼び出された段階で初めてInsert文が発行される
        context.SaveChanges();
    }
}
```

上記の場合、データをAddした段階では、DBに状態は反映されるわけではなく、SaveChangesを呼び出した段階で初めてデータが更新される。

DbContext内部では変更を加える前のオブジェクトの状態と変更を加えた後のオブジェクトの状態を保持している。データを挿入する場合は、Addを呼び出した段階で、新規オブジェクトをAdded状態としてDbContext内に挿入し、SaveChangesを呼び出すことで、DBにSQLが発行され、オブジェクトがAddedの状態からUnchanged状態に変化する。DbContext内のオブジェクトは、Contextを破棄するまで残り続けるため、不必要になったらDisposeをする

```c#
using(var context = new ShoppingContext())
{
   context.Products.Add(new Product(...)) // この時点で，Contextに新しいオブジェクトが追加されAdded状態になる
   context.SaveChanges(); // この時点でContextに保存されているデータがDBに反映される
}
```
エンティティの状態

- Unchanged
  DBにデータが存在していて、全く更新が加えれてない状態
- Added
  ContextにEntityがトラッキングされた状態かつDBにデータが存在しない状態。SaveChangeを呼び出すとEntityのInsert文が発行され、Unchange状態になる
- Deleted
  DBにデータが存在していて、これから削除しようとしている状態。 SaveChangeを呼び出すと、Delete文が発行され、Detached状態になる。
- Detached
  オブジェクトは存在するが、DbContextによって状態がトラッキングされてない状態。
- Modified
  オブジェクトの一部が変更され、SaveChangeが呼び出されていない状態。SaveChangesを呼び出すと、UPDATE文が発行され、UnChanged状態になる

  ### 参考

  [4\. データの挿入、読み出し、更新、削除 \| densan\-labs\.net](https://densan-labs.net/tech/codefirst/adddelete.html)
