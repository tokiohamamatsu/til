# CSV出力

```C#
 using System;
 using System.IO;
 using System.Text;
 
 
 public class Program
 {
  static void Main(string[] args)
  {
   string[] words = new string[] { ""りんご"", ""apple"", ""みかん"", ""orange"", ""バナナ"", ""banana"", ""もも"", ""peach"" };
   try
   {
    // ファイルを開く
    StreamWriter file = new StreamWriter(@""C:\test\test.csv"", false, Encoding.UTF8);
    for (int i = 0; i < words.Length; i += 2)
    {
     file.WriteLine(string.Format(""{0},{1}"", words[i], words[i + 1]));
    }
    file.Close();
    Console.WriteLine(""test.csvに書き込みました。"");
   }
   catch (Exception e)
   {
    Console.WriteLine(e.Message); // 例外検出時にエラーメッセージを表示
   }
  }
 }
```

`file.WriteLine(string.Format(""{0},{1}"", words[i], words[i + 1]));`の部分は要編集で、このままだと一行に２つしかデータが入らない

### 参考

[C\#でのCSVファイルの出力とは？方法をご紹介！ \| \.NETコラム](https://www.fenet.jp/dotnet/column/language/3790/)