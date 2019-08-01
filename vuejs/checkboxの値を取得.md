# checkboxの値を取得

チェックボックスの値を取得したい

```html
<template>
    <table class="table">
    <tr>
        <th>担当者CD</th>
        <th>始業時刻</th>
        <th>終業時刻</th>
        <th>休憩時間</th>
        <th>運転手当申請</th>
    </tr>
    <tr v-for="datail in datails" :key="datail.id">
        <input type="hidden" name="datails[id][]" :value=" datail.id ">
        <td><input type="text" name="datails[担当者CD][]" :value=" datail.担当者CD " class="form-control-sm col-auto"></td>
        <td><input type="time" name="datails[始業時刻][]" :value=" datail.始業時刻 " class="form-control-sm col-auto"></td>
        <td><input type="time" name="datails[終業時刻][]" :value=" datail.終業時刻 " class="form-control-sm col-auto"></td>
        <td><input type="time" name="datails[休憩時間][]" :value=" datail.休憩時間 " class="form-control-sm col-auto"></td>
        <td><input type="hidden" name="datails[運転手当申請][]" :value="datail.運転手当申請" class="value">
        <input type="checkbox" :checked="datail.運転手当申請==1" v-on:change="checked" class="check"></td>
    </tr>
    
    </table>
</template>
<script>
export default{
        
        props:["data","datails"],
        
    mounted() {
        console.log('ExampleComponent mounted.')
        console.log(this.$props.data)
        if(this.$props.data.length==0){
            this.push(5)
            console.log('a');
        }
        
    },
    
    methods:{
        checked(event){
            var check=document.getElementsByClassName('check')
            var value=document.getElementsByClassName('value')
            for(var i=0;i<this.$props.datails.length;i++){
            if(check[i].checked==true){
                value[i].value=1
            }else{
                value[i].value=0
            }
            console.log(check[i].checked);
            }        
        }
    }
};
</script>
```

## 概要

- `document.getElementsByClassName()`でクラス名から要素を取得
- `checkbox`がcheckされた時`hidden`の`value`に値を入れる
- `for()`でテーブルの行の数まで繰り返す

### 何とかしたいこと

- テーブルの行を追加する時記入の途中だと記入した文字が消える
- 一度もチェックボックスに触れていなかったらnullが送信される