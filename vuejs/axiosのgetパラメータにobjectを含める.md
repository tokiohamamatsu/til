# axiosのgetパラメータにobjectを含める

```js
search() {
	if (this.startdate == null || this.enddate == null) {
		return false;
	} else if (this.startdate < this.enddate) {
		const params = {
			startdate: this.startdate,
			enddate: this.enddate
		};
		axios
			.get(appRoot + "/api/report/search/", {
				params
			})
			.then(response => {
				this.datas = response.data;
				if (this.datas.length == 0) {
					this.notfound = true;
				} else {
					this.notfound = false;
				}
			})
	} else {
		return false;
	}
		},
```

下記の状態で送信するとobject型がstring型に変換された。

```js
.get(appRoot + "/api/report/search/", {
	params:{
        startdate: this.startdate,
		enddate: this.enddate
    }
})
```


### 参考

[axiosでGETリクエストのクエリパラメータにObject型を含める方法 \| TOMILOG](https://blog.ryou103.com/post/axios-send-object-query/)

[axiosのパラメータ指定方法まとめ \- Qiita](https://qiita.com/taroc/items/f22f7dd5d6d5443c72a4)