# DOMの変化の監視

DOMの変化を検知するにはMutationObserverを使う

```js
var observer = new MutationObserver(function(){
  /** DOMの変化が起こった時の処理 */
  console.log('DOMが変化しました');
});
 
/** 監視対象の要素オブジェクト */
const elem = document.getElementById('#my_example');
 
/** 監視時のオプション */
const config = { 
  attributes: true, 
  childList: true, 
  characterData: true 
};
 
/** 要素の変化監視をスタート */
observer.observe(elem, config);
```

### 参考

[JavaScriptで要素の追加・削除やテキストの変更を監視する方法 \| PisukeCode \- Web開発まとめ](https://pisuke-code.com/mutation-observer-usage/)