# Form

## Form control

`.form-control`クラスは`<input>,<select>,<textarea>`のようなテキスト形式に使う、一般的な外観、フォーカス状態、サイズなどのスタイルを含む

### コントロールのサイズ

- `.form-control-lg` コントロールのサイズを大きめにする
- `.form-control-sm` コントロールのサイズを小さめにする

## Form group

Bootstrapのフォームはデフォルトで積み重ねられる。フォーム単位でレイアウトを変更するには追加のクラスを使用する。

`.form-group`クラスはフォームに構造体を追加する最も簡単な方法で、適切なグループ化を促す柔軟なクラス

### Form grid

複雑なフォームはグリッドクラスを使い構築する

`form-row` クラスを使えばグリッドシステムを使うことができる、これによって水平フォームを作成でき `<label>` に `.col-form-label` を追加するとフォームコントロールの中央に垂直で配置出来る

水平フォームのサイズを変えるには `.col-form-control-sm` または `.col-form-control-lg` を使用する

横並びフォームは`<form>`に `.form-inline` クラスを使用し、ラベルやフォームコントロール、ボタンを水平の1行で表示できる

ラベルを隠す場合は `<label>` に `.sr-only` を入れる


### 参考

[フォーム～Bootstrap4移行ガイド](https://cccabinet.jpn.org/bootstrap4/components/forms)

# Navbar

- ナビゲーションバーは `.navbar-expand`と配色のクラスが必要
- サポート済みのコンテンツ
   - `navbar-brand`は、会社や製品、プロジェクト名に使用
   - `navbar-nav`はナビゲーションに使用
   - `navbar-toggler`は折り畳みプラグインに使用
   - `collpase.navbar-collpase`は親要素のブレークポイントに使用ナビゲーションバーのコンテンツをグループ化して非表示にする。 

```php
　<header class="sticky-top">
        <nav class="navbar navbar-expand-sm navbar-dark bg-primary">
            <a class="navbar-brand" href="">Home</a>
            <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>

            <div class="collapse navbar-collapse" id="navbarSupportedContent">
                <ul class="navbar-nav mr-auto">
                    <li class="nav-item">
                        <a class="nav-link" href="{{route('business.index')}}">企業マスタ</a>
                    </li>
                    <li class="nav-item">    
                        <a class="nav-link" href="{{route('JobType.search')}}">職種マスタ</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="{{route('calendar.index')}}">休日マスタ</a>
                    </li>
                    <li class="navitem">
                        <a class="nav-link" href="/">摘要マスタ</a>
                    </li> 
                </ul>
            </div>
        </nav>
    </header>

```

### 参考

[ナビゲーションバー～Bootstrap4移行ガイド](https://cccabinet.jpn.org/bootstrap4/components/navbar)