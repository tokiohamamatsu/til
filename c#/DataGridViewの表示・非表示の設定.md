# DataGridViewの表示・非表示の設定

DataGridViewの表示・非表示の設定を設定するには下記のようにする

```c#
dataGridView1.DataSource = dt;
dataGridView1.Columns["EmployeeID"].Visible = false;
```

"EmployeeID"の部分はデザインのNameに置き換える

### 参考

[DataGridView のカラムを非表示にする方法 \- DataGridView の使い方 \- C\# を用いた開発 \- C\# 入門](https://csharp.keicode.com/topics/database-datagridview-2.php)