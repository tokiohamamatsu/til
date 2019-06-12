# phpの配列について

## 配列とオブジェクト呼び出し方の違い

 - 配列は変数[]
 - オブジェクトは クラス名->変数名

## 配列の中からランダムに取り出す
array_rand($配列名,[取得数])を使う
※[]は省略可
配列の番号を取り出すので、中身が欲しい場合は
取り出した番号をもとに配列から呼び出す

## テキストファイルを配列にする方法
file(ファイル名)を使う　
※このまま使うと改行コード含まれるのでファイル名の後に「FILE_IGNORE_NEW_LINES」を追加して改行コードを削除してください

# 参考

[【PHP】オブジェクトと連想配列の違いについて調べてみた【初心者向け】 \| もんプロ～問題解決としてのプログラミング〜](https://coinbaby8.com/different-between-object-and-array.html)

[PHP: array\_rand \- Manual](https://www.php.net/manual/ja/function.array-rand.php)

[【PHP】テキストファイルのデータを配列に入れる方法 – ysklog](https://ysklog.net/php/1039.html)