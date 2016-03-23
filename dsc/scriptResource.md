# DSC Script 資源

 
> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

Windows PowerShell 預期狀態設定 (DSC) 的 **Script** 資源提供了在目標節點執行 Windows PowerShell 指令碼區塊的機制。

## 語法

```
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## [內容]

|  屬性  |  描述   | 
|---|---| 
| GetScript| 提供叫用 [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx) Cmdlet 時所執行的 Windows PowerShell 指令碼區塊。 這個區塊必須傳回雜湊表。| 
| SetScript| 提供 Windows PowerShell 指令碼區塊。 當您叫用 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) Cmdlet 時，**TestScript** 區塊會先執行。 如果 **TestScript** 區塊傳回 **$false**，則 **SetScript** 區塊就會執行。 如果 **TestScript** 區塊傳回 **$true**，則 **SetScript** 區塊就會執行。| 
| TestScript| 提供 Windows PowerShell 指令碼區塊。 當您叫用 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) Cmdlet 時，這個區塊就會執行。 如果傳回 **$false**，SetScript 區塊就會執行。 如果傳回 **$true**，SetScript 區塊就不會執行。 **TestScript** 區塊也會在叫用 [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) Cmdlet 時執行。 不過，在此情況下，無論 TestScript 區塊傳回何值，**SetScript** 區塊都不會執行。 如果實際的設定符合目前的預期狀態設定，則 **TestScript** 區塊必須傳回 True；如果不符合，則為 False。 (目前的預期狀態設定是上次使用 DSC 的節點上施行的設定)。| 
| 認證| 如果需要認證，表示執行這個指令碼所要使用的認證。| 
| DependsOn| 表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 **ResourceName**，而它的類型是 **ResourceType**，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。

## 範例
```powershell
Script ScriptExample
{
    SetScript = { 
        $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
        $sw.WriteLine("Some sample string")
        $sw.Close()
    }
    TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
    GetScript = { <# This must return a hash table #> }          
}
```

<!--HONumber=Feb16_HO4-->
