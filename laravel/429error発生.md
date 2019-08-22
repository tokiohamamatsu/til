# 429errorの発生

## 429errorとは

[429 Too Many Requests \- HTTP \| MDN](https://developer.mozilla.org/ja/docs/Web/HTTP/Status/429)

リクエストの制限に引っかかった時に発生するエラー

LaravelのMiddlewareにThrottleRequestsというものがありデフォルトで有効になっている。

app/Http/kernel.php

```php
protected $middlewareGroups = [
    'api' => [
        'throttle:60,1',
    ],
];

protected $routeMiddleware = [
    'throttle' => \Illuminate\Routing\Middleware\ThrottleRequests::class,
];
```

`throttle:60,1`の意味はリクエストの制限は1分間に60回まで

## ThrottleRequestsの中身

vendor/laravel/framework/src/Illuminate/Routing/Middleware/ThrottleRequests.php

```php
protected function resolveRequestSignature($request)
{
    if ($route = $request->route()) {
        return sha1($route->getDomain().'|'.$request->ip());
    }
}
```

ドメインとIPをキーにしてリクエスト回数をカウントしている

```php
protected function getHeaders($maxAttempts, $remainingAttempts, $retryAfter = null)
{
    $headers = [
        'X-RateLimit-Limit' => $maxAttempts,
        'X-RateLimit-Remaining' => $remainingAttempts,
    ];
}
```

Headerを見ればリクエスト回数の上限と残り回数が確認できる。

## Headerの中身

```php
$ curl -Is -X GET 'http://localhost/api/test' | grep RateLimit
X-RateLimit-Limit: 60 //上限
X-RateLimit-Remaining: 59 //残り
```

対策は`throttle:60`のところを別の数字に変える

### 参考

[Laravel5\.5 \+ Vue\.js で SPAサイトを作成したら、”429 Too Many Requests”が頻発した \- bitA Tech Blog](https://tech.bita.jp/article/11)

[429 \(Too Many Requests\)への対処法 \| TECH & LIFE in NAGOYA](https://techassist.jp/blog?id=6)