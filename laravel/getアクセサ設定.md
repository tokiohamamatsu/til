# getアクセサ設定

アクセサは`get属性名Attribute`で設定できる


例
```php
<?php

namespace App;

use Illuminate\Database\Eloquent\Model;

class User extends Model
{
    /**
     * ユーザーのファーストネームを取得
     *
     * @param  string  $value
     * @return string
     */
    public function getFirstNameAttribute($value)
    {
        return ucfirst($value);
    }
}
```

first_nameにアクセスするとfirst_nameの処理が呼び出される。

```php
$user = App\User::find(1);

$firstName = $user->first_name;
```

### 参考

[Eloquent：ミューテタ 5\.6 Laravel](https://readouble.com/laravel/5.6/ja/eloquent-mutators.html)