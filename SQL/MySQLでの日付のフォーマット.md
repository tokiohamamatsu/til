# MySQLでの日付のフォーマット

構文
```
DATE_FORMAT(datem format)
```

構文の種類
|指定子|内容|例|
|---|---|---|
|%Y|4桁の年|2024|
|%y|2桁の年|24|
|%c|月|1|
|%m|2桁の月|01|
|%e|日|1|
|%d|2桁の日|01|


## 例

```
SET @in_date = '2024-09-25 21:40:13';

SELECT 	DATE_FORMAT(@in_date, '%m/%d/%Y') AS 'MM/dd/yyyy', -- 09/25/2024
		DATE_FORMAT(@in_date, '%m/%d/%y') AS 'MM/dd/yy', -- 09/25/24
        DATE_FORMAT(@in_date, '%Y/%m/%d') AS 'yyyy/MM/dd', -- 2024/09/25
		DATE_FORMAT(@in_date, '%y/%m/%d') AS 'yy/MM/dd', -- 24/09/25
        DATE_FORMAT(@in_date, '%d/%m/%Y') AS 'dd/MM/yyyy', -- 25/09/2024
		DATE_FORMAT(@in_date, '%Y%m%d') AS 'yyyyMMdd', -- 20240925
		DATE_FORMAT(@in_date, '%H:%i:%s') AS 'HH:mm:ss', -- 21:40:13
		DATE_FORMAT(@in_date, '%T') AS 'HH:mm:ss', -- 21:40:13
        DATE_FORMAT(@in_date, '%r') AS 'hh:mm:ss AM or PM', -- 09:40:13 PM
		DATE_FORMAT(@in_date, '%Y%m%d%H%i%s') AS 'yyyyMMddHHmmss', -- 20240925214013
        DATE_FORMAT(@in_date, '%Y/%m/%d %T') AS 'yyyy/MM/dd HH:mm:ss', -- 2024/09/25 21:40:13
		DATE_FORMAT(@in_date, '%Y年%m月%d日 %H時%i分%s秒') AS '日時'; -- 2024年09月25日 21時40分13秒
```
### 参考

[MySQL で日付をフォーマットされた文字列に変換する \- MySQL の便利なクエリー集 \- MySQL 入門](https://mysql.sql55.com/query/mysql-date-format.php)