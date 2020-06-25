# DataGridViewで表示すデータを絞り込む

BindigSourceにDataGridViewのDatasourceを代入し、BindigSourceのfilterに条件式を入れる。

※条件式を記述するときはDataGridViewに表示されている列名を対象にする。

```c#
Private void DataGridViewFilter{
    BindingSource bs = new BindingSource();
    string strFilter;
    bs.DataSource = dgvAppList.DataSource;
    strFilter = "Color like '%" & 条件 & "%'"
    bs.Filter = strFilter
}
```

### 参考

[c\# \- BindingSourceをDataTableにキャストする方法](https://stackoverrun.com/ja/q/10533772)

[DataGridView上のデータを絞り込み表示する \- mamori017\.log](https://mamori017.hatenablog.com/entry/2018/03/09/112828)