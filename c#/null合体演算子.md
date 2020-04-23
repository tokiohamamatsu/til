# 合体演算子

null合体演算子`??`は左側のオペランドがnullだった場合、右側のオペランドが処理される。

```c#
User user = TryGetUser(id) ?? DefaultUser();
```

上記の場合、TryGetUser()がnullを返すとDefaultUser()が実行される。

### 参考

[?? および ??= 演算子 \- C\# リファレンス \| Microsoft Docs](https://docs.microsoft.com/ja-jp/dotnet/csharp/language-reference/operators/null-coalescing-operator)

[C\# 8 で null 安全が導入されるらしいので、??（null 合体演算子）、?\. ?\[\]（null 条件演算子）を復習する \- Qiita](https://qiita.com/Nossa/items/1fd4881a0b97a5f32901)