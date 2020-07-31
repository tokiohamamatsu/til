# ADOのLockTypeの種類

|定数|値|内容|
|---|---|---|
|adLockBatchOptimistic|4|楽観的なバッチ更新を示す|
|adLockOptimistic|3|レコードごとに楽観的ロックを行なう<br>プロバイダーは楽観的ロックを使用し、Updateメソッドを呼び出すときのみロックする|
|adLockPessimistic|2|レコードごとに悲観的ロックを行なう<br>編集後すぐにレコードをロックする|
|adLockReadOnly|1|読み取り専用で、変更できない|
|adLockUnspecified|-1|ロックの種類を設定しない<br>複製の場合、複製元と同じ複製の種類で作成される|

楽観的ロックと悲観的ロックについては下記参照

[排他制御（楽観ロック・悲観ロック）の基礎　 \- Qiita](https://qiita.com/NagaokaKenichi/items/73040df85b7bd4e9ecfc)

エラーメッセージは出ない

### 参考

[ADO(ActiveX Data Objects)の使い方の要点｜VBA技術解説](https://excel-ubara.com/excelvba4/EXCEL273.html)

[LockTypeEnum \- SQL Server \| Microsoft Docs](https://docs.microsoft.com/ja-jp/sql/ado/reference/ado-api/locktypeenum?view=sql-server-ver15)