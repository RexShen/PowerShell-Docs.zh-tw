---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-information?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Information
ms.openlocfilehash: 9fe1e66cbd8ae55e0a26d9702998564dcd7f9450
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208496"
---
# Write-Information

## 概要

指定 PowerShell 如何處理命令的資訊串流資料。

## SYNTAX

```
Write-Information [-MessageData] <Object> [[-Tags] <String[]>] [<CommonParameters>]
```

## DESCRIPTION

`Write-Information`Cmdlet 會指定 PowerShell 如何處理命令的資訊串流資料。

Windows PowerShell 5.0 引進了新的結構化資訊串流。 您可以使用此資料流程在腳本及其呼叫端或主應用程式之間傳輸結構化資料。
`Write-Information` 可讓您將參考用訊息新增至資料流程，並指定 PowerShell 如何處理命令的資訊串流資料。 資訊串流也適用于 `PowerShell.Streams` 、作業和排程工作。

> [!NOTE]
> 資訊資料流程未遵循在其訊息前面加上 "[Stream Name]：" 的標準慣例。 這是為了簡潔和 visual cleanliness。

`$InformationPreference`喜好設定變數值會決定您所提供的訊息是否 `Write-Information` 會顯示在腳本作業的預期位置。 因為這個變數的預設值是 `SilentlyContinue` ，預設不會顯示資訊訊息。 如果您不想要變更的值 `$InformationPreference` ，可以藉由將一般參數新增至您的命令來覆寫它的值 `InformationAction` 。 如需詳細資訊，請參閱 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md) 和 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

> [!NOTE]
> 從 Windows PowerShell 5.0 開始，是的包裝函式，可 `Write-Host` `Write-Information` 讓您用 `Write-Host` 來發出輸出至資訊串流。 這可讓您 **捕捉** 或 **隱藏** 使用撰寫的資料， `Write-Host` 同時保留回溯相容性。 如需詳細資訊，請參閱 [寫入主機](Write-Host.md)

`Write-Information` 也是 PowerShell 5.x 中支援的工作流程活動。

## 範例

### 範例 1：寫入 Get- 結果的資訊

在此範例中，您會在執行命令之後顯示參考用訊息「取得您的功能！」， `Get-WindowsFeature` 以尋找名稱值開頭為 ' p ' 的所有功能。
因為 `$InformationPreference` 變數仍然設定為預設值，所以 `SilentlyContinue` 您要加入 `InformationAction` 參數來覆寫 `$InformationPreference` 該值，並顯示訊息。 此 `InformationAction` 值為 Continue，表示會顯示您的訊息，但腳本或命令會繼續（如果尚未完成）。

```powershell
Get-WindowsFeature -Name p*
Write-Information -MessageData "Got your features!" -InformationAction Continue
```

```Output
Display Name                                            Name                       Install State
------------                                            ----                       -------------
[ ] Print and Document Services                         Print-Services                 Available
    [ ] Print Server                                    Print-Server                   Available
    [ ] Distributed Scan Server                         Print-Scan-Server              Available
    [ ] Internet Printing                               Print-Internet                 Available
    [ ] LPD Service                                     Print-LPD-Service              Available
[ ] Peer Name Resolution Protocol                       PNRP                           Available
[X] Windows PowerShell                                  PowerShellRoot                 Installed
    [X] Windows PowerShell 5.0                          PowerShell                     Installed
    [ ] Windows PowerShell 2.0 Engine                   PowerShell-V2                    Removed
    [X] Windows PowerShell ISE                          PowerShell-ISE                 Installed
Got your features!
```

### 範例 2︰寫入資訊並加以標記

在此範例中，您會使用 `Write-Information` 來讓使用者知道，他們在執行目前的命令之後，必須執行另一個命令。 此範例會在告知性訊息中新增 Instructions 標記。 執行此命令之後，如果您要針對已標記 Instructions 的訊息搜尋資訊資料流，則此處指定的訊息會位於結果之中。

```powershell
$message = "To filter your results for PowerShell, pipe your results to the Where-Object cmdlet."
Get-WindowsFeature -Name p*
Write-Information -MessageData $message -Tags "Instructions" -InformationAction Continue
```

```Output
Display Name                                            Name                       Install State
------------                                            ----                       -------------
[ ] Print and Document Services                         Print-Services                 Available
    [ ] Print Server                                    Print-Server                   Available
    [ ] Distributed Scan Server                         Print-Scan-Server              Available
    [ ] Internet Printing                               Print-Internet                 Available
    [ ] LPD Service                                     Print-LPD-Service              Available
[ ] Peer Name Resolution Protocol                       PNRP                           Available
[X] Windows PowerShell                                  PowerShellRoot                 Installed
    [X] Windows PowerShell 5.0                          PowerShell                     Installed
    [ ] Windows PowerShell 2.0 Engine                   PowerShell-V2                    Removed
    [X] Windows PowerShell ISE                          PowerShell-ISE                 Installed
To filter your results for PowerShell, pipe your results to the Where-Object cmdlet.
```

### 範例 3︰將資訊寫入檔案

在此範例中，您會使用程式碼將函式中的資訊資料流程重新導向至 `Info.txt` `6>` 。 當您開啟檔案時， `Info.txt` 您會看到「這裡的內容」。

```powershell
function Test-Info
{
    Get-Process P*
    Write-Information "Here you go"
}
Test-Info 6> Info.txt
```

### 範例4：傳遞物件以寫入資訊

在此範例中，您可以使用 `Write-Information` 從 `Get-Process` 通過多個管線的物件輸出中，寫入前10個最高 CPU 使用率的進程。

```powershell
Get-Process | Sort-Object CPU -Descending |
    Select-Object Id, ProcessName, CPU -First 10 |
        Write-Information -InformationAction Continue
```

```Output
@{Id=12692; ProcessName=chrome; CPU=39431.296875}
@{Id=21292; ProcessName=OUTLOOK; CPU=23991.875}
@{Id=10548; ProcessName=CefSharp.BrowserSubprocess; CPU=20546.203125}
@{Id=312848; ProcessName=Taskmgr; CPU=13173.1875}
@{Id=10848; ProcessName=SnapClient; CPU=7014.265625}
@{Id=9760; ProcessName=Receiver; CPU=6792.359375}
@{Id=12040; ProcessName=Teams; CPU=5605.578125}
@{Id=498388; ProcessName=chrome; CPU=3062.453125}
@{Id=6900; ProcessName=chrome; CPU=2546.9375}
@{Id=9044; ProcessName=explorer; CPU=2358.765625}
```

## PARAMETERS

### -MessageData

指定您想要在使用者執行指令碼或命令時顯示的告知性訊息。 為了獲得最佳結果，請以引號括住告知性訊息。

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases: Msg, Message

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Tags

指定簡單字串，您可以用來排序和篩選您已新增至資訊資料流程的訊息 `Write-Information` 。 這個參數的運作方式類似于中的 **Tags** 參數 `New-ModuleManifest` 。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.Object

`Write-Information` 接受傳送至資訊資料流程的管道物件。

## 輸出

### System.Management.Automation.InformationRecord

## 注意

## 相關連結

[about_Output_Streams](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)

[about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[Write-Debug](Write-Debug.md)

[Write-Host](Write-Host.md)

[Write-Information](Write-Information.md)

[Write-Progress](Write-Progress.md)

[Write-Verbose](Write-Verbose.md)

[Write-Warning](Write-Warning.md)

[Write-Output](Write-Output.md)
