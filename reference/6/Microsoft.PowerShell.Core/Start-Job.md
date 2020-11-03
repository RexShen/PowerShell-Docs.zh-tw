---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/start-job?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Job
ms.openlocfilehash: 69cebe735e413b226bd40539df075bf3a49bce95
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204868"
---
# Start-Job

## 概要
啟動 PowerShell 背景工作。

## SYNTAX

### ComputerName (預設值)

```
Start-Job [-Name <String>] [-ScriptBlock] <ScriptBlock> [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>] [-RunAs32]
 [-PSVersion <Version>] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### DefinitionName

```
Start-Job [-DefinitionName] <String> [[-DefinitionPath] <String>] [[-Type] <String>]
 [<CommonParameters>]
```

### LiteralFilePathComputerName

```
Start-Job [-Name <String>] [-Credential <PSCredential>] -LiteralPath <String>
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>] [-RunAs32]
 [-PSVersion <Version>] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### FilePathComputerName

```
Start-Job [-Name <String>] [-Credential <PSCredential>] [-FilePath] <String>
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>] [-RunAs32]
 [-PSVersion <Version>] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

## DESCRIPTION

`Start-Job`Cmdlet 會在本機電腦上啟動 PowerShell 背景工作。

PowerShell 背景工作會執行命令，而不會與目前的會話互動。 當您啟動背景工作時，工作物件會立即傳回，即使作業需要花費很長的時間才能完成。 工作執行時，您可以在工作階段中繼續工作，而不需中斷。

工作物件包含工作的相關實用資訊，但是不包含工作結果。
當作業完成時，請使用 `Receive-Job` Cmdlet 來取得作業的結果。 如需背景工作的詳細資訊，請參閱 [about_Jobs](./About/about_Jobs.md)。

若要在遠端電腦上執行背景工作，請使用可在許多 Cmdlet 上使用的 **AsJob** 參數，或使用 `Invoke-Command` Cmdlet 在 `Start-Job` 遠端電腦上執行命令。 如需詳細資訊，請參閱 [about_Remote_Jobs](./About/about_Remote_Jobs.md)。

從 PowerShell 3.0 開始， `Start-Job` 可以啟動自訂工作類型的實例，例如排程工作。 如需如何使用 `Start-Job` 以自訂類型啟動作業的詳細資訊，請參閱工作類型功能的說明文件。

從 PowerShell 6.0 開始，您可以使用連字號 (`&`) 背景運算子來啟動作業。 背景運算子的功能類似于 `Start-Job` 。 這兩種啟動作業的方法都會建立 **PSRemotingJob** 工作物件。 如需使用連字號 () 的詳細資訊 `&` ，請參閱 [about_Operators](./about/about_operators.md#background-operator-)。

工作的預設工作目錄會進行硬式編碼。 Windows 預設值為 `$HOME\Documents` ，而 Linux 或 macOS 上的預設值為 `$HOME` 。 在背景工作中執行的腳本程式碼需要視需要管理工作目錄。

> [!NOTE]
> `Start-Job`在 powershell 裝載于其他應用程式（例如 powershell Azure Functions）的案例中，不支援使用建立跨進程背景工作。
>
> 這是設計的原因 `Start-Job` ，取決於 `pwsh` 在下可執行檔可執行檔 `$PSHOME` 背景工作，但是當應用程式裝載 powershell 時，它會直接使用 powershell NuGet SDK 套件，且不會隨之出 `pwsh` 貨。
>
> 此案例中的替代方式是 `Start-ThreadJob` 從模組 **[ThreadJob](https://www.powershellgallery.com/packages/ThreadJob)** 。

## 範例

### 範例1：啟動背景工作

此範例會啟動在本機電腦上執行的背景工作。

```powershell
Start-Job -ScriptBlock { Get-Process -Name pwsh }
```

```Output
Id  Name   PSJobTypeName   State     HasMoreData   Location    Command
--  ----   -------------   -----     -----------   --------    -------
1   Job1   BackgroundJob   Running   True          localhost   Get-Process -Name pwsh
```

`Start-Job` 使用 **ScriptBlock** 參數，以 `Get-Process` 背景工作的形式執行。 **Name** 參數指定尋找 PowerShell 處理常式 `pwsh` 。 當工作在背景中執行時，會顯示工作資訊，並將 PowerShell 返回提示。

若要查看作業的輸出，請使用 `Receive-Job` Cmdlet。 例如： `Receive-Job -Id 1` 。

### 範例2：使用背景運算子來啟動背景工作

這個範例會使用連字號 (`&`) 背景運算子，在本機電腦上啟動背景工作。 作業取得的結果與 `Start-Job` 範例1相同。

```powershell
Get-Process -Name pwsh &
```

```Output
Id    Name   PSJobTypeName   State       HasMoreData     Location      Command
--    ----   -------------   -----       -----------     --------      -------
5     Job5   BackgroundJob   Running     True            localhost     Microsoft.PowerShell.Man...
```

`Get-Process` 使用 **Name** 參數來指定 PowerShell 處理常式 `pwsh` 。 & 符號 (`&`) 會以背景工作的方式執行命令。 當工作在背景中執行時，會顯示工作資訊，並將 PowerShell 返回提示。

若要查看作業的輸出，請使用 `Receive-Job` Cmdlet。 例如： `Receive-Job -Id 5` 。

### 範例3：使用 Invoke-Command 啟動作業

此範例會在多部電腦上執行工作。 作業會儲存在變數中，並使用 PowerShell 命令列上的變數名稱來執行。

```powershell
$jobWRM = Invoke-Command -ComputerName (Get-Content -Path C:\Servers.txt) -ScriptBlock {
   Get-Service -Name WinRM } -JobName WinRM -ThrottleLimit 16 -AsJob
```

使用的作業 `Invoke-Command` 會建立並儲存在變數中 `$jobWRM` 。 `Invoke-Command` 使用 **ComputerName** 參數來指定執行作業的電腦。 `Get-Content` 從檔案取得伺服器名稱 `C:\Servers.txt` 。

**ScriptBlock** 參數指定可 `Get-Service` 取得 **WinRM** 服務的命令。 **JobName** 參數會指定作業的易記名稱，也就是 **WinRM** 。 **ThrottleLimit** 參數會將並行命令的數目限制為16。 **AsJob** 參數會啟動在伺服器上執行命令的背景工作。

### 範例4：取得作業資訊

此範例會取得作業的相關資訊，並顯示在本機電腦上執行之已完成工作的結果。

```powershell
$j = Start-Job -ScriptBlock { Get-WinEvent -Log System } -Credential Domain01\User01
$j | Select-Object -Property *
```

```Output
State         : Completed
HasMoreData   : True
StatusMessage :
Location      : localhost
Command       : Get-WinEvent -Log System
JobStateInfo  : Completed
Finished      : System.Threading.ManualResetEvent
InstanceId    : 27ce3fd9-40ed-488a-99e5-679cd91b9dd3
Id            : 18
Name          : Job18
ChildJobs     : {Job19}
PSBeginTime   : 8/8/2019 14:41:57
PSEndTime     : 8/8/2019 14:42:07
PSJobTypeName : BackgroundJob
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
Information   : {}
```

`Start-Job` 使用 **ScriptBlock** 參數來執行命令，以指定 `Get-WinEvent` 要取得 **系統** 記錄檔。 **Credential** 參數指定具有在電腦上執行作業許可權的網域使用者帳戶。 工作物件會儲存在變數中 `$j` 。

變數中的物件 `$j` 會向下傳送到管線 `Select-Object` 。 **Property** 參數會指定星號 (`*`) 來顯示所有工作物件的屬性。

### 範例5：以背景工作的形式執行腳本

在此範例中，本機電腦上的腳本會以背景工作的形式執行。

```powershell
Start-Job -FilePath C:\Scripts\Sample.ps1
```

`Start-Job` 使用 **FilePath** 參數來指定儲存在本機電腦上的腳本檔案。

### 範例6：使用背景工作取得處理常式

這個範例會使用背景工作，依名稱取得指定的進程。

```powershell
Start-Job -Name PShellJob -ScriptBlock { Get-Process -Name PowerShell }
```

`Start-Job` 使用 **Name** 參數來指定易記的作業名稱 **PShellJob** 。 **ScriptBlock** 參數指定 `Get-Process` 要取得名稱為 **PowerShell** 的進程。

### 範例7：使用背景工作來收集和儲存資料

此範例會啟動一個作業來收集大量的地圖資料，然後將它儲存在檔案中 `.tif` 。

```powershell
Start-Job -Name GetMappingFiles -InitializationScript {Import-Module MapFunctions} -ScriptBlock {
   Get-Map -Name * | Set-Content -Path D:\Maps.tif } -RunAs32
```

`Start-Job` 使用 **Name** 參數來指定易記的作業名稱 **GetMappingFiles** 。 **InitializationScript** 參數會執行匯入 **MapFunctions** 模組的腳本區塊。 **ScriptBlock** 參數會執行 `Get-Map` ，並將 `Set-Content` 資料儲存在 **Path** 參數所指定的位置。 **RunAs32** 參數會以32位的形式執行程式，即使是在64位的作業系統上也一樣。

### 範例8：將輸入傳遞給背景工作

這個範例會使用 `$input` 自動變數來處理輸入物件。 用 `Receive-Job` 來查看作業的輸出。

```powershell
Start-Job -ScriptBlock { Get-Content $input } -InputObject "C:\Servers.txt"
Receive-Job -Name Job45 -Keep
```

```Output
Server01
Server02
Server03
Server04
```

`Start-Job` 使用 **ScriptBlock** 參數搭配 `Get-Content` `$input` 自動變數執行。 `$input`變數會從 **InputObject** 參數取得物件。 `Receive-Job` 使用 **Name** 參數來指定作業並輸出結果。 **Keep** 參數會儲存工作輸出，以便在 PowerShell 會話期間再次查看。

### 範例9：使用 ArgumentList 參數來指定陣列

此範例使用 **ArgumentList** 參數來指定引數陣列。 陣列是以逗號分隔的進程名稱清單。

```powershell
Start-Job -ScriptBlock { Get-Process -Name $args } -ArgumentList powershell, pwsh, notepad
```

```Output
Id     Name      PSJobTypeName   State       HasMoreData     Location     Command
--     ----      -------------   -----       -----------     --------     -------
1      Job1      BackgroundJob   Running     True            localhost    Get-Process -Name $args
```

此 `Start-Job` Cmdlet 會使用 **ScriptBlock** 參數來執行命令。 `Get-Process` 使用 **Name** 參數來指定自動變數 `$args` 。 **ArgumentList** 參數會將處理常式名稱的陣列傳遞至 `$args` 。 程式會將 powershell、pwsh 和 notepad 等程式命名為在本機電腦上執行的處理常式。

若要查看作業的輸出，請使用 `Receive-Job` Cmdlet。 例如： `Receive-Job -Id 1` 。

## PARAMETERS

### -ArgumentList

針對 **FilePath** 參數所指定的腳本或使用 **ScriptBlock** 參數指定的命令，指定引數或參數值的陣列。

引數必須以單一維度陣列引數的形式傳遞至 **ArgumentList** 。 例如，以逗號分隔的清單。 如需有關 **ArgumentList** 行為的詳細資訊，請參閱 [about_Splatting](about/about_Splatting.md#splatting-with-arrays)。

```yaml
Type: System.Object[]
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Authentication

指定用來驗證使用者認證的機制。

此參數可接受的值如下：

- 預設
- 基本
- Credssp
- Digest
- Kerberos
- 交涉
- NegotiateWithImplicitCredential

預設值為 Default。

CredSSP 驗證僅適用于 Windows Vista、Windows Server 2008 和更新版本的 Windows 作業系統。

如需此參數值的詳細資訊，請參閱 [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。

> [!CAUTION]
> 使用者認證會傳遞至要驗證之遠端電腦的「認證安全性支援提供者 (CredSSP)」驗證，是設計用於需要在一個以上資源進行驗證的命令，例如存取遠端網路共用。 此機制會使得遠端作業的安全性風險變高。 若遠端電腦遭到入侵，傳遞給它的認證便可用來控制網路工作階段。

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

指定具有執行此動作權限的使用者帳戶。 如果未指定 **Credential** 參數，此命令會使用目前使用者的認證。

輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 Cmdlet 所產生的 **PSCredential** 物件 `Get-Credential` 。 如果您輸入使用者名稱，系統就會提示您輸入密碼。

認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。

> [!NOTE]
> 如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -DefinitionName

指定此 Cmdlet 啟動之作業的定義名稱。 使用這個參數來啟動具有定義名稱的自訂工作類型，例如已排程的工作。

當您使用 `Start-Job` 來啟動排程工作的實例時，該作業會立即啟動，不論工作觸發程式或工作選項為何。 產生的工作實例是已排程的工作，但不會儲存到磁片，例如觸發的排程工作。 您無法使用的 **ArgumentList** 參數 `Start-Job` 來提供在排程工作中執行的腳本參數值。

此參數是在 PowerShell 3.0 中引進。

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DefinitionPath

指定此 Cmdlet 啟動之作業的定義路徑。 輸入定義路徑。 **DefinitionPath** 和 **DefinitionName** 參數的值串連是作業定義的完整路徑。 使用這個參數來啟動具有定義路徑的自訂工作類型，例如已排程的工作。

針對排程工作， **DefinitionPath** 參數的值為 `$home\AppData\Local\Windows\PowerShell\ScheduledJob` 。

此參數是在 PowerShell 3.0 中引進。

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

指定以 `Start-Job` 背景工作方式執行的本機腳本。 輸入腳本的路徑和檔案名，或使用管線將腳本路徑傳送至 `Start-Job` 。 腳本必須位於本機電腦或本機電腦可以存取的資料夾中。

當您使用此參數時，PowerShell 會將指定之指令檔的內容轉換為腳本區塊，並以背景工作的形式執行腳本區塊。

```yaml
Type: System.String
Parameter Sets: FilePathComputerName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InitializationScript

指定要在工作開始之前執行的命令。 若要建立腳本區塊，請以大括弧括住命令 (`{}`) 。

使用這個參數來準備執行工作的工作階段。 例如，您可以使用它來新增函式、嵌入式管理單元和模組到工作階段。

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定命令的輸入。 輸入包含物件的變數，或輸入可產生物件的命令或運算式。

在 **ScriptBlock** 參數的值中，使用 `$input` 自動變數來代表輸入物件。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

指定此 Cmdlet 以背景工作方式執行的本機腳本。 輸入本機電腦上腳本的路徑。

`Start-Job` 使用 **LiteralPath** 參數的值，與其輸入的完全相同。 沒有字元會被視為萬用字元。 如果路徑包含逸出字元，請將它括在單引號中。 單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。

```yaml
Type: System.String
Parameter Sets: LiteralFilePathComputerName
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

指定新工作的好記名稱。 您可以使用此名稱來識別其他工作 Cmdlet 的作業，例如 `Stop-Job` Cmdlet。

預設的易記名稱是 `Job#` ，其中 `#` 是每個作業的遞增序號。

```yaml
Type: System.String
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PSVersion

指定版本。 `Start-Job` 使用 PowerShell 版本執行作業。 此參數可接受的值包括： `2.0` 和 `3.0` 。

此參數是在 PowerShell 3.0 中引進。

```yaml
Type: System.Version
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunAs32

表示 `Start-Job` 在32位進程中執行作業。 **RunAs32** 會強制工作在32位的進程中執行，即使是在64位的作業系統上也一樣。

在64位版本的 Windows 7 和 Windows Server 2008 R2 上，當 `Start-Job` 命令包含 **RunAs32** 參數時，您不能使用 **Credential** 參數來指定其他使用者的認證。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptBlock

指定要在背景工作執行的命令。 若要建立腳本區塊，請以大括弧括住命令 (`{}`) 。 使用 `$input` 自動變數來存取 **InputObject** 參數的值。 這是必要參數。

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ComputerName
Aliases: Command

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Type

指定所啟動之工作的自訂類型 `Start-Job` 。 輸入自訂工作類型名稱，例如，已排程工作的 PSScheduledJob 或工作流程工作的 PSWorkflowJob。 此參數對於標準背景工作無效。

此參數是在 PowerShell 3.0 中引進。

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String

您可以使用管線將含有 **name** 屬性的物件傳送至 **name** 參數。 例如，您可以將 **FileInfo** 物件從管線 `Get-ChildItem` 到 `Start-Job` 。

## 輸出

### System.Management.Automation.PSRemotingJob

`Start-Job` 傳回代表其啟動作業的 **PSRemotingJob** 物件。

## 注意

若要在背景中執行，請在 `Start-Job` 目前會話中自己的會話中執行。 當您使用 `Invoke-Command` Cmdlet 在 `Start-Job` 遠端電腦的會話中執行命令時，會 `Start-Job` 在遠端會話的會話中執行。

## 相關連結

[about_Arrays](./about/about_arrays.md)

[about_Automatic_Variables](./about/about_automatic_variables.md)

[about_Jobs](./About/about_Jobs.md)

[about_Job_Details](./About/about_Job_Details.md)

[about_Remote_Jobs](./About/about_Remote_Jobs.md)

[Get-Job](Get-Job.md)

[Invoke-Command](Invoke-Command.md)

[Receive-Job](Receive-Job.md)

[Remove-Job](Remove-Job.md)

[Stop-Job](Stop-Job.md)

[Wait-Job](Wait-Job.md)
