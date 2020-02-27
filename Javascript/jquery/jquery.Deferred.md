# jquery.Deferred

jquery.Deferredは非同期処理を簡単に扱うための標準機能

使い方

1. $.Deferred()でDeferredオブジェクトを作る
2. 非同期処理が終わったらDeferredオブジェクトの状態を変更するように設定しつつ、処理を返す
3. Deferredオブジェクトが持っているPromiseオブジェクトをreturnする

```js
/**
 * 1秒後にHello!を出力するDeferred対応関数。必ずresolveする
 *
 * @returns Promise
 */
function delayHello()
{
  var d = new $.Deferred;
  setTimeout(function(){
    console.log('Hello!');
    d.resolve();
  }, 1000);
  return d.promise();
}

/**
 * 1秒後にエラーを発生させるDeferred対応関数。必ずrejectする
 *
 * @returns Promise
 */
function delayError() {
  var d = new $.Deferred;
  setTimeout(function(){
    d.reject('Error!!');
  }, 1000);
  return d.promise();
}
```

promiseオブジェクトの状態がresolvedなら`done()`メソッドでコールバックされ、rejectedなら、`fail()`メソッドのコールバックされる

コールバックの設定

```js
var promise = delayHello();
promise.done(function(){ /* resolvedで実行 */ });
promise.fail(function(e){ /* rejectedで実行 */ });
```

`.then()`を使うと.doneと.failを一気に登録でき、第2引数は省略可能で、その場合.doneのみ登録される

```js
delayHello()
.then(function(){ /* resolvedで実行 */ }, function(e){ /* rejectedで実行 */ });
```

### 参考

[爆速でわかるjQuery\.Deferred超入門 \- Yahoo\! JAPAN Tech Blog](https://techblog.yahoo.co.jp/programming/jquery-deferred/)

[jQuery $\.Deferredのthen,done,fail,alwaysの使い分けメモ \- Qiita](https://qiita.com/michiko89/items/2ee0235d95eb399960e4)

[async:false とは何か。或いは、非同期処理を諦めるのはまだ早い\! \- Qiita](https://qiita.com/sukobuto/items/0ee5026776e1bab10fb4)

[jQueryのDeferredが便利過ぎた \- Qiita](https://qiita.com/yamamoto_hiroya/items/9380375b11c99f056663#deferred%E3%82%92%E4%BD%BF%E3%81%A3%E3%81%9F%E5%A0%B4%E5%90%88)