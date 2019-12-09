# rem

## remとは

html要素のフォントサイズを基準にサイズをきめる。

## cssのフォントサイズの指定方法は２つ

絶対値 :10pxなら10px

相対値 :親要素のサイズで変わる。

px:数値を絶対値で固定
em:親要素のfont-sizeを基準に大きさを計算する
%:親要素の相対値で決定する

要素が入れ込んでくると、どの親要素を基準にしているが分かりにくくなるが、
remはhtml要素のfont-sizeを基準にするため分かりやすい

## ブラウザのデフォルトサイズ

```css
html {
  font-size: 100%; /* -> 16px; */
}
```

htmlのfont-sizeを62.5%にすると1emが10pxになる

### 参考

[CSSの基本単位としてremを使うと超絶便利 \- Qiita](https://qiita.com/butchi_y/items/453654828d9d6c9f94b0)

[CSS3のremとemの違いについて \- Qiita](https://qiita.com/masarufuruya/items/bb40d7e39f56e6c25f0d)