# VeeValidateのエラー取得

VeeValdateでエラーを取得するにはErrorBagクラスを使う

```js
<button
    type="submit"
    class="btn btn-secondary btnspace"
    :disabled="errors.any()||axios"
    >{{mode}}</button>
```

`erros.any()`でエラーの存在の有無が確認できる

## API

|メソッド|戻り値の型|説明|
|---|---|---|
|add（error：ErrorObject）|void|エラーをerrorbagに追加する。|
|all（scope ?: string）|Array|配列内のすべてのエラーメッセージを取得する。スコープを指定すると、そのスコープ内のメッセージを取得する|
|any（scope ?: string）|boolean|エラーが存在するかどうか確認する。スコープを指定するとスコープ内のみ確認する。|
|clear（scope ?: string）|void|全てのエラーを削除する。スコープを指定すると、スコープに関連するエラーのみ削除される|
|collect（field ?: string、scope？：string、mapped ?: boolean）|Array or Object|特定のフィールドに関するエラーを取得する。フィールド名を渡さなければ代わりにすべてのエラーがフィールド名でグループ化される。|スコープを指定すると、収集だ動作がスコープに制限される。オプションで、エラーオブジェクトをエラーメッセージにマップするかどうか指定できる。falseを指定すると、エラーに関する情報を含むオブジェクトを返す。
|count()|number|エラーの数を返す|
|first(field: string, scope?: string)|string or null|フィールドに関連した、もしくはセレクターによって指定された最初のエラーメッセージを返す。|
|firstById(id: string)|string or null|指定されたIDを持つフィールドの最初のエラーメッセージを返す。|
|firstRule(field: string)|string or null|特定のフィールドに関連した最初のエラーメッセージを返す|
|firstByRule(field: string, rule: string, scope?: string)|string or null|特定のフィールドとルールに関連した最初のエラーメッセージを返す|
|has(field: string, scope?: string)|boolean|特定のフィールドに関連した、もしくはセレクターに指定されたエラーメッセージがあるか確認する。|
|remove(field: string, scope?: string)|void|特定のフィールドに関連するすべてのエラーを削除する。|
|removeById(id: string)|void|指定されたIDと一致するフィールドを削除する|
|update(id: string, diff: ErrorObject)|void|フィールドエラースコープを最新の状態を保つため内部的に使用される特定のフィールドのエラーメッセージデータを更新する。|

## 子コンポーネントのバリデーションエラーを取得する

親のバリデータススコープを継承させる

親

```js
export default {
  inject: ['$validator'],
```

子

```js
export default {
  inject: {
    $validator: '$validator'
  },
```

上記によりすべてのエラーと検証状態を共有できる。


### 参考

[ErrorBag \| VeeValidate](https://baianat.github.io/vee-validate/api/errorbag.html#api)

[【Vee\-Validate】個々のエラーだけをリセットする方法 \- Qiita](https://qiita.com/_Keitaro_/items/ff770f22691c5e661b12)

[【Vee\-Validate】子コンポーネントのバリデーションエラーを検出する方法（依存性の注入） \- Qiita](https://qiita.com/_Keitaro_/items/b46487ec8282690a0216)