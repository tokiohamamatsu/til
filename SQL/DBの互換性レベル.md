# DBの互換性レベル

互換性レベルはMicrosoft SQL Serverのそれぞれのバージョンに設定されている

互換性レベルで関数がつかえないなどの問題が発生する

例

互換性レベルが130でないとstring_splitが使えない


現在の互換性レベルを特定するには下記のSQLを実行する

`SELECT name, compatibility_level FROM sys.databases;`

### 参考

[ALTER DATABASE 互換性レベル \(Transact\-SQL\) \- SQL Server \| Microsoft Docs](https://docs.microsoft.com/ja-jp/sql/t-sql/statements/alter-database-transact-sql-compatibility-level?view=sql-server-ver15)

[ALTER DATABASE 互換性レベル \(Transact\-SQL\) \- SQL Server \| Microsoft Docs](https://docs.microsoft.com/ja-jp/sql/t-sql/statements/alter-database-transact-sql-compatibility-level?view=sql-server-ver15)

[【SQL Server】互換性レベルについて解説 \| 100%レンタルサーバーを使いこなすサイト](https://go-journey.club/archives/11157)