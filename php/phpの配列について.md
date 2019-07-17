# phpの配列について

## 配列とオブジェクト呼び出し方の違い

 - 配列は変数[]
 - オブジェクトは クラス名->変数名

## 配列の中からランダムに取り出す
array_rand($配列名,[取得数])を使う
※[]は省略可
配列の番号を取り出すので、中身が欲しい場合は
取り出した番号をもとに配列から呼び出す

## 使い方

```php
$array=[0,1,2,3,4,5,6];
$rand=array_rand($array);
print($rand);
```

## テキストファイルを配列にする方法
file(テキストファイル)を使う　
※このまま使うと改行コード含まれるのでファイル名の後に「FILE_IGNORE_NEW_LINES」を追加して改行コードを削除してください

## 使い方

$sampe_file_path=storage_path("sample/corporate/sample.txt");
$samples=file($sample_file_path,FILE_IGNORE_NEW_LINES);

### 参考

[【PHP】オブジェクトと連想配列の違いについて調べてみた【初心者向け】 \| もんプロ～問題解決としてのプログラミング〜](https://coinbaby8.com/different-between-object-and-array.html)

[PHP: array\_rand \- Manual](https://www.php.net/manual/ja/function.array-rand.php)

[【PHP】テキストファイルのデータを配列に入れる方法 – ysklog](https://ysklog.net/php/1039.html)

## 連想配列のキーの取得

### やりたいこと

セレクトボックスのオプションを連想配列と同じにしたい

#### やり方

`foreach(配列 as キー => 値)`で連想配列のすべてのキーと値を取得できる

```php 
<select>
@foreach($array as $key => $value)
    <option value={{$key}}>{{$value}}</option>
@endforeach
</select>
``` 

#### 参考

[【PHP】連想配列の作成と、連想配列のキー・値を取得し出力する例](https://blog-and-destroy.com/2651)