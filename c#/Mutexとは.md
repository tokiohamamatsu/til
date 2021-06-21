# Mutexとは

MutexはMUTual EXclusionの略らしく、相互排除という意味らしい。

Mutexは排他制御のための仕組みでアプリケーションを1度に1つしか起動させたくない場合などに使う。

Mutexは2種類あり、アプリケーションの多重起動を禁止にする場合に使う「名前付きMutex」、
アプリケーション内で排他制御する場合に使う「名前無しMutex」がある。

Mutexは解放しないとリリースリークが発生する。

### 参考

[C\#のMutexとは？2つの種類と使用方法を理解しよう！ \| \.NETコラム](https://www.fenet.jp/dotnet/column/tool/3862/#Mutex-4)