---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-module?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Module
ms.openlocfilehash: 4098b40c01085b266fa279107e5795b1283705cd
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202300"
---
# Get-Module

## 概要
取得已匯入或可匯入目前工作階段的模組。

## SYNTAX

### 已載入 (預設) 

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-All] [<CommonParameters>]
```

### 可用

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-All] [-ListAvailable]
 [-PSEdition <String>] [-Refresh] [<CommonParameters>]
```

### PsSession

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-ListAvailable]
 [-PSEdition <String>] [-Refresh] -PSSession <PSSession> [<CommonParameters>]
```

### CimSession

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-ListAvailable] [-Refresh]
 -CimSession <CimSession> [-CimResourceUri <Uri>] [-CimNamespace <String>] [<CommonParameters>]
```

## DESCRIPTION

此 `Get-Module` Cmdlet 會取得已匯入或可匯入至 powershell 會話的 powershell 模組。
傳回的模組物件 `Get-Module` 包含有關模組的重要資訊。
您也可以透過管線將模組物件傳送至其他 Cmdlet，例如 `Import-Module` 和 `Remove-Module` Cmdlet。

如果沒有參數，會 `Get-Module` 取得已匯入目前會話的模組。
若要取得所有已安裝的模組，請指定 **ListAvailable** 參數。

`Get-Module` 取得模組，但不會將它們匯入。
從 Windows PowerShell 3.0 開始，當您使用模組中的命令時，系統會自動匯入模組，但命令不會 `Get-Module` 觸發自動匯入。
您也可以使用 Cmdlet，將模組匯入到您的會話 `Import-Module` 。

從 Windows PowerShell 3.0 開始，您可以從遠端會話匯入模組，然後匯入本機會話。
此策略使用 PowerShell 的隱含遠端功能，相當於使用 `Import-PSSession` Cmdlet。
當您在從另一個會話匯入的模組中使用命令時，命令會隱含地在遠端會話中執行。 這項功能可讓您從本機會話管理遠端電腦。

此外，從 Windows PowerShell 3.0 開始，您可以使用 `Get-Module` 和 `Import-Module` 來取得和匯入通用訊息模型 (CIM) 模組，其中的 Cmdlet 定義于 CMDLET 定義 XML (CDXML) 檔中。
這項功能可讓您使用在非受控程式碼元件中執行的 Cmdlet，例如以 c + + 撰寫的 Cmdlet。

利用這些新功能， `Get-Module` 和 `Import-Module` Cmdlet 成為管理異類企業的主要工具，包括執行 Windows 作業系統的電腦和執行其他作業系統的電腦。

若要管理執行 Windows 作業系統且已啟用 PowerShell 和 PowerShell 遠端功能的遠端電腦，請在遠端電腦上建立 **pssession** ，然後使用的 **Pssession** 參數 `Get-Module` 取得 **pssession** 中的 PowerShell 模組。
當您匯入模組，然後在目前的會話中使用匯入的命令時，命令會隱含地在遠端電腦上的 **PSSession** 中執行。
您可以使用這個策略來管理遠端電腦。

您可以使用類似的策略來管理未啟用 PowerShell 遠端功能的電腦。
這些包括不是執行 Windows 作業系統的電腦，以及具有 PowerShell 但未啟用 PowerShell 遠端功能的電腦。

一開始先在遠端電腦上建立 CIM 會話。
CIM 會話是連接至遠端電腦上 Windows Management Instrumentation (WMI) 的連線。
然後使用的 **CIMSession** 參數 `Get-Module` ，從 CIM 會話取得 cim 模組。
當您使用 Cmdlet 匯入 CIM 模組， `Import-Module` 然後執行匯入的命令時，命令會隱含地在遠端電腦上執行。
您可以使用這個 WMI 和 CIM 策略來管理遠端電腦。

## 範例

### 範例1：取得匯入目前會話的模組

```powershell
Get-Module
```

此命令取得已匯入目前工作階段的模組。

### 範例2：取得已安裝的模組和可用的模組

```powershell
Get-Module -ListAvailable
```

此命令取得已安裝於電腦上，且可匯入目前工作階段的模組。

`Get-Module` 在 **$env:P smodulepath** 環境變數所指定的路徑中尋找可用的模組。
如需 **PSModulePath** 的詳細資訊，請參閱 [about_Modules](About/about_Modules.md) 和 [about_Environment_Variables](About/about_Environment_Variables.md)。

### 範例3：取得所有匯出的檔案

```powershell
Get-Module -ListAvailable -All
```

此命令取得所有可用模組的所有匯出檔案。

### 範例4：依完整名稱取得模組

```powershell
$FullyQualifedName = @{ModuleName="Microsoft.PowerShell.Management";ModuleVersion="3.1.0.0"}
Get-Module -FullyQualifiedName $FullyQualifedName | Format-Table -Property Name,Version
```

```Output
Name                             Version
----                             -------
Microsoft.PowerShell.Management  3.1.0.0
```

此命令會使用 **FullyQualifiedName** 參數來指定模組的完整名稱，以取得 **Microsoft. 管理** 模組。
命令接著會使用管線將結果傳送至 `Format-Table` Cmdlet，將結果格式化為具有 **Name** 和 **Version** 的資料表做為資料行標題。

### 範例5：取得模組的屬性

```powershell
Get-Module | Get-Member -MemberType Property | Format-Table Name
```

```Output
Name
----
AccessMode
Author
ClrVersion
CompanyName
Copyright
Definition
Description
DotNetFrameworkVersion
ExportedAliases
ExportedCmdlets
ExportedCommands
ExportedFormatFiles
ExportedFunctions
ExportedTypeFiles
ExportedVariables
ExportedWorkflows
FileList
Guid
HelpInfoUri
LogPipelineExecutionDetails
ModuleBase
ModuleList
ModuleType
Name
NestedModules
OnRemove
Path
PowerShellHostName
PowerShellHostVersion
PowerShellVersion
PrivateData
ProcessorArchitecture
RequiredAssemblies
RequiredModules
RootModule
Scripts
SessionState
Version
```

此命令會取得傳回之 **PSModuleInfo** 物件的屬性 `Get-Module` 。
每個模組檔案都有一個物件。

您可以使用屬性來格式化和篩選模組物件。
如需屬性的詳細資訊，請參閱 [PSModuleInfo 屬性](/dotnet/api/system.management.automation.psmoduleinfo)。

輸出包含在 Windows PowerShell 3.0 中引進的新屬性，例如 **Author** 和 **公司名稱** 。

### 範例6：依名稱將所有模組分組

```powershell
Get-Module -ListAvailable -All | Format-Table -Property Name, Moduletype, Path -Groupby Name
```

```Output
Name: AppLocker

Name      ModuleType Path
----      ---------- ----
AppLocker   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\AppLocker\AppLocker.psd1


   Name: Appx

Name ModuleType Path
---- ---------- ----
Appx   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Appx\en-US\Appx.psd1
Appx   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Appx\Appx.psd1
Appx     Script C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Appx\Appx.psm1


   Name: BestPractices

Name          ModuleType Path
----          ---------- ----
BestPractices   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\BestPractices\BestPractices.psd1


   Name: BitsTransfer

Name         ModuleType Path
----         ---------- ----
BitsTransfer   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\BitsTransfer\BitsTransfer.psd1
```

此命令會取得所有模組檔案（已匯入和可用），然後依模組名稱將它們分組。 這可讓您查看每個指令碼正在匯出的模組檔案。

### 範例7：顯示模組資訊清單的內容

這些命令會顯示 Windows PowerShell **BitsTransfer** 模組的模組資訊清單內容。

模組不需要有資訊清單檔案。
當他們有資訊清單檔時，資訊清單檔只需要包含版本號碼。
不過，資訊清單檔案通常會提供模組、其需求及其內容的實用資訊。

```powershell
# First command
$m = Get-Module -list -Name BitsTransfer

# Second command
Get-Content $m.Path
```

```Output
@ {
    GUID               = "{8FA5064B-8479-4c5c-86EA-0D311FE48875}"
    Author             = "Microsoft Corporation"
    CompanyName        = "Microsoft Corporation"
    Copyright          = "Microsoft Corporation. All rights reserved."
    ModuleVersion      = "1.0.0.0"
    Description        = "Windows PowerShell File Transfer Module"
    PowerShellVersion  = "2.0"
    CLRVersion         = "2.0"
    NestedModules      = "Microsoft.BackgroundIntelligentTransfer.Management"
    FormatsToProcess   = "FileTransfer.Format.ps1xml"
    RequiredAssemblies = Join-Path $psScriptRoot "Microsoft.BackgroundIntelligentTransfer.Management.Interop.dll"
}
```

第一個命令取得代表 BitsTransfer 模組的 PSModuleInfo 物件。 它會將物件儲存在 `$m` 變數中。

第二個命令會使用 `Get-Content` Cmdlet 取得指定路徑中資訊清單檔的內容。 它會使用點標記法，取得儲存在物件的 Path 屬性中的資訊清單檔案路徑。 輸出會顯示模組資訊清單的內容。

### 範例8：列出模組目錄中的檔案

```powershell
dir (Get-Module -ListAvailable FileTransfer).ModuleBase
```

```Output
Directory: C:\Windows\system32\WindowsPowerShell\v1.0\Modules\FileTransfer
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        12/16/2008  12:36 PM            en-US
-a---        11/19/2008  11:30 PM      16184 FileTransfer.Format.ps1xml
-a---        11/20/2008  11:30 PM       1044 FileTransfer.psd1
-a---        12/16/2008  12:20 AM     108544 Microsoft.BackgroundIntelligentTransfer.Management.Interop.dll
```

此命令會列出模組目錄中的檔案。
這是在您將模組匯入之前，可用來判斷模組中有哪些內容的另一種方式。
某些模組可能含有說明檔或描述模組的讀我檔案。

### 範例9：取得安裝在電腦上的模組

```powershell
$s = New-PSSession -ComputerName Server01

Get-Module -PSSession $s -ListAvailable
```

這些命令會取得 Server01 電腦上安裝的模組。

第一個命令會使用 `New-PSSession` Cmdlet 在 Server01 電腦上建立 **PSSession** 。 命令會將 **PSSession** 儲存在 $s 變數中。

第二個命令使用的 **pssession** 和 **ListAvailable** 參數 `Get-Module` ，取得 $s 變數中 **pssession** 內的模組。

如果您使用管線將模組從其他會話傳送至 `Import-Module` Cmdlet，則會 `Import-Module` 使用隱含的遠端功能，將模組匯入目前的會話中。
這相當於使用 `Import-PSSession` Cmdlet。
您可以使用目前工作階段中模組的 Cmdlet，但是，使用這些 Cmdlet 的命令實際上會執行遠端工作階段。
如需詳細資訊，請參閱 [`Import-Module`](Import-Module.md) 和 [`Import-PSSession`](../Microsoft.PowerShell.Utility/Import-PSSession.md)。

### 範例10：管理未執行 Windows 作業系統的電腦

此範例中的命令可讓您管理不是執行 Windows 作業系統之遠端電腦的儲存系統。
在這個範例中，因為電腦的系統管理員已安裝「模組探索」WMI 提供者，所以 CIM 命令可以使用專為提供者設計的預設值。

```powershell
$cs = New-CimSession -ComputerName RSDGF03
Get-Module -CimSession $cs -Name Storage | Import-Module
Get-Command Get-Disk
```

```Output
CommandType     Name                  ModuleName
-----------     ----                  ----------
Function        Get-Disk              Storage
```

```powershell
Get-Disk
```

```Output
Number Friendly Name              OperationalStatus          Total Size Partition Style
------ -------------              -----------------          ---------- ---------------
0      Virtual HD ATA Device      Online                          40 GB MBR
```

第一個命令會使用 `New-CimSession` Cmdlet 在 RSDGF03 遠端電腦上建立會話。 工作階段會連線遠端電腦上的 WMI。 此命令會將 CIM 會話儲存在 `$cs` 變數中。

第二個命令會使用變數中的 CIM 會話 `$cs` ，在 `Get-Module` RSDGF03 電腦上執行命令。 命令使用 Name 參數指定 Storage 模組。 命令使用管線運算子 (|) 將儲存體模組傳送至 `Import-Module` Cmdlet，以將它匯入本機會話。

第三個命令會在 `Get-Command` `Get-Disk` 儲存體模組中的命令上執行 Cmdlet。
當您將 CIM 模組匯入本機會話時，PowerShell 會將代表 CIM 模組的 CDXML 檔案轉換成 PowerShell 腳本，這會顯示為本機會話中的函式。

第四個命令會執行 `Get-Disk` 命令。 雖然命令是在本機工作階段中輸入，但是它會在匯入它的遠端電腦上隱含執行。 命令會從遠端電腦取得物件，並將其傳回本機工作階段。

## PARAMETERS

### -All

指出此 Cmdlet 會取得每個模組資料夾中的所有模組，包括嵌套模組、資訊清單 ( .psd1) 檔案、腳本模組 (. .psm1) 檔案，以及二進位模組 ( .dll) 檔。
如果沒有這個參數，則 `Get-Module` 只會取得每個模組資料夾中的預設模組。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Loaded, Available
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -CimNamespace

指定公開 CIM 模組的替代 CIM 提供者命名空間。
預設值為「模組探索」WMI 提供者的命名空間。

使用此參數從不是執行 Windows 作業系統的電腦和裝置取得 CIM 模組。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.String
Parameter Sets: CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CimResourceUri

指定 CIM 模組的替代位置。
預設值為遠端電腦上「模組探索」 WMI 提供者的資源 URI。

使用此參數從不是執行 Windows 作業系統的電腦和裝置取得 CIM 模組。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Uri
Parameter Sets: CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CimSession

指定遠端電腦上的 CIM 工作階段。
輸入包含 CIM 會話的變數，或輸入可取得 CIM 會話的命令，例如 [CimSession](/powershell/module/cimcmdlets/get-cimsession) 命令。

`Get-Module` 使用 CIM 會話連接從遠端電腦取得模組。
當您使用 Cmdlet 匯入模組 `Import-Module` ，並在目前的會話中使用匯入模組的命令時，命令實際上會在遠端電腦上執行。

您可以使用此參數從不是執行 Windows 作業系統的電腦和裝置，以及具有 PowerShell 但未啟用 PowerShell 遠端處理的電腦取得模組。

**CimSession** 參數會取得 **CIMSession** 中的所有模組。
不過，您可以只匯入 CIM 型和「Cmdlet 定義 XML (CDXML)」型模組。

```yaml
Type: Microsoft.Management.Infrastructure.CimSession
Parameter Sets: CimSession
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FullyQualifiedName

以 **ModuleSpecification** 物件的形式指定模組的名稱。
這些物件會在 MSDN library 中 [ModuleSpecification (表的「雜湊表) ](https://msdn.microsoft.com/library/jj136290) 的「備註」一節中描述。
例如， **FullyQualifiedName** 參數會接受以下列格式指定的模組名稱：

- @ {ModuleName = "modulename";ModuleVersion = "version_number"}
- @ {ModuleName = "modulename";ModuleVersion = "version_number";Guid = "GUID"}

**ModuleName** 和 **ModuleVersion** 是必要參數，但 **Guid** 是選擇性參數。

您無法在與 **Name** 參數相同的命令中指定 **FullyQualifiedName** 參數。

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ListAvailable

指出此 Cmdlet 會取得所有已安裝的模組。
`Get-Module` 取得 **PSModulePath** 環境變數所列路徑中的模組。
如果沒有這個參數，則 `Get-Module` 只會取得 **PSModulePath** 環境變數中所列的模組，以及在目前的會話中載入的模組。
**ListAvailable** 不會傳回 **PSModulePath** 環境變數中找不到的模組相關資訊，即使這些模組已載入目前工作階段也一樣。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Available, PsSession, CimSession
Aliases:

Required: True (Available), False (PsSession, CimSession)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

指定此 Cmdlet 取得之模組的名稱或名稱模式。
允許使用萬用字元。
您也可以透過管線將名稱傳送至 `Get-Module` 。
您無法在與 **Name** 參數相同的命令中指定 **FullyQualifiedName** 參數。

**名稱** 不能接受模組 GUID 做為值。
若要藉由指定 GUID 來傳回模組，請改用 **FullyQualifiedName** 。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### -PSEdition

取得支援指定 PowerShell 版本的模組。

此參數可接受的值為：

- 桌面
- 核心

Get-Module Cmdlet 會針對指定的值檢查 **PSModuleInfo** 物件的 **CompatiblePSEditions** 屬性，並只傳回已設定的模組。

> [!NOTE]
>
> - **Desktop Edition：** 建置在 .NET Framework 上，並與目標為完整版 Windows (Server Core 和 Windows Desktop 等) 上執行之 PowerShell 版本的指令碼和模組相容。
> - **Core Edition：** 建置在 .NET Core 上，並與目標為縮減版 Windows (Nano Server 和 Windows IoT 等) 上執行之 PowerShell 版本的指令碼和模組相容。

```yaml
Type: System.String
Parameter Sets: PsSession, Available
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PSSession

取得指定之使用者管理的 PowerShell 會話中的模組 ( **PSSession** ) 。
輸入包含會話的變數、可取得會話的命令（例如 `Get-PSSession` 命令）或建立會話的命令（例如 `New-PSSession` 命令）。

當會話連線到遠端電腦時，您必須指定 **ListAvailable** 參數。

`Get-Module`使用 **pssession** 參數的命令相當於使用 `Invoke-Command` Cmdlet `Get-Module -ListAvailable` 在 **PSSession** 中執行命令。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: PsSession
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Refresh

指出此 Cmdlet 會重新整理已安裝命令的快取。
當工作階段啟動時，即會建立命令快取。
它可讓 `Get-Command` Cmdlet 從未匯入會話的模組中取得命令。

這個參數是專為開發和測試案例所設計，在這類案例中，模組的內容會在工作階段開始後變更。

當您在命令中指定 **Refresh** 參數時，必須指定 **ListAvailable** 。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PsSession, Available, CimSession
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String

您可以透過管線將模組名稱傳送至此 Cmdlet。

## 輸出

### System.Management.Automation.PSModuleInfo

此 Cmdlet 會傳回代表模組的物件。
當您指定 **ListAvailable** 參數時， `Get-Module` 會傳回 **ModuleInfoGrouping** 物件，這是具有相同屬性和方法的 **PSModuleInfo** 物件類型。

## 注意

- 從 Windows PowerShell 3.0 開始，PowerShell 隨附的核心命令會封裝在模組中。 例外狀況是 **PSSnapin** ) 的嵌入式管理單元 **(。** 依照預設，只會新增 **Microsoft.PowerShell.Core** 嵌入式管理單元至工作階段。
模組會在第一次使用時自動匯入，而您可以使用 `Import-Module` Cmdlet 將它們匯入。
- 從 Windows PowerShell 3.0 開始，隨 PowerShell 安裝的核心命令會封裝在模組中。 在 Windows PowerShell 2.0，以及在較新版本的 PowerShell 中建立舊版會話的主機程式中，會將核心命令封裝在嵌入式管理單元中， ( **PSSnapins** ) 。 **Microsoft.PowerShell.Core** 是一個例外，它一律是一個嵌入式管理單元。 此外，遠端會話（例如由 Cmdlet 啟動的會話） `New-PSSession` 都是包含核心嵌入式管理單元的較舊樣式會話。

  如需有關使用核心模組建立較新樣式會話的 **CreateDefault2** 方法的詳細資訊，請參閱 MSDN library 中的 [CreateDefault2 方法](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2) 。

- `Get-Module` 只會取得位置中的模組，這些位置會儲存在 **PSModulePath** 環境變數的值 ($Env:P smodulepath) 中。 您可以使用 Cmdlet 的 **Path** 參數 `Import-Module` ，在其他位置匯入模組，但您無法使用 `Get-Module` Cmdlet 來取得它們。
- 此外，從 PowerShell 3.0 開始，已在傳回的物件中加入新的屬性，讓您可以在匯 `Get-Module` 入模組之前，更輕鬆地瞭解它們。 所有屬性都會在匯入之前填入。 其中包括 **ExportedCommands** 、 **ExportedCmdlets** 和 **ExportedFunctions** 屬性，這些屬性會列出模組匯出的命令。
- **ListAvailable** 參數只會取得格式正確的模組，也就是至少包含一個檔案的資料夾，其基底名稱與模組資料夾的名稱相同。 基底名稱是不含副檔名的名稱。 包含具有不同名稱之檔案的資料夾會被視為容器，而非模組。

  若要取得實作為 .dll 檔案，但未包含在模組資料夾中的模組，請同時指定 **ListAvailable** 和 **All** 參數。

- 若要使用 CIM 工作階段功能，遠端電腦必須具備 WS-Management 遠端功能和 Windows Management Instrumentation (WMI)，這是 Microsoft 實作的「通用訊息模型 (CIM)」標準。 電腦也必須擁有具有相同基本功能的「模組探索」WMI 提供者或替代 WMI 提供者。

  您可以在未執行 Windows 作業系統的電腦上，以及在具有 PowerShell 但未啟用 PowerShell 遠端功能的 Windows 電腦上，使用 CIM 會話功能。

  您也可以使用 CIM 參數，從已啟用 PowerShell 遠端功能的電腦取得 CIM 模組。 這包括本機電腦。
當您在本機電腦上建立 CIM 會話時，PowerShell 會使用 DCOM （而不是 WMI）來建立會話。

## 相關連結

[Get-CimSession](../CimCmdlets/Get-CimSession.md)

[New-CimSession](../CimCmdlets/New-CimSession.md)

[about_Modules](About/about_Modules.md)

[Get-PSSession](Get-PSSession.md)

[Import-Module](Import-Module.md)

[Import-PSSession](../Microsoft.PowerShell.Utility/Import-PSSession.md)

[New-PSSession](New-PSSession.md)

[Remove-Module](Remove-Module.md)
