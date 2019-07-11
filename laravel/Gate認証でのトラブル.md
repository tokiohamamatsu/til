# Gate認証でのトラブル

- ログインは担当者マスタをもとに行う
- クレデンシャルは担当者CDとパスワード
- 担当者マスタの権限フラグでロールを設定
  - None : ログイン不可
  - User：一般ユーザー
  - PowerUser : 管理者

という状況でGateを使い認証を設定したところNoneのユーザーでログインしたところ403が表示された。

## エラーの時に表示されるページを変えたい

認証時に権限flgを確認し権限flgが0の時403errorがでる、この時403errorページではなく認証画面に戻りたい

errorページが出た時、ログイン画面にリダイレクトしたいので下記を実行してみた

### 実行したこと

Handler.phpに下記を記述

```php
public function render($request, Exception $exception)
    {
        if($this->isHttpException($exception)){
            if($exception->getStatusCode()==403){
                Auth::logout();
                return redirect()->route('login');
            }
        }
        return parent::render($request, $exception);
    }
```

#### 参考

[Laravel5: エラーページを共通化〜どんなステータスコードでもどんと来い！ \- Qiita](https://qiita.com/M_Ishikawa/items/1f0d72fc93286109464e)

#### 結果

効果なし

そもそもerrorページはこの際関係ないのかもしれない

次にerrorページが出てしまうならページごとかえればいいと思い下記を実行した

## 実行したことその２

- resources/views/errorsを作成
- errorsフォルダの中に403.blade.phpを作成
- 403.blade.php内を認証画面と同じにする

### 参考

[Laravelで独自の動的エラーページ（404/503 etc）を手早く作成する（多言語対応も）](https://www.ritolab.com/)

### 結果

認証画面が出たが認証すると認証画面に戻る

## 　細分化して考える

今やろうとしていることは

>1. ログインページでログイン
>2. Authミドルウェアで認証
    - OKの場合　行きたいページにリダイレクト
    - NGの場合　ログイン画面に戻る
>3. リダイレクト先でGateを使い権限の確認
    - OKの場合　そのまま
    - NGの場合　権限がないので403errorが出る
       -  **ログイン画面に戻そうとしている**

となる。

しかし、細分化してみて考えると**権限がないのに認証できているのがおかしい**ことに気づいた

なので、そもそも認証の部分で権限フラグを判定させて

>1. ログインページでログイン
>2. Authミドルウェアで認証　**ログイン権限がない場合はここでNGを出す**
    - OKの場合　行きたいページにリダイレクト
    - NGの場合　ログイン画面に戻る
>3. リダイレクト先でGateを使い権限の確認　**権限があるはずなのでOKが出るはず**
    - OKの場合　そのまま

としたい


[認証 5\.8 Laravel](https://readouble.com/laravel/5.8/ja/authentication.html) に認証条件を追加することができると書いてあったので認証の条件に権限flgを追加しようとし下記のコードを書いた

LoginController.php
```php
public function authenticate(Request $request)
{
    $credentials = $request->only('担当者CD','password');
    if (Auth::attempt(['担当者CD'=>$credentials['担当者CD'],'password'=>$credentials['password'],'権限flg'=>1])) {
        return redirect()->intended('home');
    }
}
```

しかしこのコードではうまくいかなかった,調べた結果 [php \- overridden authenticated method in Login Controller doesn't work \- Stack Overflow](https://stackoverflow.com/questions/50474763/overridden-authenticated-method-in-login-controller-doesnt-work)に同じような現象のことが書いてあった、原因はauthenticate関数をオーバーライドしていると思っていたからだ、なので書いてある解決したコードをもとに上記のコードを下記に書き換えた

```php
public function login(Request $request)
{
    $credentials = $request->only('担当者CD','password');
    if (Auth::attempt(['担当者CD'=>$credentials['担当者CD'],'password'=>$credentials['password'],'権限flg'=>[1,2]])) {
        return $this->sendLoginResponse($request);
    }else{
        // return $this->sendFailedLoginResponse($request, 'auth.failed_status');
        return view('auth.login');
    }
}
```

### 結果

権限による認証ができた

## Gateの使い道

これまでの結果を踏まえてGateは認証に使うのではなく認可に使う事を学んだ