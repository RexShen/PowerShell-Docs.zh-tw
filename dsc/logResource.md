# DSC 記錄檔資源 

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

Windows PowerShell 預期狀態設定 (DSC) 的 __Log__ 資源會提供一個機制，將訊息寫入 Microsoft Windows 預期狀態設定/分析事件記錄檔。

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

## [內容]
|  屬性  |  描述   | 
|---|---| 
| 訊息| 表示要寫入 Microsoft Windows 預期狀態設定/分析事件記錄檔的訊息。| 
| DependsOn | 表示必須先執行另一個資源的設定，再寫入這個登入訊息。 例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 __ResourceName__，而它的類型是 __ResourceType__，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。| 

## 範例

下列範例示範如何將訊息加入 Microsoft Windows 預期狀態設定/分析事件記錄檔中。

> **注意**：如果您在設定此資源的情況下執行 [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx)，它一律會傳回 **$false**。

```powershell 
Log LogExample
{
    Message = "This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log."
} 
```

<!--HONumber=Feb16_HO4-->
