# GridViewで最大値取得

```c#
int maxTimeSlot = grid.Rows.OfType<GridViewRow>().Max(r => int.Parse(r.Cells[1].Text));
```

### 参考

[c\# \- GridViewでmaxを取得するためにOrderedDictionaryでlinqを使用する \- ITツールウェブ](https://ja.ojit.com/so/c%23/1705398)