# DataGridViewからEnterで値を取得

DataGridViewのKeyDownイベントでDataGridViewのCurrentCellから選択されたセルの位置を取得でき、それを使い値を取り出せる。


```C#
    private void dgvList_KeyDown(object sender, KeyEventArgs e)
    {
        DataGridView dgv = (DataGridView)sender;

        if(e.KeyCode != Keys.Enter)
        {
            return;
        }

        string selectCellValue = dgv_出荷指示履歴一覧[dgv.CurrentCell.ColumnIndex, dgv.CurrentCell.RowIndex].Value.ToString();
    }
```