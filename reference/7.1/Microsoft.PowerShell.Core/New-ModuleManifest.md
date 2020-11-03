---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 11/02/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-modulemanifest?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ModuleManifest
ms.openlocfilehash: 5fbd197f6c22de0ca50b4d2b6b76a914b85f7120
ms.sourcegitcommit: fcf7bd222f5ee3fdbe21ffddcae47050cffe7e42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2020
ms.locfileid: "93239769"
---
# <span data-ttu-id="72eeb-103">New-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="72eeb-103">New-ModuleManifest</span></span>

## <span data-ttu-id="72eeb-104">概要</span><span class="sxs-lookup"><span data-stu-id="72eeb-104">SYNOPSIS</span></span>
<span data-ttu-id="72eeb-105">建立新的模組資訊清單。</span><span class="sxs-lookup"><span data-stu-id="72eeb-105">Creates a new module manifest.</span></span>

## <span data-ttu-id="72eeb-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="72eeb-106">SYNTAX</span></span>

### <span data-ttu-id="72eeb-107">全部</span><span class="sxs-lookup"><span data-stu-id="72eeb-107">All</span></span>

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

## <span data-ttu-id="72eeb-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="72eeb-108">DESCRIPTION</span></span>

<span data-ttu-id="72eeb-109">`New-ModuleManifest`Cmdlet 會建立新的模組資訊清單 (`.psd1`) 檔案、填入其值，並將資訊清單檔案儲存在指定的路徑中。</span><span class="sxs-lookup"><span data-stu-id="72eeb-109">The `New-ModuleManifest` cmdlet creates a new module manifest (`.psd1`) file, populates its values, and saves the manifest file in the specified path.</span></span>

<span data-ttu-id="72eeb-110">模組作者可以使用這個 Cmdlet 建立其模組資訊清單。</span><span class="sxs-lookup"><span data-stu-id="72eeb-110">Module authors can use this cmdlet to create a manifest for their module.</span></span> <span data-ttu-id="72eeb-111">模組資訊清單是 `.psd1` 包含雜湊表的檔案。</span><span class="sxs-lookup"><span data-stu-id="72eeb-111">A module manifest is a `.psd1` file that contains a hash table.</span></span> <span data-ttu-id="72eeb-112">雜湊表中的索引鍵和值描述模組的內容和屬性、定義先決條件，和決定元件的處理方式。</span><span class="sxs-lookup"><span data-stu-id="72eeb-112">The keys and values in the hash table describe the contents and attributes of the module, define the prerequisites, and determine how the components are processed.</span></span> <span data-ttu-id="72eeb-113">模組不需要資訊清單。</span><span class="sxs-lookup"><span data-stu-id="72eeb-113">Manifests aren't required for a module.</span></span>

<span data-ttu-id="72eeb-114">`New-ModuleManifest` 建立資訊清單，其中包含所有常用的資訊清單索引鍵，因此您可以使用預設輸出做為資訊清單範本。</span><span class="sxs-lookup"><span data-stu-id="72eeb-114">`New-ModuleManifest` creates a manifest that includes all the commonly used manifest keys, so you can use the default output as a manifest template.</span></span> <span data-ttu-id="72eeb-115">若要新增或變更值，或新增此 Cmdlet 未新增的模組索引鍵，請在文字編輯器中開啟產生的檔案。</span><span class="sxs-lookup"><span data-stu-id="72eeb-115">To add or change values, or to add module keys that this cmdlet doesn't add, open the resulting file in a text editor.</span></span>

<span data-ttu-id="72eeb-116">除了 **Path** 和 **PassThru** 之外，每個參數都會建立模組資訊清單索引鍵和其值。</span><span class="sxs-lookup"><span data-stu-id="72eeb-116">Each parameter, except for **Path** and **PassThru** , creates a module manifest key and its value.</span></span>
<span data-ttu-id="72eeb-117">在模組資訊清單中，只有 **ModuleVersion** 索引鍵是必要的。</span><span class="sxs-lookup"><span data-stu-id="72eeb-117">In a module manifest, only the **ModuleVersion** key is required.</span></span> <span data-ttu-id="72eeb-118">除非在參數描述中指定，否則如果您從命令省略參數，則會 `New-ModuleManifest` 為沒有效果的關聯值建立批註字串。</span><span class="sxs-lookup"><span data-stu-id="72eeb-118">Unless specified in the parameter description, if you omit a parameter from the command, `New-ModuleManifest` creates a comment string for the associated value that has no effect.</span></span>

<span data-ttu-id="72eeb-119">在 PowerShell 2.0 中， `New-ModuleManifest` 除了必要參數值之外，還會提示您輸入命令中未指定之常用參數的值。</span><span class="sxs-lookup"><span data-stu-id="72eeb-119">In PowerShell 2.0, `New-ModuleManifest` prompts you for the values of commonly used parameters that aren't specified in the command, in addition to required parameter values.</span></span> <span data-ttu-id="72eeb-120">從 PowerShell 3.0 開始， `New-ModuleManifest` 只有在未指定必要的參數值時，才會提示。</span><span class="sxs-lookup"><span data-stu-id="72eeb-120">Beginning in PowerShell 3.0, `New-ModuleManifest` prompts only when required parameter values aren't specified.</span></span>

<span data-ttu-id="72eeb-121">如果您打算在 PowerShell 資源庫中發行您的模組，資訊清單必須包含特定屬性的值。</span><span class="sxs-lookup"><span data-stu-id="72eeb-121">If you are planning to publish your module in the PowerShell Gallery, the manifest must contain values for certain properties.</span></span> <span data-ttu-id="72eeb-122">如需詳細資訊，請參閱資源庫檔中 [發佈至 PowerShell 資源庫之專案的必要中繼資料](/powershell/scripting/gallery/how-to/publishing-packages/publishing-a-package#required-metadata-for-items-published-to-the-powershell-gallery) 。</span><span class="sxs-lookup"><span data-stu-id="72eeb-122">For more information, see [Required metadata for items published to the PowerShell Gallery](/powershell/scripting/gallery/how-to/publishing-packages/publishing-a-package#required-metadata-for-items-published-to-the-powershell-gallery) in the Gallery documentation.</span></span>

## <span data-ttu-id="72eeb-123">範例</span><span class="sxs-lookup"><span data-stu-id="72eeb-123">EXAMPLES</span></span>

### <span data-ttu-id="72eeb-124">範例 1-建立新的模組資訊清單</span><span class="sxs-lookup"><span data-stu-id="72eeb-124">Example 1 - Create a new module manifest</span></span>

<span data-ttu-id="72eeb-125">此範例會在 **Path** 參數所指定的檔案中建立新的模組資訊清單。</span><span class="sxs-lookup"><span data-stu-id="72eeb-125">This example creates a new module manifest in the file that is specified by the **Path** parameter.</span></span>
<span data-ttu-id="72eeb-126">**PassThru** 參數會將輸出傳送至管線和檔案。</span><span class="sxs-lookup"><span data-stu-id="72eeb-126">The **PassThru** parameter sends the output to the pipeline and to the file.</span></span>

<span data-ttu-id="72eeb-127">輸出顯示資訊清單中所有索引鍵的預設值。</span><span class="sxs-lookup"><span data-stu-id="72eeb-127">The output shows the default values of all keys in the manifest.</span></span>

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

### <span data-ttu-id="72eeb-128">範例 2-使用一些預先填入的設定來建立新的資訊清單</span><span class="sxs-lookup"><span data-stu-id="72eeb-128">Example 2 - Create a new manifest with some prepopulated settings</span></span>

<span data-ttu-id="72eeb-129">這個範例會建立新的模組資訊清單。</span><span class="sxs-lookup"><span data-stu-id="72eeb-129">This example creates a new module manifest.</span></span> <span data-ttu-id="72eeb-130">它使用 **PowerShellVersion** 和 **AliasesToExport** 參數，將值新增至對應的資訊清單索引鍵。</span><span class="sxs-lookup"><span data-stu-id="72eeb-130">It uses the **PowerShellVersion** and **AliasesToExport** parameters to add values to the corresponding manifest keys.</span></span>

```powershell
New-ModuleManifest -PowerShellVersion 1.0 -AliasesToExport JKBC, DRC, TAC -Path C:\ps-test\ManifestTest.psd1
```

### <span data-ttu-id="72eeb-131">範例 3-建立需要其他模組的資訊清單</span><span class="sxs-lookup"><span data-stu-id="72eeb-131">Example 3 - Create a manifest that requires other modules</span></span>

<span data-ttu-id="72eeb-132">此範例會使用字串格式來指定 **BitsTransfer** 模組的名稱，以及使用雜湊表格式來指定名稱、 **GUID** 和 **PSScheduledJob** 模組的版本。</span><span class="sxs-lookup"><span data-stu-id="72eeb-132">This example uses a string format to specify the name of the **BitsTransfer** module and the hash table format to specify the name, a **GUID** , and a version of the **PSScheduledJob** module.</span></span>

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

<span data-ttu-id="72eeb-133">此範例顯示如何使用 **ModuleList** 、 **RequiredModules** 和 **NestedModules** 參數的字串和雜湊表格式。</span><span class="sxs-lookup"><span data-stu-id="72eeb-133">This example shows how to use the string and hash table formats of the **ModuleList** , **RequiredModules** , and **NestedModules** parameter.</span></span> <span data-ttu-id="72eeb-134">您可以在相同的參數值中結合字串和雜湊表。</span><span class="sxs-lookup"><span data-stu-id="72eeb-134">You can combine strings and hash tables in the same parameter value.</span></span>

### <span data-ttu-id="72eeb-135">範例 4-建立支援可更新說明的資訊清單</span><span class="sxs-lookup"><span data-stu-id="72eeb-135">Example 4 - Create a manifest that supports updateable help</span></span>

<span data-ttu-id="72eeb-136">此範例使用 **HelpInfoUri** 參數在模組資訊清單中建立 **HelpInfoUri** 索引鍵。</span><span class="sxs-lookup"><span data-stu-id="72eeb-136">This example uses the **HelpInfoUri** parameter to create a **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="72eeb-137">參數的值和索引鍵的開頭必須是 **HTTP** 或 **HTTPs** 。</span><span class="sxs-lookup"><span data-stu-id="72eeb-137">The value of the parameter and the key must begin with **http** or **https**.</span></span> <span data-ttu-id="72eeb-138">此值指示「可更新的說明」系統尋找模組 HelpInfo XML 可更新的說明資訊檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="72eeb-138">This value tells the Updatable Help system where to find the HelpInfo XML updatable help information file for the module.</span></span>

```powershell
$moduleSettings = @{
  HelpInfoUri = 'http://https://go.microsoft.com/fwlink/?LinkID=603'
  Path = 'C:\ps-test\ManifestTest.psd1'
}
New-ModuleManifest @moduleSettings
```

<span data-ttu-id="72eeb-139">如需「可更新的說明」的詳細資訊，請參閱 [about_Updatable_Help](./About/about_Updatable_Help.md)。</span><span class="sxs-lookup"><span data-stu-id="72eeb-139">For information about Updatable Help, see [about_Updatable_Help](./About/about_Updatable_Help.md).</span></span>
<span data-ttu-id="72eeb-140">如需 HelpInfo XML 檔案的相關資訊，請參閱 [支援可更新](/powershell/scripting/developer/module/supporting-updatable-help)的說明。</span><span class="sxs-lookup"><span data-stu-id="72eeb-140">For information about the HelpInfo XML file, see [Supporting Updatable Help](/powershell/scripting/developer/module/supporting-updatable-help).</span></span>

### <span data-ttu-id="72eeb-141">範例 5-取得模組資訊</span><span class="sxs-lookup"><span data-stu-id="72eeb-141">Example 5 - Getting module information</span></span>

<span data-ttu-id="72eeb-142">此範例顯示如何取得模組的設定值。</span><span class="sxs-lookup"><span data-stu-id="72eeb-142">This example shows how to get the configuration values of a module.</span></span> <span data-ttu-id="72eeb-143">模組資訊清單中的值會反映在模組物件的屬性值中。</span><span class="sxs-lookup"><span data-stu-id="72eeb-143">The values in the module manifest are reflected in the values of properties of the module object.</span></span>

<span data-ttu-id="72eeb-144">此 `Get-Module` Cmdlet 會用來取得使用 **List** 參數的 **Microsoft. Diagnostics** 模組。</span><span class="sxs-lookup"><span data-stu-id="72eeb-144">The `Get-Module` cmdlet is used to get the **Microsoft.PowerShell.Diagnostics** module using the **List** parameter.</span></span> <span data-ttu-id="72eeb-145">此命令會將模組傳送至 `Format-List` Cmdlet，以顯示模組物件的所有屬性和值。</span><span class="sxs-lookup"><span data-stu-id="72eeb-145">The command sends the module to the `Format-List` cmdlet to display all properties and values of the module object.</span></span>

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

## <span data-ttu-id="72eeb-146">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="72eeb-146">PARAMETERS</span></span>

### <span data-ttu-id="72eeb-147">-AliasesToExport</span><span class="sxs-lookup"><span data-stu-id="72eeb-147">-AliasesToExport</span></span>

<span data-ttu-id="72eeb-148">指定模組匯出的別名。</span><span class="sxs-lookup"><span data-stu-id="72eeb-148">Specifies the aliases that the module exports.</span></span> <span data-ttu-id="72eeb-149">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="72eeb-149">Wildcards are permitted.</span></span>

<span data-ttu-id="72eeb-150">您可以使用此參數來限制模組匯出的別名。</span><span class="sxs-lookup"><span data-stu-id="72eeb-150">You can use this parameter to restrict the aliases that are exported by the module.</span></span> <span data-ttu-id="72eeb-151">它可以從匯出的別名清單中移除別名，但不能將別名新增到清單中。</span><span class="sxs-lookup"><span data-stu-id="72eeb-151">It can remove aliases from the list of exported aliases, but it can't add aliases to the list.</span></span>

<span data-ttu-id="72eeb-152">如果您省略此參數，則 `New-ModuleManifest` 會建立 **AliasesToExport** 索引鍵，其值為 `*` (all) ，表示模組中定義的所有別名都是由資訊清單匯出。</span><span class="sxs-lookup"><span data-stu-id="72eeb-152">If you omit this parameter, `New-ModuleManifest` creates an **AliasesToExport** key with a value of `*` (all), meaning that all aliases defined in the module are exported by the manifest.</span></span>

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

### <span data-ttu-id="72eeb-153">-作者</span><span class="sxs-lookup"><span data-stu-id="72eeb-153">-Author</span></span>

<span data-ttu-id="72eeb-154">指定模組作者。</span><span class="sxs-lookup"><span data-stu-id="72eeb-154">Specifies the module author.</span></span>

<span data-ttu-id="72eeb-155">如果您省略此參數，則會 `New-ModuleManifest` 使用目前使用者的名稱建立 **作者** 金鑰。</span><span class="sxs-lookup"><span data-stu-id="72eeb-155">If you omit this parameter, `New-ModuleManifest` creates an **Author** key with the name of the current user.</span></span>

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

### <span data-ttu-id="72eeb-156">-CmdletsToExport</span><span class="sxs-lookup"><span data-stu-id="72eeb-156">-CmdletsToExport</span></span>

<span data-ttu-id="72eeb-157">指定模組匯出的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="72eeb-157">Specifies the cmdlets that the module exports.</span></span> <span data-ttu-id="72eeb-158">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="72eeb-158">Wildcards are permitted.</span></span>

<span data-ttu-id="72eeb-159">您可以使用此參數來限制模組匯出的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="72eeb-159">You can use this parameter to restrict the cmdlets that are exported by the module.</span></span> <span data-ttu-id="72eeb-160">它可以從匯出的 Cmdlet 清單中移除 Cmdlet，但是不能將 Cmdlet 新增至清單。</span><span class="sxs-lookup"><span data-stu-id="72eeb-160">It can remove cmdlets from the list of exported cmdlets, but it can't add cmdlets to the list.</span></span>

<span data-ttu-id="72eeb-161">如果您省略此參數，則 `New-ModuleManifest` 會建立 **CmdletsToExport** 索引鍵，其值為 `*` (所有) ，表示模組中定義的所有 Cmdlet 都會由資訊清單匯出。</span><span class="sxs-lookup"><span data-stu-id="72eeb-161">If you omit this parameter, `New-ModuleManifest` creates a **CmdletsToExport** key with a value of `*` (all), meaning that all cmdlets defined in the module are exported by the manifest.</span></span>

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

### <span data-ttu-id="72eeb-162">-公司名稱</span><span class="sxs-lookup"><span data-stu-id="72eeb-162">-CompanyName</span></span>

<span data-ttu-id="72eeb-163">識別建立模組的公司或廠商。</span><span class="sxs-lookup"><span data-stu-id="72eeb-163">Identifies the company or vendor who created the module.</span></span>

<span data-ttu-id="72eeb-164">如果您省略此參數，則會 `New-ModuleManifest` 建立一個值為 "Unknown" 的 **公司名稱** 索引鍵。</span><span class="sxs-lookup"><span data-stu-id="72eeb-164">If you omit this parameter, `New-ModuleManifest` creates a **CompanyName** key with a value of "Unknown".</span></span>

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

### <span data-ttu-id="72eeb-165">-CompatiblePSEditions</span><span class="sxs-lookup"><span data-stu-id="72eeb-165">-CompatiblePSEditions</span></span>

<span data-ttu-id="72eeb-166">指定模組的相容 PSEditions。</span><span class="sxs-lookup"><span data-stu-id="72eeb-166">Specifies the module's compatible PSEditions.</span></span> <span data-ttu-id="72eeb-167">如需 PSEdition 的相關資訊，請參閱 [具有相容 PowerShell 版本的模組](/powershell/scripting/gallery/concepts/module-psedition-support)。</span><span class="sxs-lookup"><span data-stu-id="72eeb-167">For information about PSEdition, see [Modules with compatible PowerShell Editions](/powershell/scripting/gallery/concepts/module-psedition-support).</span></span>

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

### <span data-ttu-id="72eeb-168">-著作權</span><span class="sxs-lookup"><span data-stu-id="72eeb-168">-Copyright</span></span>

<span data-ttu-id="72eeb-169">指定模組的著作權聲明。</span><span class="sxs-lookup"><span data-stu-id="72eeb-169">Specifies a copyright statement for the module.</span></span>

<span data-ttu-id="72eeb-170">如果您省略此參數，則 `New-ModuleManifest` 會建立一個值為的 **著作權** 金鑰， `(c) <year> <username>. All rights reserved.` 其中 `<year>` 是目前年份，而 `<username>` 是 **作者** 索引鍵的值。</span><span class="sxs-lookup"><span data-stu-id="72eeb-170">If you omit this parameter, `New-ModuleManifest` creates a **Copyright** key with a value of `(c) <year> <username>. All rights reserved.` where `<year>` is the current year and `<username>` is the value of the **Author** key.</span></span>

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

### <span data-ttu-id="72eeb-171">-DefaultCommandPrefix</span><span class="sxs-lookup"><span data-stu-id="72eeb-171">-DefaultCommandPrefix</span></span>

<span data-ttu-id="72eeb-172">指定當匯入會話時，在模組中所有命令的名詞前面加上的前置詞。</span><span class="sxs-lookup"><span data-stu-id="72eeb-172">Specifies a prefix that is prepended to the nouns of all commands in the module when they're imported into a session.</span></span> <span data-ttu-id="72eeb-173">輸入前置詞字串。</span><span class="sxs-lookup"><span data-stu-id="72eeb-173">Enter a prefix string.</span></span> <span data-ttu-id="72eeb-174">前置詞可避免使用者工作階段中的命令名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="72eeb-174">Prefixes prevent command name conflicts in a user's session.</span></span>

<span data-ttu-id="72eeb-175">模組使用者可以藉由指定 Cmdlet 的 **prefix** 參數，來覆寫這個前置詞 `Import-Module` 。</span><span class="sxs-lookup"><span data-stu-id="72eeb-175">Module users can override this prefix by specifying the **Prefix** parameter of the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="72eeb-176">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="72eeb-176">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="72eeb-177">-Description</span><span class="sxs-lookup"><span data-stu-id="72eeb-177">-Description</span></span>

<span data-ttu-id="72eeb-178">說明模組的內容。</span><span class="sxs-lookup"><span data-stu-id="72eeb-178">Describes the contents of the module.</span></span>

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

### <span data-ttu-id="72eeb-179">-DotNetFrameworkVersion</span><span class="sxs-lookup"><span data-stu-id="72eeb-179">-DotNetFrameworkVersion</span></span>

<span data-ttu-id="72eeb-180">指定模組所需要的 Microsoft .NET Framework 最低版本。</span><span class="sxs-lookup"><span data-stu-id="72eeb-180">Specifies the minimum version of the Microsoft .NET Framework that the module requires.</span></span>

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

### <span data-ttu-id="72eeb-181">-DscResourcesToExport</span><span class="sxs-lookup"><span data-stu-id="72eeb-181">-DscResourcesToExport</span></span>

<span data-ttu-id="72eeb-182">指定模組匯出的 Desired State Configuration (DSC) 資源。</span><span class="sxs-lookup"><span data-stu-id="72eeb-182">Specifies the Desired State Configuration (DSC) resources that the module exports.</span></span> <span data-ttu-id="72eeb-183">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="72eeb-183">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="72eeb-184">-ExternalModuleDependencies</span><span class="sxs-lookup"><span data-stu-id="72eeb-184">-ExternalModuleDependencies</span></span>

<span data-ttu-id="72eeb-185">此模組所相依的外部模組清單。</span><span class="sxs-lookup"><span data-stu-id="72eeb-185">A list of external modules that this module is depends on.</span></span>

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

### <span data-ttu-id="72eeb-186">-FileList</span><span class="sxs-lookup"><span data-stu-id="72eeb-186">-FileList</span></span>

<span data-ttu-id="72eeb-187">指定模組中所包含的所有項目。</span><span class="sxs-lookup"><span data-stu-id="72eeb-187">Specifies all items that are included in the module.</span></span>

<span data-ttu-id="72eeb-188">這個索引鍵被設計來做為模組詳細目錄。</span><span class="sxs-lookup"><span data-stu-id="72eeb-188">This key is designed to act as a module inventory.</span></span> <span data-ttu-id="72eeb-189">當模組發行時，會包含機碼中列出的檔案，但不會自動匯出任何函式。</span><span class="sxs-lookup"><span data-stu-id="72eeb-189">The files listed in the key are included when the module is published, but any functions aren't automatically exported.</span></span>

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

### <span data-ttu-id="72eeb-190">-FormatsToProcess</span><span class="sxs-lookup"><span data-stu-id="72eeb-190">-FormatsToProcess</span></span>

<span data-ttu-id="72eeb-191">指定匯 `.ps1xml` 入模組時所執行)  (格式檔案。</span><span class="sxs-lookup"><span data-stu-id="72eeb-191">Specifies the formatting files (`.ps1xml`) that run when the module is imported.</span></span>

<span data-ttu-id="72eeb-192">當您匯入模組時，PowerShell 會 `Update-FormatData` 使用指定的檔案來執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="72eeb-192">When you import a module, PowerShell runs the `Update-FormatData` cmdlet with the specified files.</span></span>
<span data-ttu-id="72eeb-193">因為格式化檔案未設定範圍，所以它們會影響會話中所有的會話狀態。</span><span class="sxs-lookup"><span data-stu-id="72eeb-193">Because formatting files aren't scoped, they affect all session states in the session.</span></span>

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

### <span data-ttu-id="72eeb-194">-FunctionsToExport</span><span class="sxs-lookup"><span data-stu-id="72eeb-194">-FunctionsToExport</span></span>

<span data-ttu-id="72eeb-195">指定模組匯出的函式。</span><span class="sxs-lookup"><span data-stu-id="72eeb-195">Specifies the functions that the module exports.</span></span> <span data-ttu-id="72eeb-196">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="72eeb-196">Wildcards are permitted.</span></span>

<span data-ttu-id="72eeb-197">您可以使用此參數來限制模組匯出的函式。</span><span class="sxs-lookup"><span data-stu-id="72eeb-197">You can use this parameter to restrict the functions that are exported by the module.</span></span> <span data-ttu-id="72eeb-198">它可以從匯出的別名清單中移除函式，但它無法將函式新增至清單。</span><span class="sxs-lookup"><span data-stu-id="72eeb-198">It can remove functions from the list of exported aliases, but it can't add functions to the list.</span></span>

<span data-ttu-id="72eeb-199">如果您省略這個參數，則 `New-ModuleManifest` 會建立 **FunctionsToExport** 索引鍵，其值為 `*` (all) ，表示模組中定義的所有函式都會由資訊清單匯出。</span><span class="sxs-lookup"><span data-stu-id="72eeb-199">If you omit this parameter, `New-ModuleManifest` creates an **FunctionsToExport** key with a value of `*` (all), meaning that all functions defined in the module are exported by the manifest.</span></span>

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

### <span data-ttu-id="72eeb-200">-Guid</span><span class="sxs-lookup"><span data-stu-id="72eeb-200">-Guid</span></span>

<span data-ttu-id="72eeb-201">指定模組的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="72eeb-201">Specifies a unique identifier for the module.</span></span> <span data-ttu-id="72eeb-202">**GUID** 可以用來區別具有相同名稱的模組。</span><span class="sxs-lookup"><span data-stu-id="72eeb-202">The **GUID** can be used to distinguish among modules with the same name.</span></span>

<span data-ttu-id="72eeb-203">如果您省略此參數，則會 `New-ModuleManifest` 在資訊清單中建立 **guid** 金鑰，並產生值的 **guid** 。</span><span class="sxs-lookup"><span data-stu-id="72eeb-203">If you omit this parameter, `New-ModuleManifest` creates a **GUID** key in the manifest and generates a **GUID** for the value.</span></span>

<span data-ttu-id="72eeb-204">若要在 PowerShell 中建立新的 **GUID** ，請輸入 `[guid]::NewGuid()` 。</span><span class="sxs-lookup"><span data-stu-id="72eeb-204">To create a new **GUID** in PowerShell, type `[guid]::NewGuid()`.</span></span>

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

### <span data-ttu-id="72eeb-205">-HelpInfoUri</span><span class="sxs-lookup"><span data-stu-id="72eeb-205">-HelpInfoUri</span></span>

<span data-ttu-id="72eeb-206">指定模組 HelpInfo XML 檔案的網際網路位址。</span><span class="sxs-lookup"><span data-stu-id="72eeb-206">Specifies the internet address of the HelpInfo XML file for the module.</span></span> <span data-ttu-id="72eeb-207">輸入以 **HTTP** 或 **HTTPS** 開頭 (URI) 的統一資源識別項。</span><span class="sxs-lookup"><span data-stu-id="72eeb-207">Enter a Uniform Resource Identifier (URI) that begins with **http** or **https**.</span></span>

<span data-ttu-id="72eeb-208">HelpInfo XML 檔案支援 PowerShell 3.0 中引進的可更新說明功能。</span><span class="sxs-lookup"><span data-stu-id="72eeb-208">The HelpInfo XML file supports the Updatable Help feature that was introduced in PowerShell 3.0.</span></span> <span data-ttu-id="72eeb-209">它包含模組可下載說明檔案的位置，以及每個支援的地區設定最新說明檔案版本號碼。</span><span class="sxs-lookup"><span data-stu-id="72eeb-209">It contains information about the location of downloadable help files for the module and the version numbers of the newest help files for each supported locale.</span></span>

<span data-ttu-id="72eeb-210">如需「可更新的說明」的詳細資訊，請參閱 [about_Updatable_Help](./About/about_Updatable_Help.md)。</span><span class="sxs-lookup"><span data-stu-id="72eeb-210">For information about Updatable Help, see [about_Updatable_Help](./About/about_Updatable_Help.md).</span></span>
<span data-ttu-id="72eeb-211">如需 HelpInfo XML 檔案的相關資訊，請參閱 [支援可更新](/powershell/scripting/developer/module/supporting-updatable-help)的說明。</span><span class="sxs-lookup"><span data-stu-id="72eeb-211">For information about the HelpInfo XML file, see [Supporting Updatable Help](/powershell/scripting/developer/module/supporting-updatable-help).</span></span>

<span data-ttu-id="72eeb-212">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="72eeb-212">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="72eeb-213">-IconUri</span><span class="sxs-lookup"><span data-stu-id="72eeb-213">-IconUri</span></span>

<span data-ttu-id="72eeb-214">指定模組的圖示 URL。</span><span class="sxs-lookup"><span data-stu-id="72eeb-214">Specifies the URL of an icon for the module.</span></span> <span data-ttu-id="72eeb-215">指定的圖示會顯示在該模組的資源庫網頁上。</span><span class="sxs-lookup"><span data-stu-id="72eeb-215">The specified icon is displayed on the gallery web page for the module.</span></span>

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

### <span data-ttu-id="72eeb-216">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="72eeb-216">-LicenseUri</span></span>

<span data-ttu-id="72eeb-217">指定模組的授權條款 URL。</span><span class="sxs-lookup"><span data-stu-id="72eeb-217">Specifies the URL of licensing terms for the module.</span></span>

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

### <span data-ttu-id="72eeb-218">-ModuleList</span><span class="sxs-lookup"><span data-stu-id="72eeb-218">-ModuleList</span></span>

<span data-ttu-id="72eeb-219">列出此模組中所包含的所有模組。</span><span class="sxs-lookup"><span data-stu-id="72eeb-219">Lists all modules that are included in this module.</span></span>

<span data-ttu-id="72eeb-220">輸入每個模組名稱做為字串或含 **ModuleName** 和 **ModuleVersion** 索引鍵的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="72eeb-220">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="72eeb-221">雜湊表也可以有選用的 **GUID** 索引鍵。</span><span class="sxs-lookup"><span data-stu-id="72eeb-221">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="72eeb-222">您可以在參數值中結合字串和雜湊表。</span><span class="sxs-lookup"><span data-stu-id="72eeb-222">You can combine strings and hash tables in the parameter value.</span></span>

<span data-ttu-id="72eeb-223">這個索引鍵被設計來做為模組詳細目錄。</span><span class="sxs-lookup"><span data-stu-id="72eeb-223">This key is designed to act as a module inventory.</span></span> <span data-ttu-id="72eeb-224">系統不會自動處理此索引鍵值中所列的模組。</span><span class="sxs-lookup"><span data-stu-id="72eeb-224">The modules that are listed in the value of this key aren't automatically processed.</span></span>

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

### <span data-ttu-id="72eeb-225">-ModuleVersion</span><span class="sxs-lookup"><span data-stu-id="72eeb-225">-ModuleVersion</span></span>

<span data-ttu-id="72eeb-226">指定模組的版本。</span><span class="sxs-lookup"><span data-stu-id="72eeb-226">Specifies the module's version.</span></span>

<span data-ttu-id="72eeb-227">不需要此參數，但資訊清單中需要 **ModuleVersion** 索引鍵。</span><span class="sxs-lookup"><span data-stu-id="72eeb-227">This parameter isn't required, but a **ModuleVersion** key is required in the manifest.</span></span> <span data-ttu-id="72eeb-228">如果您省略此參數，則會 `New-ModuleManifest` 建立值為1.0 的 **ModuleVersion** 索引鍵。</span><span class="sxs-lookup"><span data-stu-id="72eeb-228">If you omit this parameter, `New-ModuleManifest` creates a **ModuleVersion** key with a value of 1.0.</span></span>

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

### <span data-ttu-id="72eeb-229">-NestedModules</span><span class="sxs-lookup"><span data-stu-id="72eeb-229">-NestedModules</span></span>

<span data-ttu-id="72eeb-230">指定腳本模組 (`.psm1`) 和二進位模組， (`.dll`) 匯入模組的會話狀態。</span><span class="sxs-lookup"><span data-stu-id="72eeb-230">Specifies script modules (`.psm1`) and binary modules (`.dll`) that are imported into the module's session state.</span></span> <span data-ttu-id="72eeb-231">**NestedModules** 機碼中的檔案會依它們在值中的列出循序執行。</span><span class="sxs-lookup"><span data-stu-id="72eeb-231">The files in the **NestedModules** key run in the order in which they're listed in the value.</span></span>

<span data-ttu-id="72eeb-232">輸入每個模組名稱做為字串或含 **ModuleName** 和 **ModuleVersion** 索引鍵的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="72eeb-232">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="72eeb-233">雜湊表也可以有選用的 **GUID** 索引鍵。</span><span class="sxs-lookup"><span data-stu-id="72eeb-233">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="72eeb-234">您可以在參數值中結合字串和雜湊表。</span><span class="sxs-lookup"><span data-stu-id="72eeb-234">You can combine strings and hash tables in the parameter value.</span></span>

<span data-ttu-id="72eeb-235">一般而言，巢狀模組包含根模組內部處理所需要的命令。</span><span class="sxs-lookup"><span data-stu-id="72eeb-235">Typically, nested modules contain commands that the root module needs for its internal processing.</span></span>
<span data-ttu-id="72eeb-236">根據預設，嵌套模組中的命令會從模組的會話狀態匯出為呼叫端的會話狀態，但根模組可限制其匯出的命令。</span><span class="sxs-lookup"><span data-stu-id="72eeb-236">By default, the commands in nested modules are exported from the module's session state into the caller's session state, but the root module can restrict the commands that it exports.</span></span> <span data-ttu-id="72eeb-237">例如，使用 `Export-ModuleMember` 命令。</span><span class="sxs-lookup"><span data-stu-id="72eeb-237">For example, by using an `Export-ModuleMember` command.</span></span>

<span data-ttu-id="72eeb-238">模組會話狀態中的嵌套模組可供根模組使用，但 `Get-Module` 呼叫端的會話狀態中的命令不會傳回它們。</span><span class="sxs-lookup"><span data-stu-id="72eeb-238">Nested modules in the module session state are available to the root module, but they aren't returned by a `Get-Module` command in the caller's session state.</span></span>

<span data-ttu-id="72eeb-239">NestedModules 索引 `.ps1` 鍵中列出的腳本 ( **NestedModules** ) 會在模組會話狀態下執行，而不是在呼叫端的會話狀態中執行。</span><span class="sxs-lookup"><span data-stu-id="72eeb-239">Scripts (`.ps1`) that are listed in the **NestedModules** key are run in the module's session state, not in the caller's session state.</span></span> <span data-ttu-id="72eeb-240">如果要在呼叫者工作階段狀態下執行指令碼，請在資訊清單的 **ScriptsToProcess** 索引鍵值中列出指令碼檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="72eeb-240">To run a script in the caller's session state, list the script file name in the value of the **ScriptsToProcess** key in the manifest.</span></span>

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

### <span data-ttu-id="72eeb-241">-PassThru</span><span class="sxs-lookup"><span data-stu-id="72eeb-241">-PassThru</span></span>

<span data-ttu-id="72eeb-242">將產生的模組資訊清單寫入主控台並建立檔案 `.psd1` 。</span><span class="sxs-lookup"><span data-stu-id="72eeb-242">Writes the resulting module manifest to the console and creates a `.psd1` file.</span></span> <span data-ttu-id="72eeb-243">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="72eeb-243">By default, this cmdlet doesn't generate any output.</span></span>

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

### <span data-ttu-id="72eeb-244">-Path</span><span class="sxs-lookup"><span data-stu-id="72eeb-244">-Path</span></span>

<span data-ttu-id="72eeb-245">指定新模組資訊清單的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="72eeb-245">Specifies the path and file name of the new module manifest.</span></span> <span data-ttu-id="72eeb-246">輸入副檔名為的路徑和檔案名 `.psd1` ，例如 `$pshome\Modules\MyModule\MyModule.psd1` 。</span><span class="sxs-lookup"><span data-stu-id="72eeb-246">Enter a path and file name with a `.psd1` file name extension, such as `$pshome\Modules\MyModule\MyModule.psd1`.</span></span> <span data-ttu-id="72eeb-247">需要 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="72eeb-247">The **Path** parameter is required.</span></span>

<span data-ttu-id="72eeb-248">如果您指定現有檔案的路徑，則 `New-ModuleManifest` 會在沒有警告的情況下取代檔案，除非檔案具有唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="72eeb-248">If you specify the path to an existing file, `New-ModuleManifest` replaces the file without warning unless the file has the read-only attribute.</span></span>

<span data-ttu-id="72eeb-249">資訊清單應該位於模組的目錄中，且資訊清單檔案名應該與模組目錄名稱相同，但是 `.psd1` 副檔名為。</span><span class="sxs-lookup"><span data-stu-id="72eeb-249">The manifest should be located in the module's directory, and the manifest file name should be the same as the module directory name, but with a `.psd1` file name extension.</span></span>

> [!NOTE]
> <span data-ttu-id="72eeb-250">您無法使用變數（例如 `$PSHOME` 或 `$HOME` ）來回應 **路徑** 參數值的提示。</span><span class="sxs-lookup"><span data-stu-id="72eeb-250">You cannot use variables, such as `$PSHOME` or `$HOME`, in response to a prompt for a **Path** parameter value.</span></span> <span data-ttu-id="72eeb-251">如果要使用變數，請在命令中包含 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="72eeb-251">To use a variable, include the **Path** parameter in the command.</span></span>

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

### <span data-ttu-id="72eeb-252">-PowerShellHostName</span><span class="sxs-lookup"><span data-stu-id="72eeb-252">-PowerShellHostName</span></span>

<span data-ttu-id="72eeb-253">指定模組所需之 PowerShell 主機程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="72eeb-253">Specifies the name of the PowerShell host program that the module requires.</span></span> <span data-ttu-id="72eeb-254">輸入主機程式的名稱，例如 **Windows PowerShell ISE host** 或 **ConsoleHost** 。</span><span class="sxs-lookup"><span data-stu-id="72eeb-254">Enter the name of the host program, such as **Windows PowerShell ISE Host** or **ConsoleHost**.</span></span> <span data-ttu-id="72eeb-255">不允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="72eeb-255">Wildcards aren't permitted.</span></span>

<span data-ttu-id="72eeb-256">若要尋找主機程式的名稱，請在程式中輸入 `$Host.Name` 。</span><span class="sxs-lookup"><span data-stu-id="72eeb-256">To find the name of a host program, in the program, type `$Host.Name`.</span></span>

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

### <span data-ttu-id="72eeb-257">-PowerShellHostVersion</span><span class="sxs-lookup"><span data-stu-id="72eeb-257">-PowerShellHostVersion</span></span>

<span data-ttu-id="72eeb-258">指定適用于模組的 PowerShell 主機程式的最小版本。</span><span class="sxs-lookup"><span data-stu-id="72eeb-258">Specifies the minimum version of the PowerShell host program that works with the module.</span></span> <span data-ttu-id="72eeb-259">輸入版本號碼，例如 1.1。</span><span class="sxs-lookup"><span data-stu-id="72eeb-259">Enter a version number, such as 1.1.</span></span>

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

### <span data-ttu-id="72eeb-260">-PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="72eeb-260">-PowerShellVersion</span></span>

<span data-ttu-id="72eeb-261">指定可與此模組搭配運作的 PowerShell 最低版本。</span><span class="sxs-lookup"><span data-stu-id="72eeb-261">Specifies the minimum version of PowerShell that works with this module.</span></span> <span data-ttu-id="72eeb-262">例如，您可以輸入1.0、2.0 或3.0 作為參數的值。</span><span class="sxs-lookup"><span data-stu-id="72eeb-262">For example, you can enter 1.0, 2.0, or 3.0 as the parameter's value.</span></span>

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

### <span data-ttu-id="72eeb-263">-發行前版本</span><span class="sxs-lookup"><span data-stu-id="72eeb-263">-Prerelease</span></span>

<span data-ttu-id="72eeb-264">此課程模組的發行前版本字串。</span><span class="sxs-lookup"><span data-stu-id="72eeb-264">Prerelease string of this module.</span></span> <span data-ttu-id="72eeb-265">新增發行前版本字串會將模組識別為發行前版本。</span><span class="sxs-lookup"><span data-stu-id="72eeb-265">Adding a Prerelease string identifies the module as a prerelease version.</span></span> <span data-ttu-id="72eeb-266">當模組發行至 PowerShell 資源庫時，此資料會用來識別發行前版本套件。</span><span class="sxs-lookup"><span data-stu-id="72eeb-266">When the module is published to the PowerShell Gallery, this data is used to identify prerelease packages.</span></span> <span data-ttu-id="72eeb-267">若要從資源庫取得發行前版本套件，您必須使用 **AllowPrerelease** 參數搭配 PowerShellGet 命令 `Find-Module` 、、 `Install-Module` `Update-Module` 和 `Save-Module` 。</span><span class="sxs-lookup"><span data-stu-id="72eeb-267">To acquire prerelease packages from the Gallery, you must use the **AllowPrerelease** parameter with the PowerShellGet commands `Find-Module`, `Install-Module`, `Update-Module`, and `Save-Module`.</span></span>

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

### <span data-ttu-id="72eeb-268">-PrivateData</span><span class="sxs-lookup"><span data-stu-id="72eeb-268">-PrivateData</span></span>

<span data-ttu-id="72eeb-269">指定匯入模組時傳遞給模組的資料。</span><span class="sxs-lookup"><span data-stu-id="72eeb-269">Specifies data that is passed to the module when it's imported.</span></span>

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

### <span data-ttu-id="72eeb-270">-ProcessorArchitecture</span><span class="sxs-lookup"><span data-stu-id="72eeb-270">-ProcessorArchitecture</span></span>

<span data-ttu-id="72eeb-271">指定模組需要的處理器架構。</span><span class="sxs-lookup"><span data-stu-id="72eeb-271">Specifies the processor architecture that the module requires.</span></span> <span data-ttu-id="72eeb-272">有效的值為 x86、AMD64、IA64、MSIL 和 None (未知或未指定的) 。</span><span class="sxs-lookup"><span data-stu-id="72eeb-272">Valid values are x86, AMD64, IA64, MSIL, and None (unknown or unspecified).</span></span>

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

### <span data-ttu-id="72eeb-273">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="72eeb-273">-ProjectUri</span></span>

<span data-ttu-id="72eeb-274">指定與這個專案相關之網頁的 URL。</span><span class="sxs-lookup"><span data-stu-id="72eeb-274">Specifies the URL of a web page about this project.</span></span>

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

### <span data-ttu-id="72eeb-275">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="72eeb-275">-ReleaseNotes</span></span>

<span data-ttu-id="72eeb-276">指定版本資訊。</span><span class="sxs-lookup"><span data-stu-id="72eeb-276">Specifies release notes.</span></span>

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

### <span data-ttu-id="72eeb-277">-RequiredAssemblies</span><span class="sxs-lookup"><span data-stu-id="72eeb-277">-RequiredAssemblies</span></span>

<span data-ttu-id="72eeb-278">指定模組所需 () 檔案的元件 `.dll` 。</span><span class="sxs-lookup"><span data-stu-id="72eeb-278">Specifies the assembly (`.dll`) files that the module requires.</span></span> <span data-ttu-id="72eeb-279">輸入組件檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="72eeb-279">Enter the assembly file names.</span></span>
<span data-ttu-id="72eeb-280">PowerShell 會在更新類型或格式、匯入嵌套模組，或匯入在 **RootModule** 索引鍵值中指定的模組檔案之前，先載入指定的元件。</span><span class="sxs-lookup"><span data-stu-id="72eeb-280">PowerShell loads the specified assemblies before updating types or formats, importing nested modules, or importing the module file that is specified in the value of the **RootModule** key.</span></span>

<span data-ttu-id="72eeb-281">使用這個參數來列出模組需要的所有組件，包含必須載入以更新任何格式的組件，或是 **FormatsToProcess** 或 **TypesToProcess** 索引鍵中列出的類型檔案，即使這些組件也在 **NestedModules** 索引鍵中列為二進位模組。</span><span class="sxs-lookup"><span data-stu-id="72eeb-281">Use this parameter to list all the assemblies that the module requires, including assemblies that must be loaded to update any formatting or type files that are listed in the **FormatsToProcess** or **TypesToProcess** keys, even if those assemblies are also listed as binary modules in the **NestedModules** key.</span></span>

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

### <span data-ttu-id="72eeb-282">-RequiredModules</span><span class="sxs-lookup"><span data-stu-id="72eeb-282">-RequiredModules</span></span>

<span data-ttu-id="72eeb-283">指定必須在全域工作階段狀態的模組。</span><span class="sxs-lookup"><span data-stu-id="72eeb-283">Specifies modules that must be in the global session state.</span></span> <span data-ttu-id="72eeb-284">如果必要的模組不在全域會話狀態中，則 PowerShell 會將它們匯入。</span><span class="sxs-lookup"><span data-stu-id="72eeb-284">If the required modules aren't in the global session state, PowerShell imports them.</span></span> <span data-ttu-id="72eeb-285">如果無法使用必要的模組，則 `Import-Module` 命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="72eeb-285">If the required modules aren't available, the `Import-Module` command fails.</span></span>

<span data-ttu-id="72eeb-286">輸入每個模組名稱做為字串或含 **ModuleName** 和 **ModuleVersion** 索引鍵的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="72eeb-286">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="72eeb-287">雜湊表也可以有選用的 **GUID** 索引鍵。</span><span class="sxs-lookup"><span data-stu-id="72eeb-287">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="72eeb-288">您可以在參數值中結合字串和雜湊表。</span><span class="sxs-lookup"><span data-stu-id="72eeb-288">You can combine strings and hash tables in the parameter value.</span></span>

<span data-ttu-id="72eeb-289">在 PowerShell 2.0 中， `Import-Module` 不會自動匯入必要的模組。</span><span class="sxs-lookup"><span data-stu-id="72eeb-289">In PowerShell 2.0, `Import-Module` doesn't import required modules automatically.</span></span> <span data-ttu-id="72eeb-290">它只會驗證必要的模組會在全域工作階段狀態。</span><span class="sxs-lookup"><span data-stu-id="72eeb-290">It just verifies that the required modules are in the global session state.</span></span>

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

### <span data-ttu-id="72eeb-291">-RequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="72eeb-291">-RequireLicenseAcceptance</span></span>

<span data-ttu-id="72eeb-292">旗標，指出模組是否需要明確接受使用者的安裝、更新、orsave。</span><span class="sxs-lookup"><span data-stu-id="72eeb-292">Flag to indicate whether the module requires explicit user acceptance for install, update, orsave.</span></span>

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

### <span data-ttu-id="72eeb-293">-RootModule</span><span class="sxs-lookup"><span data-stu-id="72eeb-293">-RootModule</span></span>

<span data-ttu-id="72eeb-294">指定模組的主要或根檔案。</span><span class="sxs-lookup"><span data-stu-id="72eeb-294">Specifies the primary or root file of the module.</span></span> <span data-ttu-id="72eeb-295">輸入腳本 (的檔案名 `.ps1`) 、腳本模組 (`.psm1`) 、模組資訊清單 () `.psd1` 、元件 () 、 `.dll` Cmdlet 定義 XML 檔案 (`.cdxml`) 或工作流程 (`.xaml`) 。</span><span class="sxs-lookup"><span data-stu-id="72eeb-295">Enter the file name of a script (`.ps1`), a script module (`.psm1`), a module manifest(`.psd1`), an assembly (`.dll`), a cmdlet definition XML file (`.cdxml`), or a workflow (`.xaml`).</span></span> <span data-ttu-id="72eeb-296">匯入模組時，從根模組檔案匯出的成員會匯入呼叫者工作階段狀態。</span><span class="sxs-lookup"><span data-stu-id="72eeb-296">When the module is imported, the members that are exported from the root module file are imported into the caller's session state.</span></span>

<span data-ttu-id="72eeb-297">如果模組有資訊清單檔案，但 **RootModule** 索引鍵中沒有指定根檔案，資訊清單會變成模組的主要檔案，且該模組會變成 (ModuleType = 資訊清單) 的資訊清單模組。</span><span class="sxs-lookup"><span data-stu-id="72eeb-297">If a module has a manifest file and no root file was designated in the **RootModule** key, the manifest becomes the primary file for the module, and the module becomes a manifest module (ModuleType = Manifest).</span></span>

<span data-ttu-id="72eeb-298">若要從 `.psm1` 具有資訊清單之模組中的或檔案匯出成員 `.dll` ，則必須在資訊清單中的 **RootModule** 或 **NestedModules** 索引鍵的值中指定這些檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="72eeb-298">To export members from `.psm1` or `.dll` files in a module that has a manifest, the names of those files must be specified in the values of the **RootModule** or **NestedModules** keys in the manifest.</span></span> <span data-ttu-id="72eeb-299">否則，不會匯出其成員。</span><span class="sxs-lookup"><span data-stu-id="72eeb-299">Otherwise, their members aren't exported.</span></span>

> [!NOTE]
> <span data-ttu-id="72eeb-300">在 PowerShell 2.0 中，此機碼稱為 **ModuleToProcess** 。</span><span class="sxs-lookup"><span data-stu-id="72eeb-300">In PowerShell 2.0, this key was called **ModuleToProcess**.</span></span> <span data-ttu-id="72eeb-301">您可以使用 **RootModule** 參數名稱或其 **ModuleToProcess** 別名。</span><span class="sxs-lookup"><span data-stu-id="72eeb-301">You can use the **RootModule** parameter name or its **ModuleToProcess** alias.</span></span>

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

### <span data-ttu-id="72eeb-302">-ScriptsToProcess</span><span class="sxs-lookup"><span data-stu-id="72eeb-302">-ScriptsToProcess</span></span>

<span data-ttu-id="72eeb-303">指定匯 `.ps1` 入模組時，在呼叫者會話狀態中執行的腳本 () 檔。</span><span class="sxs-lookup"><span data-stu-id="72eeb-303">Specifies script (`.ps1`) files that run in the caller's session state when the module is imported.</span></span>
<span data-ttu-id="72eeb-304">您可以使用這些指令碼來準備環境，就像您使用登入指令碼一般。</span><span class="sxs-lookup"><span data-stu-id="72eeb-304">You can use these scripts to prepare an environment, just as you might use a login script.</span></span>

<span data-ttu-id="72eeb-305">如果要指定在模組工作階段狀態中執行的指令碼，請使用 **NestedModules** 索引鍵。</span><span class="sxs-lookup"><span data-stu-id="72eeb-305">To specify scripts that run in the module's session state, use the **NestedModules** key.</span></span>

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

### <span data-ttu-id="72eeb-306">-Tags</span><span class="sxs-lookup"><span data-stu-id="72eeb-306">-Tags</span></span>

<span data-ttu-id="72eeb-307">指定標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="72eeb-307">Specifies an array of tags.</span></span>

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

### <span data-ttu-id="72eeb-308">-TypesToProcess</span><span class="sxs-lookup"><span data-stu-id="72eeb-308">-TypesToProcess</span></span>

<span data-ttu-id="72eeb-309">指定匯入模組時要執行的類型檔案 (`.ps1xml`) 。</span><span class="sxs-lookup"><span data-stu-id="72eeb-309">Specifies the type files (`.ps1xml`) that run when the module is imported.</span></span>

<span data-ttu-id="72eeb-310">當您匯入模組時，PowerShell 會 `Update-TypeData` 使用指定的檔案來執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="72eeb-310">When you import the module, PowerShell runs the `Update-TypeData` cmdlet with the specified files.</span></span>
<span data-ttu-id="72eeb-311">因為類型檔案未設定範圍，所以它們會影響會話中所有的會話狀態。</span><span class="sxs-lookup"><span data-stu-id="72eeb-311">Because type files aren't scoped, they affect all session states in the session.</span></span>

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

### <span data-ttu-id="72eeb-312">-VariablesToExport</span><span class="sxs-lookup"><span data-stu-id="72eeb-312">-VariablesToExport</span></span>

<span data-ttu-id="72eeb-313">指定模組匯出的變數。</span><span class="sxs-lookup"><span data-stu-id="72eeb-313">Specifies the variables that the module exports.</span></span> <span data-ttu-id="72eeb-314">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="72eeb-314">Wildcards are permitted.</span></span>

<span data-ttu-id="72eeb-315">您可以使用此參數來限制模組匯出的變數。</span><span class="sxs-lookup"><span data-stu-id="72eeb-315">You can use this parameter to restrict the variables that are exported by the module.</span></span> <span data-ttu-id="72eeb-316">它可以從匯出的變數清單中移除變數，但它無法將變數新增至清單。</span><span class="sxs-lookup"><span data-stu-id="72eeb-316">It can remove variables from the list of exported variables, but it can't add variables to the list.</span></span>

<span data-ttu-id="72eeb-317">如果您省略這個參數，則 `New-ModuleManifest` 會建立 **VariablesToExport** 索引鍵，其值為 `*` (all) ，表示模組中定義的所有變數都會由資訊清單匯出。</span><span class="sxs-lookup"><span data-stu-id="72eeb-317">If you omit this parameter, `New-ModuleManifest` creates a **VariablesToExport** key with a value of `*` (all), meaning that all variables defined in the module are exported by the manifest.</span></span>

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

### <span data-ttu-id="72eeb-318">-Confirm</span><span class="sxs-lookup"><span data-stu-id="72eeb-318">-Confirm</span></span>

<span data-ttu-id="72eeb-319">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="72eeb-319">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="72eeb-320">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="72eeb-320">-WhatIf</span></span>

<span data-ttu-id="72eeb-321">顯示執行時所發生 `New-ModuleManifest` 的情況。</span><span class="sxs-lookup"><span data-stu-id="72eeb-321">Shows what would happen if `New-ModuleManifest` runs.</span></span> <span data-ttu-id="72eeb-322">不會執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="72eeb-322">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="72eeb-323">-ClrVersion</span><span class="sxs-lookup"><span data-stu-id="72eeb-323">-ClrVersion</span></span>

<span data-ttu-id="72eeb-324">指定模組所需要的 Microsoft .NET Framework Common Language Runtime (CLR) 最低版本。</span><span class="sxs-lookup"><span data-stu-id="72eeb-324">Specifies the minimum version of the Common Language Runtime (CLR) of the Microsoft .NET Framework that the module requires.</span></span>

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

### <span data-ttu-id="72eeb-325">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="72eeb-325">CommonParameters</span></span>
<span data-ttu-id="72eeb-326">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="72eeb-326">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="72eeb-327">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="72eeb-327">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="72eeb-328">輸入</span><span class="sxs-lookup"><span data-stu-id="72eeb-328">INPUTS</span></span>

### <span data-ttu-id="72eeb-329">無</span><span class="sxs-lookup"><span data-stu-id="72eeb-329">None</span></span>

<span data-ttu-id="72eeb-330">您無法透過管道傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="72eeb-330">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="72eeb-331">輸出</span><span class="sxs-lookup"><span data-stu-id="72eeb-331">OUTPUTS</span></span>

### <span data-ttu-id="72eeb-332">無或 System.String</span><span class="sxs-lookup"><span data-stu-id="72eeb-332">None or System.String</span></span>

<span data-ttu-id="72eeb-333">依預設， `New-ModuleManifest` 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="72eeb-333">By default, `New-ModuleManifest` doesn't generate any output.</span></span> <span data-ttu-id="72eeb-334">但是，如果您使用 **PassThru** 參數，它會產生代表模組資訊清單的 **system.string** 物件。</span><span class="sxs-lookup"><span data-stu-id="72eeb-334">However, if you use the **PassThru** parameter, it generates a **System.String** object representing the module manifest.</span></span>

## <span data-ttu-id="72eeb-335">注意</span><span class="sxs-lookup"><span data-stu-id="72eeb-335">NOTES</span></span>

<span data-ttu-id="72eeb-336">`New-ModuleManifest` 在 Windows 和非 Windows 平臺上執行時，會建立模組資訊清單 (`.psd1`) 編碼為 **UTF8NoBOM** 的檔案。</span><span class="sxs-lookup"><span data-stu-id="72eeb-336">`New-ModuleManifest` running on Windows and non-Windows platforms creates module manifest (`.psd1`) files encoded as **UTF8NoBOM**.</span></span>

<span data-ttu-id="72eeb-337">模組資訊清單通常為選擇性。</span><span class="sxs-lookup"><span data-stu-id="72eeb-337">Module manifests are usually optional.</span></span> <span data-ttu-id="72eeb-338">不過，需要模組資訊清單才能匯出安裝在全域組件快取中的組件。</span><span class="sxs-lookup"><span data-stu-id="72eeb-338">However, a module manifest is required to export an assembly that is installed in the global assembly cache.</span></span>

<span data-ttu-id="72eeb-339">若要在目錄中新增或變更檔案 `$pshome\Modules` ，請使用 [以 **系統管理員身分執行** ] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="72eeb-339">To add or change files in the `$pshome\Modules` directory, start PowerShell with the **Run as administrator** option.</span></span>

> [!NOTE]
> <span data-ttu-id="72eeb-340">從 PowerShell 6.2 開始，PowerShell 會嘗試載入模組資訊清單的 **FileList** 屬性中所列的所有 DLL 檔案。</span><span class="sxs-lookup"><span data-stu-id="72eeb-340">Beginning in PowerShell 6.2, PowerShell attempts to load all the DLL files listed in **FileList** property of the module manifest.</span></span> <span data-ttu-id="72eeb-341">**FileList** 中的原生 dll 無法在進程中載入，而且會忽略錯誤。</span><span class="sxs-lookup"><span data-stu-id="72eeb-341">Native DLLs is in the **FileList** fail to load in the process and the error is ignored.</span></span> <span data-ttu-id="72eeb-342">所有 managed Dll 都會載入到進程中。</span><span class="sxs-lookup"><span data-stu-id="72eeb-342">All managed DLLs are loaded in the process.</span></span> <span data-ttu-id="72eeb-343">此行為已在 PowerShell 7.1 中移除。</span><span class="sxs-lookup"><span data-stu-id="72eeb-343">This behavior was removed in PowerShell 7.1.</span></span>

<span data-ttu-id="72eeb-344">在 PowerShell 2.0 中，許多的參數 `New-ModuleManifest` 都是強制性的，即使在模組資訊清單中不需要它們也是一樣。</span><span class="sxs-lookup"><span data-stu-id="72eeb-344">In PowerShell 2.0, many parameters of `New-ModuleManifest` were mandatory, even though they weren't required in a module manifest.</span></span> <span data-ttu-id="72eeb-345">從 PowerShell 3.0 開始，只有 **Path** 參數是必要的。</span><span class="sxs-lookup"><span data-stu-id="72eeb-345">Beginning in PowerShell 3.0, only the **Path** parameter is mandatory.</span></span>

<span data-ttu-id="72eeb-346">會話是 PowerShell 執行環境的實例。</span><span class="sxs-lookup"><span data-stu-id="72eeb-346">A session is an instance of the PowerShell execution environment.</span></span> <span data-ttu-id="72eeb-347">工作階段可以有一或多個工作階段狀態。</span><span class="sxs-lookup"><span data-stu-id="72eeb-347">A session can have one or more session states.</span></span> <span data-ttu-id="72eeb-348">依預設，工作階段只有全域工作階段狀態，但每個匯入的模組有自己的工作階段狀態。</span><span class="sxs-lookup"><span data-stu-id="72eeb-348">By default, a session has only a global session state, but each imported module has its own session state.</span></span> <span data-ttu-id="72eeb-349">工作階段狀態允許執行模組中的命令，而不會影響全域工作階段狀態。</span><span class="sxs-lookup"><span data-stu-id="72eeb-349">Session states allow the commands in a module to run without affecting the global session state.</span></span>

<span data-ttu-id="72eeb-350">呼叫端的會話狀態是模組匯入的會話狀態。</span><span class="sxs-lookup"><span data-stu-id="72eeb-350">The caller's session state is the session state into which a module is imported.</span></span> <span data-ttu-id="72eeb-351">一般而言，它是指全域會話狀態，但當模組匯入嵌套模組時，呼叫端是模組，而呼叫端的會話狀態是模組的會話狀態。</span><span class="sxs-lookup"><span data-stu-id="72eeb-351">Typically, it refers to the global session state, but when a module imports nested modules, the caller is the module and the caller's session state is the module's session state.</span></span>

## <span data-ttu-id="72eeb-352">相關連結</span><span class="sxs-lookup"><span data-stu-id="72eeb-352">RELATED LINKS</span></span>

[<span data-ttu-id="72eeb-353">Export-ModuleMember</span><span class="sxs-lookup"><span data-stu-id="72eeb-353">Export-ModuleMember</span></span>](Export-ModuleMember.md)

[<span data-ttu-id="72eeb-354">Get-Module</span><span class="sxs-lookup"><span data-stu-id="72eeb-354">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="72eeb-355">Import-Module</span><span class="sxs-lookup"><span data-stu-id="72eeb-355">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="72eeb-356">New-Module</span><span class="sxs-lookup"><span data-stu-id="72eeb-356">New-Module</span></span>](New-Module.md)

[<span data-ttu-id="72eeb-357">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="72eeb-357">Remove-Module</span></span>](Remove-Module.md)

[<span data-ttu-id="72eeb-358">Test-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="72eeb-358">Test-ModuleManifest</span></span>](Test-ModuleManifest.md)

[<span data-ttu-id="72eeb-359">about_Modules</span><span class="sxs-lookup"><span data-stu-id="72eeb-359">about_Modules</span></span>](./About/about_Modules.md)
