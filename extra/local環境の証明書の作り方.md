# local環境の証明書の作り方

1. 下記コマンドを管理者で実行して証明書作成
    `New-SelfSignedCertificate -DnsName "localhost" -CertStoreLocation "cert:\LocalMachine\My"`
2. ファイル名を指定して実行からcertlm.mscを実行
3. 個人の証明書から作られた証明書を信頼されたルート証明機関の証明書に貼り付ける
4. iisのサイトのバインドに設定する


### 参考

[ローカルIIS Webサイトの自己署名証明書の作成方法](https://qiita.com/SY81517/items/347e86582054f8e92742)