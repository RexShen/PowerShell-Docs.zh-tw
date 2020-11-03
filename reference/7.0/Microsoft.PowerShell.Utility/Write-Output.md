---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-output?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Output
ms.openlocfilehash: be2c506a928a96f66fd7318bdb0da1c57c5474b8
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208499"
---
# Write-Output

## 概要
將指定的物件傳送給管線中的下一個命令。 如果命令是管線中的最後一個命令，物件就會顯示在主控台中。

## SYNTAX

```
Write-Output [-InputObject] <PSObject[]> [-NoEnumerate] [<CommonParameters>]
```

## DESCRIPTION

`Write-Output`Cmdlet 會將指定的物件沿著管線向下傳送至下一個命令。
如果命令是管線中的最後一個命令，物件就會顯示在主控台中。

`Write-Output` 將物件沿著主要管線（也稱為「輸出資料流程」或「成功管線」）向下傳送。 若要將錯誤物件沿著錯誤管線向下傳送，請使用 Write-Error。

這個 Cmdlet 通常是在指令碼中用來在主控台上顯示字串及其他物件。 的其中一個內建別名， `Write-Output` 類似于 `echo` 使用的其他 shell `echo` ，預設行為是在管線結尾顯示輸出。 在 PowerShell 中，通常不需要在預設顯示輸出的實例中使用此 Cmdlet。 例如，`Get-Process | Write-Output` 相當於 `Get-Process`。 或者， `echo "Home directory: $HOME"` 可以撰寫， `"Home directory: $HOME"`

依預設，會 `Write-Output` 透過提供給 Cmdlet 的集合來列舉。 不過， `Write-Output` 也可以使用 **NoEnumerate** 參數，將集合以單一物件的形式傳遞至管線。

## 範例

### 範例1：取得物件並將它們寫入主控台

```powershell
$P = Get-Process
Write-Output $P
```

第一個命令會取得在電腦上執行的處理常式，並將它們儲存在 `$P` 變數中。

第二個和第三個命令會在主控台中顯示處理常式物件 `$P` 。

### 範例2：將輸出傳遞至另一個 Cmdlet

```powershell
Write-Output "test output" | Get-Member
```

此命令會將 "test output" 字串傳送至 `Get-Member` Cmdlet，以顯示 system.string 類別的成員 **System.String** ，示範此字串是沿著管線傳遞。

### 範例3：在輸出中隱藏列舉

```powershell
Write-Output 1,2,3 | Measure-Object
```

```Output
Count    : 3
...
```

```powershell
Write-Output 1,2,3 -NoEnumerate | Measure-Object
```

```Output
Count    : 1
...
```

此命令會新增 **NoEnumerate** 參數，以透過管線將集合或陣列視為單一物件。

## PARAMETERS

### -InputObject

指定要沿著管線向下傳送的物件。 輸入包含物件的變數，或輸入可取得物件的命令或運算式。

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -NoEnumerate

根據預設，此 `Write-Output` Cmdlet 一律會列舉其輸出。 **NoEnumerate** 參數會隱藏預設行為，並防止 `Write-Output` 列舉輸出。 如果命令是以括弧括住， **NoEnumerate** 參數就沒有任何作用，因為括弧會強制列舉。 例如， `(Write-Output 1,2,3)` 仍會列舉陣列。

> [!NOTE]
> 此參數僅適用于 PowerShell Core 6.2 和更新版本。 在較舊版本的 PowerShell Core 上，即使使用這個參數，仍會列舉集合。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.Management.Automation.PSObject

您可以透過管線將物件傳送至 `Write-Output` 。

## 輸出

### System.Management.Automation.PSObject

`Write-Output` 傳回提交為輸入的物件。

## 注意

## 相關連結

[about_Output_Streams](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[Tee-Object](Tee-Object.md)

[Write-Debug](Write-Debug.md)

[Write-Error](Write-Error.md)

[Write-Host](Write-Host.md)

[Write-Information](Write-Information.md)

[Write-Progress](Write-Progress.md)

[Write-Verbose](Write-Verbose.md)

[Write-Warning](Write-Warning.md)
