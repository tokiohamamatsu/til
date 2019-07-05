# Dropdown

## ドロップダウン

`.dropdown`,`.dropdown-toggle`,`.data-toggle="dropdown"`,`.dropdown-menu`,`.dropdown-item`を組み合わせ表示する

```php
<div class="dropdown">
  <button type="button" id="dropdown" class="btn bg-white dropdown-toggle btn-sm" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
      @php($user=Auth::user())
    {{$user->担当者名}}
  </button>
  <div class="dropdown-menu dropdown-menu-right" aria-labelledby="dropdown">
    <a class="dropdown-item" href="{{route('menu.logout')}}">ログアウト</a>
    <a class="dropdown-item" href="{{route('staff.update',['cd'=>$user->企業CD,'staff_cd'=>$user->担当者CD])}}">パスワード変更</a>
  </div>
</div>
```
`aria-haspopuo="true"`ポップアップ部品を持つことを、`aria-expanded="false"`はポップアップの閉塞状態を示す

## ドロップ方向

`.dropup`は上に`.dropright`は右に`.dropleft`は左にドロップの方向を変更する

## メニュー位置

`.dropdown-menu-right`はボタンの右、`.dropdown-menu-left`はボタンの左の位置に合わせて表示する

画面の横幅に応じて位置を制御する`.dropdown-menu-breakpoint-right`,`.dropdown-menu-breakpoint-left`も使用可能

## 参考

[とほほのBootstrap 4入門 \- ドロップダウン](http://www.tohoho-web.com/bootstrap/dropdown.html)

[ドロップダウン～Bootstrap4移行ガイド](https://cccabinet.jpn.org/bootstrap4/components/dropdowns#dropright)