# Webルート外の静的ファイル読み込み

```c#
app.UseStaticFiles(new StaticFileOptions
{
    FileProvider = new PhysicalFileProvider(
           Path.Combine(builder.Environment.ContentRootPath, "MyStaticFiles")),
    RequestPath = "/StaticFiles"
});
```

'MyStaticFiles'は接続するパスでRequestPathはその略称みたいなもの

MyStaticFilesは`../MyStaticFiles`とすることができる。

### 参考

[ASP.NET Coreで静的コンテンツを提供する](https://qiita.com/gushwell/items/462fb61ff9025657256e)