# OneDrive

## 必要なもの

Microsoftアカウント

## 使い方

Windows10と8.1には最初から組み込まれている
- 作業中のドキュメントをOneDriveに保存するには、保存場所一覧から    OneDriveを選択する
- OneDriveにファイルを移動するには、エクスプローラーからOneDriveフォルダーにファイルをドラッグする

上記以外のWindowsはWindows用のOneDriveデスクトップアプリをインストールする

Macの場合はOneDriveをインストールする

通知領域(デフォルトで右下)にある雲のアイコンをクリックするかWebブラウザからアクセスすることでOneDriveを使う事ができる。

### ファイルを共有する方法

1. 共有するフォルダー(ファイル)を選択し、上部にある共有をクリックする
2. 共有したい相手の、メールアドレスを入力し、送信することで、相手がメールのリンクからファイルを確認できれば正しく共有されている
3. 初期設定では、共有先の相手は編集できず、編集してもらいたい場合は、共有する際に受信者は表示のみ可能という項目を受信者に編集を許可するに変更する

[OneDriveとは？基本的な使い方から設定までをわかりやすく解説 \| 365日Officeライフ\!](https://www.onamae-office.com/office365column/oaapp/onedrive/)

## Excelを共有する

Excel 2016 からOneDriveでブックを共有する

画面右上にある共有をクリックすることでOneDriveで共有できる。

手順

1. 共有をクリック
2. クラウドに保存
クラウドに保存するにはサインインする必要がある
3. 共有する相手を招待する
   - ユーザーの招待に相手のメールアドレスを入力する
   - 権限が編集可能になっているか確認する
   - メッセージを入力できる
   - 共有をクリックすることで、相手に招待メールが送信される

### 共有を受けたユーザーがファイルを開く方法

OneDriveのWebページからExcel Onelineを利用してブックを開くことができる。

そのまま編集することは可能だが、共有しているほかのユーザーがExcelでブックを開いていると編集できない。

編集可能な条件

|他のユーザーの作業状態|Excelでの編集|Excel Onlineでの編集|
|---|---|---|
|Excelで編集中|不可(読み取り専用で開ける)|不可(表示のみ)|
|Excel Onlineで編集中|不可(読み取り専用で開ける)|可(同時編集)|
|編集していない|可|可|

Excel Onlineからブックを開き、ブックの編集→ブラウザで編集をクリックすることでExcel Onlineで編集できる。

他のユーザーがExcel編集中だと編集はできない

### Excel Onlineでの共同編集

Excel Onlineで共同作業する場合は、複数のユーザーでの同時編集が可能で、チャットを使用することができる。

同時編集での注意点

- 操作の記録は全ユーザのがまとめれ、元に戻すの結果などが、意図しないものになることがある。
- 並び替えやフィルターを利用すると、結果が編集中の全員に適用される
- エクスプローラーからOneDriveのファイルを開いて編集すると共有した他のユーザーが編集中でも同時編集とは判断されず、
その状態で別々にファイルを保存すると、編集内容をマージ(統合)できなかったとして、別のファイルとして保存される。

### 参考

[Excel文書をOneDriveで共有して共同編集（Excel Onlineで同時編集） \| できるネット](https://dekiru.net/article/14121/)

[Excelで共同作業を始めよう！OneDriveを使った共有と編集権限の設定方法 \| できるネット](https://dekiru.net/article/13654/)

# Excel Online

## 必要なもの

Microsoftアカウント

## 使い方

1. Office.comにサインする
   Microsoftのアカウントのメールアドレスとパスワードを入力する
2. Officeの画面からExcelを選択する

### インストール版との違い

|機能|Excel Onlineでの動作|
|---|---|
|データの入力規則|データの入力規則|
|関数|一部の関数では動作が異なる場合がある　<br> 例 NOW関数はPCの日付ではなくサーバーの日付を返す|
|マクロ|マクロの作成、実行、編集はできないが,マクロを含むブックをひらいて編集できる|
|CSV|CSVファイルは開くことができない|
|ワークシートの保護またはブックの保護|パスワード保護されているブックは表示できず、保護を解除するにはインストール版のExcelで開く|
|画像|画像などのクリップコードは利用不可|
|図の編集|画像のトリミングと画像に文字を追加ぐらいしかできない|
|ショートカットキー|WebブラウザのためExcelのショートカットキーは使えない|
|保存|自動保存のため、保存せずに閉じるができない|

マクロ・VBAを含むブックをOneDriveからダウンロードしたところマクロは無効化されていたが有効化できるためとくに問題はない

### Excel Onlineから自分のPCの保存する方法

名前をつけて保存からコピーのダウンロードを選択することで、コンピュータのダウンロード先にコピーしたファイルが保存される。

### 参考

[無料で使えるExcel Online（エクセルオンライン）の特徴と使い方 \| Office Hack](https://office-hack.com/excel/online/#section3_1)

[Excel Onlineの違いとは？無料のブラウザ版で出来る・出来ない事まとめ \| スッキリわかる\.net](https://sukkiri-wakaru.net/excel-online-chigai/)
