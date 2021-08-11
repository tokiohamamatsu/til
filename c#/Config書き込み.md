# Config書き込み

```c#
public void LogSave()
{
    var configFile = @"test.config";
    var exeFileMap = new ExeConfigurationFileMap { ExeConfigFilename = configFile };
    var config = ConfigurationManager.OpenMappedExeConfiguration(exeFileMap, ConfigurationUserLevel.None);

    // config書き込み
    config.AppSettings.Settings["FileName"].Value = FileName;
    config.AppSettings.Settings["StartTime"].Value = StartTime;
    config.AppSettings.Settings["EndTime"].Value = EndTime;
    config.AppSettings.Settings["Class"].Value = Class;
    config.AppSettings.Settings["Code"].Value = Code;
    config.AppSettings.Settings["Reason"].Value = Reason;
    config.AppSettings.Settings["Approver"].Value = Approver;

    config.Save();

}
```

### 参考

[C\#でconfigファイルを使うやり方メモ \- Qiita](https://qiita.com/ikenohotori/items/10c3a79254ea52496904)