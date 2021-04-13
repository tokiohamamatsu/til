# CSVをインポート

SQLでCSVをインポートするには BULK INSERTを使う

```sql
BULK INSERT Students
FROM 'c:\NewStudents.txt'
WITH
(
   FIELDTERMINATOR = ',',
   ROWTERMINATOR = '\n'
);
```

CSVがタブ区切りの場合は`','`の部分を'\t'に変える
ROWTERMINATORは1行の終わりの文字を指定する。

### 参考

[CSV ファイルを BULK INSERT を使ってインポートする \- 便利なT\-SQL＆クエリー集 \- SQL Server 入門](https://sql55.com/query/bulk-insert.php)