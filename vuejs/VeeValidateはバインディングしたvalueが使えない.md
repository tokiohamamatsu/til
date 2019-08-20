# VeeValidateはバインディングしたvalueが使えない

VeeValidateを使いバリデーションをしたところ入力ロックがかかってしまった。
調べたところ[Validating Initial Values \| VeeValidate](https://baianat.github.io/vee-validate/examples/initial-value.html#input-locking-and-value-binding)に`:value`を使い初期値を設定すると入力がロックされると書いてあり,理由はコンポーネントが更新されるたび実行され、入力がバインドされた値に戻るからだそうだ。

[Initial inline input value · Issue \#3924 · vuejs/vue](https://github.com/vuejs/vue/issues/3924)に
>Vue 2\.0では、テンプレートは関数のようなものです。何かが変更されるたびに呼び出されます。これを念頭に置いて、インラインを持つことvalueは、基本的に入力の値が静的であり、決して変更されないことを意味しますv\-model。

と書いてあり`:value`のところを`v-model`に変えてみた

```php
    <div class="card">
        <div class="card-body">
            <div class="inputarea">
                <div>
                    <label>id</label>
                    <div name="id" class="field">{{data.id}}</div>
                    <input type="hidden" name="id" :value=data.id id="id">
                </div>
                <div>
                    <label>営業日</label>
                    <input type="text" class="field" name="営業日" :value=data.営業日>
                </div>
                <div>
                    <label>入力担当者</label>
                    <input type="text" class="vuefield col-3" :value=input readonly>
                    <input v-validate="'required|numeric'" type="text" class="vuefield col-2" name="入力担当者" v-model=data.入力担当者 v-on:input="inputstaff" id="input">
                    <span class="error">{{errors.first('入力担当者')}}</span>  
                </div>
                <div>
                    <label>承認担当者</label>
                    <input type="text" class="vuefield col-3" :value=approval readonly>
                    <input v-validate="'required|numeric'" type="text" class="vuefield col-2" name="承認担当者" v-model=data.承認担当者 v-on:input="approvalstaff" id="approval">
                    <span class="error">{{errors.first('承認担当者')}}</span>
                </div>
                <div>
                    <label>現場</label>
                    <input type="text" class="vuefield col-3" name="現場名" v-model=data.現場名 id="sitename" readonly>
                    <input v-validate="'required|numeric'" type="text" class="vuefield col-2" name="現場CD" v-model=data.現場CD v-on:input="site" id="sitecd">
                    <span class="error">{{errors.first('現場CD')}}</span> 
                </div>
                <div>
                    <label>天候</label>
                    <input type="text" class="field" name="天候" :value=data.天候>
                </div> 
                <div>
                    <label>note</label>
                    <input type="text" class="field" name="note" :value=data.note>
                </div>   
                <div class="blockbtn card-footer">
                    <button type="submit" class="btn btn-secondary btnspace" >{{mode}}</button>
                    <button class="btn btn-secondary btnspace" onclick="history.back()">戻る</button>
                </div>
            </div>
        </div>
    </div>
```

変えてみたところ入力ができるようになった