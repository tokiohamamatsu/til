# phpの配列にデータ追加時のエラー

配列にデータを追加しようとしたがエラーが出た

```
Message: [] operator not supported for strings
```

これは配列の初期化の型がおかしい場合におきるらしい

変数を配列として初期化することで解決するようだ。

配列の初期化は

```php
$post_type = array(); // array型
```
か
```php
$post_type = NULL; // NULL型
```

で行う

## 参考

[PHPのエラーメッセージ \[\] operator not supported for strings \- JavaScript勉強会](http://jsstudy.hatenablog.com/entry/PHP-error-message_bracket-operator-not-supported-for-strings)