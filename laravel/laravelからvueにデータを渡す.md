# laravelからvueにデータを渡す

## bladeの作成

- vueにデータを渡す

```php
<div id="app">
    <example-component test="GET DATA: {{ $_GET['AAA'] }}"></example-component>
</div>
```

## Componentの作成

- データの受け取り

```javascript
    props: {
        test: String,
    }
```

propsでデータを受けとることができ、受け取る型も指定できる

- データの表示

```php
<span class="test">{{test}}</span>
```
propsで受け取った変数の中身は{{}}使えば表示できる

### 参考

[STEP01：Laravel5\.7 \+ Vue2\.5 でLaravelからVueにデータを渡す \- Qiita](https://qiita.com/nobu-maple/items/a704fe70809b0394b5c9)

[Vue\.jsの書き方実例集\(随時追加\)※逆引きリファレンス的な \- Qiita](https://qiita.com/Yorinton/items/a0144c34e4edb0777493)

[Vue\.jsのコンポーネント入門\[props\]\[$emit\]](https://noumenon-th.net/programming/2019/02/22/component/)