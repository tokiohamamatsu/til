# CURSORの使い方

## 宣言

```sql
DECLARE @cur CURSOR
```

## カーソルの中身の設定

```sql
SET @cur CURSOR FOR 'SELECT文'
```

## SELECTの結果を回す

```sql
FETCH NEXT FROM @cur INTO 'SELECTの結果を入れる変数'
WHILE(@@FETCH_STATUS = 0)
BEGIN
--　ループ処理
FETCH NEXT FROM @cur INTO 'SELECTの結果を入れる変数'
END
```

`@@FETCH_STATUS`は最終行を取ると1を返す

## カーソル使用後にやるべきこと

カーソルを閉じて、メモリ上から解放する

```sql
CLOSE @cur
DEALLOCATE @cur
```