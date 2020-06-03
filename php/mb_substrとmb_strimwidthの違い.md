# mb_substrとmb_strimwidthの違い

mb_substrは文字列から指定した文字数を取得する時に使い、mb_strimwidthは文字列を指定した文字列に丸めるのに使う。

どちらも文字数制限を作る時に使えるが、文字数の数え方に違いがある。

mb_substrは全角、半角問わず1文字として扱うが、mb_strimwidthは半角は1文字、全角は2文字として扱う。

これらは文字数の数え方を把握していないと、思いも寄らない不具合が生まれることになる。

### 参考

[指定した数で文字列を丸める（n文字目で…にする）関数substr、mb\_substr、mb\_strimwidthの違い \| エス技研](https://blog.s-giken.net/365.html)

[PHP: mb\_substr \- Manual](https://www.php.net/manual/ja/function.mb-substr.php)

[PHP: mb\_strimwidth \- Manual](https://www.php.net/manual/ja/function.mb-strimwidth.php)