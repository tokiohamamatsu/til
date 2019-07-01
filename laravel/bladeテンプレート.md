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

孫 edit.blade.php
```php
@extends('layouts.list')

@section('title','担当者マスタ('.$mode.')')

@section('calendar')
<link rel="stylesheet" href="https://ajax.googleapis.com/ajax/libs/jqueryui/1.12.1/themes/redmond/jquery-ui.css">
<script src = "{{asset('/js/jquery-calendar.js')}}"></script>
<script src="https://ajax.googleapis.com/ajax/libs/jqueryui/1.12.1/jquery-ui.min.js"></script>
<script src="http://ajax.googleapis.com/ajax/libs/jqueryui/1/i18n/jquery.ui.datepicker-ja.min.js"></script>
@endsection

@section('main')
<div class="col-2">&nbsp;</div>
<div class="col-8">
{{Form::open(['method'=>'post','route'=>$route])}}
    <div class="form-group" >
    
        
        @if($mode=='削除')
            <h4>本当に削除しますか？</h4>
        @endif
        <div class="input">
            <div class="inputarea">
                <div class="formarea">
                {{Form::label('担当者CD','担当者CD')}}
                    @php($class=['class'=>'textbox form-control-sm','readonly'=>true])
                    @php($label=null)
                    @php($dateclass=['class'=>'textbox form-control-sm datepicker','placeholder'=>'例）2019/01/01'])
                    @if($mode=='登録')
                        @php($label=['class'=>'required'])
                        @php($class=['class'=>'textbox form-control-sm','disabled'=>true])
                        @php($No=null)
                        @php($name=null)
                        @php($date=null)
                        @php($retirement=null)
                    @else
                        @php($No=$data->担当者CD)
                        @php($name=$data->担当者名)
                        @php($date=$data->入社日)
                        @php($retirement=$data->退職日)
                    @endif
                    @if($mode=='参照作成')
                        @php($class=['class'=>'textbox form-control-sm','disabled'=>true])
                        @php($No=null)
                    @endif

                {{Form::text('担当者CD',$No,$class)}}
                </div>
                <div class="formarea">
                    {{Form::label('担当者名','担当者名',$label)}}
                    @php($class=['class'=>'textbox form-control-sm'
                            ,'maxlength'=>'40'
                            ,'placeholder'=>'入力してください'
                            ,'required'=>true])
                    @if($mode=='削除'or $mode=='参照作成')
                        @php($class=['class'=>'textbox form-control-sm'
                                ,'readonly'=>true])
                    @endif
                    {{Form::text('担当者名',$name,$class)}}
                </div>
                <div class="formarea">
                    {{Form::label('企業CD','企業名')}}
                    <span class="textbox">{{$data->businessName->企業名}}</span>
                    {{Form::hidden('企業CD',$data->企業CD)}}
                </div>
                <div class="formarea">
                    {{Form::label('職種名','職種名')}}

                    <select name="職種CD" class="textbox form-control-sm">
                        @foreach($jobtypes as $jobtype)
                        <option value={{$jobtype->職種CD}} @if($data->職種CD==$jobtype->職種CD and $mode!='登録') selected @endif>{{$jobtype->職種名}}</option>
                        @endforeach
                    </select>
                </div>
                <div class="formarea">
                    {{Form::label('入社日','入社日',$label)}}
                    @if($date==null)
                    {{Form::text('入社日',null,$dateclass)}}
                    @else
                    {{Form::text('入社日',date("Y/m/d",strtotime($date)),$dateclass)}}
                    @endif
                </div>
                <div class="formarea">
                    {{Form::label('退職日','退職日')}}
                    @if($retirement==null)
                    {{Form::text('退職日',null,$dateclass)}}
                    @else
                    {{Form::text('退職日',date("Y/m/d",strtotime($retirement)),$dateclass)}}
                    @endif
                </div>
                <div class="formarea">
                    {{Form::label('給与形態','月給')}}
                    {{Form::radio('給与形態','0',true)}}
                    {{Form::label('給与形態','日給')}}
                    {{Form::radio('給与形態','1')}}
                    
                </div>
                
                <div class="formarea">
                    {{Form::label('権限flg','権限')}}
                    <select name="権限flg" class="textbox form-control-sm">
                        <option value="0" @if($data->権限flg==0 and $mode!='登録') selected @endif >ログイン不可</option>
                        <option value="1" @if($data->権限flg==1 and $mode!='登録') selected @endif >ログイン可能</option>
                        <option value="2" @if($data->権限flg==2 and $mode!='登録') selected @endif >金額調整権限あり</option>
                    </select>
                </div>
                <div class="blockbtn">
                {{Form::submit($mode,['class' => "btn btn-secondary btnspace"])}}
                {{Form::button('戻る',['class'=>'btn btn-secondary btnspace','onclick'=>'history.back()'])}}
                </div>
            </div>
        </div>
    </div>
{{Form::close()}}
</div>
@endsection
```

### 概要

孫が子を継承し、その子が親を継承しているので孫が親を継承できる

### 参考

[[Laravel] レイアウトを多重継承する \- Qiita](https://qiita.com/kamikosi/items/b7ec871657d25a00ef67)