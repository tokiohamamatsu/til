# Formについて

## できなかったこと

Form:modelを使ってフォーム作ったが送信したらerrorがでた


index.blade.php
```php
{{Form:model(['method'=>'post','route'=>'$route'])}}

<!--フォームの内容-->

{{Form::close()}}
```

FormController.php
```php
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;
use App\Http\Controllers\Controller;

class FormController extends Controller
{
    public function index()
    {
        $route=route('test.post') ;
        return view('test.index',compact('route'));
    }

    public function post()
    {
        /*フォームの処理*/

        return redirect('test.index');
    }
}
```

web.php
```php
Route::get('test','FormController@index');
Route::post('test/post','FormController@post')->name('test.post');
```

## 原因

フォームのルートにurlで渡したから

## 修正

Form::modelのrouteはurlを受け付けずroute()を使うとurlになってしまうのでFormに渡すものにはroute()をつかわず直接渡すかFormのrouteをurlにする
Form::modelはmodelと結びつけてないのForm::openでいい

index.blade.php
```php
{{Form:open(['method'=>'post','route'=>'$route'])}}

<!--フォームの内容-->

{{Form::close()}}
```

FormController.php
```php
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;
use App\Http\Controllers\Controller;

class FormController extends Controller
{
    public function index()
    {
        return view('test.index',['route'=>'test.post']);
    }

    public function post()
    {
        /*フォームの処理*/

        return redirect('test.index');
    }
}
```

### 参考

[Laravel Recipes日本語版 \| HTMLフォームを作成する](http://recipes.laravel.jp/recipe/224)

