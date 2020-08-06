# ActiveReportsを触ってみた

ActiveReportsを触ってわかったこと

グループの追加方法

1. 右クリック
2. 挿入
3. グループ　ヘッダー/フッター


ActiveReportsにFieldとShapeがあるのだが、どちらもツールボックスを探してもなく、いろいろためしてみると以下の事がわかった

- Fieldはテキストボックス
- Shapeは図形

ActiveReportsでDBから値を受け取るにはDataFieldプロパティにカラム名を指定する。

DataFieldプロパティは、グループヘッダーにもあり、指定すると

Detailに指定したカラムごとにグループの内容が出力される。