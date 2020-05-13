# apacheのsuexec

suexecはcgiの実行ユーザーを任意のものにする仕組みのこと
エスユーエグゼクと読むらしい。

[suEXEC ‐ 通信用語の基礎知識](https://www.wdic.org/w/TECH/suEXEC)

cgiはコモン・ゲートウェイ・インターフェースの略称でWebサーバー上のプログラムを動かすための仕組みのこと

[CGIとは｜「分かりそう」で「分からない」でも「分かった」気になれるIT用語辞典](https://wa3.i-3-i.info/word112.html)

suexecは適切に使用できれば、セキュリティ上の危険を減らすことが出来るが、不適切に使うとセキュリティホールを作ってしまう。俗に言う諸刃の剣。

### 参考

[\[Apache\] CGI 使うなら suEXEC 設定しとこ \| バシャログ。](http://bashalog.c-brains.jp/12/01/24-114146.php)

[suEXEC サポート \- Apache HTTP サーバ バージョン 2\.4](https://httpd.apache.org/docs/2.4/ja/suexec.html)