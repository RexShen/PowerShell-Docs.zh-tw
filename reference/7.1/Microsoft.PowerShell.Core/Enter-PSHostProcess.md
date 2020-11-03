---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pshostprocess?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enter-PSHostProcess
ms.openlocfilehash: 14f6173e318c6abd223ddff85a3694cfaac75c93
ms.sourcegitcommit: 9dddf1d2e91ebcd347fcfb7bf6ef670d49a12ab7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "93205771"
---
# Enter-PSHostProcess

## 概要
連線到互動式工作階段並進入具本機處理程序的互動式工作階段。

## SYNTAX

### ProcessIdParameterSet (預設值)

```
Enter-PSHostProcess [-Id] <Int32> [[-AppDomainName] <String>] [<CommonParameters>]
```

### ProcessParameterSet

```
Enter-PSHostProcess [-Process] <Process> [[-AppDomainName] <String>] [<CommonParameters>]
```

### ProcessNameParameterSet

```
Enter-PSHostProcess [-Name] <String> [[-AppDomainName] <String>] [<CommonParameters>]
```

### PSHostProcessInfoParameterSet

```
Enter-PSHostProcess [-HostProcessInfo] <PSHostProcessInfo> [[-AppDomainName] <String>]
 [<CommonParameters>]
```

### PipeNameParameterSet

```
Enter-PSHostProcess -CustomPipeName <String> [<CommonParameters>]
```

## DESCRIPTION

指令 `Enter-PSHostProcess` 程式會連接到具有本機進程的互動式會話並進入其中。 從 PowerShell 6.2 開始，非 Windows 平臺支援此 Cmdlet。

遠端互動式會話會在已執行 PowerShell 的現有進程中執行，而不是建立新的進程來裝載 PowerShell 並執行遠端會話。 當您在指定的處理常式上與遠端會話進行互動時，您可以列舉執行中的執行空間，然後藉由執行或來選取要進行偵錯工具的執行時間 `Debug-Runspace` `Enable-RunspaceDebug` 。

您要輸入的進程必須將 PowerShell 裝載 ( # A0) 。
您在找到處理序的電腦上必須是 Administrators 群組的成員，或者您必須是執行啟動處理序之指令碼的使用者。

選取要進行偵錯的 Runspace 之後，如果該 Runspace 目前正在執行命令，或已在偵錯工具中停止，就會為該 Runspace 開啟遠端偵錯工作階段。 然後您可以使用對其他遠端工作階段指令碼進行偵錯相同的方式對 Runspace 指令碼進行偵錯。

與偵錯工作階段中斷，然後執行兩次 exit 中斷具處理程序的互動式工作階段，或在現有的偵錯工具執行 quit 命令停止指令碼執行。

如果您使用 **Name** 參數指定處理程序，而且只找到一個具指定名稱的處理程序，就會進入該處理程序。 如果找到一個以上具有指定名稱的進程，則 PowerShell 會傳回錯誤，並列出以指定名稱找到的所有進程。

為了支援連接到遠端電腦上的處理常式，已 `Enter-PSHostProcess` 在指定的遠端電腦上啟用 Cmdlet，讓您可以附加至遠端 PowerShell 會話內的本機進程。

## 範例

### 範例1：在 PowerShell ISE 進程中開始對執行時間進行偵錯工具

在此範例中，您會在 `Enter-PSHostProcess` powershell 主控台內執行以進入 POWERSHELL ISE 進程。 在產生的互動式會話中，您可以藉由執行來尋找您想要進行偵錯工具的運行空間 `Get-Runspace` ，然後再進行偵錯工具。

```
PS C:\> Enter-PSHostProcess -Name powershell_ise
[Process:1520]: PS C:\Test\Documents>

Next, get available runspaces within the process you have entered.
PS C:\> [Process:1520]: PS C:\>  Get-Runspace
Id    Name          InstanceId                               State           Availability
--    -------       -----------                              ------          -------------
1     Runspace1     2d91211d-9cce-42f0-ab0e-71ac258b32b5     Opened          Available
2     Runspace2     a3855043-cb16-424a-a616-685360c3763b     Opened          RemoteDebug
3     MyLocalRS     2236dbd8-2105-4dec-a15a-a27d0bfaacb5     Opened          LocalDebug
4     MyRunspace    771356e9-8c44-4b70-9de5-dd17cb41e48e     Opened          Busy
5     Runspace8     3e517382-a97a-49ba-9c3c-fd21f6664288     Broken          None

The runspace objects returned by Get-Runspace also have a NoteProperty called ScriptStackTrace of
the running command stack, if available.Next, debug runspace ID 4, that is running another user's
long-running script. From the list returned from Get-Runspace, note that the runspace state is
Opened, and Availability is Busy, meaning that the runspace is still running the long-running
script.

PS C:\> [Process:1520]: PS C:\>  (Get-Runspace -Id 4).ScriptStackTrace
Command                    Arguments                           Location
-------                    ---------                           --------
MyModuleWorkflowF1         {}                                  TestNoFile3.psm1: line 6
WFTest1                    {}                                  TestNoFile2.ps1: line 14
TestNoFile2.ps1            {}                                  TestNoFile2.ps1: line 22
<ScriptBlock>              {}                                  <No file>

Start an interactive debugging session with this runspace by running the Debug-Runspace cmdlet.

PS C:\> [Process: 1520]: PS C:\>  Debug-Runspace -Id 4
Hit Line breakpoint on 'C:\TestWFVar1.ps1:83'

At C:\TestWFVar1.ps1:83 char:1
+ $scriptVar = "Script Variable"
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[Process: 1520]: [RSDBG: 4]: PS C:\> >

After you are finished debugging, allow the script to continue running without the debugger attached
by running the exit debugger command. Alternatively, you can quit the debugger with the q or Stop
commands.

PS C:\> [Process:346]: [RSDBG: 3]: PS C:\> > exit
[Process:1520]: PS C:\>

When you are finished working in the process, exit the process by running the Exit-PSHostProcess
cmdlet. This returns you to the PS C:\> prompt.

PS C:\> [Process:1520]: PS C:\>  Exit-PSHostProcess
PS C:\>
```

## PARAMETERS

### -AppDomainName

如果省略，則指定要連接的應用程式功能變數名稱，使用 **DefaultAppDomain** 。 用 `Get-PSHostProcessInfo` 來顯示應用程式功能變數名稱。

```yaml
Type: System.String
Parameter Sets: ProcessIdParameterSet, ProcessParameterSet, ProcessNameParameterSet, PSHostProcessInfoParameterSet
Aliases:

Required: False
Position: 1
Default value: DefaultAppDomain
Accept pipeline input: False
Accept wildcard characters: False
```

### -HostProcessInfo

指定可使用 PowerShell 連接的 **exit-pshostprocessinfo** 物件。 使用 `Get-PSHostProcessInfo` 取得物件。

```yaml
Type: Microsoft.PowerShell.Commands.PSHostProcessInfo
Parameter Sets: PSHostProcessInfoParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Id

依處理序識別碼指定處理程序。 若要取得處理序識別碼，請執行 `Get-Process` Cmdlet。

```yaml
Type: System.Int32
Parameter Sets: ProcessIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

依處理程序名稱指定處理程序。 若要取得處理常式名稱，請執行 `Get-Process` Cmdlet。 您也可以從 [工作管理員] 中處理程序的 [內容] 對話方塊取得處理程序名稱。

```yaml
Type: System.String
Parameter Sets: ProcessNameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Process

依處理程序物件指定處理程序。 使用此參數最簡單的方式是儲存命令的結果，此 `Get-Process` 命令會傳回您要在變數中輸入的進程，然後將變數指定為此參數的值。

```yaml
Type: System.Diagnostics.Process
Parameter Sets: ProcessParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -CustomPipeName

取得或設定要連接的自訂具名管道名稱。 這通常會與一起使用 `pwsh -CustomPipeName` 。

此參數是在 PowerShell 6.2 中引進。

```yaml
Type: System.String
Parameter Sets: PipeNameParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.Diagnostics.Process

## 輸出

## 注意

`Enter-PSHostProcess` 無法輸入您執行命令所在的 PowerShell 會話的處理常式。 不過，您可以輸入另一個 PowerShell 會話的處理常式，或輸入與執行中的會話相同的時間執行的 PowerShell ISE 會話 `Enter-PSHostProcess` 。

`Enter-PSHostProcess` 只能輸入裝載 PowerShell 的處理常式。 也就是說，他們已載入 PowerShell 引擎。

若要從進程內結束處理常式，請輸入 **exit** ，然後按 <kbd>enter</kbd>。

在 PowerShell 7.1 之前，透過 SSH 進行遠端處理不支援第二躍點遠端工作階段。 這項功能僅限於使用 WinRM 的工作階段。 PowerShell 7.1 可讓 `Enter-PSSession` 與 `Enter-PSHostProcess` 在任何互動式遠端工作階段中作業。

## 相關連結

[Exit-PSHostProcess](Exit-PSHostProcess.md)

[Get-PSHostProcessInfo](Get-PSHostProcessInfo.md)

