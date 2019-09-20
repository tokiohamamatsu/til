# veevalidateのエラーを消す

## エラーオブジェクトのアクセス方法

```js
this.$validator.errorBag
//もしくは
this.errors
```

エラーオブジェクトの中身

```
ErrorBag {__ob__: Observer}
items: Array(3)
vmId: 1
__ob__: Observer {value: ErrorBag, dep: Dep, vmCount: 0}
get items: ƒ reactiveGetter()
set items: ƒ reactiveSetter(newVal)
get vmId: ƒ reactiveGetter()
set vmId: ƒ reactiveSetter(newVal)
__proto__: Object
```





itemsにエラーが入る
```
items: Array(3)
0: {__ob__: Observer}
1:
field: "担当者CD"
id: "3"
msg: "担当者CDは必須項目です"
regenerate: ƒ ()
rule: "required"
scope: "0"
vmId: 1
```

data-* Attributes

inputタグなどに記述する

- data-vv-as
  name属性を変えることなくエラー表示にフィールド名を設定できる
- data-vv-delay
  検証までの時間をミリ秒で設定できる
- data-vv-name
  name属性を変えることなく、検証等に使われるフィールド名を設定できる
- data-vv-scope
  フィールドにスコープを設定できる


## 消す方法

`$validator.errors.remove`を使う


## 個別に消す方法

```js
remove() {
	const matchOptions = {
		id: 3 + this.index,
		name: "担当者CD",
		scope: this.index
	};
	const field = this.$validator.fields.items[3 + this.index];
	this.$validator.errors.remove("担当者CD", this.index);
}
```

### 参考

[【Vee\-Validate】個々のエラーだけをリセットする方法 \- Qiita](https://qiita.com/_Keitaro_/items/ff770f22691c5e661b12)

[VeeValidate サンプル集 \- Qiita](https://qiita.com/motohirock/items/d1301318cf16962d23e3#data--attributes)

[VeeValidate](http://vee-validate.logaretm.com/v2/api/data-attrs.html)