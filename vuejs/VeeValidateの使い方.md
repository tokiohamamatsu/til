# VeeValidateの使い方

## インストール

TERMINALに`npm install vee-validate --save`を入力する

## 使い方

- VeeValidateを読み込む

```js
<script>
import Vue from 'vue';
import VeeValidate from 'vee-validate';

Vue.use(VeeValidate);
</script>
```

- バリデートの設定

VeeValidateはhtmlタグの中に`v-validate=ルール名`を記述すれば設定してくれる

```php
<input v-validate="'required'" type="text" class="vuefield col-2" name="承認担当者" :value=data.承認担当者>
```

複数のルールを指定する時は`|`で区切る

- エラーメッセージの表示

エラーメッセージを表示するにはフィールドに対して生成された最初のエラーを取得する`{{ errors.first('ルールを指定した場所名')}}`を使う。
また、`v-show="errors.has('ルールを指定した場所名')"`とすれば値を入ってるときは、メッセージを非表示、空の時はメッセージを表示することができる。

しかし、このままではエラーメッセージが日本語ではないため日本語にする

```js
import ja from 'vee-validate/dist/locale/ja'

Validator.localize('ja',ja);
Vue.use(VeeValidate,{locale: ja});
```

上記のように記述したら日本語化される
### 参考

[Getting Started \| VeeValidate](https://baianat.github.io/vee-validate/guide/getting-started.html#installation)

[VeeValidate を使って、vue\.jsで簡単にバリデートしてみた \- Qiita](https://qiita.com/youdie/items/417ed2df1bcb6a60001c)