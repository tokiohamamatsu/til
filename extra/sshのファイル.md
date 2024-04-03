# sshのファイル

主に`C:\Users\ユーザ名\.ssh`の直下にファイルを作る

## Config

下記のように記述
```
Host hoge
    HostName 192.168.11.10
    User mothule
    Port 2200
    IdentityFile ~/.ssh/my_second_pc.key
```

## Known_hosts

接続したことがある公開鍵が書かれているファイル
vscodeのremote接続で"プロセスが、存在しないパイプに書き込もうとしました。"とでたらここが怪しい?

[VSCodeのリモートエクスプローラー実行時に"プロセスが、存在しないパイプに書き込もうとしました。"と出た。 \#VSCode \- Qiita](https://qiita.com/sutoronnjiumu/items/b3767f30f157cb1ffd51)


### 参考

[エンジニアなら知らないとヤバいSSHの基礎 \- もちゅろぐ](https://blog.mothule.com/tools/ssh/tools-ssh-basic)