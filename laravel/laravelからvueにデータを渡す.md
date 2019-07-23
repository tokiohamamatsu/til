# laravelからvueにデータを渡す

## bladeの作成

- vueにデータを渡す

```php
<div id="app">
    <example-component test="GET DATA: {{ $_GET['AAA'] }}"></example-component>
</div>
```

## Componentの作成

- データの受け取り

```javascript
    props: {
        test: String,
    }
```

propsでデータを受けとることができ、受け取る型も指定できる

- データの表示

```php
<template>
    <span class="test">{{test}}</span>
</template>
```
propsで受け取った変数の中身は{{}}使えば表示できる

### 参考

[STEP01：Laravel5\.7 \+ Vue2\.5 でLaravelからVueにデータを渡す \- Qiita](https://qiita.com/nobu-maple/items/a704fe70809b0394b5c9)

[Vue\.jsの書き方実例集\(随時追加\)※逆引きリファレンス的な \- Qiita](https://qiita.com/Yorinton/items/a0144c34e4edb0777493)

[Vue\.jsのコンポーネント入門\[props\]\[$emit\]](https://noumenon-th.net/programming/2019/02/22/component/)

## laravelから配列をvueに渡したい

index.blade.php

```php
<div class="app">
    <item-component :data={{$data}}></item-component>
</div>
```

ItemComponent.vue

```php
<template>
<table>
    <tr>
        <th>担当者</th>
        <th>始業</th>
        <th>終業</th>
        <th>休憩</th>
        <th>手当</th>
    </tr>
</table>
</template>
<script>
export default{
    props:[data],
    mounted() {
        console.log('ExampleComponent mounted.')
    },
};
</script>
```

ReportControler.php

```php
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;
use App\Report_model;

class ReportController extends Controller
{
    public function index()
    {

        $data =[
            "id"=>1,
            "営業日"=>"2019/07/22",
            "入力担当者"=>1,
            "承認担当者"=>2,
            "現場CD"=>1,
            "現場名"=>"東光６条",
            "天候"=>"晴れ",
            "Details"=>Report_model::$datail
        ];

        return view('report.index')->with(['data'=>$data]);
    }
}

```

Report_model.php

```php
<?php

namespace App;

use Illuminate\Database\Eloquent\Model;


class Report_model extends Model
{
    public static $datail=[
        [
            "id"=>1,
            "日報id"=>1,
            "行"=>1,
            "営業日"=>"2019/07/22",
            "担当者CD"=>"5011",
            "始業時刻"=>"09:00",
            "終業時刻"=>"18:00",
            "休憩時間"=>"01:00",
            "運転手当申請"=>1
        ],
        [
            "id"=>2,
            "日報id"=>1,
            "行"=>2,
            "営業日"=>"2019/07/22",
            "担当者CD"=>"5016",
            "始業時刻"=>"09:00",
            "終業時刻"=>"18:00",
            "休憩時間"=>"01:00",
            "運転手当申請"=>0
    
        ]
    ];
}
```

これで実行すると[\[laravel\] 'htmlspecialchars\(\) expects parameter 1 to be string,～' というエラーについて \- Qiita](https://qiita.com/kuhblume/items/37aa2981de6d36d4d3d7)というエラーがでたどうやら配列は渡せないらしく文字列を渡さないといけないらしい

[Vue\.jsの書き方実例集\(随時追加\)※逆引きリファレンス的な \- Qiita](https://qiita.com/Yorinton/items/a0144c34e4edb0777493#10laravel%E3%81%8B%E3%82%89vuejs%E3%81%ABv-bind%E3%81%A7%E9%85%8D%E5%88%97%E3%82%92%E6%B8%A1%E3%81%99)に配列をjson形式に変換するとあったので変換してみた

```php
<div id="app">
    <item-component data={{ json_encode($data) }} />
</div>
```

vueへ送ることができたのだが文字列がエスケープしてしまったのでコードを変える

[Bladeテンプレート 5\.5 Laravel](https://readouble.com/laravel/5.5/ja/blade.html)
[テンプレート構文 — Vue\.js](https://jp.vuejs.org/v2/guide/syntax.html#v-bind-%E7%9C%81%E7%95%A5%E8%A8%98%E6%B3%95)

```php
<div id="app">
    <item-component :data={{!! json_encode($data) !!}} />
</div>
```

これでエスケープしなくなった

vue内で配列を展開する

```php
<template>
<table>
    <tr>
        <th>担当者</th>
        <th>始業</th>
        <th>終業</th>
        <th>休憩</th>
        <th>手当</th>
    </tr>
    <tr v-for="detail in data.Details">
        <td>{{ detail.担当者CD }}</td>
        <td>{{detail.始業時刻}}</td>
        <td>{{detail.終業時刻}}</td>
        <td>{{detail.休憩時間}}</td>
        <td></td>
    </tr>
</table>

</template>

<script>
export default{
    props:["data"],
    mounted() {
        console.log('ExampleComponent mounted.')
    },
};


</script>
```

### 参考

[リストレンダリング — Vue\.js](https://jp.vuejs.org/v2/guide/list.html#v-for-%E3%81%A7%E9%85%8D%E5%88%97%E3%81%AB%E8%A6%81%E7%B4%A0%E3%82%92%E3%83%9E%E3%83%83%E3%83%94%E3%83%B3%E3%82%B0%E3%81%99%E3%82%8B)