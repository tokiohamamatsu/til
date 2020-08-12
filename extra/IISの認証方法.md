# IISの認証方法

1. ASP.NET偽装
   - 規定のASP.NETアカウント以外のコンテキストでASP.NETアプリケーションを実行できる。
2. フォーム認証
   -  クライアント側のリダイレクトを使用し、認証されていないユーザーをHTMLフォームに転送し、資格情報を入手する。
3. 匿名認証
   - ユーザー名とパスワードを入力しなくても、すべてのユーザーがアクセスできる

他にも種類があるが、今の環境では上記の３つが確認できた。

### 参考

[認証\| Microsoftドキュメント](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831496(v=ws.11)?redirectedfrom=MSDN#Anonymous)