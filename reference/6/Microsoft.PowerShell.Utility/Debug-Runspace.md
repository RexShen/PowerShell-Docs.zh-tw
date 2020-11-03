---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/debug-runspace?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Runspace
ms.openlocfilehash: 96282d28249f28744cf7dff436fa2e6c601c10ca
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204675"
---
# Debug-Runspace

## 概要
啟動具有運行空間的互動式偵錯工具會話。

## SYNTAX

### RunspaceParameterSet (預設) 

```
Debug-Runspace [-Runspace] <Runspace> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NameParameterSet

```
Debug-Runspace [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### IdParameterSet

```
Debug-Runspace [-Id] <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceIdParameterSet

```
Debug-Runspace [-InstanceId] <Guid> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Debug-Runspace`Cmdlet 會啟動具有本機或遠端使用中運行空間的互動式偵錯工具。 您可以尋找您想要先執行的運行時， `Get-Process` 尋找與 PowerShell 相關聯的進程，然後 `Enter-PSHostProcess` 使用 **id** 參數中指定的處理序識別碼來附加至進程，然後 `Get-Runspace` 列出 PowerShell 主機進程內的執行程式。

當您選取要進行偵錯工具的執行時間時，如果執行時間目前正在執行命令或腳本，或腳本已在中斷點停止，則 PowerShell 會開啟該執行時間的遠端偵錯程式會話。 您可以用相同的方式，以調試遠端會話腳本的相同方式來偵測運行空間腳本。

如果您是執行進程之電腦的系統管理員，或您正在執行要進行偵錯工具的腳本，您只能附加至 PowerShell 主機進程。 此外，您無法輸入正在執行目前 PowerShell 會話的主機進程。 您只能輸入正在執行不同 PowerShell 會話的主機進程。

## 範例

### 範例1： Debug remote 運行空間

```
PS C:\> Get-Process -ComputerName "WS10TestServer" -Name "*powershell*"

Handles      WS(K)   VM(M)      CPU(s)    Id  ProcessName
-------      -----   -----      ------    --  -----------
    377      69912     63     2.09      2420  powershell
    399     123396    829     4.48      1152  powershell_ise

PS C:\> Enter-PSSession -ComputerName "WS10TestServer"
[WS10TestServer]:PS C:\> Enter-PSHostProcess -Id 1152
[WS10TestServer:][Process:1152]: PS C:\Users\Test\Documents> Get-Runspace

Id Name            ComputerName    Type          State         Availability
-- ----            ------------    ----          -----         ------------
 1 Runspace1       WS10TestServer  Remote        Opened        Available
 2 RemoteHost      WS10TestServer  Remote        Opened        Busy

PS C:\> [WS10TestServer][Process:1152]: PS C:\Users\Test\Documents> Debug-Runspace -Id 2

Hit Line breakpoint on 'C:\TestWFVar1.ps1:83'
At C:\TestWFVar1.ps1:83 char:1
+ $scriptVar = "Script Variable"
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
[Process:1152]: [RSDBG: 2]: PS C:\> >
```

在此範例中，您會對在遠端電腦上開啟的運行空間進行 WS10TestServer 的偵錯工具。 在命令的第一行中，您會在 `Get-Process` 遠端電腦上執行，並篩選 Windows PowerShell 的主機進程。 在此範例中，您想要將處理序識別碼1152（Windows PowerShell ISE 的主機進程）進行偵錯工具。

在第二個命令中，您會執行 `Enter-PSSession` 以開啟 WS10TestServer 上的遠端會話。 在第三個命令中，藉由執行來附加至遠端伺服器上執行的 Windows PowerShell ISE 主機進程， `Enter-PSHostProcess` 並指定您在第一個命令1152中取得之主機進程的識別碼。

在第四個命令中，您可以藉由執行來列出處理序識別碼為1152的可用執行空間 `Get-Runspace` 。
您會記下忙碌的運行空間的識別碼：它正在執行您想要進行偵錯工具的腳本。

在最後一個命令中，您會藉由新增 Id 參數，開始將執行腳本的已開啟執行時間（藉由執行 `Debug-Runspace` ，並依識別碼（2）識別 **Id** 執行時間）進行 TestWFVar1.ps1 的偵錯工具。 因為腳本中有一個中斷點，偵錯工具會開啟。

## PARAMETERS

### -Id

指定運行空間的識別碼。 您可以執行 `Get-Runspace` 以顯示運行時識別碼。

```yaml
Type: System.Int32
Parameter Sets: IdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InstanceId

依實例識別碼指定運行空間，這是您可以藉由執行來顯示的 GUID `Get-Runspace` 。

```yaml
Type: System.Guid
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

依名稱指定運行時。 您可以執行 `Get-Runspace` 以顯示執行空間的名稱。

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -運行時

指定運行時物件。 為此參數提供值最簡單的方式，就是指定包含已篩選命令之結果的變數 `Get-Runspace` 。

```yaml
Type: System.Management.Automation.Runspaces.Runspace
Parameter Sets: RunspaceParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

顯示執行 Cmdlet 後會發生的情況。 Cmdlet 並不會執行。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 系統管理。運行空間

您可以使用管線將命令的結果傳送 `Get-Runspace` 至 **Debug-運行空間。**

## 輸出

## 注意

`Debug-Runspace` 適用于處於開啟狀態的工作空間。 如果運行時狀態從 [開啟] 變更為另一個狀態，則會自動從執行清單中移除該執行空間。 只有當運行空間符合下列準則時，才會將它新增至執行清單。

- 如果是來自 Invoke 命令，則為。也就是說，它有 `Invoke-Command` GUID 識別碼。
- 如果來自 `Debug-Runspace` ，也就是它有 `Debug-Runspace` GUID 識別碼。
- 如果是來自 PowerShell 工作流程，而且其工作流程工作識別碼與目前作用中的偵錯工具工作流程工作識別碼相同。

## 相關連結

[about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md)

[Debug-Job](../Microsoft.PowerShell.Core/Debug-Job.md)

[Get-Runspace](Get-Runspace.md)

[Get-Process](../Microsoft.PowerShell.Management/Get-Process.md)

[Enter-PSHostProcess](../Microsoft.PowerShell.Core/Enter-PSHostProcess.md)

[Enter-PSSession](../Microsoft.PowerShell.Core/Enter-PSSession.md)
