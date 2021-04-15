# SQLServerの変換エラー

SQLServerにテキストファイルを読み込ませようと思ったらエラーが発生

```sql
BULK INSERT テーブル名
From 'テキストファイルのパス'
With(
  codepage = '932',
  FIELDTERMINATOR = '\t',
  ROWTERMINATOR = '\n'
)
```

ある列の全データがNULLの文字列であり、それをテキストファイルから消せばテキストファイルを読み込むようになった。
しかし、NuLLの文字列でエラーになるのはなぜなのだろうか？