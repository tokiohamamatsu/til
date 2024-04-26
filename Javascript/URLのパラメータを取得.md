# URLのパラメータ取得

```js
let Params = new URL(location.href).searchParams

if (Params.has('パラメータ名')) {
    let Param = Params.get('パラメータ名');
}   

```

`new URL()`の部分は別の書き方ができるらしい。

### 参考

[URLに含まれるGETパラメータを取得する \| GRAYCODE JavaScript](https://gray-code.com/javascript/get-parameter-of-url/)

[URLのパラメータの値を取得](https://zenn.dev/nagiri/articles/9c7e2dcc5a8a72)

[URLに特定のGETパラメータが含まれるか確認する \| GRAYCODE JavaScript](https://gray-code.com/javascript/check-get-parameter-from-url/)