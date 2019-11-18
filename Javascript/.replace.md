# .replace()

パターンにマッチした文字列の一部または全てをreplacementで置き換えた新しい文字列を返す。

```html
<FORM>
テキストボックス
<input type="text" value="" onInput="checkForm(this)">
 
テキストエリア
<textarea rows="2" onInput="checkForm(this)"></textarea>
</FORM>
 
<script type="text/javascript">
<!--
function checkForm($this)
{
    var str=$this.value;
    while(str.match(/[^A-Z^a-z\d\-]/))
    {
        str=str.replace(/[^A-Z^a-z\d\-]/,"");
    }
    $this.value=str;
}
//-->
</script>
```

上記は数字、[A-Z],[a-z],[-],以外の文字が入力されたらその文字を消す。

### 参考

[String\.prototype\.replace\(\) \- JavaScript \| MDN](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/String/replace)

[フォームのテキスト入力を半角文字のみ許可する方法](https://toolmania.info/post-6660/)