# C#とSQL Serverとの型比較

SQL ServerにByteがないことから調べだした

|C#|SQL Server|
|---|---|
|decimal|decimal|
|int|int|
|long|bigint|
|string|ntext(文字数指定なし)<br>nvarchar(文字数指定あり)|
|bool|bit|
|byte|tinyint|

### 参考

[[C#][データベース]データ型比較 | Swipoke](https://www.swipoke.jp/categories/develop/csharp/numtype/)