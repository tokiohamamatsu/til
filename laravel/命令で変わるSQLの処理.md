# 命令で変わるSQLの処理

```php
public function index(Request $request)
    {
        $date = $request->input('営業日');
        $site = $request->input('現場名');
        $select_list = $request->input('select_lists');
        if ($select_list == null) {
            $select_list = 10;
        }
        $query = ReportHeader_model::whereRaw("1=1")->orderBy('営業日', 'desc')->orderBy('現場CD', 'asc');
        if (!empty($request->query('現場名'))) {
            $query = $query->where('現場名', 'like', '%' . $site . '%');
        }
        if (!empty($request->query('営業日'))) {
            $datas = $query->where('営業日', $date);
        }
        $datas = $query->paginate($select_list);
        return view('report.index')->with(['datas' => $datas, 'site' => $site,'date' => $date, 'select_list' => $select_list]);
    }
```

上記はユーザーの命令で`where('現場名', 'like', '%' . $site . '%');`を処理するか,`where('営業日', $date);`を処理するか、もしくは両方処理するか、しないかの4つのパターンに分けられる。

SQL文の条件指定は、書き出しがwhere、2つ目以降はandにしなくてはならないという仕様があり、whereだけでいいのか、andはいるのかなど、条件分岐が面倒になる。しかし、`whereRaw("1=1")`を使えば条件分岐をなくすことができる。

`whereRaw("1=1")`は必ず正であるという意味でこれを使えば最初のwhere句を確定でき、条件を付けたければandでつなげればいい

whereRawはwhere句にSQL文を直書きでき、laravelはクエリビルダでwhereを連結させることで、andを生成できる。

### 参考

[「WHERE 1=1」は条件付きSQL文が書きやすくなる魔法の言葉 \| キノコログ](https://kinocolog.com/where11/)

[データベース：クエリビルダ 5\.8 Laravel](https://readouble.com/laravel/5.8/ja/queries.html)