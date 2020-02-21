# style属性をすべて消す

jqueryでstyle属性をすべて消すには`.removeAttr()`を使う

```js
$('#area *').removeAttr('style');
```

これで、`.prop()`で追加したstyleも削除できる

### 参考

[jQueryで追加したstyle属性を全て削除する方法 \- FEVDES BLOGFEVDES BLOG](http://blog.idea-clippin.com/?p=1446)