# veevalidateのエラーメッセージを変更する

```js
mounted() {
	const dict = {
		custom: {
			運転手当: {
				numeric: "運転手当は半角数字のみ使用できます"
			}
		}
	};
Validator.localize("ja", dict);
```

カスタム内容を`Validator.localize`にいれることで上書きできる

### 参考
[Vue\.js VeeValidateの固有メッセージを変更する](https://mseeeen.msen.jp/change-a-message-of-the-veevalidate/)