# artisan commandの作り方

1. Terminal(Ctrl+Shift+@)から `php artisan make:command`を使う
2. コマンド名名入力時:ではなく/を使う
3. 作成成功した場合ファイルの `$signature`をコマンド名にする
4. `php artisan list`でファイルがあるか確認する
5. `public function handle()`の中にコマンドの処理を書く
6. `$description`にコマンドのコメントを書く
7. 保存

## コマンドから別のコマンドを呼び出す

$this->call('コマンド名');
これで別のコマンドを呼び出せる


# 参考

[【Laravel】Artisanコマンドを自作する方法 \| とものブログ](https://se-tomo.com/2018/10/13/laravel-%E3%82%AB%E3%82%B9%E3%82%BF%E3%83%A0%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89/)

[artisanコマンドからartisanコマンドを呼び出す方法の比較 \- Qiita](https://qiita.com/orange634nty/items/9cbcc5cbe9174966a74b)