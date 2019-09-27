# classの追加・削除

## 追加

```js
$("要素").addClass("changed");
```

指定の要素にchangedが追加される

## 削除

```js
$("要素").removeClass("changed");
```

指定の要素から削除される

## クラスがあれば削除、なければ追加

```js
 $(this).toggleClass("clicked");
```

第二引数に論理式を渡せる、結果がtrueだと`add`(追加)、falseだと`remove`(削除)する

```js
$('textarea').on('change', function(){
  var $this = $(this);
  $this.toggleClass('error', $this.val().length > 10);
});
```

### 参考

[jQuery classの追加・削除 \- Qiita](https://qiita.com/Scheme/items/300739f6da6a95e58306)