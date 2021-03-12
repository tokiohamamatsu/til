# NULLと空白の同時判定

```vba
IF len(NZ(調べたい値）) = 0 then 
処理
end if
```

`IF len(NZ(調べたい値）) = 0 then `文字列の長さが0かつNULLであれば空文字列に変換される。

### 参考

[Access VBA での Null と ""　 \-以前組んだAccessVBA（ADPファイルにて\- その他（データベース） \| 教えて\!goo](https://oshiete.goo.ne.jp/qa/7250869.html)