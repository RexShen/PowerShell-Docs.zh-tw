# Import-DscResource 關鍵字支援 -ModuleVersion 參數

我們將新的參數新增至撰寫 DSC 設定時可用的 `Import-DscResource` 動態關鍵字。 設定作者現在可以指定要從哪個模組版本中載入 DSC 資源。 新關鍵字的語法為︰

```powershell
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>] [-ModuleVersion <ModuleVersion>]
```

* **名稱**︰要匯入的一個或多個資源名稱。
* **ModuleName**︰要匯入之一個或多個模組的名稱或 ModuleSpecification 物件。
* **ModuleVersion**︰要匯入的模組版本。 如果使用了的話，ModuleName 必須只以名稱代表一個模組。 

在 Windows PowerShell ISE 中，它和 IntelliSense 一同顯示：

![](../images/Import-DscResource-Modversion.jpg)

**注意：**`–ModuleVersion` 參數只能搭配 `–ModuleName` 參數一起使用。 它不能搭配僅以 `–Name` 參數作為名稱的資源名稱。

在這之前，載入 DSC 資源時指定模組版本的唯一方法是使用模組規格物件，例如︰ `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`



<!--HONumber=Jul16_HO1-->


