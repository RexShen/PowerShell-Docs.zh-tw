---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-debug?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Debug
ms.openlocfilehash: f4e29d06dc92d1d9aee61df7fd0c2de142fb1c7a
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208539"
---
# Write-Debug

## 概要
將偵錯訊息寫入主控台。

## SYNTAX

```
Write-Debug [-Message] <String> [<CommonParameters>]
```

## DESCRIPTION

`Write-Debug`Cmdlet 會從腳本或命令將 debug 訊息寫入至主機。

根據預設，偵錯工具訊息不會顯示在主控台中，但是您可以使用 **debug** 參數或變數來顯示它們 `$DebugPreference` 。

## 範例

### 範例1：瞭解 $DebugPreference

此範例會寫入 debug 訊息。

```powershell
Write-Debug "Cannot open file."
```

的預設值 `$DebugPreference` 為 **SilentlyContinue** 。 因此，此訊息不會顯示在主控台中。

### 範例2：變更 $DebugPreference 的值

此範例顯示變更變數值的效果 `$DebugPreference` 。 首先，我們會顯示的目前值 `$DebugPreference` ，並嘗試寫入偵錯工具訊息。 接著，我們會將的值變更 `$DebugPreference` 為 **Continue** ，讓您能夠顯示 debug 訊息。

```
PS> $DebugPreference
SilentlyContinue
PS> Write-Debug "Cannot open file."
PS>
PS> $DebugPreference = "Continue"
PS> Write-Debug "Cannot open file."
DEBUG: Cannot open file.
```

如需的詳細資訊 `$DebugPreference` ，請參閱 [about_Preference_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Preference_Variables)。

### 範例3：使用 Debug 參數覆寫 $DebugPreference

函式會將 `Test-Debug` 變數的值寫入 `$DebugPreference` 至 PowerShell 主機和偵錯工具資料流程。 在此範例中，我們使用 **Debug** 參數來覆寫此 `$DebugPreference` 值。

```powershell
function Test-Debug {
    [CmdletBinding()]
    param()
    Write-Debug ('$DebugPreference is ' + $DebugPreference)
    Write-Host ('$DebugPreference is ' + $DebugPreference)
}
```

```
PS> Test-Debug
$DebugPreference is SilentlyContinue

PS> Test-Debug -Debug
DEBUG: $DebugPreference is Continue
$DebugPreference is Continue
PS> $DebugPreference
SilentlyContinue
```

請注意， `$DebugPreference` 當您使用 **Debug** 參數時，會變更的值。 這項變更只會影響函數的範圍。 此值不會在函式之外受到影響。

如需有關 **Debug** 一般參數的詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## PARAMETERS

### -Message

指定要傳送至主控台的偵錯訊息。

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

您可以使用管線將包含 debug 訊息的字串傳送至 `Write-Debug` 。

## 輸出

### 無

`Write-Debug` 只寫入至 debug 資料流程。 它不會將任何物件寫入管線。

## 注意

## 相關連結

[about_Output_Streams](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[Write-Error](Write-Error.md)

[Write-Host](Write-Host.md)

[Write-Output](Write-Output.md)

[Write-Progress](Write-Progress.md)

[Write-Verbose](Write-Verbose.md)

[Write-Warning](Write-Warning.md)
