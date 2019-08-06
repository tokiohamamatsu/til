# axiosでデータ取得

axiosでデータを取得したい

DateilComponent.vue

```js
<template>
<tr>
    <td><input type="text" name="datails[担当者CD][]" :value=" datail.担当者CD " class="form-control-sm offset-1 col-5 name" v-on:change="getname()" >
    <input type="text" :value=name class="form-control-sm col-5"></td>
</tr>
</template>


<script>
export default{
        
    props:["datail","datails"],
    data:function(){
        return{
        name:[]
        }
    },
    mounted(){
        axios.get('api/staff/getName/'+this.$props.datail.担当者CD).then(response=>{
                this.name=response.data;
        })
    },
    methods:{
        getname(){
            var name=document.getElementsByClassName('name');
            console.log(this.$props.datail.担当者CD);
            for(var i=0;i<name.length;i++){
                if(name[i].value!=this.$props.datails[i].担当者CD){
                    var cd=name[i].value;
                    this.$props.datail.担当者CD =cd;
                }
            }
            axios.get('api/staff/getName/'+cd).then(response=>{
                this.name=response.data;
                
            }) 
        }
    }
}
</scropt>    
```

StaffContoller.php

```php
public function getName($staff_cd){
        return json_encode(Mstaff_model::find($staff_cd)->担当者名);
    }
```

api.php

```php
Route::get('/staff/getName/{staff_cd}', 'StaffController@getName');
```

## 概要

- `mounted(){
        axios.get('api/staff/getName/'+this.$props.datail.担当者CD).then(response=>{
                this.name=response.data;
        })
    },`でapi.phpに設定したルートを実行し、StaffController.phpのgetName関数を実行し名前を取得する


- `<input type="text" name="datails[担当者CD][]" :value=" datail.担当者CD " class="form-control-sm offset-1 col-5 name" v-on:change="getname()">`の値を変えると`getName()`が実行され、`<input type="text" :value=name class="form-control-sm col-5">`の値が連動して変わる

### 参考

[laravel で vue\.js , axios を使う \- Qiita](https://qiita.com/ma7ma7pipipi/items/d58b1a8114f122bf918d)

[Vueの子コンポーネントで警告：\[Vue warn\]: The “data” option should be a function that returns a per\-instance value in component definitions\.が表示されたとき – ひびテク](https://yoshikiito.net/blog/archives/2275)