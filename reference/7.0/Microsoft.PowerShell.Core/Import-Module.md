---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/import-module?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Module
ms.openlocfilehash: 218a4cb447c85a7362efebe9b50a917703cccc35
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564440"
---
# Import-Module

## 概要
將模組新增到目前的工作階段。

## SYNTAX

### Name (預設值)

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>]  [<CommonParameters>]
```

### PSSession

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] -PSSession <PSSession>  [<CommonParameters>]
```

### CimSession

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] -CimSession <CimSession> [-CimResourceUri <Uri>] [-CimNamespace <String>]
 [<CommonParameters>]
```

### UseWindowsPowerShell

```
Import-Module [-Name] <string[]> -UseWindowsPowerShell [-Global] [-Prefix <string>]
 [-Function <string[]>] [-Cmdlet <string[]>] [-Variable <string[]>] [-Alias <string[]>]
 [-Force] [-PassThru] [-AsCustomObject] [-MinimumVersion <version>] [-MaximumVersion <string>]
 [-RequiredVersion <version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <string>] [<CommonParameters>]
```

### FullyQualifiedName

```
Import-Module [-Global] [-Prefix <String>] [-FullyQualifiedName] <ModuleSpecification[]>
 [-Function <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force]
 [-SkipEditionCheck] [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking]
 [-NoClobber] [-Scope <String>]  [<CommonParameters>]
```

### FullyQualifiedNameAndPSSession

```
Import-Module [-Global] [-Prefix <String>] [-FullyQualifiedName] <ModuleSpecification[]>
 [-Function <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force]
 [-SkipEditionCheck] [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking]
 [-NoClobber] [-Scope <String>] -PSSession <PSSession>  [<CommonParameters>]
```

### FullyQualifiedNameAndUseWindowsPowerShell

```
Import-Module [-FullyQualifiedName] <ModuleSpecification[]> -UseWindowsPowerShell [-Global]
 [-Prefix <string>] [-Function <string[]>] [-Cmdlet <string[]>] [-Variable <string[]>]
 [-Alias <string[]>] [-Force] [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>]
 [-DisableNameChecking] [-NoClobber] [-Scope <string>] [<CommonParameters>]
```

### 組件

```
Import-Module [-Global] [-Prefix <String>] [-Assembly] <Assembly[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>]  [<CommonParameters>]
```

### ModuleInfo

```
Import-Module [-Global] [-Prefix <String>] [-Function <String[]>] [-Cmdlet <String[]>]
 [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck] [-PassThru]
 [-AsCustomObject] [-ModuleInfo] <PSModuleInfo[]> [-ArgumentList <Object[]>] [-DisableNameChecking]
 [-NoClobber] [-Scope <String>]  [<CommonParameters>]
```

## DESCRIPTION

`Import-Module`Cmdlet 會將一或多個模組新增到目前的會話。 從 PowerShell 3.0 開始，當您使用模組中的任何命令或提供者時，已安裝的模組會自動匯入至會話。 不過，您仍然可以使用 `Import-Module` 命令匯入模組。
您可以使用喜好設定變數停用自動匯入模組 `$PSModuleAutoloadingPreference` 。 如需變數的詳細資訊 `$PSModuleAutoloadingPreference` ，請參閱 [about_Preference_Variables](About/about_Preference_Variables.md)。

模組是一個套件，其中包含可在 PowerShell 中使用的成員。 成員包括 Cmdlet、提供者、腳本、函式、變數和其他工具和檔案。 在匯入模組之後，您可以在工作階段中使用模組成員。 如需模組的詳細資訊，請參閱 [about_Modules](About/about_Modules.md)。

根據預設， `Import-Module` 會匯入模組匯出的所有成員，但您可以使用 **別名**、 函式、 **Cmdlet** 和 **變數** 參數來限制要匯入的成員。 **NoClobber** 參數會防止匯 `Import-Module` 入與目前會話中的成員具有相同名稱的成員。

`Import-Module` 只將模組匯入到目前的會話。 若要將模組匯入到每個新的會話，請將 `Import-Module` 命令新增至您的 PowerShell 設定檔。 如需設定檔的詳細資訊，請參閱 [about_Profiles](About/about_Profiles.md)。

您可以在遠端電腦上建立 **PSSession** ，以管理已啟用 PowerShell 遠端功能的遠端 Windows 電腦。 然後使用的 **PSSession** 參數 `Import-Module` ，匯入在遠端電腦上安裝的模組。 當您在目前的會話中使用匯入的命令時，命令會隱含地在遠端電腦上執行。

從 Windows PowerShell 3.0 開始，您可以使用匯 `Import-Module` 入通用訊息模型 (CIM) 模組。 CIM 模組會在 Cmdlet 定義 XML (CDXML) 檔中定義 Cmdlet。 這項功能可讓您使用在非受控程式碼元件中執行的 Cmdlet，例如以 c + + 撰寫的 Cmdlet。

針對未啟用 PowerShell 遠端處理的遠端電腦，包括不是執行 Windows 作業系統的電腦，您可以使用的 **CIMSession** 參數， `Import-Module` 從遠端電腦匯入 CIM 模組。 匯入的命令會隱含地在遠端電腦上執行。 **CIMSession** 是連線到遠端電腦上的 WINDOWS MANAGEMENT INSTRUMENTATION (WMI) 的連接。

## 範例

### 範例1：將模組的成員匯入到目前的會話

此範例會將 **PSDiagnostics** 模組的成員匯入到目前的會話。

```powershell
Import-Module -Name PSDiagnostics
```

### 範例2：匯入模組路徑所指定的所有模組

此範例會將環境變數所指定路徑中的所有可用模組匯入 `$env:PSModulePath` 到目前的會話。

```powershell
Get-Module -ListAvailable | Import-Module
```

### 範例3：將數個模組的成員匯入到目前的會話

此範例會將 **PSDiagnostics** 和 **Dism** 模組的成員匯入到目前的會話。

```powershell
$m = Get-Module -ListAvailable PSDiagnostics, Dism
Import-Module -ModuleInfo $m
```

`Get-Module`Cmdlet 會取得 **PSDiagnostics** 和 **Dism** 模組，並將物件儲存在變數中 `$m` 。 當您取得尚未匯入至會話的模組時，必須要有 **ListAvailable** 參數。

的 **ModuleInfo** 參數 `Import-Module` 是用來將模組匯入到目前的會話。

### 範例4：匯入路徑指定的所有模組

此範例會使用明確的路徑來識別要匯入的模組。

```powershell
Import-Module -Name c:\ps-test\modules\test -Verbose
```

```Output
VERBOSE: Loading module from path 'C:\ps-test\modules\Test\Test.psm1'.
VERBOSE: Exporting function 'my-parm'.
VERBOSE: Exporting function 'Get-Parameter'.
VERBOSE: Exporting function 'Get-Specification'.
VERBOSE: Exporting function 'Get-SpecDetails'.
```

使用 **Verbose** 參數會導致在 `Import-Module` 載入模組時報告進度。
如果沒有 **Verbose**、 **PassThru** 或 **AsCustomObject** 參數， `Import-Module` 則在匯入模組時不會產生任何輸出。

### 範例5：限制匯入到會話的模組成員

此範例顯示如何限制將哪些模組成員匯入會話，以及此命令在會話上的效果。 **函數** 參數會限制從模組匯入的成員。 您也可以使用 **別名**、 **變數** 和 **Cmdlet** 參數來限制模組所匯入的其他成員。

`Get-Module`Cmdlet 會取得代表 **PSDiagnostics** 模組的物件。 **ExportedCmdlets** 屬性會列出模組匯出的所有 Cmdlet，即使它們並未全部匯入也一樣。

```powershell
Import-Module PSDiagnostics -Function Disable-PSTrace, Enable-PSTrace
(Get-Module PSDiagnostics).ExportedCommands
```

```Output
Key                          Value
---                          -----
Disable-PSTrace              Disable-PSTrace
Disable-PSWSManCombinedTrace Disable-PSWSManCombinedTrace
Disable-WSManTrace           Disable-WSManTrace
Enable-PSTrace               Enable-PSTrace
Enable-PSWSManCombinedTrace  Enable-PSWSManCombinedTrace
Enable-WSManTrace            Enable-WSManTrace
Get-LogProperties            Get-LogProperties
Set-LogProperties            Set-LogProperties
Start-Trace                  Start-Trace
Stop-Trace                   Stop-Trace
```

```powershell
Get-Command -Module PSDiagnostics
```

```Output
CommandType     Name                 Version    Source
-----------     ----                 -------    ------
Function        Disable-PSTrace      6.1.0.0    PSDiagnostics
Function        Enable-PSTrace       6.1.0.0    PSDiagnostics
```

使用 Cmdlet 的 **Module** 參數， `Get-Command` 會顯示從 **PSDiagnostics** 模組匯入的命令。 結果會確認只匯 `Disable-PSTrace` 入和 `Enable-PSTrace` Cmdlet。

### 範例6：匯入模組的成員並新增前置詞

此範例會將 **PSDiagnostics** 模組匯入到目前的會話、將前置詞新增至成員名稱，然後顯示前置詞的成員名稱。 的 **prefix** 參數 `Import-Module` 會將 **x** 前置詞加入至從模組匯入的所有成員。 前置詞只適用于目前會話中的成員。 它不會變更模組。 **PassThru** 參數會傳回代表匯入模組的模組物件。

```powershell
Import-Module PSDiagnostics -Prefix x -PassThru
```

```Output
ModuleType Version    Name               ExportedCommands
---------- -------    ----               ----------------
Script     6.1.0.0    PSDiagnostics      {Disable-xPSTrace, Disable-xPSWSManCombinedTrace, Disable-xW...
```

```powershell
Get-Command -Module PSDiagnostics
```

```Output
CommandType     Name                                   Version    Source
-----------     ----                                   -------    ------
Function        Disable-xPSTrace                       6.1.0.0    PSDiagnostics
Function        Disable-xPSWSManCombinedTrace          6.1.0.0    PSDiagnostics
Function        Disable-xWSManTrace                    6.1.0.0    PSDiagnostics
Function        Enable-xPSTrace                        6.1.0.0    PSDiagnostics
Function        Enable-xPSWSManCombinedTrace           6.1.0.0    PSDiagnostics
Function        Enable-xWSManTrace                     6.1.0.0    PSDiagnostics
Function        Get-xLogProperties                     6.1.0.0    PSDiagnostics
Function        Set-xLogProperties                     6.1.0.0    PSDiagnostics
Function        Start-xTrace                           6.1.0.0    PSDiagnostics
Function        Stop-xTrace                            6.1.0.0    PSDiagnostics
```

`Get-Command` 取得已從模組匯入的成員。 輸出會顯示已正確為模組成員加上前置詞。

### 範例7：取得和使用自訂物件

這個範例示範如何取得和使用所傳回的自訂物件 `Import-Module` 。

自訂物件包括代表每個匯入之模組成員的綜合成員。 例如，模組中的 Cmdlet 和函式會轉換成自訂物件的指令碼方法。

自訂物件在撰寫腳本時非常有用。 它們在有數個匯入的物件有相同名稱時也非常有用。 使用物件的指令碼方法相當於指定匯入成員的完整名稱，包括其模組名稱。

只有在匯入腳本模組時，才能使用 **AsCustomObject** 參數。 用 `Get-Module` 來判斷哪些可用的模組是腳本模組。

```powershell
Get-Module -List | Format-Table -Property Name, ModuleType -AutoSize
```

```Output
Name          ModuleType
----          ----------
Show-Calendar     Script
BitsTransfer    Manifest
PSDiagnostics   Manifest
TestCmdlets       Script
...
```

```powershell
$a = Import-Module -Name Show-Calendar -AsCustomObject -Passthru
$a | Get-Member
```

```Output
    TypeName: System.Management.Automation.PSCustomObject
Name          MemberType   Definition
----          ----------   ----------
Equals        Method       bool Equals(System.Object obj)
GetHashCode   Method       int GetHashCode()
GetType       Method       type GetType()
ToString      Method       string ToString()
Show-Calendar ScriptMethod System.Object Show-Calendar();
```

```powershell
$a."Show-Calendar"()
```

`Show-Calendar`使用 **AsCustomObject** 參數匯入腳本模組，以要求自訂物件，並使用 **PassThru** 參數來傳回物件。 產生的自訂物件會儲存在 `$a` 變數中。

此 `$a` 變數會透過管道傳送至 `Get-Member` Cmdlet，以顯示已儲存物件的屬性和方法。 輸出會顯示 `Show-Calendar` 腳本方法。

若要呼叫 `Show-Calendar` 腳本方法，方法名稱必須以引號括住，因為名稱包含連字號。

### 範例8：將模組重新匯入到相同的會話

這個範例示範 `Import-Module` 當您在相同的會話中重新匯入模組時，如何使用的 Force 參數。 **Force** 參數會移除載入的模組，然後重新匯入。

```powershell
Import-Module PSDiagnostics
Import-Module PSDiagnostics -Force -Prefix PS
```

第一個命令會匯入 **PSDiagnostics** 模組。 第二個命令再次匯入該模組，這次是使用 **Prefix** 參數。

如果沒有 **Force** 參數，會話會包含每個 **PSDiagnostics** Cmdlet 的兩個複本，一個具有標準名稱，另一個具有首碼名稱。

### 範例9：執行已匯入命令隱藏的命令

此範例顯示如何執行由匯入命令所隱藏的命令。 **TestModule** 模組包含名為的函式，該函式會傳回年的 `Get-Date` 年份和日。

```powershell
Get-Date
```

```Output
Thursday, August 15, 2019 2:26:12 PM
```

```powershell
Import-Module TestModule
Get-Date
```

```Output
19227
```

```powershell
Get-Command Get-Date -All | Format-Table -Property CommandType, Name, ModuleName -AutoSize
```

```Output
CommandType     Name         ModuleName
-----------     ----         ----------
Function        Get-Date     TestModule
Cmdlet          Get-Date     Microsoft.PowerShell.Utility
```

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

```Output
Thursday, August 15, 2019 2:28:31 PM
```

第一個 `Get-Date` Cmdlet 會傳回包含目前日期的 **DateTime** 物件。 匯入 **TestModule** 模組之後，會傳回一 `Get-Date` 年的年份和日。

使用的 **all** 參數會 `Get-Command` 顯示 `Get-Date` 會話中的所有命令。 結果顯示會話中有兩個 `Get-Date` 命令、 **TestModule** 模組中的函式，以及來自于 **Microsoft PowerShell** 模組的 Cmdlet。

因為函式優先于 Cmdlet，所以 `Get-Date` **TestModule** 模組中的函式會執行，而不是 `Get-Date` Cmdlet。 若要執行的原始版本 `Get-Date` ，您必須使用模組名稱來限定命令名稱。

如需 PowerShell 中之命令優先順序的詳細資訊，請參閱 [about_Command_Precedence](about/about_Command_Precedence.md)。

### 範例10：匯入模組的最小版本

此範例會匯入 **PowerShellGet** 模組。 它使用的 **MinimumVersion** 參數 `Import-Module` ，只匯入2.0.0 或更高版本的模組。

```powershell
Import-Module -Name PowerShellGet -MinimumVersion 2.0.0
```

您也可以使用 **RequiredVersion** 參數匯入特定版本的模組，或使用關鍵字的 **模組** 和 **版本** 參數 `#Requires` 來要求腳本中特定版本的模組。

### 範例11：使用完整名稱匯入

此範例會使用 FullyQualifiedName 來匯入特定版本的模組。

```powershell
PS> Get-Module -ListAvailable PowerShellGet | Select-Object Name, Version

Name          Version
----          -------
PowerShellGet 2.2.1
PowerShellGet 2.1.3
PowerShellGet 2.1.2
PowerShellGet 1.0.0.1

PS> Import-Module -FullyQualifiedName @{ModuleName = 'PowerShellGet'; ModuleVersion = '2.1.3' }
```

### 範例12：使用完整路徑匯入

此範例會使用完整路徑來匯入特定版本的模組。

```powershell
PS> Get-Module -ListAvailable PowerShellGet | Select-Object Path

Path
----
C:\Program Files\PowerShell\Modules\PowerShellGet\2.2.1\PowerShellGet.psd1
C:\program files\powershell\6\Modules\PowerShellGet\PowerShellGet.psd1
C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\2.1.2\PowerShellGet.psd1
C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PowerShellGet.psd1

PS> Import-Module -Name 'C:\Program Files\PowerShell\Modules\PowerShellGet\2.2.1\PowerShellGet.psd1'
```

### 範例13：從遠端電腦匯入模組

此範例示範如何使用 `Import-Module` Cmdlet 從遠端電腦匯入模組。
此命令會使用 PowerShell 的隱含遠端功能。

當您從另一個工作階段匯入模組時，您可以在目前的工作階段中使用 Cmdlet。
不過，使用 Cmdlet 的命令會在遠端會話中執行。

```powershell
$s = New-PSSession -ComputerName Server01
Get-Module -PSSession $s -ListAvailable -Name NetSecurity
```

```Output
ModuleType Name             ExportedCommands
---------- ----             ----------------
Manifest   NetSecurity      {New-NetIPsecAuthProposal, New-NetIPsecMainModeCryptoProposal, New-Ne...
```

```powershell
Import-Module -PSSession $s -Name NetSecurity
Get-Command -Module NetSecurity -Name Get-*Firewall*
```

```Output
CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Function        Get-NetFirewallAddressFilter                       NetSecurity
Function        Get-NetFirewallApplicationFilter                   NetSecurity
Function        Get-NetFirewallInterfaceFilter                     NetSecurity
Function        Get-NetFirewallInterfaceTypeFilter                 NetSecurity
Function        Get-NetFirewallPortFilter                          NetSecurity
Function        Get-NetFirewallProfile                             NetSecurity
Function        Get-NetFirewallRule                                NetSecurity
Function        Get-NetFirewallSecurityFilter                      NetSecurity
Function        Get-NetFirewallServiceFilter                       NetSecurity
Function        Get-NetFirewallSetting                             NetSecurity
```

```powershell
Get-NetFirewallRule -DisplayName "Windows Remote Management*" |
  Format-Table -Property DisplayName, Name -AutoSize
```

```Output
DisplayName                                              Name
-----------                                              ----
Windows Remote Management (HTTP-In)                      WINRM-HTTP-In-TCP
Windows Remote Management (HTTP-In)                      WINRM-HTTP-In-TCP-PUBLIC
Windows Remote Management - Compatibility Mode (HTTP-In) WINRM-HTTP-Compat-In-TCP
```

`New-PSSession` 建立 (**PSSession**) 至 Server01 電腦的遠端會話。 **PSSession** 會儲存在變數中 `$s` 。

`Get-Module`以 **PSSession** 參數執行時，會顯示已在遠端電腦上安裝並使用 **NetSecurity** 模組。 此命令相當於使用 `Invoke-Command` Cmdlet `Get-Module` 在遠端會話中執行命令。 例如： (`Invoke-Command $s {Get-Module -ListAvailable -Name NetSecurity`

`Import-Module`以 **PSSession** 參數執行時，會將 **NetSecurity** 模組從遠端電腦匯入到目前的會話。 此 `Get-Command` Cmdlet 是用來取得以 **get** 開頭的命令，並從 **NetSecurity** 模組包含 **防火牆**。 輸出會確認模組及其 Cmdlet 已匯入至目前的會話。

接著， `Get-NetFirewallRule` Cmdlet 會取得 Server01 電腦上 Windows 遠端管理的防火牆規則。 這相當於使用 `Invoke-Command` Cmdlet `Get-NetFirewallRule` 在遠端會話上執行。

### 範例14：不使用 Windows 作業系統來管理遠端電腦上的存放裝置

在此範例中，電腦的系統管理員已安裝「模組探索」 WMI 提供者，可讓您使用專為提供者設計的 CIM 命令。

此 `New-CimSession` Cmdlet 會在名為 RSDGF03 的遠端電腦上建立會話。 會話會連接到遠端電腦上的 WMI 服務。 CIM 會話會儲存在變數中 `$cs` 。
`Import-Module`使用中的 CimSession `$cs` ，從 RSDGF03 電腦匯入 **儲存體** CIM 模組。

此 `Get-Command` Cmdlet 會 `Get-Disk` 在 **儲存體** 模組中顯示命令。 當您將 CIM 模組匯入本機會話時，PowerShell 會將每個命令的 CDXML 檔案轉換成 PowerShell 腳本，這會在本機會話中以函式的形式出現。

雖然 `Get-Disk` 是在本機會話中輸入的，但此 Cmdlet 會隱含地在其匯入的遠端電腦上執行。 此命令會將物件從遠端電腦傳回至本機會話。

```powershell
$cs = New-CimSession -ComputerName RSDGF03
Import-Module -CimSession $cs -Name Storage
# Importing a CIM module, converts the CDXML files for each command into PowerShell scripts.
# These appear as functions in the local session.
Get-Command Get-Disk
```

```Output
CommandType     Name                  ModuleName
-----------     ----                  ----------
Function        Get-Disk              Storage
```

```powershell
# Use implicit remoting to query disks on the remote computer from which the module was imported.
Get-Disk
```

```Output
Number Friendly Name           OperationalStatus  Total Size Partition Style
------ -------------           -----------------  ---------- ---------------
0      Virtual HD ATA Device   Online                  40 GB MBR
```

## PARAMETERS

### -Alias

指定此 Cmdlet 從模組匯入至目前會話的別名。 輸入以逗號分隔的別名清單。 允許使用萬用字元。

當您匯入模組時，某些模組會自動將選取的別名匯出至您的工作階段。
此參數可讓您從匯出的別名中選取。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -ArgumentList

指定在命令期間傳遞至腳本模組的引數或參數值陣列 `Import-Module` 。 只有在匯入腳本模組時，此參數才有效。

您也可以使用其別名（ **args**）來參考 **ArgumentList** 參數。 如需有關 **ArgumentList** 行為的詳細資訊，請參閱 [about_Splatting](about/about_Splatting.md#splatting-with-arrays)。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsCustomObject

指出此 Cmdlet 會傳回自訂物件，其成員代表已匯入的模組成員。 此參數只適用於指令碼模組。

當您使用 **AsCustomObject** 參數時，會將 `Import-Module` 模組成員匯入到會話中，然後傳回 **PSCustomObject** 物件，而非 **PSModuleInfo** 物件。 您可以將自訂物件儲存在變數中，並使用點標記法來叫用成員。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Assembly

指定元件物件的陣列。 此 Cmdlet 會匯入在指定元件物件中執行的 Cmdlet 和提供者。 輸入包含組件物件的變數，或輸入可建立組件物件的命令。 您也可以使用管線將元件物件傳送至 `Import-Module` 。

當您使用此參數時，只會匯入指定組件所實作的 Cmdlet 與提供者。 如果模組包含其他檔案，則不會匯入它們，而且您可能會遺失模組的重要成員。 您可以使用此參數來偵測和測試模組，或在您指示模組作者使用它時使用此參數。

```yaml
Type: System.Reflection.Assembly[]
Parameter Sets: Assembly
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -CimNamespace

指定公開 CIM 模組的替代 CIM 提供者命名空間。 預設值為「模組探索」WMI 提供者的命名空間。

使用此參數從不是執行 Windows 作業系統的電腦和裝置匯入 CIM 模組。

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

指定 CIM 模組的替代位置。 預設值為遠端電腦上「模組探索」 WMI 提供者的資源 URI。

使用此參數從不是執行 Windows 作業系統的電腦和裝置匯入 CIM 模組。

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

指定遠端電腦上的 CIM 工作階段。 輸入包含 CIM 會話的變數，或輸入可取得 CIM 會話的命令，例如 [CimSession](../CimCmdlets/Get-CimSession.md) 命令。

`Import-Module` 使用 CIM 會話連線，從遠端電腦將模組匯入到目前的會話。 當您在目前會話中使用匯入模組的命令時，命令會在遠端電腦上執行。

您可以使用此參數從不是執行 Windows 作業系統的電腦和裝置，以及具有 PowerShell 但未啟用 PowerShell 遠端功能的 Windows 電腦匯入模組。

此參數是在 Windows PowerShell 3.0 引進。

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

### -Cmdlet

指定此 Cmdlet 從模組匯入至目前會話的 Cmdlet 陣列。
允許使用萬用字元。

當您匯入模組時，某些模組會自動將選取的 Cmdlet 匯出至您的工作階段。
此參數可讓您從匯出的 Cmdlet 中選取。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -DisableNameChecking

指出當您匯入的 Cmdlet 或函式的名稱包含未核准的動詞或禁止的字元時，此 Cmdlet 會隱藏警告您的訊息。

依預設，當您匯入的模組會匯出其名稱中具有未核准動詞的 Cmdlet 或函式時，PowerShell 會顯示下列警告訊息：

> 警告：某些匯入的命令名稱包含未核准的動詞命令，可能會讓它們更不容易探索。 請使用 Verbose 參數取得詳細資訊，或輸入 Get-Verb 查看核准的動詞清單。

這則訊息只是一個警告。 模組仍然完整匯入，包括不合格的命令。 雖然訊息是顯示給模組的使用者，但命名的問題應該由模組作者修正。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

此參數會在目前的模組上載入或重載模組。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -FullyQualifiedName

將模組的完整名稱指定為雜湊表。 此值可以是字串和雜湊表的組合。 雜湊表具有下列索引鍵。

- `ModuleName` - **必要** 指定模組名稱。
- `GUID` - **選擇性** 指定模組的 GUID。
- 您也 **必須** 指定下列三個索引鍵中的其中一個。 這些金鑰無法一起使用。
  - `ModuleVersion` -指定模組可接受的最小版本。
  - `RequiredVersion` -指定完全必要的模組版本。
  - `MaximumVersion` -指定模組可接受的最大版本。

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: FullyQualifiedNameAndPSSession, FullyQualifiedName, FullyQualifiedNameAndWinCompat
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Function

指定此 Cmdlet 從模組匯入至目前會話的函式陣列。
允許使用萬用字元。 當您匯入模組時，某些模組會自動將選取的函式匯出至您的工作階段。 此參數可讓您從匯出的函式中選取。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Global

指出此 Cmdlet 會將模組匯入到全域會話狀態，使其可供會話中的所有命令使用。

根據預設，當 `Import-Module` 從命令提示字元、腳本檔或 scriptblock 呼叫 Cmdlet 時，會將所有命令匯入到全域會話狀態。

從其他模組叫用時，Cmdlet 會將 `Import-Module` 模組中的命令（包括從嵌套模組載入的命令）匯入至呼叫模組的會話狀態。

> [!TIP]
> 您應該避免 `Import-Module` 從模組內呼叫。 相反地，請在父模組的資訊清單中，將目的模組宣告為嵌套模組。 宣告嵌套模組可改善相依性的可探索性。

**Global** 參數等同於值為 **Global** 的 **Scope** 參數。

若要限制模組所匯出的命令，請使用 `Export-ModuleMember` 腳本模組中的命令。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumVersion

指定最大版本。 此 Cmdlet 只會匯入小於或等於指定值的模組版本。 如果沒有任何版本符合資格，就會傳回 `Import-Module` 錯誤。

```yaml
Type: System.String
Parameter Sets: Name, PSSession, CimSession, WinCompat
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MinimumVersion

指定最小版本。 此 Cmdlet 只會匯入大於或等於指定值的模組版本。 使用 **MinimumVersion** 參數名稱或它的別名，**Version**。 如果沒有任何版本符合資格，就會 `Import-Module` 產生錯誤。

若要指定確切的版本，請使用 **RequiredVersion** 參數。 您也可以使用 **#Requires** 關鍵字的 **module** 和 **Version** 參數，要求在腳本中使用特定版本的模組。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Version
Parameter Sets: Name, PSSession, CimSession, WinCompat
Aliases: Version

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ModuleInfo

指定要匯入之模組物件的陣列。 輸入包含模組物件的變數，或輸入可取得模組物件的命令，例如下列命令： `Get-Module -ListAvailable` 。 您也可以透過管線將模組物件傳送至 `Import-Module` 。

```yaml
Type: System.Management.Automation.PSModuleInfo[]
Parameter Sets: ModuleInfo
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

指定要匯入之模組的名稱。 輸入模組的名稱或模組中的檔案名，例如 `.psd1` 、、 `.psm1` 或檔案 `.dll` `.ps1` 。 檔案路徑為選擇性。 不允許使用萬用字元。 您也可以透過管線將模組名稱與檔案名傳送至 `Import-Module` 。

如果您省略路徑，會 `Import-Module` 在環境變數中所儲存的路徑中尋找模組 `$env:PSModulePath` 。

盡可能只指定模組名稱。 當您指定檔案名稱時，只會匯入該檔案中實作的成員。 如果模組包含其他檔案，則不會匯入它們，而且您可能會遺失模組的重要成員。

> [!NOTE]
> 雖然可以將腳本 () 檔匯入 `.ps1` 為模組，但腳本檔案通常不像腳本模組檔案 () 檔一樣 `.psm1` 。 匯入腳本檔案並不保證可作為模組使用。 如需詳細資訊，請參閱 [about_Modules](about/about_Modules.md)。

```yaml
Type: System.String[]
Parameter Sets: Name, PSSession, CimSession, WinCompat
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### -NoClobber

防止匯入與目前會話中現有命令具有相同名稱的命令。 預設會匯 `Import-Module` 入所有匯出的模組命令。

具有相同名稱的命令可以隱藏或取代會話中的命令。 為避免工作階段中發生命令名稱衝突，請使用 **Prefix** 或 **NoClobber** 參數。 如需名稱衝突和命令優先順序的詳細資訊，請參閱 [about_Modules](about/about_Modules.md) 中的「模組和名稱衝突」和 [about_Command_Precedence](about/about_Command_Precedence.md)。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

傳回代表您正在使用之專案的物件。 根據預設，此 Cmdlet 不會產生任何輸出。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -前置詞

指定此 Cmdlet 在匯入的模組成員名稱中新增至名詞的前置詞。

使用此參數來避免工作階段中不同成員具有相同名稱時可能會發生的名稱衝突。 此參數不會變更模組，而且不會影響模組匯入以供自己使用的檔案。 這些稱為「嵌套模組」。 此 Cmdlet 只會影響目前會話中的成員名稱。

例如，如果您指定首碼 UTC，然後匯入 `Get-Date` Cmdlet，則此 Cmdlet 在會話中會是已知的 `Get-UTCDate` ，且不會與原始的 Cmdlet 混淆 `Get-Date` 。

此參數的值優先順序高於模組中指定預設前置詞的 **DefaultCommandPrefix** 屬性。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PSSession

指定 PowerShell 使用者管理的會話 (**PSSession**) ，此 Cmdlet 會將模組匯入目前的會話中。 輸入包含 **pssession** 的變數，或輸入可取得 **pssession** 的命令，例如 `Get-PSSession` 命令。

當您將不同工作階段的模組匯入到目前工作階段時，您可以使用目前的工作階段之模組的 Cmdlet，就如同您使用本機模組的 Cmdlet 一樣。 使用遠端 Cmdlet 的命令會在遠端會話中執行，但遠端處理詳細資料是由 PowerShell 在背景中管理。

此參數會使用 PowerShell 的隱含遠端功能。 它相當於使用指令程式 `Import-PSSession` 從會話匯入特定模組。

`Import-Module` 無法從另一個會話匯入 PowerShell Core 模組。 PowerShell Core 的模組都有以 Microsoft. PowerShell 開頭的名稱。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: PSSession, FullyQualifiedNameAndPSSession
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredVersion

指定此 Cmdlet 匯入之模組的版本。 如果未安裝該版本，則會 `Import-Module` 產生錯誤。

根據預設，匯 `Import-Module` 入模組時不會檢查版本號碼。

若要指定最小版本，請使用 **MinimumVersion** 參數。 您也可以使用 **#Requires** 關鍵字的 **module** 和 **Version** 參數，要求在腳本中使用特定版本的模組。

此參數是在 Windows PowerShell 3.0 引進。

使用 **RequiredVersion** 匯入隨附于現有 windows 作業系統版本之模組的腳本，不會在未來的 windows 作業系統版本中自動執行。 這是因為在未來的 Windows 作業系統版本中，PowerShell 模組版本號碼高於現有 Windows 作業系統版本中的模組版本號碼。

```yaml
Type: System.Version
Parameter Sets: Name, PSSession, CimSession, WinCompat
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Scope

指定此 Cmdlet 匯入模組的範圍。

此參數可接受的值為：

- **Global**。 適用於工作階段中的所有命令。 等同於 **Global** 參數。
- **本機**。 只適用於目前的範圍。

根據預設，當 `Import-Module` 從命令提示字元、腳本檔或 scriptblock 呼叫 Cmdlet 時，會將所有命令匯入到全域會話狀態。 您可以使用 `-Scope Local` 參數將模組內容匯入至腳本或 scriptblock 範圍中。

從其他模組叫用時，Cmdlet 會將 `Import-Module` 模組中的命令（包括從嵌套模組載入的命令）匯入至呼叫端的會話狀態。 指定 `-Scope Global` 或 `-Global` 表示此 Cmdlet 會將模組匯入到全域會話狀態，使其可供會話中的所有命令使用。

**Global** 參數等同於值為 **Global** 的 **Scope** 參數。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Local, Global

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Variable

指定此 Cmdlet 從模組匯入至目前會話的變數陣列。
輸入變數的清單。 允許使用萬用字元。

當您匯入模組時，某些模組會自動將選取的變數匯出至您的工作階段。
此參數可讓您從匯出的變數中選取。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -SkipEditionCheck

略過欄位的檢查 `CompatiblePSEditions` 。

`"$($env:windir)\System32\WindowsPowerShell\v1.0\Modules"`當模組未 `Core` 在資訊清單欄位中指定時，允許從模組目錄將模組載入至 PowerShell Core `CompatiblePSEditions` 。

從另一個路徑匯入模組時，此參數不會執行任何動作，因為不會執行檢查。 在 Linux 和 macOS 上，此參數不會執行任何動作。

如需詳細資訊，請參閱 [about_PowerShell_Editions](About/about_PowerShell_Editions.md)。

> [!WARNING]
> `Import-Module -SkipEditionCheck` 仍可能無法匯入模組。 即使成功，叫用模組中的命令稍後可能會在嘗試使用不相容的 API 時失敗。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Name, PSSession, CimSession, FullyQualifiedNameAndPSSession, FullyQualifiedName, Assembly, ModuleInfo
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseWindowsPowerShell

使用 Windows PowerShell 相容性功能載入模組。 如需詳細資訊，請參閱 [about_Windows_PowerShell_Compatibility](About/about_Windows_PowerShell_Compatibility.md) 。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WinCompat, FullyQualifiedNameAndWinCompat
Aliases: UseWinPS

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.string，PSModuleInfo，System.string. Assembly （系統）

您可以使用管線將模組名稱、模組物件或元件物件傳送至此 Cmdlet。

## 輸出

### None、PSModuleInfo 或 PSCustomObject，或 Automation。

依預設，不 `Import-Module` 會產生任何輸出。 如果您指定 **PassThru** 參數，此 Cmdlet 會產生代表模組的 **PSModuleInfo** 物件。 如果您指定 **AsCustomObject** 參數，它會產生 **PSCustomObject** 物件。

## 注意

- 您必須先將模組安裝在本機電腦上，才能匯入模組。 也就是說，必須將模組目錄複寫到本機電腦可以存取的目錄中。 如需詳細資訊，請參閱 [about_Modules](About/about_Modules.md)。

  您也可以使用 **PSSession** 和 **CIMSession** 參數，匯入在遠端電腦安裝的模組。 不過，在這些模組中使用 Cmdlet 的命令會在遠端電腦上的遠端會話中執行。

- 如果您將具有相同名稱和相同類型的成員匯入到您的會話中，則 PowerShell 預設會使用最後匯入的成員。 變數和別名會被取代，而且無法存取原始變數和別名。 函式、Cmdlet 和提供者只會由新成員遮蔽。 您可以使用嵌入式管理單元、模組或函式路徑的名稱來限定命令名稱來存取它們。

- 若要更新已從模組匯入之命令的格式設定資料，請使用 `Update-FormatData` Cmdlet。 `Update-FormatData` 也會在會話中，針對從模組匯入的命令更新格式化資料。 如果模組的格式化檔案變更，您可以執行 `Update-FormatData` 命令來更新匯入命令的格式化資料。 您不需要再次匯入模組。

- 從 Windows PowerShell 3.0 開始，隨 PowerShell 安裝的核心命令會封裝在模組中。 在 Windows PowerShell 2.0，以及在較新版本的 PowerShell 中建立舊版會話的主機程式中，會將核心命令封裝在嵌入式管理單元中， (**PSSnapins**) 。 **Microsoft.PowerShell.Core** 是一個例外，它一律是一個嵌入式管理單元。 此外，遠端會話（例如由 Cmdlet 啟動的會話） `New-PSSession` 都是包含核心嵌入式管理單元的較舊樣式會話。

  如需使用核心模組建立較新樣式會話之 **CreateDefault2** 方法的詳細資訊，請參閱 [CreateDefault2 方法](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2)。

- 在 Windows PowerShell 2.0 中，模組物件的某些屬性值（例如 **ExportedCmdlets** 和 **NestedModules** 屬性值），在匯入模組之前都不會填入。

- 如果您嘗試匯入包含與 Windows PowerShell 3.0 + 不相容之混合模式元件的模組，則會傳回 `Import-Module` 類似下列的錯誤訊息。

  > Import-Module：混合模式元件是針對執行時間的版本 ' v 2.0.50727 ' 所建立，而且無法在4.0 執行時間中載入，而不需要額外的設定資訊。

  針對 Windows PowerShell 2.0 設計的模組至少包含一個混合模組元件時，就會發生此錯誤。 混合模組元件，其中包括 managed 和非 managed 程式碼，例如 c + + 和 c #。

  若要匯入包含混合模式元件的模組，請使用下列命令啟動 Windows PowerShell 2.0，然後 `Import-Module` 再次嘗試命令。

  `PowerShell.exe -Version 2.0`

- 若要使用 CIM 工作階段功能，遠端電腦必須具備 WS-Management 遠端功能和 Windows Management Instrumentation (WMI)，這是 Microsoft 實作的「通用訊息模型 (CIM)」標準。 電腦也必須擁有具有相同基本功能的「模組探索」WMI 提供者或替代 CIM 提供者。

  您可以在不是執行 Windows 作業系統的電腦上，以及在具有 PowerShell 但未啟用 PowerShell 遠端功能的 Windows 電腦上，使用 CIM 會話功能。

  您也可以使用 CIM 參數，從已啟用 PowerShell 遠端功能的電腦（包括本機電腦）取得 CIM 模組。 當您在本機電腦上建立 CIM 會話時，PowerShell 會使用 DCOM （而不是 WMI）來建立會話。

- 根據預設，會 `Import-Module` 在全域範圍內匯入模組，即使是從子系範圍呼叫也一樣。 最上層範圍和所有子代範圍都可以存取模組的匯出元素。

  在子代範圍中， `-Scope Local` 將匯入限制在該範圍及其所有子系範圍內。 父範圍接著看不到匯入的成員。

  > [!NOTE]
  > `Get-Module` 顯示目前會話中載入的所有模組。 這包括在子系範圍中本機載入的模組。 使用 `Get-Command -Module modulename` 以查看哪些成員會在目前的範圍中載入。

  `Import-Module` 未在模組中載入類別和列舉定義。 使用 `using module` 腳本開頭的語句。 這會匯入模組，包括類別和列舉定義。 如需詳細資訊，請參閱 [about_Using](About/about_Using.md)。

## 相關連結

[about_Modules](about/about_Modules.md)

[Export-ModuleMember](Export-ModuleMember.md)

[Get-Module](Get-Module.md)

[New-Module](New-Module.md)

[Remove-Module](Remove-Module.md)

[about_PowerShell_Editions](About/about_PowerShell_Editions.md)
