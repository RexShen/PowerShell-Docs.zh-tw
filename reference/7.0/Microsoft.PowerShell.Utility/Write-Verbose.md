---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-verbose?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Verbose
ms.openlocfilehash: 34e8d6edd7199921254a3835a9f13b6331c2d26e
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208479"
---
# Write-Verbose

## 概要
將文字寫入詳細資訊訊息串流。

## SYNTAX

```
Write-Verbose [-Message] <String> [<CommonParameters>]
```

## DESCRIPTION

Cmdlet 會將 `Write-Verbose` 文字寫入 PowerShell 中的詳細資訊訊息串流。 一般而言，詳細資訊訊息串流是用來提供更深入的命令處理相關資訊。

根據預設，不會顯示詳細資訊訊息串流，但您可以變更變數的值 `$VerbosePreference` 或在任何命令中使用 **verbose** 一般參數來顯示它。

## 範例

### 範例1：寫入狀態訊息

```powershell
Write-Verbose -Message "Searching the Application Event Log."
Write-Verbose -Message "Searching the Application Event Log." -Verbose
```

這些命令會使用 `Write-Verbose` Cmdlet 來顯示狀態訊息。 根據預設，不會顯示訊息。

第二個命令會使用 **verbose** 一般參數，其會顯示任何詳細資訊訊息，不論變數的值為何 `$VerbosePreference` 。

### 範例2：設定 $VerbosePreference 並寫入狀態訊息

```powershell
$VerbosePreference = "Continue"
Write-Verbose "Copying file $filename"
```

這些命令會使用 `Write-Verbose` Cmdlet 來顯示狀態訊息。 根據預設，不會顯示訊息。

第一個命令會將 Continue 的值指派給 `$VerbosePreference` 喜好設定變數。 預設值會 `SilentlyContinue` 抑制詳細資訊訊息。 第二個命令寫入詳細資訊訊息。

## PARAMETERS

### -Message

指定要顯示的訊息。 這是必要參數。 您也可以使用管線將訊息字串傳送至 `Write-Verbose` 。

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

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

### System.String

您可以使用管線將包含訊息的字串傳送至 `Write-Verbose` 。

## 輸出

### 無

`Write-Verbose` 只寫入詳細資訊訊息串流。

## 注意

- 只有在此命令使用 **Verbose** 一般參數時，才會傳回詳細資訊訊息。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。
- 在 Windows PowerShell 背景工作和遠端命令中， `$VerbosePreference` 工作會話和遠端會話中的變數會決定預設是否顯示詳細資訊訊息。
  如需變數的詳細資訊 `$VerbosePreference` ，請參閱 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)。

## 相關連結

[about_Output_Streams](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[Write-Debug](Write-Debug.md)

[Write-Error](Write-Error.md)

[Write-Host](Write-Host.md)

[Write-Information](Write-Information.md)

[Write-Output](Write-Output.md)

[Write-Progress](Write-Progress.md)

[Write-Warning](Write-Warning.md)
