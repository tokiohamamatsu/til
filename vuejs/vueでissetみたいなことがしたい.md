# vueでissetみたいなことがしたい

## vueにissetがない

javascriptで値の有無を判断したいのだがphpにあるissetがなかった。
なので[JavaScriptでPHPのisset関数みたいなものを使う｜プログラムメモ](https://pgmemo.tokyo/data/archives/765.html)を参考に下記を記述

```php
if(this.$props.datail.担当者CD!=undefined){
            axios.get('../../api/staff/getName/'+this.$props.datail.担当者CD).then(response=>{
                this.name=response.data;    
            })
        }
```

変数を定義しておらず、変数を出力しようとすればundefindが返ってくるので判断することができる

## javascriptのnullとundefinedの違い

- undefinedは変数の値が未定義
- nullは変数の値が空

### 参考

[Javascriptでissetとin\_array \| ITかあさん](http://www.kaasan.info/archives/1706)