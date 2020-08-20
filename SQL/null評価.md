# null評価

sqlでnullかどうかはIS NULLかIS NOT NULLを使い判断する

```sql
case when a is null then '' else A end

case when a is not null  then A  else '' end
```

### 参考

[「NULLの場合はそのまま、NULLでない場合は「1」に変換したい」（1） Insider\.NET － ＠IT](https://www.atmarkit.co.jp/bbs/phpBB/viewtopic.php?topic=38422&forum=7)