---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/24/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssessionconfigurationfile?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSessionConfigurationFile
ms.openlocfilehash: 4f326fcfb2c2af6816ae7cc58f12699e748f163a
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201624"
---
# New-PSSessionConfigurationFile

## 概要
建立定義工作階段設定的檔案。

## SYNTAX

```
New-PSSessionConfigurationFile [-Path] <String> [-SchemaVersion <Version>] [-Guid <Guid>]
 [-Author <String>] [-Description <String>] [-CompanyName <String>] [-Copyright <String>]
 [-SessionType <SessionType>] [-TranscriptDirectory <String>] [-RunAsVirtualAccount]
 [-RunAsVirtualAccountGroups <String[]>] [-MountUserDrive] [-UserDriveMaximumSize <Int64>]
 [-GroupManagedServiceAccount <String>] [-ScriptsToProcess <String[]>]
 [-RoleDefinitions <IDictionary>] [-RequiredGroups <IDictionary>] [-LanguageMode <PSLanguageMode>]
 [-ExecutionPolicy <ExecutionPolicy>] [-PowerShellVersion <Version>] [-ModulesToImport <Object[]>]
 [-VisibleAliases <String[]>] [-VisibleCmdlets <Object[]>] [-VisibleFunctions <Object[]>]
 [-VisibleExternalCommands <String[]>] [-VisibleProviders <String[]>]
 [-AliasDefinitions <IDictionary[]>] [-FunctionDefinitions <IDictionary[]>]
 [-VariableDefinitions <Object>] [-EnvironmentVariables <IDictionary>] [-TypesToProcess <String[]>]
 [-FormatsToProcess <String[]>] [-AssembliesToLoad <String[]>] [-Full] [<CommonParameters>]
```

## DESCRIPTION

此 `New-PSSessionConfigurationFile` Cmdlet 會建立設定的檔案，這些設定會定義會話設定，以及使用會話設定建立之會話的環境。
若要在會話設定中使用此檔案，請使用或 Cmdlet 的 **Path** 參數 `Register-PSSessionConfiguration` `Set-PSSessionConfiguration` 。

建立的會話設定檔 `New-PSSessionConfigurationFile` 是人們可讀取的文字檔，其中包含會話設定屬性和值的雜湊表。 檔案的副檔名為 `.pssc` 副檔名。

的所有參數 `New-PSSessionConfigurationFile` 都是選擇性的，但 **Path** 參數除外。
如果您省略某個參數，除了在參數描述中註明之外，將會在工作階段設定檔中相對應的索引鍵上加上註解使它無效。

會話設定（也稱為端點）是本機電腦上的一組設定集合，用來定義 PowerShell 會話的環境， ( **pssession** ) 連接到電腦。 所有 **pssession** 都會使用會話設定。 若要指定特定的會話設定，請使用建立會話之 Cmdlet 的 **ConfigurationName** 參數，例如 `New-PSSession` Cmdlet。

session configuration file 不需要複雜的指令碼或程式碼組件，就能輕鬆定義工作階段設定。 檔案中的設定會搭配選用的啟動腳本和會話設定中的任何元件使用。

如需會話設定和會話設定檔的詳細資訊，請參閱 [about_Session_Configurations](About/about_Session_Configurations.md) 和 [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)。

此 Cmdlet 是在 PowerShell 3.0 中引進。

## 範例

### 範例1：建立和使用 NoLanguage 會話

這個範例示範如何建立使用無語言會話的效果。

步驟包括：

1. 建立新的設定檔。
1. 註冊設定。
1. 建立使用設定的新會話。
1. 在新的會話中執行命令。

若要執行此範例中的命令，請使用 [以系統管理員身分執行] 選項啟動 PowerShell。 需要此選項才能執行 `Register-PSSessionConfiguration` Cmdlet。

```powershell
New-PSSessionConfigurationFile -Path .\NoLanguage.pssc -LanguageMode NoLanguage
Register-PSSessionConfiguration -Path .\NoLanguage.pssc -Name NoLanguage -Force
$NoLanguageSession = New-PSSession -ComputerName Srv01 -ConfigurationName NoLanguage
Invoke-Command -Session $NoLanguageSession -ScriptBlock {
  if ((Get-Date) -lt '1January2099') {'Before'} else {'After'}
}
```

```Output
The syntax is not supported by this runspace. This might be because it is in no-language mode.
    + CategoryInfo          : ParserError: (if ((Get-Date) ...') {'Before'}  :String) [], ParseException
    + FullyQualifiedErrorId : ScriptsNotAllowed
    + PSComputerName        : localhost
```

在此範例中， `Invoke-Command` 因為 **LanguageMode** 設定為 **NoLanguage** ，所以失敗。

### 範例2：建立和使用 RestrictedLanguage 會話

這個範例示範如何建立使用無語言會話的效果。

步驟包括：

1. 建立新的設定檔。
1. 註冊設定。
1. 建立使用設定的新會話。
1. 在新的會話中執行命令。

若要執行此範例中的命令，請使用 [以系統管理員身分執行] 選項啟動 PowerShell。 需要此選項才能執行 `Register-PSSessionConfiguration` Cmdlet。

```powershell
New-PSSessionConfigurationFile -Path .\NoLanguage.pssc -LanguageMode RestrictedLanguage
Register-PSSessionConfiguration -Path .\NoLanguage.pssc -Name RestrictedLanguage -Force
$RestrictedSession = New-PSSession -ComputerName Srv01 -ConfigurationName RestrictedLanguage
Invoke-Command -Session $RestrictedSession -ScriptBlock {
  if ((Get-Date) -lt '1January2099') {'Before'} else {'After'}
}
```

```Output
Before
```

在此範例中， `Invoke-Command` 會成功，因為 **LanguageMode** 設定為 **RestrictedLanguage** 。

### 範例3：變更會話設定檔

此範例顯示如何變更在名為 "ITTasks" 的現有會話中使用的會話設定檔。 之前，這些會話只有核心模組和內部 **ITTasks** 模組。 系統管理員想要將 **PSScheduledJob** 模組新增至使用 ITTasks 會話設定建立的會話。

```powershell
New-PSSessionConfigurationFile -Path .\New-ITTasks.pssc -ModulesToImport Microsoft*, ITTasks, PSScheduledJob
Set-PSSessionConfiguration -Name ITTasks -Path .\New-ITTasks.pssc
```

此 `New-PSSessionConfigurationFile` Cmdlet 會建立可匯入必要模組的會話設定檔。 Cmdlet 會將 `Set-PSSessionConfiguration` 目前的設定檔取代為新的設定檔。 這種新設定只會影響變更後所建立的新會話。
現有的「ITTasks」會話不會受到影響。

### 範例4：編輯會話設定檔

此範例說明如何透過編輯設定檔的使用中工作階段設定複本，來變更工作階段設定。 若要修改設定檔的會話設定複本，您必須擁有該檔案的「完全控制」存取權限。 這可能需要您變更檔案的許可權。

在此案例中，我們想要藉 `Select-String` 由編輯使用中的設定檔來新增 Cmdlet 的別名。

下列程式碼範例會執行下列步驟來進行這項變更：

1. 取得 ITConfig 會話的設定檔路徑。
1. 使用者使用 **Notepad.exe** 編輯設定檔，以變更 **AliasDefinitions** 值，如下所示： `AliasDefinitions = @(@{Name='slst';Value='Select-String'})` 。
1. 測試已更新的設定檔。

```powershell
$ITConfig = Get-PSSessionConfiguration -Name ITConfig
notepad.exe $ITConfig.ConfigFilePath
Test-PSSessionConfigurationFile -Path $ITConfig.ConfigFilePath
```

```Output
True
```

使用 **Verbose** 參數搭配 `Test-PSSessionConfigurationFile` 來顯示任何偵測到的錯誤。 `$True`如果未在檔案中偵測到錯誤，則 Cmdlet 會傳回。

### 範例5：建立範例設定檔

此範例顯示 `New-PSSessionConfigurationFile` 使用所有 Cmdlet 參數的命令。
它也會顯示每個參數的正確輸入格式。

輸出中會顯示產生的 SampleFile.pssc。

```powershell
$configSettings = @{
    Path = '.\SampleFile.pssc'
    SchemaVersion = '1.0.0.0'
    Author = 'User01'
    Copyright = '(c) Fabrikam Corporation. All rights reserved.'
    CompanyName = 'Fabrikam Corporation'
    Description = 'This is a sample file.'
    ExecutionPolicy = 'AllSigned'
    PowerShellVersion = '3.0'
    LanguageMode = 'FullLanguage'
    SessionType = 'Default'
    EnvironmentVariables = @{TESTSHARE='\\Test2\Test'}
    ModulesToImport = @{ModuleName='PSScheduledJob'; ModuleVersion='1.0.0.0'; GUID='50cdb55f-5ab7-489f-9e94-4ec21ff51e59'},'PSDiagnostics'
    AssembliesToLoad = 'System.Web.Services','FSharp.Compiler.CodeDom.dll'
    TypesToProcess = 'Types1.ps1xml','Types2.ps1xml'
    FormatsToProcess = 'CustomFormats.ps1xml'
    ScriptsToProcess = 'Get-Inputs.ps1'
    AliasDefinitions = @{Name='hlp';Value='Get-Help';Description='Gets help.';Options='AllScope'},
        @{Name='Update';Value='Update-Help';Description='Updates help';Options='ReadOnly'}
    FunctionDefinitions = @{Name='Get-Function';ScriptBlock={Get-Command -CommandType Function};Options='ReadOnly'}
    VariableDefinitions = @{Name='WarningPreference';Value='SilentlyContinue'}
    VisibleAliases = 'c*','g*','i*','s*'
    VisibleCmdlets = 'Get*'
    VisibleFunctions = 'Get*'
    VisibleProviders = 'FileSystem','Function','Variable'
    RunAsVirtualAccount = $true
    RunAsVirtualAccountGroups = 'Backup Operators'
}
New-PSSessionConfigurationFile @configSettings
Get-Content SampleFile.pssc
```

```Output
@{

# Version number of the schema used for this document
SchemaVersion = '1.0.0.0'

# ID used to uniquely identify this document
GUID = '1caeff7f-27ca-4360-97cf-37846f594235'

# Author of this document
Author = 'User01'

# Description of the functionality provided by these settings
Description = 'This is a sample file.'

# Company associated with this document
CompanyName = 'Fabrikam Corporation'

# Copyright statement for this document
Copyright = '(c) Fabrikam Corporation. All rights reserved.'

# Session type defaults to apply for this session configuration. Can be 'RestrictedRemoteServer' (recommended), 'Empty', or 'Default'
SessionType = 'Default'

# Directory to place session transcripts for this session configuration
# TranscriptDirectory = 'C:\Transcripts\'

# Whether to run this session configuration as the machine's (virtual) administrator account
RunAsVirtualAccount = $true

# Groups associated with machine's (virtual) administrator account
RunAsVirtualAccountGroups = 'Backup Operators'

# Scripts to run when applied to a session
ScriptsToProcess = 'Get-Inputs.ps1'

# User roles (security groups), and the role capabilities that should be applied to them when applied to a session
# RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\SqlManaged' = @{ RoleCapabilityFiles = 'C:\RoleCapability\SqlManaged.psrc' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }

# Language mode to apply when applied to a session. Can be 'NoLanguage' (recommended), 'RestrictedLanguage', 'ConstrainedLanguage', or 'FullLanguage'
LanguageMode = 'FullLanguage'

# Execution policy to apply when applied to a session
ExecutionPolicy = 'AllSigned'

# Version of the PowerShell engine to use when applied to a session
PowerShellVersion = '3.0'

# Modules to import when applied to a session
ModulesToImport = @{
    'GUID' = '50cdb55f-5ab7-489f-9e94-4ec21ff51e59'
    'ModuleName' = 'PSScheduledJob'
    'ModuleVersion' = '1.0.0.0' }, 'PSDiagnostics'

# Aliases to make visible when applied to a session
VisibleAliases = 'c*', 'g*', 'i*', 's*'

# Cmdlets to make visible when applied to a session
VisibleCmdlets = 'Get*'

# Functions to make visible when applied to a session
VisibleFunctions = 'Get*'

# Providers to make visible when applied to a session
VisibleProviders = 'FileSystem', 'Function', 'Variable'

# Aliases to be defined when applied to a session
AliasDefinitions = @{
    'Description' = 'Gets help.'
    'Name' = 'hlp'
    'Options' = 'AllScope'
    'Value' = 'Get-Help' }, @{
    'Description' = 'Updates help'
    'Name' = 'Update'
    'Options' = 'ReadOnly'
    'Value' = 'Update-Help' }

# Functions to define when applied to a session
FunctionDefinitions = @{
    'Name' = 'Get-Function'
    'Options' = 'ReadOnly'
    'ScriptBlock' = {Get-Command -CommandType Function} }

# Variables to define when applied to a session
VariableDefinitions = @{
    'Name' = 'WarningPreference'
    'Value' = 'SilentlyContinue' }

# Environment variables to define when applied to a session
EnvironmentVariables = @{
    'TESTSHARE' = '\\Test2\Test' }

# Type files (.ps1xml) to load when applied to a session
TypesToProcess = 'Types1.ps1xml', 'Types2.ps1xml'

# Format files (.ps1xml) to load when applied to a session
FormatsToProcess = 'CustomFormats.ps1xml'

# Assemblies to load when applied to a session
AssembliesToLoad = 'System.Web.Services', 'FSharp.Compiler.CodeDom.dll'

}
```

## PARAMETERS

### -AliasDefinitions

將指定的別名新增至使用工作階段設定的工作階段。 輸入包含下列索引鍵的雜湊表：

- 名稱-別名的名稱。 此為必要索引鍵。
- Value-別名所代表的命令。 此為必要索引鍵。
- 描述-描述別名的文字字串。 此為選擇性索引鍵。
- 選項-別名選項。 此為選擇性索引鍵。 預設值為 **None** 。 此參數可接受的值為： None、ReadOnly、常數、私用或 AllScope。

例如：`@{Name='hlp';Value='Get-Help';Description='Gets help';Options='ReadOnly'}`

```yaml
Type: System.Collections.IDictionary[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AssembliesToLoad

指定要載入至使用工作階段設定之工作階段的組件。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -作者

指定會話設定或設定檔案的作者。 預設為目前使用者。 此參數的值會出現在工作階段設定中，但它不是工作階段物件的屬性。

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

### -公司名稱

指定建立會話設定或設定檔的公司。 預設值為 [未知]  。 此參數的值會出現在工作階段設定中，但它不是工作階段物件的屬性。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Unknown
Accept pipeline input: False
Accept wildcard characters: False
```

### -著作權

指定會話設定檔的著作權。 此參數的值會出現在工作階段設定中，但它不是工作階段物件的屬性。

如果您省略此參數，則會 `New-PSSessionConfigurationFile` 使用 **Author** 參數的值產生著作權語句。

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

### -Description

指定會話設定或會話設定檔的描述。 此參數的值會出現在工作階段設定中，但它不是工作階段物件的屬性。

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

### -EnvironmentVariables

新增環境變數至工作階段。 輸入雜湊表，其中索引鍵為環境變數名稱，值為環境變數值。

例如：`EnvironmentVariables=@{TestShare='\\Server01\TestShare'}`

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ExecutionPolicy

指定使用工作階段設定之工作階段的執行原則。 如果您省略此參數，會話設定檔中的 **ExecutionPolicy** 索引鍵值會 **受到限制** 。 如需 PowerShell 中執行原則的詳細資訊，請參閱 [about_Execution_Policies](about/about_Execution_Policies.md)。

```yaml
Type: Microsoft.PowerShell.ExecutionPolicy
Parameter Sets: (All)
Aliases:
Accepted values: Unrestricted, RemoteSigned, AllSigned, Restricted, Default, Bypass, Undefined

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FormatsToProcess

指定在使用工作階段設定的工作階段中執行的格式化檔案 (.ps1xml)。
此參數的值必須是格式化檔案的完整路徑或絕對路徑。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Full

指出此作業會在會話設定檔中包含所有可能的設定屬性。

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

### -FunctionDefinitions

將指定函式新增至使用工作階段設定的工作階段。 輸入包含下列索引鍵的雜湊表：

- 名稱-函數的名稱。 此為必要索引鍵。
- ScriptBlock 函數主體。 輸入指令碼區塊。 此為必要索引鍵。
- 選項功能選項。 此為選擇性索引鍵。 預設值為 **None** 。 此參數可接受的值為： None、ReadOnly、常數、私用或 AllScope。

例如：`@{Name='Get-PowerShellProcess';ScriptBlock={Get-Process PowerShell};Options='AllScope'}`

```yaml
Type: System.Collections.IDictionary[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Msds-groupmanagedserviceaccount

使用此會話設定來設定會話，以在指定群組受管理的服務帳戶的內容下執行。 註冊此會話設定的電腦必須具有要求 gMSA 密碼的許可權，才能成功建立會話。 這個欄位不能搭配 **將 runasvirtualaccount 設** 參數使用。

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

### -Guid

指定工作階段設定檔的唯一識別碼。 如果您省略此參數，則會產生檔案的 `New-PSSessionConfigurationFile` GUID。 若要在 PowerShell 中建立新的 GUID，請輸入 `New-Guid` 。

```yaml
Type: System.Guid
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LanguageMode

判斷使用此會話設定的會話中允許的 PowerShell 語言元素。 您可以使用此參數來限制特定使用者可在電腦上執行的命令。

此參數可接受的值為：

- >fulllanguage-允許所有語言元素。
- ConstrainedLanguage：不允許包含要評估之腳本的命令。 ConstrainedLanguage 模式會限制使用者存取 Microsoft .NET Framework 類型、物件或方法。
- NoLanguage-使用者可以執行 Cmdlet 和函式，但不允許使用任何語言專案，例如腳本區塊、變數或運算子。
- RestrictedLanguage-使用者可以執行 Cmdlet 和函式，但不允許使用腳本區塊或變數，除了下列允許的變數： `$PSCulture` 、 `$PSUICulture` 、 `$True` 、 `$False` 和 `$Null` 。 使用者只能使用基本的比較運算子 (`-eq` 、 `-gt` `-lt`) 。 不允許指派陳述式、屬性參照及方法呼叫。

**LanguageMode** 參數的預設值需視 **SessionType** 參數的值而定。

- 空白-NoLanguage
- RestrictedRemoteServer-NoLanguage
- 預設值->fulllanguage

```yaml
Type: System.Management.Automation.PSLanguageMode
Parameter Sets: (All)
Aliases:
Accepted values: FullLanguage, RestrictedLanguage, NoLanguage, ConstrainedLanguage

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ModulesToImport

指定要自動匯入使用工作階段設定之工作階段的模組和嵌入式管理單元。

依預設，只會將 **Microsoft 的 PowerShell** 嵌入式管理單元匯入至遠端會話，但除非排除 Cmdlet，否則使用者可以使用 `Import-Module` 和 `Add-PSSnapin` Cmdlet 將模組和嵌入式管理單元新增至會話。

此參數值中的每個模組或嵌入式管理單元都可以用字串或雜湊表代表。 模組字串只包含模組或嵌入式管理單元的名稱。 模組雜湊表可包括 **ModuleName** 、 **ModuleVersion** 和 **GUID** 索引鍵。 只有 **ModuleName** 索引鍵是必要的。

例如，以下的值包含字串和雜湊表。 字串或雜湊表以任何順序組成的任何組合都是有效的。

`'TroubleshootingPack', @{ModuleName='PSDiagnostics'; ModuleVersion='1.0.0.0';GUID='c61d6278-02a3-4618-ae37-a524d40a7f44'}`

Cmdlet 的 **ModulesToImport** 參數值 `Register-PSSessionConfiguration` 優先順序高於會話設定檔中的 **ModulesToImport** 索引鍵值。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MountUserDrive

設定使用此會話設定的會話，以公開 `User:` new-psdrive。 使用者磁片磁碟機對於每個連線的使用者都是唯一的，而且即使檔案系統提供者未公開，也可讓使用者在 PowerShell 端點之間複製資料。 建立使用者磁片磁碟機根目錄 `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\` 。 對於每位連線到端點的使用者，都會建立名為 `$env:USERDOMAIN_$env:USERNAME` 的資料夾。

使用者磁片磁碟機中的內容會在使用者會話中保存，且不會自動移除。 根據預設，使用者只能在使用者磁片磁碟機中儲存最多50MB 的資料。 您可以使用 **UserDriveMaximumSize** 參數自訂此參數。

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

### -Path

指定會話設定檔的路徑和檔案名。 檔案的副檔名必須是 `.pssc` 副檔名。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PowerShellVersion

在使用會話設定的會話中指定 PowerShell 引擎的版本。 此參數可接受的值為：2.0 和3.0。 如果您省略此參數，則會將 **PowerShellVersion** 金鑰批註化，並在會話中執行最新版的 PowerShell。

Cmdlet 的 **PSVersion** 參數值 `Register-PSSessionConfiguration` 優先順序高於會話設定檔中的 **PowerShellVersion** 索引鍵值。

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredGroups

為連接到使用此會話設定之會話的使用者指定條件式存取規則。

輸入雜湊表，以使用每個雜湊表 ' 和 ' 或 ' Or ' 的1個索引鍵來撰寫規則清單，然後將值設定為安全性群組名稱或其他雜湊表的陣列。

要求將使用者連接到單一群組成員的範例： `@{ And = 'MyRequiredGroup' }`

要求使用者屬於群組 A （或群組 B 和 C）以存取端點的範例： `@{ Or = 'GroupA', @{ And = 'GroupB', 'GroupC' } }`

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RoleDefinitions

指定安全性群組 (或使用者) 與角色功能之間的對應。 使用者將被授與在會話建立時套用至其群組成員資格的所有角色功能的存取權。

輸入雜湊表，其中索引鍵為安全性群組的名稱，而值為雜湊表，其中包含應提供給安全性群組的角色功能清單。

例如：`@{'Contoso\Level 2 Helpdesk Users' = @{ RoleCapabilities = 'Maintenance', 'ADHelpDesk' }}`

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -將 runasvirtualaccount 設

設定使用此會話設定的會話，以電腦的 (virtual) 系統管理員帳戶執行。 這個欄位不能搭配 **msds-groupmanagedserviceaccount** 參數使用。

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

### -RunAsVirtualAccountGroups

當使用會話設定的會話以虛擬帳戶的形式執行時，指定要與虛擬帳戶相關聯的安全性群組。 如果省略，虛擬帳戶屬於網域控制站上的 Domain Admins 和所有其他電腦上的系統管理員。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SchemaVersion

指定工作階段設定檔架構的版本。 預設值為 "1.0.0.0"。

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptsToProcess

將指定指令碼新增至使用工作階段設定的工作階段。 輸入指令碼的路徑和檔案名稱。 此參數的值必須是指令檔名的完整路徑或絕對路徑。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SessionType

指定使用工作階段設定建立之工作階段的類型。 預設值為 Default。 此參數可接受的值為：

- 空白-預設不會將任何模組新增至會話。 使用此 Cmdlet 的參數將模組、函式、指令碼及其他功能新增至工作階段。 此選項的設計目的是要讓您藉由新增選取的命令來建立自訂會話。 如果您沒有新增命令至空的工作階段，工作階段會限制只能使用運算式，因此可能無法使用。
- 預設值-將 Microsoft. Core 模組新增至會話。 此模組包含 `Import-Module` 使用者可以用來匯入其他模組的 Cmdlet，除非您明確禁止此 Cmdlet。
- RestrictedRemoteServer. 只包含下列 proxy 函數： `Exit-PSSession` 、 `Get-Command` 、 `Get-FormatData` 、 `Get-Help` 、 `Measure-Object` 、 `Out-Default` 和 `Select-Object` 。
  使用此 Cmdlet 的參數將模組、函式、指令碼及其他功能新增至工作階段。

```yaml
Type: System.Management.Automation.Remoting.SessionType
Parameter Sets: (All)
Aliases:
Accepted values: Empty, RestrictedRemoteServer, Default

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TranscriptDirectory

指定使用此會話設定為會話放置會話文字記錄的目錄。

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

### -TypesToProcess

將指定的 `.ps1xml` 類型檔案加入至使用會話設定的會話。 輸入類型檔案名。 此參數的值必須是類型檔案名的完整路徑或絕對路徑。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UserDriveMaximumSize

指定在使用此會話設定的會話中，所公開使用者磁片磁碟機的大小上限。
若省略，則會50MB 每個 `User:` 磁片磁碟機根目錄的預設大小。

此參數應與 **MountUserDrive** 搭配使用。

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -VariableDefinitions

將指定變數新增至使用工作階段設定的工作階段。 輸入包含下列索引鍵的雜湊表：

- 名稱：變數的名稱。 此為必要索引鍵。
- 值變數值。 此為必要索引鍵。
- 選項-變數選項。 此為選擇性索引鍵。 預設值為 **None** 。 此參數可接受的值為： None、ReadOnly、常數、私用或 AllScope。

例如：`@{Name='WarningPreference';Value='SilentlyContinue';Options='AllScope'}`

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Visiblealiase

將工作階段中的別名限制為此參數的值中指定的別名，以及您在 **AliasDefinition** 參數中定義的任何別名。 支援使用萬用字元。 根據預設，會話中會顯示所有由 PowerShell 引擎定義的別名，以及模組匯出的所有別名。

例如：`VisibleAliases='gcm', 'gp'`

當會話設定檔中包含任何 **可見** 的參數時，PowerShell 會 `Import-Module` 從會話中移除此 Cmdlet 和其 ipmo 別名。

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

### -VisibleCmdlets

將工作階段中的 Cmdlet 限制為此參數的值中指定的 Cmdlet。 支援萬用字元和模組限定名稱。

根據預設，在工作階段中可以看見工作階段中的模組匯出的所有 Cmdlet。 使用 **SessionType** 和 **ModulesToImport** 參數決定要在工作階段中匯入哪些模組和嵌入式管理單元。 如果 **ModulesToImport** 中沒有任何模組公開 Cmdlet，則會嘗試自動載入適當的模組。

當會話設定檔中包含任何 **可見** 的參數時，PowerShell 會 `Import-Module` 從會話中移除此 Cmdlet 和其 ipmo 別名。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -了 visibleexternalcommands

將會話中可執行檔外部二進位檔、腳本和命令限制為此參數值中指定的二進位檔、腳本和命令。 支援使用萬用字元。

依預設，會話中不會顯示任何外部命令。

當會話設定檔中包含任何 **可見** 的參數時，PowerShell 會 `Import-Module` 從會話中移除 Cmdlet 和其 ipmo 別名。

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

### -VisibleFunctions

將工作階段中的函式限制為此參數的值中指定的函式，以及您在 **FunctionDefinition** 參數中定義的任何函式。 支援使用萬用字元。

根據預設，在工作階段中可以看見工作階段中的模組匯出的所有函式。 使用 **SessionType** 和 **ModulesToImport** 參數決定要在工作階段中匯入哪些模組和嵌入式管理單元。

當會話設定檔中包含任何 **可見** 的參數時，PowerShell 會 `Import-Module` 從會話中移除此 Cmdlet 和其 ipmo 別名。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -VisibleProviders

將會話中的 PowerShell 提供者限制為此參數的值中指定的提供者。
支援使用萬用字元。

根據預設，在工作階段中可以看見工作階段中的模組匯出的所有提供者。 您可以使用 **SessionType** 和 **ModulesToImport** 參數來判斷要將哪些模組匯入到會話中。

當會話設定檔中包含任何 **可見** 的參數時，PowerShell 會 `Import-Module` 從會話中移除該 Cmdlet 和其 `ipmo` 別名。

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

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

您無法透過管線將任何物件傳送至此 Cmdlet。

## 輸出

### 無

此 Cmdlet 不會產生任何輸出。

## 注意

- 參數（例如 **VisibleCmdlets** 和 **VisibleProviders** ）不會將專案匯入到會話中。 而是會從匯入工作階段的項目中選取。 例如，如果 **VisibleProviders** 參數的值為 certificate 提供者，但 **ModulesToImport** 參數未指定包含憑證提供者的 **安全性** 模組，則會話中不會顯示憑證提供者。
- `New-PSSessionConfigurationFile` 在您于 **path** 參數中指定的路徑中，建立副檔名為 .pssc 的會話設定檔。 當您使用會話設定檔建立會話設定時，此 Cmdlet 會 `Register-PSSessionConfiguration` 複製設定檔，並將檔案的使用中複本儲存在目錄的 **SessionConfig** 子目錄中 `$PSHOME` 。

  會話設定的 **ConfigFilePath** 屬性包含使用中會話設定檔的完整路徑。 您可以隨時 `$PSHOME` 使用任何文字編輯器來修改目錄中的使用中設定檔。 您所做的變更會影響所有使用工作階段設定的新工作階段，但不會影響現有的工作階段。

  使用已編輯的會話設定檔之前，請使用 `Test-PSSessionConfigurationFile` Cmdlet 來確認設定檔案專案是否有效。

## 相關連結

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Test-PSSessionConfigurationFile](Test-PSSessionConfigurationFile.md)

[Unregister-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[WSMan 提供者](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)
