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

## 多重継承

多重継承とはbladeテンプレートを親と子と孫の関係で継承させること

- 親　headerとかfooterなどの全体的に共通なもの
- 子　一部に共通なもの
- 孫　共通ではないもの

### 使い方

親 menu.blade.php
```php
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <title>@yield('title')</title>

    <link href = "{{asset('/css/bootstrap.min.css')}}" rel="stylesheet">
    <link href = "{{asset('/css/main.css')}}" rel="stylesheet">
    <script src = "{{asset('/js/jquery-3.4.1.min.js')}}"></script>
    <script src = "{{asset('/js/popper.min.js')}}"></script>
    <script src = "{{asset('/js/bootstrap.min.js')}}"></script>
          
    @yield('calendar')
    @yield("additionalHeader")
</head>
<body>
    <header class="sticky-top">
        <nav class="navbar navbar-expand-sm navbar-dark bg-primary">
            <a class="navbar-brand" href="">Home</a>
            <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarSupportedContent">
                <ul class="navbar-nav mr-auto">
                    <li class="nav-item">
                        <a class="nav-link" href="{{route('business.index')}}">企業マスタ</a>
                    </li>
                    <li class="nav-item">    
                        <a class="nav-link" href="{{route('JobType.search')}}">職種マスタ</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="{{route('calendar.index')}}">休日マスタ</a>
                    </li>
                    <li class="navitem">
                        <a class="nav-link" href="/">摘要マスタ</a>
                    </li> 
                </ul>
            </div>
        </nav>
        @yield('message')
        @include('error')
    </header>
    <div class="contents row">
    @yield('view')
    </div>
    <footer class="fixed-bottom">
        <small>copyright&copy; {{date("Y")}} AS-TECS Co.,Ltd. All Rights Reserved.</small>
    </footer>
</body>
</html>
```

子 list.blade.php
```php
@extends('layouts.menu')

@section('message')
@if(session('flash_message'))
    <div class="alert alert-success">
        {{session('flash_message')}}
    </div>
@elseif(session('message'))
    <div class="alert alert-danger">
        {{session('message')}}
    </div>
@endif
@endsection
@section('view')


<div class="contents row"> 
        
    @yield('sidevar')    
    @yield('main')
</div>
@endsection
```

孫 view.blade.php
```php
@extends('layouts.list')

@section('title',$data->企業名.'の詳細')

@section('sidevar') 
<div class="col-2">&nbsp;</div>
<div class="col-8">
    <div class="card">
        <div class="card-body">
            <div class="inputarea">
                <div class="formarea">
                    <label>企業CD</label>
                    <span class="form-control">{{$data->企業CD}}</span>
                </div>
                <div class="formarea">
                    <label>企業名</label>
                    <span class="form-control">{{$data->企業名}}</span>
                </div>
                <div class="formarea">
                    <label>略称名</label>
                    <span class="form-control">{{$data->略称名}}</span>
                </div>
                <div class="blockbtn card-footer">
                <button class="btn btn-secondary btnspace" onclick="location.href='{{route('business.update',['cd'=>$data->企業CD])}}'">修正</button>
                <a href="{{route('business.index')}}"><input type="button" class="btn btn-secondary btnspace" value="戻る"></a>
                </div>
            </div>
        </div>
    </div>
</div>
<div class="col-2">&nbsp;</div>  
@endsection
```

### 参考

[[Laravel] レイアウトを多重継承する \- Qiita](https://qiita.com/kamikosi/items/b7ec871657d25a00ef67)