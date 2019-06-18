# artisan command

artisan commandでコンソールからlaravelを使用したコマンドを作成できる。

- [【Laravel】Artisanコマンドを自作する方法 \| とものブログ](https://se-tomo.com/2018/10/13/laravel-%E3%82%AB%E3%82%B9%E3%82%BF%E3%83%A0%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89/)


## 使い方

Terminal(Ctrl+Shift+@)から `php artisan make:command`を使う

```bash:sample
$php artisan make:command test/testCommand
```
- コマンドのディレクトリを分けるときは/で区切る

### 実行例

`artisan list`でコマンドが作成されているか確認できる。
(デフォルトではcommand:nameが作成される)

```bash
$ php artisan make:command test/testCommand
Console command created successfully.
$ php artisan list
Laravel Framework 5.8.21
(略)
 cache
  cache:clear              Flush the application cache
  cache:forget             Remove an item from the cache
  cache:table              Create a migration for the cache database table
 command
  command:name             Command description
 config
  config:cache             Create a cache file for faster configuration loading
```


## プログラムの記述方法

作成されたファイルは`app/console/commands`に出力されている。

```php
<?php

namespace App\Console\Commands\test;
use Illuminate\Console\Command;
class testCommand extends Command
{
    /**
     * The name and signature of the console command.
     *
     * @var string
     */
    protected $signature = 'command:name';

    /**
     * The console command description.
     *
     * @var string
     */
    protected $description = 'Command description';

    /**
     * Create a new command instance.
     *
     * @return void
     */
    public function __construct()
    {
        parent::__construct();
    }

    /**
     * Execute the console command.
     *
     * @return mixed
     */
    public function handle()
    {
        //
    }
}

```


1. `$signature`をartisan listに出力されるコマンド名を設定する
2. `$description`に概要を書く
3. `public function handle()`の中にコマンドの処理を書く



## コマンドから別のコマンドを呼び出す

[artisanコマンドからartisanコマンドを呼び出す方法の比較 \- Qiita](https://qiita.com/orange634nty/items/9cbcc5cbe9174966a74b)

`$this->call('aaa');`でaaaのコマンドを呼び出せる

```php
public function handle() 
    {
        $this->call('test:testCommand');

        //そのほかの処理
    }
```
