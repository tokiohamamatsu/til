# vueでbootstrapが動かない時の対処法

bootstrap.min.jsとapp.jsを読み込むと二重に読み込むことになるのでドロップダウンが動かなくなる

対処法

```js
mounted() {
    $('[data-toggle="dropdown"]').dropdown();
}
```

### 参考

[Vue \+ bootstrapのツールチップが動かないときの対処法 – console dot log](https://blog.capilano-fw.com/?p=4773#i-3)