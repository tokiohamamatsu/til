# countを使わないでレコード数を取得する方法

SUMの条件にCASE文を入れ、Trueだったら1、Falseだったら0を出すようにし、それらを合計する。

例

```sql
SELECT
  SUM(CASE WHEN 性別='男' THEN 1 ELSE 0 END) AS 男の数
  ,SUM(CASE WHEN 性別='女' THEN 1 ELSE 0 END)  AS 女の数
FROM テーブル
```

### 参考

[【SQL】COUNT関数で条件に合致する件数を取得する \- Qiita](https://qiita.com/zb185423/items/f20b21ca041989410b5f)のコメント