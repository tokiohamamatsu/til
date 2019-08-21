# input groupとmodal

## input group

インプットグループは`<input>`や`<select>`などに、にテキストやボタンを配置する
`.input-group-preapend`は前方部品、`.input-group-append`は後方部品を示す,前方・後方部品にテキストを用いる場合は`.input-group-text`を示す。

```php
<div class="input-group mb-3">
  <div class="input-group-prepend">
    <span class="input-group-text" id="text1a">@</span>
  </div>
  <input type="text" class="form-control" placeholder="Username"
      aria-label="Username" aria-describedby="text1a">
</div>
<div class="input-group mb-3">
  <input type="text" class="form-control" placeholder="Username"
      aria-label="Username" aria-describedby="text1b">
  <div class="input-group-append">
    <span class="input-group-text" id="text1b">@example.com</span>
  </div>
</div>
```

サイズの変更には`.input-group-sm`,`.input-group-lg`を指定する

### 参考

[とほほのBootstrap 4入門 \- インプットグループ](http://www.tohoho-web.com/bootstrap/input_group.html)

[入力グループ・ブートストラップ](https://getbootstrap.com/docs/4.0/components/input-group/)

## modal

モーダルはJavascriptモーダルプラグインを使用してダイアログをサイトに追加する

モーダルダイアログは`.modal`,`.modal-dialog`で構成され、コンテンツは`.modal-content`、ヘッダは`.modal-header`、タイトルは`.modal-title`、ボディは`.modal-body`、フッタは`.modal-footer`はフッタを構成する。
モーダルダイアログを表示するボタンには、`data-toggle="modal"`および`data-target="#..."`を指定する。

```php
<button type="button" class="btn btn-primary" data-toggle="modal" data-target="#modal1">
  Launch demo modal
</button>
<div class="modal fade" id="modal1" tabindex="-1"
      role="dialog" aria-labelledby="label1" aria-hidden="true">
  <div class="modal-dialog" role="document">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="label1">Modal title</h5>
        <button type="button" class="close" data-dismiss="modal" aria-label="Close">
          <span aria-hidden="true">&times;</span>
        </button>
      </div>
      <div class="modal-body">
        Modal body
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
        <button type="button" class="btn btn-primary">OK</button>
      </div>
    </div>
  </div>
</div>
```

縦方向中央に表示するには以下のように追記する

```php
  <div class="modal-dialog modal-dialog-centered" role="document">
   ...
 </div>
```

サイズの変更は`.modal-sm`や`.modal-lg`、`.modal-xl`を使う

```php
  <div class="modal-dialog modal-sm" role="document">...</div>
  <div class="modal-dialog" role="document">...</div>
  <div class="modal-dialog modal-lg" role="document">...</div>
  <div class="modal-dialog modal-xl" role="document">...</div>
```

オプション

`data-*="..."`で下記のオプションを指定できる

|名前|型|規定値|説明|
|---|---|---|---|
|show|boolean|true|モーダルダイアログを表示する|
|focus|boolean|true|モーダルダイアログにフォーカスを与える|
|keyboard|boolean|true|ESCキーでモーダルダイアログを閉じる|
|backdrop|boolean or 'static'|true|trueを指定すると背景を灰色にし、背景クリックでダイアログを閉じる。falseを指定すると背景は灰色にならず、クリックしてもダイアログ閉じない。'static'を指定すると背景を灰色にするが、クリックしてもダイアログは閉じない。|

### 参考

[とほほのBootstrap 4入門 \- モーダル](http://www.tohoho-web.com/bootstrap/modal.html)

[モーダル・ブートストラップ](https://getbootstrap.com/docs/4.0/components/modal/)