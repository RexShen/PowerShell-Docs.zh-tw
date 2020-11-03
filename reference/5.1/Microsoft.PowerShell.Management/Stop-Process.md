---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-process?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Process
ms.openlocfilehash: 4efa22e8f2a7339e381d92270c1b127054c219cb
ms.sourcegitcommit: 11abf355ac545531c2b04217a08ebe6be609c0bb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2020
ms.locfileid: "93206288"
---
# Stop-Process

## 概要
停止一或多個執行中的處理程序。

## SYNTAX

### Id (預設值)

```
Stop-Process [-Id] <Int32[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Name

```
Stop-Process -Name <String[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InputObject

```
Stop-Process [-InputObject] <Process[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

**停止進程指令程式** 會停止一或多個正在執行的進程。
您可以依處理常式名稱或處理序識別碼 (PID) 來指定處理常式，或將處理常式物件傳遞至 **停止進程** 。
**停止進程** 只能在本機電腦上執行的進程上運作。

在 Windows Vista 和更新版本的 Windows 作業系統上，若要停止不是目前使用者擁有的處理常式，您必須使用 [以系統管理員身分執行] 選項啟動 PowerShell。
此外，除非您指定 *Confirm* 參數，否則系統不會提示您進行確認。

## 範例

### 範例1：停止進程的所有實例

```
PS C:\> Stop-Process -Name "notepad"
```

此命令會停止電腦上記事本處理程序的所有執行個體。
記事本的每個實例會在自己的進程中執行。
它會使用 *Name* 參數來指定處理常式，這些處理常式全都具有相同的名稱。
如果您要使用 *Id* 參數來停止相同的處理常式，則必須列出每個 [記事本] 實例的處理序識別碼。

### 範例2：停止進程的特定實例

```
PS C:\> Stop-Process -Id 3952 -Confirm -PassThru
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "notepad (3952)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):y
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
41       2      996       3212    31            3952 notepad
```

此命令會停止記事本處理程序的特定執行個體。
它會使用處理程序識別碼 3952 來識別處理程序。
*Confirm* 參數會指示 PowerShell 在停止進程之前提示您。
因為提示中包括程式 namein 的識別碼，所以這是最佳作法。
*PassThru* 參數會將處理常式物件傳遞給格式器以供顯示。
如果沒有這個參數，就不會在 **停止進程** 命令之後顯示。

### 範例3：停止進程並偵測到它已停止

```
PS C:\> calc
PS C:\> $p = Get-Process -Name "calc"
PS C:\> Stop-Process -InputObject $p
PS C:\> Get-Process | Where-Object {$_.HasExited}
```

這一系列的命令會啟動及停止 Calc 處理常式，然後偵測已經停止的進程。

第一個命令會啟動計算機的實例。

第二個命令使用 **Get 處理** 程式取得代表 Calc 處理常式的物件，然後將它儲存在 $p 變數中。

第三個命令會停止 Calc 處理常式。
它會使用 *InputObject* 參數將物件傳送至 **停止進程** 。

最後一個命令會取得電腦上所有之前在執行中但現在已經停止的處理程序。
它會使用 **取得處理常式** 來取得電腦上的所有處理常式。
管線運算子 (|) 將結果傳遞給 Where-Object Cmdlet，其會選取 [ **HasExited** ] 屬性的值 $True 的值。
**HasExited** 只是處理常式物件的一個屬性。
若要尋找所有屬性，請輸入 `Get-Process | Get-Member` 。

### 範例4：停止目前使用者所擁有的進程

```
PS C:\> Get-Process -Name "lsass" | Stop-Process

Stop-Process : Cannot stop process 'lsass (596)' because of the following error: Access is denied
At line:1 char:34
+ Get-Process -Name "lsass" | Stop-Process <<<<

[ADMIN]: PS C:\> Get-Process -Name "lsass" | Stop-Process

Warning!
Are you sure you want to perform this action?
Performing operation 'Stop-Process' on Target 'lsass(596)'
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
[ADMIN]: PS C:\> Get-Process -Name "lsass" | Stop-Process -Force
[ADMIN]: PS C:\>
```

這些命令會顯示使用 *Force* 來停止不是使用者所擁有之處理常式的效果。

第一個命令會使用 **Get 進程** 來取得 Lsass 進程。
管線運算子會將處理常式傳送至 **停止進程** ，以停止進程。
如範例輸出所示，第一個命令失敗並顯示「拒絕存取」訊息，因為只有電腦上系統管理員群組的成員才能停止此處理程式。

使用 [以系統管理員身分執行] 選項開啟 PowerShell 並重覆命令時，PowerShell 會提示您進行確認。

第二個命令指定 *Force* 來抑制提示。
因此，會在不需要確認的情況下停止處理程序。

## PARAMETERS

### -Force

在沒有提示確認的情況下停止指定的處理程序。
依預設， **停止進程** 會提示您確認，然後才會停止目前使用者未擁有的任何處理程式。

若要尋找處理常式的擁有者，請使用 `Get-CimInstance` Cmdlet 取得代表進程的 **Win32_Process** 物件，然後使用物件的 **GetOwner** 方法。

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

### -Id

指定要停止之進程的處理序識別碼。
若要指定多個識別碼，請使用逗號來分隔識別碼。
若要尋找處理程序的 PID，請輸入 `Get-Process`。

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InputObject

指定要停止的處理常式物件。
輸入包含物件的變數，或輸入可取得物件的命令或運算式。

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

指定要停止之處理常式的處理常式名稱。
您可以輸入多個處理常式名稱（以逗號分隔），或使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases: ProcessName

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -PassThru

傳回表示進程的物件。
根據預設，此 Cmdlet 不會產生任何輸出。

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

### System.Diagnostics.Process

您可以使用管線將處理程序物件傳送至此 Cmdlet。

## 輸出

### 無，系統診斷。進程

如果您指定 *PassThru* 參數，此 Cmdlet 會傳回代表已停止進程的 **處理常式** 物件。
否則，此 Cmdlet 不會產生任何輸出。

## 注意

* 您也可以使用內建的別名（ **kill** 和 **spps** ）來參考 **停止進程** 。 如需詳細資訊，請參閱 about_Aliases。

  您也可以在 Windows PowerShell 中使用 Windows Management Instrumentation (WMI) **Win32_Process** 物件的屬性和方法。
如需詳細資訊，請參閱 `Get-CimInstance` 和 WMI SDK。

* 停止處理常式時，請注意，停止處理常式可能會停止相依于進程的處理常式和服務。
在極端情況下，停止處理程序可能會停止 Windows。

## 相關連結

[Debug-Process](Debug-Process.md)

[Get-Process](Get-Process.md)

[Start-Process](Start-Process.md)

[Stop-Process](Stop-Process.md)

[Wait-Process](Wait-Process.md)
