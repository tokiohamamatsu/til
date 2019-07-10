# Gate認証でのトラブル

## エラーの時に表示されるページを変えたい

認証時に権限flgを確認し権限flgが0の時403errorがでる、この時403errorページではなく認証画面に戻りたい

## 実行したこと

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

### 参考

[Laravel5: エラーページを共通化〜どんなステータスコードでもどんと来い！ \- Qiita](https://qiita.com/M_Ishikawa/items/1f0d72fc93286109464e)

## 結果

# 効果なし

そもそもエラーページはこの際関係ないのかもしれない

## 実行したことその２

- resources/views/errorsを作成
- errorsフォルダの中に403.blade.phpを作成
- 403.blade.php内を認証画面と同じにする

### 参考

[Laravelで独自の動的エラーページ（404/503 etc）を手早く作成する（多言語対応も）](https://www.ritolab.com/)

## 結果

認証画面が出たが認証すると認証画面に戻る

