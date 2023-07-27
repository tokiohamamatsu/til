# AccessでUPDATE文

UPDATEでテーブルを結合させる書き方

```
UPDATE
  tableA
INNER JOIN
  tableB
ON
 tableA.col1 = tableB.col1
SET
 tableA.col2 = tableB.col2
;
```

### 参考

[Accessで結合を使用したUPDATE：Javaってまだいけますか](http://javawock.blog.shinobi.jp/windows-%20access/access%E3%81%A7%E7%B5%90%E5%90%88%E3%82%92%E4%BD%BF%E7%94%A8%E3%81%97%E3%81%9Fupdate)