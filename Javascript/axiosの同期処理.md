# axiosの同期処理

axiosは非同期処理で 使いづらいこともあるので、同期処理にしたい

同期処理にするにはasyncとawaitを使う

使い方は
- .then()で非同期関数を呼び出すときに、awaitをつける
- 戻り値がthenに渡すコールバック関数の引数と同じにする
- awaitが使われる関数にasyncをつける

```js
const axios = require('axios');
 
const main = async ()=>{
    let res = await axios.get("https://glorificatio.org/")
    console.log(res.status)
    console.log("終了");
}
 
main();
```

上記の場合axiosの処理が終わるまで、main関数の処理を待ってくれる

### 参考

[JavaScriptの同期処理 async/awaitを分かりやすく \| Divide et impera](https://glorificatio.org/archives/3476)