# UPDATEでJOINを行う

```sql
UPDATE tablenameA
   SET col
FROM tablenameA as a
INNER JOIN tablenameB as b on a.key = b.key
```

UPDATEでJOINするにはFROMを追加する必要がありそうだ

### 参考

[UPDATE と JOIN を使ってデータを更新する \- T\-SQL でテーブルへデータの挿入・更新・削除 \- SQL Server 入門](https://sql55.com/t-sql/t-sql-update-1.php)