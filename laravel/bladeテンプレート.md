# bladeテンプレート

- @extends　継承元の宣言
- @section　継承先に反映される
- @yield　@sectionを反映させる場所
- @show　継承元の@sectionの閉じタグ
- @@parent　継承元の@sectionが反映される

## 使い方
menu.blade.php
```php
<html>
    <head>
        <title>@yield('title')</title>
    </head>
    <body>
        @section('main')
            ここがメイン
        @show
    </body>
</html>
```
main.blade.php
```php
@extends ('layouts.menu')

@section ('title','menu')

@section ('main')
    @@parent
    <p>ここがメインに追加される</p>
@endsection
```
## 概要

- mainの@extendsで継承元menuをテンプレートとして扱う
- mainの@yieldでmenuの@sectionを反映させる
- menuの@@parentでmainの@sectionを反映させる

### 参考

[Blade 使い方（早見表） \- Laravel学習帳](https://laraweb.net/knowledge/3440/)

[Laravel Recipes日本語版 \| Bladeでコンテンツの挿入を開始する](http://recipes.laravel.jp/recipe/111)

## include

- ビューの中からほかのbladeビューを取り込む
- 読み込み元で使用可能な変数は取り込み先でも使える
- 取り込み先への追加のデータは配列で渡せる

## 使い方

error.blade.php
```php
@if ($errors->any())
    <div class="alert alert-danger">
        <ul>
            @foreach ($errors->all() as $error)
                <li>{{ $error }}</li>
            @endforeach
        </ul>
    </div>
@endif
```
form.blade.php
```php
<div>
    include('error');
    <form>
        <!--フォームの内容-->
    </form>
</div>
```
## 概要

form.blade.phpにerror.blade.phpが反映される

### 参考

[Bladeテンプレート 5\.5 Laravel](https://readouble.com/)   

[Laravel 5\.7 のテンプレートエンジン Blade の使い方（ @yield , @section , @include ） \- bnote](https://www.bnote.net/blog/laravel_blade.html)