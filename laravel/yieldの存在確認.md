# yieldの存在確認

```php
@if(View::hasSection('vue'))
    @yield('vue')
@else
    <script src="{{asset('/js/bootstrap.min.js')}}"></script>
@endif
```

`View::hasSection('vue')`でコンテンツの有無を確認できる


### 参考

[Laravelのyieldで読み込んだコンテンツの存在確認 \- Qiita](https://qiita.com/kaneko_tomo/items/ae8d51b2595d2f8768f4)