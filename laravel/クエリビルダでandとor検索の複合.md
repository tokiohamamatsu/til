# クエリビルダでandとor検索の複合

クエリビルダでandとorの複合はクロージャで書く

```php
$query->where(function($query) use($value1, $value2){
    $query->where('column1', '=', $value1)
          ->orWhere('column2', '=', $value2)
});
 
$query->where(function($query) use($value3, $value4){
    $query->where('column1', '=', $value3)
          ->orWhere('column2', '=', $value4)
});
```

普通に`where()->orwhere`を書くだけではandとorの復号にならない

### 参考

[Eloquent/QueryBuilderによるAnd検索とOr検索の複合 \- Laravel5開発](https://umebius.com/laravel/querybuilder%E3%81%AB%E3%82%88%E3%82%8Band%E6%A4%9C%E7%B4%A2%E3%81%A8or%E6%A4%9C%E7%B4%A2%E3%81%AE%E8%A4%87%E5%90%88/)