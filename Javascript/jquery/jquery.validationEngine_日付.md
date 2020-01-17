# jquery.validationEngine

## 日付のバリデーション

- past

入力された日付が指定した日付以下かを判断する

nowを指定するとブラウザの日付を取得する。
```
<input value="" class="validate[required,custom[date],past[now]]" type="text" id="birthdate" name="birthdate" />
```

- future

入力された日付が指定した日付以上かを判断する

nowを指定するとブラウザの日付を取得する。
```
<input value="" class="validate[required,custom[date],future[now]]" type="text" id="appointment" name="appointment" />
```

### 参考

[jQuery\.validationEngine Plugin](http://posabsolute.github.io/jQuery-Validation-Engine/#futurenow-a-date-or-another-elements-name)