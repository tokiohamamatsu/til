# sshの作成

1. 下記からgitのインストーラ取得する

    https://git-scm.com/
2. インストローラを使いgitをインストール
    インストール方法
     [WindowsにGitをインストールする方法 \| サービス \| プロエンジニア](https://proengineer.internous.co.jp/content/columnfeature/6893)
3. `C:\Program Files\Git\usr\bin`を環境変数に登録する
   [Windows 10 環境変数の設定と反映する方法](https://www.tipsfound.com/windows10/11011)
4. コマンドプロンプトを管理者で開き鍵を作成する
  ```
  mkdir c:\Users\XXXXX\.ssh --鍵を入れるフォルダの作成
   
  PS C:\Users\XXXXX> ssh-keygen
    Generating public/private rsa key pair.
  Enter file in which to save the key (//.ssh/id_rsa): c:/Users/XXXXX/.ssh/id_rsa
  Enter passphrase (empty for no passphrase):
  Enter same passphrase again:
  Your identification has been saved in c:/Users/XXXXX/.ssh/id_rsa.
  Your public key has been saved in c:/Users/XXXXX/.ssh/id_rsa.pub.
  The key fingerprint is:
  48:--:--:--:0b:bf:0a:fd:ff:--:--:--:--:--:--:-- XXXXX@YOUR SERVER NAME
  The key's randomart image is:
  +--[ RSA 2048]----+
  |        略       |
  +-----------------+
  ```
※ id_rsaは教えてはいけない(ガチ)
5. 作成した鍵をgitlabに登録する
   1. ログインしてsetteingsを開き、SSH Keysを開く
   2. id_rsa.pubをテキストエディタで開き全てコピーし、keyの場所に張り付ける
   3. titleをつけてAdd keyをクリック

## 参考

[【GitLab】SSH認証キー（公開鍵）を登録する \- Qiita](https://qiita.com/CUTBOSS/items/462a2ed28d264aeff7d5)

[SSH認証キーをGitLabに登録・設定手順 覚書 \- Qiita](https://qiita.com/redamoon/items/07e445d1fce360cb5fa3)

[GitLabにSSHで接続するまでの手順 \- Qiita](https://qiita.com/kyamawaki/items/07fb3332cf3c2f47728a)