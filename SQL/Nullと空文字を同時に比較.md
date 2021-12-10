# Nullと空文字を同時に比較

```sql
CASE WHEN ISNULL(RESULT,'') = ''
    THEN '空文字かNULL'
    ELSE '空文字かNULL以外'
END AS HANTEI
```


### 参考

[\[SQL Server\]NULLと０または空文字を除外する \| IT☆ぱらだいす](https://blog.itparadise.jp/?p=641)