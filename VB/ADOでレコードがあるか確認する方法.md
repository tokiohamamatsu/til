# ADOでレコードがあるか確認する方法

ADOでレコードのあるか確認するにはRecordsetのEOFまたはBOFを使ったほうが1行で書けて手っ取り早い。

EOF・BOFはカレントレコードの位置を見て、カレントレコードが最後のレコードより後にあるとEOFはtrueになり、先頭のレコードより前にある場合はBOFがtrueになる。

EOF・BOFがfalseだと必ずレコードが1件以上存在することになる。

### 参考

[BOF プロパティ・EOF プロパティ（ADO） \| ExcelWork\.info](https://excelwork.info/excel/adobofeof/)