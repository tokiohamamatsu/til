# ADOでCSVに接続

ConnectionStringの引き数

- Provider = Microsoft.Jet.OLEDB.4.0;
- Data Source = DBFileName;
- Extended Properties = EXProperties;

DBFileNameは対象のファイルパスを指定する

EXPropertiesは3つのプロパティがあり

- Textはデータベースの種類を表す。
- HDRはCSVの1行目をフィールド名として扱うか指定する。NOだとフィールド名はF[列番号]となる。
- FNTはファイルのフォーマットを指定する。CSVの場合は、Delimitedを指定する。

CSVのファイル名はテーブル名として扱う。

### 参考

[CSVファイルに接続（ADO） \| ExcelWork\.info](https://excelwork.info/excel/csvado/)