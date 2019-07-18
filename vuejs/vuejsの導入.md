# vuejsの導入

## セッティング

TERMINALに`npm install`を入力しインストールする

TERMINALに`npm run dev`を入力しビルドする
ビルドが完了すると下記がTERMINALに表示される

```
 DONE  Compiled successfully in 14950ms                                                         
       Asset      Size   Chunks             Chunk Names
/css/app.css   173 KiB  /js/app  [emitted]  /js/app
  /js/app.js  1.38 MiB  /js/app  [emitted]  /js/app
```

※`npm run watch`を入力すると自動でコンパイルする

## 使い方

- app.jsを読み込む
- `<div id="app"></div>`で囲む
- `<コンポーネント名></コンポーネント名>`で呼び出す

```php
<div id="app">
    <example-component><example-component>
</div>
<script src = "{{asset('/js/app.js')}}"></script>
```

## コンポーネントの追加

- resources/js/componentsにファイルを作成する
- resources/js/app.jsにコンポーネントの定義を追記する

### 参考

[LaravelからVue\.jsを使う最短レシピ \- Qiita](https://qiita.com/fruitriin/items/e0f2c9aa035c3ff2c874)

[LaravelでVue\.jsを使って開発するファーストステップ](https://www.ritolab.com/)

[【Laravel × Vue\.js チュートリアル】HelloWorldをやってみる \| ブロックチェーンエンジニアのブログ](https://daiki-sekiguchi.com/2018/08/13/laravel-vue-js-helloworld/)

[Laravel 5\.4で Vue\.js開発環境を手軽に作る \- アシアルブログ](https://blog.asial.co.jp/1496)