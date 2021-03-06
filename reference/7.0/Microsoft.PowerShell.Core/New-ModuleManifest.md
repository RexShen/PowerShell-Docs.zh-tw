---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 11/02/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-modulemanifest?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ModuleManifest
ms.openlocfilehash: 8177b1ed45f6d6cdabf13670e36be4fcbb55a77b
ms.sourcegitcommit: fcf7bd222f5ee3fdbe21ffddcae47050cffe7e42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2020
ms.locfileid: "93239949"
---
# New-ModuleManifest

## 概要
建立新的模組資訊清單。

## SYNTAX

### 全部

```
New-ModuleManifest [-Path] <String> [-NestedModules <Object[]>] [-Guid <Guid>] [-Author <String>]
 [-CompanyName <String>] [-Copyright <String>] [-RootModule <String>] [-ModuleVersion <Version>]
 [-Description <String>] [-ProcessorArchitecture <ProcessorArchitecture>]
 [-PowerShellVersion <Version>] [-CLRVersion <Version>] [-DotNetFrameworkVersion <Version>]
 [-PowerShellHostName <String>] [-PowerShellHostVersion <Version>] [-RequiredModules <Object[]>]
 [-TypesToProcess <String[]>] [-FormatsToProcess <String[]>] [-ScriptsToProcess <String[]>]
 [-RequiredAssemblies <String[]>] [-FileList <String[]>] [-ModuleList <Object[]>]
 [-FunctionsToExport <String[]>] [-AliasesToExport <String[]>] [-VariablesToExport <String[]>]
 [-CmdletsToExport <String[]>] [-DscResourcesToExport <String[]>] [-CompatiblePSEditions <String[]>]
 [-PrivateData <Object>] [-Tags <String[]>] [-ProjectUri <Uri>] [-LicenseUri <Uri>] [-IconUri <Uri>]
 [-ReleaseNotes <String>] [-Prerelease <String>] [-RequireLicenseAcceptance]
 [-ExternalModuleDependencies <String[]>] [-HelpInfoUri <String>] [-PassThru]
 [-DefaultCommandPrefix <String>] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

## DESCRIPTION

`New-ModuleManifest`Cmdlet 會建立新的模組資訊清單 (`.psd1`) 檔案、填入其值，並將資訊清單檔案儲存在指定的路徑中。

模組作者可以使用這個 Cmdlet 建立其模組資訊清單。 模組資訊清單是 `.psd1` 包含雜湊表的檔案。 雜湊表中的索引鍵和值描述模組的內容和屬性、定義先決條件，和決定元件的處理方式。 模組不需要資訊清單。

`New-ModuleManifest` 建立資訊清單，其中包含所有常用的資訊清單索引鍵，因此您可以使用預設輸出做為資訊清單範本。 若要新增或變更值，或新增此 Cmdlet 未新增的模組索引鍵，請在文字編輯器中開啟產生的檔案。

除了 **Path** 和 **PassThru** 之外，每個參數都會建立模組資訊清單索引鍵和其值。
在模組資訊清單中，只有 **ModuleVersion** 索引鍵是必要的。 除非在參數描述中指定，否則如果您從命令省略參數，則會 `New-ModuleManifest` 為沒有效果的關聯值建立批註字串。

在 PowerShell 2.0 中， `New-ModuleManifest` 除了必要參數值之外，還會提示您輸入命令中未指定之常用參數的值。 從 PowerShell 3.0 開始， `New-ModuleManifest` 只有在未指定必要的參數值時，才會提示。

如果您打算在 PowerShell 資源庫中發行您的模組，資訊清單必須包含特定屬性的值。 如需詳細資訊，請參閱資源庫檔中 [發佈至 PowerShell 資源庫之專案的必要中繼資料](/powershell/scripting/gallery/how-to/publishing-packages/publishing-a-package#required-metadata-for-items-published-to-the-powershell-gallery) 。

## 範例

### 範例 1-建立新的模組資訊清單

此範例會在 **Path** 參數所指定的檔案中建立新的模組資訊清單。
**PassThru** 參數會將輸出傳送至管線和檔案。

輸出顯示資訊清單中所有索引鍵的預設值。

```powershell
New-ModuleManifest -Path C:\ps-test\Test-Module\Test-Module.psd1 -PassThru
```

```Output
#
# Module manifest for module 'Test-Module'
#
# Generated by: ContosoAdmin
#
# Generated on: 7/12/2019
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '0.0.1'

# Supported PSEditions
# CompatiblePSEditions = @()

# ID used to uniquely identify this module
GUID = 'e1826c6e-c420-4eef-9ac8-185e3669ca6a'

# Author of this module
Author = 'ContosoAdmin'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) ContosoAdmin. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the PowerShell engine required by this module
# PowerShellVersion = ''

# Name of the PowerShell host required by this module
# PowerShellHostName = ''

# Minimum version of the PowerShell host required by this module
# PowerShellHostVersion = ''

# Minimum version of Microsoft .NET Framework required by this module. This prerequisite is valid for the PowerShell Desktop edition only.
# DotNetFrameworkVersion = ''

# Minimum version of the common language runtime (CLR) required by this module. This prerequisite is valid for the PowerShell Desktop edition only.
# CLRVersion = ''

# Processor architecture (None, X86, Amd64) required by this module
# ProcessorArchitecture = ''

# Modules that must be imported into the global environment prior to importing this module
# RequiredModules = @()

# Assemblies that must be loaded prior to importing this module
# RequiredAssemblies = @()

# Script files (.ps1) that are run in the caller's environment prior to importing this module.
# ScriptsToProcess = @()

# Type files (.ps1xml) to be loaded when importing this module
# TypesToProcess = @()

# Format files (.ps1xml) to be loaded when importing this module
# FormatsToProcess = @()

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
# NestedModules = @()

# Functions to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no functions to export.
FunctionsToExport = @()

# Cmdlets to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no cmdlets to export.
CmdletsToExport = @()

# Variables to export from this module
VariablesToExport = '*'

# Aliases to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no aliases to export.
AliasesToExport = @()

# DSC resources to export from this module
# DscResourcesToExport = @()

# List of all modules packaged with this module
# ModuleList = @()

# List of all files packaged with this module
# FileList = @()

# Private data to pass to the module specified in RootModule/ModuleToProcess. This may also contain a PSData hashtable with additional module metadata used by PowerShell.
PrivateData = @{

    PSData = @{

        # Tags applied to this module. These help with module discovery in online galleries.
        # Tags = @()

        # A URL to the license for this module.
        # LicenseUri = ''

        # A URL to the main website for this project.
        # ProjectUri = ''

        # A URL to an icon representing this module.
        # IconUri = ''

        # ReleaseNotes of this module
        # ReleaseNotes = ''

        # Prerelease string of this module
        # Prerelease = ''

        # Flag to indicate whether the module requires explicit user acceptance for install/update/save
        # RequireLicenseAcceptance = $false

        # External dependent modules of this module
        # ExternalModuleDependencies = @()

    } # End of PSData hashtable

} # End of PrivateData hashtable

# HelpInfo URI of this module
# HelpInfoURI = ''

# Default prefix for commands exported from this module. Override the default prefix using Import-Module -Prefix.
# DefaultCommandPrefix = ''

}
```

### 範例 2-使用一些預先填入的設定來建立新的資訊清單

這個範例會建立新的模組資訊清單。 它使用 **PowerShellVersion** 和 **AliasesToExport** 參數，將值新增至對應的資訊清單索引鍵。

```powershell
New-ModuleManifest -PowerShellVersion 1.0 -AliasesToExport JKBC, DRC, TAC -Path C:\ps-test\ManifestTest.psd1
```

### 範例 3-建立需要其他模組的資訊清單

此範例會使用字串格式來指定 **BitsTransfer** 模組的名稱，以及使用雜湊表格式來指定名稱、 **GUID** 和 **PSScheduledJob** 模組的版本。

```powershell
$moduleSettings = @{
  RequiredModules = ("BitsTransfer", @{
    ModuleName="PSScheduledJob"
    ModuleVersion="1.0.0.0";
    GUID="50cdb55f-5ab7-489f-9e94-4ec21ff51e59"
  })
  Path = 'C:\ps-test\ManifestTest.psd1'
}
New-ModuleManifest @moduleSettings
```

此範例顯示如何使用 **ModuleList** 、 **RequiredModules** 和 **NestedModules** 參數的字串和雜湊表格式。 您可以在相同的參數值中結合字串和雜湊表。

### 範例 4-建立支援可更新說明的資訊清單

此範例使用 **HelpInfoUri** 參數在模組資訊清單中建立 **HelpInfoUri** 索引鍵。 參數的值和索引鍵的開頭必須是 **HTTP** 或 **HTTPs** 。 此值指示「可更新的說明」系統尋找模組 HelpInfo XML 可更新的說明資訊檔案的位置。

```powershell
$moduleSettings = @{
  HelpInfoUri = 'http://https://go.microsoft.com/fwlink/?LinkID=603'
  Path = 'C:\ps-test\ManifestTest.psd1'
}
New-ModuleManifest @moduleSettings
```

如需「可更新的說明」的詳細資訊，請參閱 [about_Updatable_Help](./About/about_Updatable_Help.md)。
如需 HelpInfo XML 檔案的相關資訊，請參閱 [支援可更新](/powershell/scripting/developer/module/supporting-updatable-help)的說明。

### 範例 5-取得模組資訊

此範例顯示如何取得模組的設定值。 模組資訊清單中的值會反映在模組物件的屬性值中。

此 `Get-Module` Cmdlet 會用來取得使用 **List** 參數的 **Microsoft. Diagnostics** 模組。 此命令會將模組傳送至 `Format-List` Cmdlet，以顯示模組物件的所有屬性和值。

```powershell
Get-Module Microsoft.PowerShell.Diagnostics -List | Format-List -Property *
```

```Output
LogPipelineExecutionDetails : False
Name                        : Microsoft.PowerShell.Diagnostics
Path                        : C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Microsoft.PowerShell.Diagnostics\Micro
                              soft.PowerShell.Diagnostics.psd1
Definition                  :
Description                 :
Guid                        : ca046f10-ca64-4740-8ff9-2565dba61a4f
HelpInfoUri                 : https://go.microsoft.com/fwlink/?LinkID=210596
ModuleBase                  : C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Microsoft.PowerShell.Diagnostics
PrivateData                 :
Version                     : 3.0.0.0
ModuleType                  : Manifest
Author                      : Microsoft Corporation
AccessMode                  : ReadWrite
ClrVersion                  : 4.0
CompanyName                 : Microsoft Corporation
Copyright                   : Microsoft Corporation. All rights reserved.
DotNetFrameworkVersion      :
ExportedFunctions           : {}
ExportedCmdlets             : {[Get-WinEvent, Get-WinEvent], [Get-Counter, Get-Counter], [Import-Counter,
                              Import-Counter], [Export-Counter, Export-Counter]...}
ExportedCommands            : {[Get-WinEvent, Get-WinEvent], [Get-Counter, Get-Counter], [Import-Counter,
                              Import-Counter], [Export-Counter, Export-Counter]...}
FileList                    : {}
ModuleList                  : {}
NestedModules               : {}
PowerShellHostName          :
PowerShellHostVersion       :
PowerShellVersion           : 3.0
ProcessorArchitecture       : None
Scripts                     : {}
RequiredAssemblies          : {}
RequiredModules             : {}
RootModule                  :
ExportedVariables           : {}
ExportedAliases             : {}
ExportedWorkflows           : {}
SessionState                :
OnRemove                    :
ExportedFormatFiles         : {C:\Windows\system32\WindowsPowerShell\v1.0\Event.format.ps1xml,
                              C:\Windows\system32\WindowsPowerShell\v1.0\Diagnostics.format.ps1xml}
ExportedTypeFiles           : {C:\Windows\system32\WindowsPowerShell\v1.0\GetEvent.types.ps1xml}
```

## PARAMETERS

### -AliasesToExport

指定模組匯出的別名。 允許使用萬用字元。

您可以使用此參數來限制模組匯出的別名。 它可以從匯出的別名清單中移除別名，但不能將別名新增到清單中。

如果您省略此參數，則 `New-ModuleManifest` 會建立 **AliasesToExport** 索引鍵，其值為 `*` (all) ，表示模組中定義的所有別名都是由資訊清單匯出。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: * (all)
Accept pipeline input: False
Accept wildcard characters: True
```

### -作者

指定模組作者。

如果您省略此參數，則會 `New-ModuleManifest` 使用目前使用者的名稱建立 **作者** 金鑰。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Name of the current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -ClrVersion

指定模組所需要的 Microsoft .NET Framework Common Language Runtime (CLR) 最低版本。

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

### -CmdletsToExport

指定模組匯出的 Cmdlet。 允許使用萬用字元。

您可以使用此參數來限制模組匯出的 Cmdlet。 它可以從匯出的 Cmdlet 清單中移除 Cmdlet，但是不能將 Cmdlet 新增至清單。

如果您省略此參數，則 `New-ModuleManifest` 會建立 **CmdletsToExport** 索引鍵，其值為 `*` (所有) ，表示模組中定義的所有 Cmdlet 都會由資訊清單匯出。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: * (all)
Accept pipeline input: False
Accept wildcard characters: True
```

### -公司名稱

識別建立模組的公司或廠商。

如果您省略此參數，則會 `New-ModuleManifest` 建立一個值為 "Unknown" 的 **公司名稱** 索引鍵。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: "Unknown"
Accept pipeline input: False
Accept wildcard characters: False
```

### -CompatiblePSEditions

指定模組的相容 PSEditions。 如需 PSEdition 的相關資訊，請參閱 [具有相容 PowerShell 版本的模組](/powershell/scripting/gallery/concepts/module-psedition-support)。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Desktop, Core

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -著作權

指定模組的著作權聲明。

如果您省略此參數，則 `New-ModuleManifest` 會建立一個值為的 **著作權** 金鑰， `(c) <year> <username>. All rights reserved.` 其中 `<year>` 是目前年份，而 `<username>` 是 **作者** 索引鍵的值。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: (c) <year> <username>. All rights reserved.
Accept pipeline input: False
Accept wildcard characters: False
```

### -DefaultCommandPrefix

指定當匯入會話時，在模組中所有命令的名詞前面加上的前置詞。 輸入前置詞字串。 前置詞可避免使用者工作階段中的命令名稱衝突。

模組使用者可以藉由指定 Cmdlet 的 **prefix** 參數，來覆寫這個前置詞 `Import-Module` 。

此參數是在 PowerShell 3.0 中引進。

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

說明模組的內容。

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

### -DotNetFrameworkVersion

指定模組所需要的 Microsoft .NET Framework 最低版本。

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

### -DscResourcesToExport

指定模組匯出的 Desired State Configuration (DSC) 資源。 允許使用萬用字元。

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

### -ExternalModuleDependencies

此模組所相依的外部模組清單。

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

### -FileList

指定模組中所包含的所有項目。

這個索引鍵被設計來做為模組詳細目錄。 當模組發行時，會包含機碼中列出的檔案，但不會自動匯出任何函式。

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

### -FormatsToProcess

指定匯 `.ps1xml` 入模組時所執行)  (格式檔案。

當您匯入模組時，PowerShell 會 `Update-FormatData` 使用指定的檔案來執行 Cmdlet。
因為格式化檔案未設定範圍，所以它們會影響會話中所有的會話狀態。

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

### -FunctionsToExport

指定模組匯出的函式。 允許使用萬用字元。

您可以使用此參數來限制模組匯出的函式。 它可以從匯出的別名清單中移除函式，但它無法將函式新增至清單。

如果您省略這個參數，則 `New-ModuleManifest` 會建立 **FunctionsToExport** 索引鍵，其值為 `*` (all) ，表示模組中定義的所有函式都會由資訊清單匯出。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: * (all)
Accept pipeline input: False
Accept wildcard characters: True
```

### -Guid

指定模組的唯一識別碼。 **GUID** 可以用來區別具有相同名稱的模組。

如果您省略此參數，則會 `New-ModuleManifest` 在資訊清單中建立 **guid** 金鑰，並產生值的 **guid** 。

若要在 PowerShell 中建立新的 **GUID** ，請輸入 `[guid]::NewGuid()` 。

```yaml
Type: System.Guid
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: A GUID generated for the module
Accept pipeline input: False
Accept wildcard characters: False
```

### -HelpInfoUri

指定模組 HelpInfo XML 檔案的網際網路位址。 輸入以 **HTTP** 或 **HTTPS** 開頭 (URI) 的統一資源識別項。

HelpInfo XML 檔案支援 PowerShell 3.0 中引進的可更新說明功能。 它包含模組可下載說明檔案的位置，以及每個支援的地區設定最新說明檔案版本號碼。

如需「可更新的說明」的詳細資訊，請參閱 [about_Updatable_Help](./About/about_Updatable_Help.md)。
如需 HelpInfo XML 檔案的相關資訊，請參閱 [支援可更新](/powershell/scripting/developer/module/supporting-updatable-help)的說明。

此參數是在 PowerShell 3.0 中引進。

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

### -IconUri

指定模組的圖示 URL。 指定的圖示會顯示在該模組的資源庫網頁上。

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LicenseUri

指定模組的授權條款 URL。

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ModuleList

列出此模組中所包含的所有模組。

輸入每個模組名稱做為字串或含 **ModuleName** 和 **ModuleVersion** 索引鍵的雜湊表。 雜湊表也可以有選用的 **GUID** 索引鍵。 您可以在參數值中結合字串和雜湊表。

這個索引鍵被設計來做為模組詳細目錄。 系統不會自動處理此索引鍵值中所列的模組。

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

### -ModuleVersion

指定模組的版本。

不需要此參數，但資訊清單中需要 **ModuleVersion** 索引鍵。 如果您省略此參數，則會 `New-ModuleManifest` 建立值為1.0 的 **ModuleVersion** 索引鍵。

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1.0
Accept pipeline input: False
Accept wildcard characters: False
```

### -NestedModules

指定腳本模組 (`.psm1`) 和二進位模組， (`.dll`) 匯入模組的會話狀態。 **NestedModules** 機碼中的檔案會依它們在值中的列出循序執行。

輸入每個模組名稱做為字串或含 **ModuleName** 和 **ModuleVersion** 索引鍵的雜湊表。 雜湊表也可以有選用的 **GUID** 索引鍵。 您可以在參數值中結合字串和雜湊表。

一般而言，巢狀模組包含根模組內部處理所需要的命令。
根據預設，嵌套模組中的命令會從模組的會話狀態匯出為呼叫端的會話狀態，但根模組可限制其匯出的命令。 例如，使用 `Export-ModuleMember` 命令。

模組會話狀態中的嵌套模組可供根模組使用，但 `Get-Module` 呼叫端的會話狀態中的命令不會傳回它們。

NestedModules 索引 `.ps1` 鍵中列出的腳本 ( **NestedModules** ) 會在模組會話狀態下執行，而不是在呼叫端的會話狀態中執行。 如果要在呼叫者工作階段狀態下執行指令碼，請在資訊清單的 **ScriptsToProcess** 索引鍵值中列出指令碼檔案名稱。

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

### -PassThru

將產生的模組資訊清單寫入主控台並建立檔案 `.psd1` 。 根據預設，此 Cmdlet 不會產生任何輸出。

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

### -Path

指定新模組資訊清單的路徑和檔案名稱。 輸入副檔名為的路徑和檔案名 `.psd1` ，例如 `$pshome\Modules\MyModule\MyModule.psd1` 。 需要 **Path** 參數。

如果您指定現有檔案的路徑，則 `New-ModuleManifest` 會在沒有警告的情況下取代檔案，除非檔案具有唯讀屬性。

資訊清單應該位於模組的目錄中，且資訊清單檔案名應該與模組目錄名稱相同，但是 `.psd1` 副檔名為。

> [!NOTE]
> 您無法使用變數（例如 `$PSHOME` 或 `$HOME` ）來回應 **路徑** 參數值的提示。 如果要使用變數，請在命令中包含 **Path** 參數。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PowerShellHostName

指定模組所需之 PowerShell 主機程式的名稱。 輸入主機程式的名稱，例如 **Windows PowerShell ISE host** 或 **ConsoleHost** 。 不允許使用萬用字元。

若要尋找主機程式的名稱，請在程式中輸入 `$Host.Name` 。

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

### -PowerShellHostVersion

指定適用于模組的 PowerShell 主機程式的最小版本。 輸入版本號碼，例如 1.1。

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

### -PowerShellVersion

指定可與此模組搭配運作的 PowerShell 最低版本。 例如，您可以輸入1.0、2.0 或3.0 作為參數的值。

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

### -發行前版本

此課程模組的發行前版本字串。 新增發行前版本字串會將模組識別為發行前版本。 當模組發行至 PowerShell 資源庫時，此資料會用來識別發行前版本套件。 若要從資源庫取得發行前版本套件，您必須使用 **AllowPrerelease** 參數搭配 PowerShellGet 命令 `Find-Module` 、、 `Install-Module` `Update-Module` 和 `Save-Module` 。

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

### -PrivateData

指定匯入模組時傳遞給模組的資料。

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

### -ProcessorArchitecture

指定模組需要的處理器架構。 有效的值為 x86、AMD64、IA64、MSIL 和 None (未知或未指定的) 。

```yaml
Type: System.Reflection.ProcessorArchitecture
Parameter Sets: (All)
Aliases:
Accepted values: None, MSIL, X86, IA64, Amd64, Arm

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProjectUri

指定與這個專案相關之網頁的 URL。

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ReleaseNotes

指定版本資訊。

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

### -RequiredAssemblies

指定模組所需 () 檔案的元件 `.dll` 。 輸入組件檔案名稱。
PowerShell 會在更新類型或格式、匯入嵌套模組，或匯入在 **RootModule** 索引鍵值中指定的模組檔案之前，先載入指定的元件。

使用這個參數來列出模組需要的所有組件，包含必須載入以更新任何格式的組件，或是 **FormatsToProcess** 或 **TypesToProcess** 索引鍵中列出的類型檔案，即使這些組件也在 **NestedModules** 索引鍵中列為二進位模組。

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

### -RequiredModules

指定必須在全域工作階段狀態的模組。 如果必要的模組不在全域會話狀態中，則 PowerShell 會將它們匯入。 如果無法使用必要的模組，則 `Import-Module` 命令會失敗。

輸入每個模組名稱做為字串或含 **ModuleName** 和 **ModuleVersion** 索引鍵的雜湊表。 雜湊表也可以有選用的 **GUID** 索引鍵。 您可以在參數值中結合字串和雜湊表。

在 PowerShell 2.0 中， `Import-Module` 不會自動匯入必要的模組。 它只會驗證必要的模組會在全域工作階段狀態。

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

### -RequireLicenseAcceptance

旗標，指出模組是否需要明確接受使用者的安裝、更新、orsave。

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

### -RootModule

指定模組的主要或根檔案。 輸入腳本 (的檔案名 `.ps1`) 、腳本模組 (`.psm1`) 、模組資訊清單 () `.psd1` 、元件 () 、 `.dll` Cmdlet 定義 XML 檔案 (`.cdxml`) 或工作流程 (`.xaml`) 。 匯入模組時，從根模組檔案匯出的成員會匯入呼叫者工作階段狀態。

如果模組有資訊清單檔案，但 **RootModule** 索引鍵中沒有指定根檔案，資訊清單會變成模組的主要檔案，且該模組會變成 (ModuleType = 資訊清單) 的資訊清單模組。

若要從 `.psm1` 具有資訊清單之模組中的或檔案匯出成員 `.dll` ，則必須在資訊清單中的 **RootModule** 或 **NestedModules** 索引鍵的值中指定這些檔案的名稱。 否則，不會匯出其成員。

> [!NOTE]
> 在 PowerShell 2.0 中，此機碼稱為 **ModuleToProcess** 。 您可以使用 **RootModule** 參數名稱或其 **ModuleToProcess** 別名。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: ModuleToProcess

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptsToProcess

指定匯 `.ps1` 入模組時，在呼叫者會話狀態中執行的腳本 () 檔。
您可以使用這些指令碼來準備環境，就像您使用登入指令碼一般。

如果要指定在模組工作階段狀態中執行的指令碼，請使用 **NestedModules** 索引鍵。

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

### -Tags

指定標記的陣列。

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

### -TypesToProcess

指定匯入模組時要執行的類型檔案 (`.ps1xml`) 。

當您匯入模組時，PowerShell 會 `Update-TypeData` 使用指定的檔案來執行 Cmdlet。
因為類型檔案未設定範圍，所以它們會影響會話中所有的會話狀態。

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

### -VariablesToExport

指定模組匯出的變數。 允許使用萬用字元。

您可以使用此參數來限制模組匯出的變數。 它可以從匯出的變數清單中移除變數，但它無法將變數新增至清單。

如果您省略這個參數，則 `New-ModuleManifest` 會建立 **VariablesToExport** 索引鍵，其值為 `*` (all) ，表示模組中定義的所有變數都會由資訊清單匯出。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: * (all)
Accept pipeline input: False
Accept wildcard characters: True
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

顯示執行時所發生 `New-ModuleManifest` 的情況。 不會執行此 Cmdlet。

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

### 無

您無法透過管道傳送輸入至此 Cmdlet。

## 輸出

### 無或 System.String

依預設， `New-ModuleManifest` 不會產生任何輸出。 但是，如果您使用 **PassThru** 參數，它會產生代表模組資訊清單的 **system.string** 物件。

## 注意

`New-ModuleManifest` 在 Windows 和非 Windows 平臺上執行時，會建立模組資訊清單 (`.psd1`) 編碼為 **UTF8NoBOM** 的檔案。

模組資訊清單通常為選擇性。 不過，需要模組資訊清單才能匯出安裝在全域組件快取中的組件。

若要在目錄中新增或變更檔案 `$pshome\Modules` ，請使用 [以 **系統管理員身分執行** ] 選項啟動 PowerShell。

> [!NOTE]
> 從 PowerShell 6.2 開始，PowerShell 會嘗試載入模組資訊清單的 **FileList** 屬性中所列的所有 DLL 檔案。 **FileList** 中的原生 dll 無法在進程中載入，而且會忽略錯誤。 所有 managed Dll 都會載入到進程中。 此行為已在 PowerShell 7.1 中移除。

在 PowerShell 2.0 中，許多的參數 `New-ModuleManifest` 都是強制性的，即使在模組資訊清單中不需要它們也是一樣。 從 PowerShell 3.0 開始，只有 **Path** 參數是必要的。

會話是 PowerShell 執行環境的實例。 工作階段可以有一或多個工作階段狀態。 依預設，工作階段只有全域工作階段狀態，但每個匯入的模組有自己的工作階段狀態。 工作階段狀態允許執行模組中的命令，而不會影響全域工作階段狀態。

呼叫端的會話狀態是模組匯入的會話狀態。 一般而言，它是指全域會話狀態，但當模組匯入嵌套模組時，呼叫端是模組，而呼叫端的會話狀態是模組的會話狀態。

## 相關連結

[Export-ModuleMember](Export-ModuleMember.md)

[Get-Module](Get-Module.md)

[Import-Module](Import-Module.md)

[New-Module](New-Module.md)

[Remove-Module](Remove-Module.md)

[Test-ModuleManifest](Test-ModuleManifest.md)

[about_Modules](./About/about_Modules.md)
