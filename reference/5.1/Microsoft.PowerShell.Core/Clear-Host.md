---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
Module Name: Microsoft.PowerShell.Core
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/functions/clear-host?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Host
ms.openlocfilehash: 973d8c4952b99954c3f40bfd11966b754a0607b8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202344"
---
# Clear-Host

## 概要

清除主機程式中的顯示。

## SYNTAX

```
Clear-Host [<CommonParameters>]
```

## DESCRIPTION

`Clear-Host`函數會從目前的顯示中移除所有文字，包括可能累積的命令和輸出。 完成時，它會顯示命令提示字元。 您可以使用函式名稱或其別名 `cls` 。

`Clear-Host` 只會影響目前的顯示。 它不會刪除已儲存的結果，也不會從工作階段中移除任何項目。 工作階段特定項目 (例如變數和函式) 不會受到此函式的影響。

由於函式的行為 `Clear-Host` 取決於主機程式，因此 `Clear-Host` 在不同的主機程式中的運作方式可能不同。

## 範例

### 範例 1

```
# Before

PS C:\> Get-Process

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    843      33    14428      22556    99    17.41   1688 CcmExec
     44       6     2196       4964    52     0.23    692 conhost
    646      12     2332       4896    49     1.12    388 csrss
    189      11     2860       7084   114     0.66   2896 csrss
     78      11     1876       4008    42     0.22   4000 csrss
     76       7     1848       5064    54     0.08   1028 dwm
    610      41    23952      44048   208     4.40   2080 explorer
      0       0        0         24     0               0 Idle
    182      32     7692      15980    91     0.23   3056 LogonUI
    186      25     7832      16068    91     0.27   3996 LogonUI
   1272      32    11512      20432    58    25.07    548 lsass
    267      10     3536       6736    34     0.80    556 lsm
    137      17     3520       7472    61     0.05   1220 msdtc
    447      31    70316      84476   201 1,429.67    836 MsMpEng
    265      18     7136      15628   134     2.20   3544 msseces
    248      16     6476       4076    76     0.22   1592 NisSrv
    368      25    61312      65508   614     1.78    848 powershell
    101       8     2304       6624    70     0.64   3648 rdpclip
    258      15     6804      12156    50     2.65    536 services
...

PS C:\> cls
#After

PS C:>
```

此命令會使用的 `cls` 別名 `Clear-Host` 來清除目前的顯示。

## PARAMETERS

### CommonParameters
這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

您無法透過管道傳送輸入 `Clear-Host` 。

## 輸出

### 無

`Clear-Host` 不會產生任何輸出

## 注意

`Clear-Host` 是簡單的函式，而非 advanced 函數。 因此，您無法在命令中使用一般參數，例如 **Debug** `Clear-Host` 。

## 相關連結

[Get-Host](../Microsoft.PowerShell.Utility/Get-Host.md)

[Out-Host](Out-Host.md)

[Read-Host](../Microsoft.PowerShell.Utility/Read-Host.md)

[Write-Host](../Microsoft.PowerShell.Utility/Write-Host.md)
