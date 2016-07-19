---
title: "DSC Script 資源"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: e1d217b8e633779f55e195fbf80aeee83db01409
ms.openlocfilehash: ad2b20a3a977dc33b27f8a1096a2b48fcb3abe0e

---

# DSC Script 資源

 
> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

Windows PowerShell 預期狀態設定 (DSC) 的 **Script** 資源提供了在目標節點執行 Windows PowerShell 指令碼區塊的機制。 `Script`資源有`GetScript`、`SetScript` 和`TestScript` 屬性。 應該要對將會在每個目標節點上執行的指令碼區塊，設定這些屬性。 

`GetScript` 指令碼區塊應該會傳回代表目前節點狀態的雜湊表。 雜湊表必須只包含一個機碼 `Result`，且值必須是 `String` 類型。 不需要傳回任何內容。 DSC 不會對此指令碼區塊的輸出進行任何動作。

`TestScript` 指令碼區塊必須判斷目前的節點是否需要修改。 若該節點處於最新的狀態，應傳回 `$true`。 若節點的設定已過期，應傳回 `$false`，並使用 `SetScript` 指令碼區塊進行更新。 `TestScript` 指令碼區塊由 DSC 呼叫。

`SetScript` 指令碼區塊應修改該節點。 若 `TestScript` 區塊傳回 `$false`，會由 DSC 加以呼叫。

若您需要使用 `GetScript`、`TestScript` 或 `SetScript` 指令碼區塊中設定指令碼的變數，請使用 `$using:` 範圍 (請參閱下方範例)


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
| GetScript| 提供叫用 [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx) Cmdlet 時所執行的 Windows PowerShell 指令碼區塊。 這個區塊必須傳回雜湊表。 雜湊表必須只包含一個機碼 **Result**，且值必須是 **String** 類型。| 
| SetScript| 提供 Windows PowerShell 指令碼區塊。 當您叫用 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) Cmdlet 時，**TestScript** 區塊會先執行。 如果 **TestScript** 區塊傳回 **$false**，則 **SetScript** 區塊就會執行。 如果 **TestScript** 區塊傳回 **$true**，則 **SetScript** 區塊就會執行。| 
| TestScript| 提供 Windows PowerShell 指令碼區塊。 當您叫用 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) Cmdlet 時，這個區塊就會執行。 如果傳回 **$false**，SetScript 區塊就會執行。 如果傳回 **$true**，SetScript 區塊就不會執行。 **TestScript** 區塊也會在叫用 [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) Cmdlet 時執行。 不過，在此情況下，無論 TestScript 區塊傳回何值，**SetScript** 區塊都不會執行。 如果實際的設定符合目前的預期狀態設定，則 **TestScript** 區塊必須傳回 True；如果不符合，則為 False。 (目前的預期狀態設定是上次使用 DSC 的節點上施行的設定)。| 
| 認證| 如果需要認證，表示執行這個指令碼所要使用的認證。| 
| DependsOn| 表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 **ResourceName**，而它的類型是 **ResourceType**，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。

## 範例 1
```powershell
Script ScriptExample
{
    SetScript = { 
        $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
        $sw.WriteLine("Some sample string")
        $sw.Close()
    }
    TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
    GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }          
}
```

## 範例 2
```powershell
$version = Get-Content 'version.txt'
Script UpdateConfigurationVersion
{
    GetScript = { 
        $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
        return @{ 'Result' = "Version: $currentVersion" }
    }          
    TestScript = { 
        $state = GetScript
        if( $state['Version'] -eq $using:version )
        {
            Write-Verbose -Message ('{0} -eq {1}' -f $state['Version'],$using:version)
            return $true
        }
        Write-Verbose -Message ('Version up-to-date: {0}' -f $using:version)
        return $false
    }
    SetScript = { 
        $using:version | Set-Content -Path (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
    }
}
```

此資源正在將設定的版本寫入文字檔。 用戶端電腦上可以使用此版本，但在其餘節點則無法使用，所以必須以 PowerShell 的 `using` 範圍，將其傳遞至各個 `Script` 資源的指令碼區塊。 產生節點的 MOF 檔案時，會從用戶端電腦的文字檔讀取 `$version` 變數的值。 DSC 會以 `$version` 變數的值，取代各個指令碼區塊中的 `$using:version` 變數。




<!--HONumber=Jul16_HO1-->


