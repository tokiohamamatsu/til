# ORをまとめる

```SQL
SELECT *
FROM `Person`
WHERE `Age` = 10 OR `Age` = 35 OR `Age` = 40; -- ORが２つもあって気分が優れない… --
```

↓

```SQL
SELECT *
FROM `Person`
WHERE `Age` IN (10, 35, 40); -- INを使うと綺麗にまとめられる！ --
```

カラムが同じならINでひとつにまとめることができる

### 参考

[SQLで複数のORをまとめる書き方 \- Qiita](https://qiita.com/27ma4_ryusei/items/7ca9e87332cbd8ea0e03)