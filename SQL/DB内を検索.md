# DB内を検索

※ SQL Server

```SQL
SELECT   O.type,
         O.name,
         M.definition
FROM     sys.sql_modules AS M
           INNER JOIN sys.objects AS O
            ON M.object_id = O.object_id
WHERE    M.definition LIKE '%キーワード%'
ORDER BY O.type,
         O.name;
```

キーワードの文言を検索したいワードにする

typeの表記
P = SQL ストアド プロシージャ
RF = レプリケーション フィルター プロシージャ
V = ビュー
TR = SQL DML トリガー
FN = SQL スカラー関数
IF = SQL インライン テーブル値関数
TF = SQL テーブル値関数
R = ルール (旧形式、スタンドアロン)
D = DEFAULT (制約またはスタンドアロン)

### 参考

[キーワードでストアドプロシージャなどを検索する \- 便利なT\-SQL＆クエリー集 \- SQL Server 入門](https://sql55.com/query/search-stored-procedures.php)