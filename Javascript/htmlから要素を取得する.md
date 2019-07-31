# htmlから要素を取得する

## scriptでhtmlを操作する

- document.getElementById()
    - id名で要素を取得する 
    - 
```html
<template>
<div id="box">This is box</div>
</template>

<script>
var box = document.grtElementById('box');
console.log(box); //<div id="box">This is box</div>
</script>
```

- document.getElementsByTagName()
    - タグ名で要素を取得する

```html
<template>
<div>element 1</div>
<div>element 2</div>
</template>

<script>
var elements= document.getElementsByTagName('div');
console.log(elements[0]);//<div>element 1</div>
console.log(elements[1]);//<div>element 2</div>
</script>
```

- document.getElementsByClassName()
    - class名で要素を取得する

```html
<template>
<div class="box">div element 1</div>
<div class="box">div element 2</div>
<p class="box">p element 1</div>
</template>

<script>
var elements= document.getElementsByClassName('box')
console.log(elements[0]);//<div class="box">div element 1</div>
console.log(elements[1]);//<div class="box">div element 2</div>
console.log(elements[2]);//<p class="box">p elements 1</p>
</script>
```

### 参考

https://www.amazon.co.jp/%E3%83%8E%E3%83%B3%E3%83%97%E3%83%AD%E3%82%B0%E3%83%A9%E3%83%9E%E3%81%AE%E3%81%9F%E3%82%81%E3%81%AEJavaScript%E3%81%AF%E3%81%98%E3%82%81%E3%81%AE%E4%B8%80%E6%AD%A9-WEB-DB-PRESS-plus/dp/4774153761/ref=sr_1_1?__mk_ja_JP=%E3%82%AB%E3%82%BF%E3%82%AB%E3%83%8A&keywords=%E3%83%8E%E3%83%B3%E3%83%97%E3%83%AD%E3%82%B0%E3%83%A9%E3%83%9E%E3%81%AE%E3%81%9F%E3%82%81%E3%81%AEjavascript%E3%81%AF%E3%81%98%E3%82%81%E3%81%AE%E4%B8%80%E6%AD%A9&qid=1564568830&s=gateway&sr=8-1