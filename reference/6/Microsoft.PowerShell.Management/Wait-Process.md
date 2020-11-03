---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/wait-process?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Process
ms.openlocfilehash: 97b29f13fd1106a04204f97f02d82e9760fa41ae
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202388"
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

**Wait-Process** Cmdlet 會等候一或多個正在執行的處理程序停止之後，才會接受輸入。
在 PowerShell 主控台中，這個 Cmdlet 會抑制命令提示字元，直到處理程式停止為止。
您可以依處理程序名稱或處理程序識別碼 (PID) 來指定處理程序，或使用管道將處理程序物件傳送至 **Wait-Process** 。

**Wait-Process** 只適用於正在本機電腦上執行的處理程序。

## 範例

### 範例 1︰停止處理程序並等候

```
PS C:\> $nid = (Get-Process notepad).id
PS C:\> Stop-Process -Id $nid
PS C:\> Wait-Process -Id $nid
```

此範例會停止「記事本」處理程序，然後等候該處理程序停止之後，才繼續進行下一個命令。

第一個命令會使用 **Get-Process** Cmdlet，來取得「記事本」處理程序的識別碼。
它會將識別碼儲存於 $nid 變數中。

第二個命令會使用 Stop-Process Cmdlet，來停止識別碼儲存於 $nid 中的處理程序。

第三個命令會使用 **Wait-Process** 來等候，直到「記事本」處理程序停止為止。
它會使用 **Wait-Process** 的 *Id* 參數來識別處理程序。

### 範例 2︰指定處理程序

```
PS C:\> $p = Get-Process notepad
PS C:\> Wait-Process -Id $p.id
PS C:\> Wait-Process -Name "notepad"
PS C:\> Wait-Process -InputObject $p
```

這些命令示範三種將處理程序指定給 **Wait-Process** 的不同方法。
第一個命令會取得「記事本」處理程序，並將它儲存於 $p 變數中。

第二個命令會使用 *Id* 參數、第三個命令會使用 *Name* 參數，而第四個命令會使用 *InputObject* 參數。

這些命令的結果皆相同，並且可交換使用。

### 範例 3︰等候處理程序一段指定的時間

```
PS C:\> Wait-Process -Name outlook, winword -Timeout 30
```

這個命令會等候 30 秒讓 Outlook 和 Winword 處理程序停止。
如果這兩個處理程序都沒有停止，則此 Cmdlet 會顯示一個非終止錯誤和命令提示字元。

## PARAMETERS

### -Id

指定處理程序的處理程序識別碼。
若要指定多個識別碼，請使用逗號來分隔識別碼。
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

藉由送出處理程序物件來指定處理程序。
輸入包含處理程序物件的變數，或輸入可取得處理程序物件的命令或運算式，例如 Get-Process Cmdlet。

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

指定處理程序的處理程序名稱。
若要指定多個名稱，請使用逗號來分隔名稱。
不支援萬用字元。

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
當這個間隔時間過期時，此命令會顯示一個非終止錯誤，當中列出仍在執行的處理程序，然後結束等候。
預設是沒有逾時。

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

### 無

此 Cmdlet 不會產生任何輸出。

## 注意

* 此 Cmdlet 會使用 System.Diagnostics.Process 類別的 **WaitForExit** 方法。 如需有關這個方法的詳細資訊，請參閱 Microsoft .NET Framework SDK。

*

## 相關連結

[Debug-Process](Debug-Process.md)

[Get-Process](Get-Process.md)

[Start-Process](Start-Process.md)

[Stop-Process](Stop-Process.md)

[Wait-Process](Wait-Process.md)
