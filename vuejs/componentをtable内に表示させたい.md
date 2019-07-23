# comonentをtable内に表示させたい

componentをtable内に表示させたい


index.balde.php

```php
<table>
    <tr>
        <th>担当者CD</th>
        <th>始業時刻</th>
        <th>終業時刻</th>
        <th>休憩時間</th>
        <th>運転手当申請</th>
    </tr>
    <tr>
        <div id="app">
            <item-component></item-component>
        </div>
    </tr>
</table>
```

ItemComponent.vue

```php
<template>
    <td><input type="text"></td>
    <td><input type="text"></td>
    <td><input type="text"></td>
    <td><input type="text"></td>
    <td><input type="checkbox"></td>
</template>
<script>
</script>
```

app.js

```javascript

require('./bootstrap');

window.Vue = require('vue');

Vue.component('item-component', require('./components/ItemComponent.vue').default);

const app = new Vue({
    el: '#app',
});
```

この書き方だとcomponentがtableからはじかれtableの上にテキストボックスなどが配置される

## 原因

htmlタグの中には決められたタグ以外は無効にする制限がかかっているものがあるらしい

### 参考

[Vue componentで気をつけるべきこと！ – console dot log](https://blog.capilano-fw.com/?p=523)