# Form.ShowDialogとApplication.Runの違い

From.ShowDialogで開いた場合、そこから開いたFromのDisposedイベントが発生しなくなる。

Application.Runではこのような問題は起きない。

### 参考

[Application\.RunとForm\.ShowDialogの違い \- \.NET Tips \(VB\.NET,C\#\.\.\.\)](https://dobon.net/vb/dotnet/form/runvsshowdialog.html)