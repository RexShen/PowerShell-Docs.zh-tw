---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/debug-process?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Process
ms.openlocfilehash: 905f3522a071fdd3f59d020b734c689a59e68a63
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205127"
---
# Debug-Process

## 概要
偵錯本機電腦上執行的一或多個處理程序。

## SYNTAX

### Name (預設值)

```
Debug-Process [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Id

```
Debug-Process [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InputObject

```
Debug-Process -InputObject <Process[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

**調試** 程式 Cmdlet 會將偵錯工具附加到本機電腦上的一或多個執行中處理常式。
您可以依處理程序名稱或處理程序識別碼 (PID) 來指定處理程序，或使用管線將處理程序物件傳送至此 Cmdlet。

此 Cmdlet 會附加目前針對該處理程序註冊的偵錯工具。
開始使用這個 Cmdlet 之前，請先確認已下載並正確設定偵錯工具。

## 範例

### 範例 1︰將偵錯工具附加到電腦上的處理程序

```
PS C:\> Debug-Process -Name "Windows Powershell"
```

此命令將偵錯工具附加到電腦上的 PowerShell 處理程序。

### 範例 2︰將偵錯工具附加到以指定字串開頭的所有處理程序

```
PS C:\> Debug-Process -Name "SQL*"
```

此命令會將偵錯工具附加到名稱開頭為 SQL 的所有處理程序。

### 範例 3︰將偵錯工具附加到多個處理程序

```
PS C:\> Debug-Process "Winlogon", "Explorer", "Outlook"
```

此命令將偵錯工具附加到 Winlogon、Explorer 及 Outlook 處理程序。

### 範例 4︰將偵錯工具附加到多個處理程序識別碼

```
PS C:\> Debug-Process -Id 1132, 2028
```

此命令將偵錯工具附加到處理程序識別碼為 1132 和 2028 的處理程序。

### 範例 5︰使用 Get-Process 取得處理程序，然後將偵錯工具附加到其中

```
PS C:\> Get-Process "Windows PowerShell" | Debug-Process
```

此命令將偵錯工具附加到電腦上的 PowerShell 處理程序。
它會使用 **取得程式** Cmdlet 取得電腦上的 PowerShell 處理常式，並使用管線運算子 (|) 將進程傳送至 **Debug 進程** Cmdlet。

若要指定特定的 PowerShell 處理常式，請使用 **Get 進程** 的 ID 參數。

### 範例 6︰將偵錯工具附加到本機電腦上目前的處理程序

```
PS C:\> $PID | Debug-Process
```

此命令將偵錯工具附加到電腦上目前的 PowerShell 處理程序。

此命令會使用 $PID 自動變數，其中包含目前 PowerShell 進程的處理序識別碼。
然後，它會使用管線運算子 (|) 將處理序識別碼傳送至 **Debug 進程** Cmdlet。

如需 $PID 自動變數的詳細資訊，請參閱 about_Automatic_Variables。

### 範例7：將偵錯工具附加至使用 InputObject 參數的進程

```
PS C:\> $P = Get-Process "Windows PowerShell"
PS C:\> Debug-Process -InputObject $P
```

此命令將偵錯工具附加到本機電腦上的 PowerShell 處理程序。

第一個命令會使用 **取得程式** Cmdlet 取得電腦上的 PowerShell 處理常式。
它會將產生的處理程序物件儲存在 $P 變數中。

第二個命令會使用 **Debug-Process** 的 *InputObject* 參數，來提交 $P 變數中的處理程序物件。

## PARAMETERS

### -Id

指定要進行偵錯之處理程序的處理程序識別碼。
*Id* 參數名稱為選擇性。

若要尋找處理程序的處理程序識別碼，請輸入 `Get-Process`。

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases: PID, ProcessId

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InputObject

指定代表要進行偵錯之處理程序的處理程序物件。
輸入包含處理程序物件的變數，或輸入可取得處理程序物件的命令，例如 Get-Process Cmdlet。
您也可以使用管線將處理程序物件傳送至此 Cmdlet。

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

指定要進行偵錯之處理程序的名稱。
如果有多個處理程序具有相同的名稱，此 Cmdlet 會將偵錯工具附加到具有該名稱的所有處理程序。
*Name* 參數是選擇性的。

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases: ProcessName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Confirm

在執行 Cmdlet 前提示您確認。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

顯示執行 Cmdlet 後會發生的情況。
Cmdlet 並不會執行。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.Int32、System.Diagnostics.Process、System.String

您可以使用管線將處理程序識別碼 (Int32)、處理程序物件 (System.Diagnostics.Process) 或處理程序名稱 (String) 傳送至此 Cmdlet。

## 輸出

### 無

此 Cmdlet 不會產生任何輸出。

## 注意

* 此 Cmdlet 會使用 Windows Management Instrumentation (WMI) Win32_Process 類別的 AttachDebugger 方法。 如需此方法的詳細資訊，請參閱 MSDN library 中的 [AttachDebugger 方法](https://go.microsoft.com/fwlink/?LinkId=143640) 。

## 相關連結

[Debug-Process](Debug-Process.md)

[Get-Process](Get-Process.md)

[Start-Process](Start-Process.md)

[Stop-Process](Stop-Process.md)

[Wait-Process](Wait-Process.md)

