---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-warning?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Warning
ms.openlocfilehash: 52f060b0dd0364b1c930cd27a4bba280e467cff4
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208428"
---
# Write-Warning

## 概要
寫入警告訊息。

## SYNTAX

```
Write-Warning [-Message] <String> [<CommonParameters>]
```

## DESCRIPTION

Cmdlet 會將 `Write-Warning` 警告訊息寫入至 PowerShell 主機。 警告的回應取決於使用者的 `$WarningPreference` 變數值和 **WarningAction** 一般參數的使用方式。

## 範例

### 範例 1︰寫入警告訊息

這個命令會顯示訊息 "WARNING: This is only a test warning."

```powershell
Write-Warning "This is only a test warning."
```

### 範例 2︰將字串傳遞給 Write-Warning

此命令顯示您可以使用管線運算子 () 將 `|` 字串傳送至 `Write-Warning` 。
您可以將字串儲存在變數中（如這個命令所示），或直接使用管線將字串傳送至 `Write-Warning` 。

```powershell
$w = "This is only a test warning."
$w | Write-Warning
```

### 範例 3︰設定 $WarningPreference 變數和寫入警告

此範例顯示命令的變數值效果 `$WarningPreference` `Write-Warning` 。

```powershell
PS> $WarningPreference
Continue
PS> Write-Warning "This is only a test warning."
This is only a test warning.
PS> $WarningPreference = "SilentlyContinue"
PS> Write-Warning "This is only a test warning."
PS> $WarningPreference = "Stop"
PS> Write-Warning "This is only a test warning."
WARNING: This is only a test message.
Write-Warning : Command execution stopped because the shell variable "WarningPreference" is set to Stop.
At line:1 char:14
     + Write-Warning <<<<  "This is only a test message."
```

第一個命令會顯示變數的預設值 `$WarningPreference` ，也就是 `Continue` 。 因此，當您撰寫警告時，便會顯示該警告訊息，然後繼續執行。

當您變更變數的值時 `$WarningPreference` ，命令的效果會 `Write-Warning` 再次變更。 的值會 `SilentlyContinue` 抑制警告。 的值會 `Stop` 顯示警告，然後停止執行命令。

如需變數的詳細資訊 `$WarningPreference` ，請參閱 [about_Preference_Variables](../Microsoft.Powershell.Core/About/about_Preference_Variables.md)。

### 範例 4︰設定 WarningAction 參數和寫入警告

此範例顯示命令的 **WarningAction** 一般參數效果 `Write-Warning` 。 您可以使用 **WarningAction** 一般參數搭配任何 Cmdlet，來判斷 PowerShell 如何回應從該命令產生的警告。 **WarningAction** 一般參數會覆寫該 `$WarningPreference` 特定命令的唯一值。

```powershell
PS> Write-Warning "This is only a test warning." -WarningAction Inquire
WARNING: This is only a test warning.
Confirm
Continue with this operation?
 [Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"):
```

此命令會使用 `Write-Warning` Cmdlet 來顯示警告。 當 **WarningAction** 一般參數的值為 "Inquire" 時，會指示系統在命令顯示警告時提示使用者。

如需 **WarningAction** 一般參數的詳細資訊，請參閱 [about_CommonParameters](../Microsoft.Powershell.Core/About/about_CommonParameters.md)。

## PARAMETERS

### -Message
指定警告訊息。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Msg

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String

您可以使用管線將包含警告的字串傳送至 `Write-Warning` 。

## 輸出

### 無

`Write-Warning` 只寫入警告串流。 它不會產生任何其他輸出。

## 注意

變數的預設值 `$WarningPreference` 是 `Continue` ，它會顯示警告，然後繼續執行命令。 若要判斷喜好設定變數（例如）的有效值 `$WarningPreference` ，請將它設定為隨機字元的字串，例如 "abc"。 產生的錯誤訊息會列出有效的值。

## 相關連結

[about_Output_Streams](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[Write-Debug](Write-Debug.md)

[Write-Error](Write-Error.md)

[Write-Host](Write-Host.md)

[Write-Information](Write-Information.md)

[Write-Output](Write-Output.md)

[Write-Progress](Write-Progress.md)

[Write-Verbose](Write-Verbose.md)
