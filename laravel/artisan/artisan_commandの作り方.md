# artisan commandの作り方

1. Terminal(Ctrl+Shift+@)から `php artisan make:command`を使う
2. コマンド名名入力時:ではなく/を使う
3. 作成成功した場合ファイルの `$signature`をコマンド名にする
4. `php artisan list`でファイルがあるか確認する 
```
php artisan make:command sample/import_job //sampleフォルダとimport_job.phpがapp/console/commandsに作られる
php artisan list //使えるコマンドの一覧が表示される
```
5. `public function handle()`の中にコマンドの処理を書く
6. `$description`にコマンドのコメントを書く
```
<?php

namespace App\Console\Commands\sample;

use Illuminate\Console\Command;
use App\Mjob_type_model;

class import_job_corporate extends Command
{
    /**
     * The name and signature of the console command.
     *
     * @var string
     */
    protected $signature = 'sample:import_job'; //フォルダ名とコマンド名

    /**
     * The console command description.
     *
     * @var string
     */
    protected $description = '職種マスタのサンプルをインポートする'; //コマンドのコメント 主に説明

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
     //テキストファイルをDBに登録する処理
    public function handle()  //コマンドの処理を書く
    {
        $sample_file_path=storage_path("sample/corporate/job type.txt");
        $samples=file($sample_file_path, FILE_IGNORE_NEW_LINES);
        
        foreach ($samples as $index=>$sample) {
            Mjob_type_model::create([
                '職種名'=>$sample,
                '略称名'=>mb_substr($sample, 0, 2),
                '勤務時間区分'=>(rand(0, 99) < 20)?1:0
            ]);
            if ($index % 100==0) {
                print "*";
            }
        }
    }
}
```
7. 保存

### 参考

[【Laravel】Artisanコマンドを自作する方法 \| とものブログ](https://se-tomo.com/2018/10/13/laravel-%E3%82%AB%E3%82%B9%E3%82%BF%E3%83%A0%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89/)

## コマンドから別のコマンドを呼び出す

$this->call('コマンド名');
これで別のコマンドを呼び出せる
```
public function handle() //コマンド sample:clear_jobとsample:import_jobを呼び出し実効する処理
    {
        $this->call('sample:clear_job');
        $this->call('sample:import_job');
    }
```

### 参考

[artisanコマンドからartisanコマンドを呼び出す方法の比較 \- Qiita](https://qiita.com/orange634nty/items/9cbcc5cbe9174966a74b)