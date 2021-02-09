# CellFormattingとPanel

DataGridViewを操作できないよう上からPanelで蓋をしようしたら

CellFormattingでDataGridViewが再描画され、その後Panelが表示される動作になり画面がチラつく。

PanelをLabelに変えたら画面がチラつかなくなった。