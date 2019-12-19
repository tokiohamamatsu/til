# migrateで更新する

```php
use Illuminate\Support\Facades\DB;// 追加

Schema::table('table_name', function($table) { 
      $table->integer('new_column')->default(0);  
    }); 
DB::table('table_name')->where('old_column',0)->update(['new_column'=>1]);

Schema::table('table_name', function (Blueprint $table) {
            $table->dropColumn("old_column");
    });
```

古いカラムが0の場合新しいカラムに1を更新する

### 参考

[データベース：クエリビルダ 5\.8 Laravel](https://readouble.com/laravel/5.8/ja/queries.html#updates)

[php \- Laravelデータ移行](https://stackoverrun.com/ja/q/6439711)