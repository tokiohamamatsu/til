# 日付に関するWhere句

## whereBetween()

範囲検索する

```php
$this->post->whereBetween('id', [1, 100])->get();
```

さらに検索したい場合は、orWhereBetweenを使用する。

## whereNotBetween

指定した2つの間ではない場合

```php
$users = DB::table('users')->whereNotBetween('votes', [1, 100])->get();
```

## whereDate()

whereDate()を使うと,created_at等のtimestamp型のカラムに対して、年月日を使って検索できる

```php
$this->post->whereDate('created_at', '=', '2018-08-03')->get();
```

## whereYear()

年を指定した検索

```php
$this->post->whereMonth('created_at', '=', '07')->get();
```

## whereMonth()

月を指定した検索

```php
$this->post->whereMonth('created_at', '=', '07')->get();
```

## whereDay()

日にち指定した検索

```php
$posts = $this->post->whereDay('created_at', '1'->get();
```

## WhereTime()

時間を指定した検索

```php
$this->post->whereTime('created_at', '=', '00:44:33')->get();
```

### 参考

[データベース：クエリビルダ 5\.8 Laravel](https://readouble.com/laravel/5.8/ja/queries.html)

[php – Laravel Eloquent Date Range – 2つの日付間のクエリ \- コードログ](https://codeday.me/jp/qa/20190301/344067.html)

[【Laravel】Query Builder\(クエリビルダー\) – 各種where句の使い方 \| Public Constructor](https://public-constructor.com/laravel-query-builder-where-clauses/)