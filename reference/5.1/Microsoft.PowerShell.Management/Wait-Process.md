---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/wait-process?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Process
ms.openlocfilehash: 6fe942f98183a3b185adf5781699bf41d03db920
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94343348"
---
# Wait-Process

## 概要
等候處理程序停止之後，才接受其他輸入。

## SYNTAX

### Name (預設值)

```
Wait-Process [-Name] <String[]> [[-Timeout] <Int32>] [<CommonParameters>]
```

### Id

```
Wait-Process [-Id] <Int32[]> [[-Timeout] <Int32>] [<CommonParameters>]
```

### InputObject

```
Wait-Process [[-Timeout] <Int32>] -InputObject <Process[]> [<CommonParameters>]
```

## DESCRIPTION

`Wait-Process`Cmdlet 會等候一或多個正在執行的進程在接受輸入之前停止。 在 PowerShell 主控台中，這個 Cmdlet 會抑制命令提示字元，直到處理程式停止為止。 您可以依處理常式名稱或處理序識別碼 (PID) 來指定處理常式，或使用管線將處理常式物件傳送至 `Wait-Process` 。

`Wait-Process` 只適用于在本機電腦上執行的處理常式。

## 範例

### 範例 1︰停止處理程序並等候

```
PS C:\> $nid = (Get-Process notepad).id
PS C:\> Stop-Process -Id $nid
PS C:\> Wait-Process -Id $nid
```

此範例會停止「記事本」處理程序，然後等候該處理程序停止之後，才繼續進行下一個命令。

第一個命令會使用 `Get-Process` Cmdlet 來取得「記事本」處理常式的識別碼。 它會將識別碼儲存在 `$nid` 變數中。

第二個命令會使用指令程式， `Stop-Process` 以儲存在中的識別碼來停止進程 `$nid` 。

第三個命令 `Wait-Process` 會使用來等候，直到「記事本」處理常式停止為止。 它會使用的 **Id** 參數 `Wait-Process` 來識別處理常式。

### 範例 2︰指定處理程序

```
PS C:\> $p = Get-Process notepad
PS C:\> Wait-Process -Id $p.id
PS C:\> Wait-Process -Name "notepad"
PS C:\> Wait-Process -InputObject $p
```

這些命令會顯示指定進程的三種不同方法 `Wait-Process` 。 第一個命令會取得「記事本」處理常式，並將它儲存在 `$p` 變數中。

第二個命令會使用 **Id** 參數、第三個命令會使用 **Name** 參數，而第四個命令會使用 **InputObject** 參數。

這些命令的結果皆相同，並且可交換使用。

### 範例 3︰等候處理程序一段指定的時間

```
PS C:\> Wait-Process -Name outlook, winword -Timeout 30
```

這個命令會等候 30 秒讓 Outlook 和 Winword 處理程序停止。 如果這兩個處理程序都沒有停止，則此 Cmdlet 會顯示一個非終止錯誤和命令提示字元。

## PARAMETERS

### -Id

指定處理程序的處理程序識別碼。 若要指定多個識別碼，請使用逗號來分隔識別碼。
若要尋找處理程序的 PID，請輸入 `Get-Process`。

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

藉由送出處理程序物件來指定處理程序。 輸入包含處理常式物件的變數，或輸入可取得處理常式物件的命令或運算式，例如 `Get-Process` Cmdlet。

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

指定處理程序的處理程序名稱。 若要指定多個名稱，請使用逗號來分隔名稱。 不支援萬用字元。

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

### -Timeout

指定此 Cmdlet 等候指定之處理程序停止的時間上限 (秒)。
當這個間隔時間過期時，此命令會顯示一個非終止錯誤，當中列出仍在執行的處理程序，然後結束等候。 預設是沒有逾時。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.Diagnostics.Process

您可以使用管線將處理程序物件傳送至此 Cmdlet。

## 輸出

### None

此 Cmdlet 不會產生任何輸出。

## 注意

這個 Cmdlet 會使用 **WaitForExit** 方法來 **處理** 類別。

## 相關連結

[Debug-Process](Debug-Process.md)

[Get-Process](Get-Process.md)

[Start-Process](Start-Process.md)

[Stop-Process](Stop-Process.md)

[Wait-Process](Wait-Process.md)
