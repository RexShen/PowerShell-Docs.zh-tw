---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: "資源庫,powershell,cmdlet,psget"
title: modulewithpseditionsupport
ms.openlocfilehash: 8a762ddf307f47ecec8d2a63098e75cde97c391f
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2018
---
# <a name="modules-with-compatible-powershell-editions"></a>具有相容 PowerShell 版本的模組
從 5.1 版開始，PowerShell 提供代表各種功能集及平台相容性的不同版本。

- **Desktop Edition︰**建置在 .NET Framework 上，與在完整使用量的 Windows 版本 (如 Server Core 和 Windows Desktop) 上執行之 PowerShell 版本的指令碼和模組相容。
- **Core Edition︰**建置在 .NET Core 上，與在降低使用量的 Windows 版本 (如 Nano Server 和 Windows IoT) 上執行之 PowerShell 版本的指令碼和模組相容。

## <a name="the-running-edition-of-powershell-is-shown-in-the-psedition-property-of-psversiontable"></a>$PSVersionTable 的 PSEdition 屬性會顯示正在執行的 PowerShell 版本。
```powershell
$PSVersionTable

Name                           Value
----                           -----
PSVersion                      5.1.14300.1000
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
CLRVersion                     4.0.30319.42000
BuildVersion                   10.0.14300.1000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

## <a name="module-authors-can-declare-their-modules-to-be-compatible-with-one-or-more-powershell-editions-using-the-compatiblepseditions-module-manifest-key-this-key-is-only-supported-on-powershell-51-or-later"></a>模組作者可以使用 CompatiblePSEditions 模組資訊清單金鑰，宣告其模組與一或多個 PowerShell 版本相容。 僅限 PowerShell 5.1 或更新版本支援此金鑰。
「請注意」一旦使用 CompatiblePSEditions 金鑰指定模組資訊清單，就無法在較低版本的 PowerShell 上進行匯入。

```powershell
New-ModuleManifest -Path .\TestModuleWithEdition.psd1 -CompatiblePSEditions Desktop,Core -PowerShellVersion 5.1
$ModuleInfo = Test-ModuleManifest -Path .\TestModuleWithEdition.psd1
$ModuleInfo.CompatiblePSEditions
Desktop
Core

$ModuleInfo | Get-Member CompatiblePSEditions

   TypeName: System.Management.Automation.PSModuleInfo

Name                 MemberType Definition
----                 ---------- ----------
CompatiblePSEditions Property   System.Collections.Generic.IEnumerable[string] CompatiblePSEditions {get;}

```
取得可用的模組清單時，您可以依據 PowerShell 版本篩選該清單。
```powershell
Get-Module -ListAvailable -PSEdition Desktop

    Directory: C:\Program Files\WindowsPowerShell\Modules


ModuleType Version    Name                                ExportedCommands
---------- -------    ----                                ----------------
Manifest   1.0        ModuleWithPSEditions

Get-Module -ListAvailable -PSEdition Core | % CompatiblePSEditions
Desktop
Core

```

## <a name="module-authors-can-publish-a-single-module-targeting-to-either-or-both-powershell-editions-desktop-and-core"></a>模組作者可以發行以其中一個 PowerShell 版本 (桌面和核心) 或兩者同時為目標的單一模組 

單一模組可在桌面和核心版本上使用，作者需在該模組的 RootModule 中或使用 $PSEdition 變數的模組資訊清單中，新增必要的邏輯。
模組可以有兩組以 CoreCLR 和 FullCLR 為目標的編譯 DLL。
以下幾個選項可用來將邏輯封裝至您的模組，以載入適當的 dll。

### <a name="option-1-packaging-a-module-for-targeting-multiple-versions-and-multiple-editions-of-powershell"></a>選項 1︰封裝將多個版本的 PowerShell 作為目標的模組

#### <a name="module-folder-contents"></a>模組資料夾內容
- Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll 
- Microsoft.Windows.PowerShell.ScriptAnalyzer.dll 
- PSScriptAnalyzer.psd1
- PSScriptAnalyzer.psm1
- ScriptAnalyzer.format.ps1xml
- ScriptAnalyzer.types.ps1xml
- coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll 
- coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll 
- en-US\about_PSScriptAnalyzer.help.txt
- en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml
- PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll 
- PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll 
- Settings\CmdletDesign.psd1
- Settings\DSC.psd1
- Settings\ScriptFunctions.psd1
- Settings\ScriptingStyle.psd1
- Settings\ScriptSecurity.psd1

#### <a name="contents-of-psscriptanalyzerpsd1-file"></a>PSScriptAnalyzer.psd1 檔案的內容

```powershell
@{
 
# Author of this module
Author = 'Microsoft Corporation'

# Script module or binary module file associated with this manifest.
RootModule = 'PSScriptAnalyzer.psm1'

# Version number of this module.
ModuleVersion = '1.6.1'

# ---
}
```

#### <a name="contents-of-psscriptanalyzerpsm1-file"></a>PSScriptAnalyzer.psm1 檔案的內容
以下邏輯會載入必要的組件，視目前版本而定。

```powershell
#
# Script module for module 'PSScriptAnalyzer'
#
Set-StrictMode -Version Latest

# Set up some helper variables to make it easier to work with the module
$PSModule = $ExecutionContext.SessionState.Module
$PSModuleRoot = $PSModule.ModuleBase

# Import the appropriate nested binary module based on the current PowerShell version
$binaryModuleRoot = $PSModuleRoot


if (($PSVersionTable.Keys -contains "PSEdition") -and ($PSVersionTable.PSEdition -ne 'Desktop')) {
    $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'coreclr'
}
else
{
    if ($PSVersionTable.PSVersion -lt [Version]'5.0') {
        $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'PSv3'
    }    
}

$binaryModulePath = Join-Path -Path $binaryModuleRoot -ChildPath 'Microsoft.Windows.PowerShell.ScriptAnalyzer.dll'
$binaryModule = Import-Module -Name $binaryModulePath -PassThru

# When the module is unloaded, remove the nested binary module that was loaded with it
$PSModule.OnRemove = {
    Remove-Module -ModuleInfo $binaryModule
} 

```

### <a name="option-2-use-psedition-variable-in-the-psd1-file-to-load-the-proper-dlls-and-nestedrequired-modules"></a>選項 2︰在 PSD1 檔案中使用 $PSEdition 變數，以載入適當的 Dll 和巢狀/必要的模組

PS 5.1 或更新版本的模組資訊清單檔案中允許 $PSEdition 全域變數。
模組作者可透過使用此變數，指定模組資訊清單檔案中的條件值。 在限制的語言模式或 [資料] 區段中，可以參考 $PSEdition 變數。 

「請注意」一旦使用 CompatiblePSEditions 金鑰指定模組資訊清單，或使用 $PSEdition 變數，就無法在較低版本的 PowerShell 上進行匯入。


#### <a name="sample-module-manifest-file-with-compatiblepseditions-key"></a>使用 CompatiblePSEditions 金鑰的模組資訊清單檔案範例

```powershell
@{ 
# - - -
 
# Script module or binary module file associated with this manifest.
RootModule = if($PSEdition -eq 'Core')
{
'coreclr\MyCoreClrRM.dll'
}
else # Desktop
{
'clr\MyFullClrRM.dll'
}
 
# Supported PSEditions
CompatiblePSEditions = 'Desktop', 'Core'
 
# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
NestedModules = if($PSEdition -eq 'Core')
{
'coreclr\MyCoreClrNM1.dll',
'coreclr\MyCoreClrNM2.dll'
}
else # Desktop
{
'clr\MyFullClrNM1.dll',
'clr\MyFullClrNM2.dll'
}
 
# -- - -
}
```

#### <a name="module-contents"></a>模組內容

```powershell

PS C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions> dir -Recurse
 
    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions
 
Mode                LastWriteTime         Length Name                                                                                
----                -------------         ------ ----                                                                                
d-----         7/5/2016   1:37 PM                clr                                                                                 
d-----         7/5/2016   1:36 PM                coreclr                                                                             
-a----         7/5/2016   1:34 PM           4906 ModuleWithEditions.psd1                                                             
 
    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\clr
 
Mode                LastWriteTime         Length Name                                                                                
----                -------------         ------ ----                                                                                
-a----         7/5/2016   1:35 PM              0 MyFullClrNM1.dll                                                                    
-a----         7/5/2016   1:35 PM              0 MyFullClrNM2.dll                                                                    
-a----         7/5/2016   1:35 PM              0 MyFullClrRM.dl                                                                      
 
    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\coreclr
 
Mode                LastWriteTime         Length Name                                                                                
----                -------------         ------ ----                                                                                
-a----         7/5/2016   1:35 PM              0 MyCoreClrNM1.dll                                                                    
-a----         7/5/2016   1:35 PM              0 MyCoreClrNM2.dll                                                                    
-a----         7/5/2016   1:35 PM              0 MyCoreClrRM.dl                                                                      
```

## <a name="powershell-gallery-users-can-find-the-list-of-modules-supported-on-a-specific-powershell-edition-using-tags-pseditiondesktop-and-pseditioncore"></a>PowerShell 資源庫使用者可以使用 PSEdition_Desktop 和 PSEdition_Core 標記，尋找特定 PowerShell 版本支援的模組清單。
模組若不具 PSEdition_Desktop 和 PSEdition_Core 標籤 ，則會視為在 PowerShell Desktop 上正常運作。

```powershell

# Find modules supported on PowerShell Desktop edition
Find-Module -Tag PSEditon_Desktop

# Find modules supported on PowerShell Core editions
Find-Module -Tag PSEditon_Core

```


## <a name="more-details"></a>更多詳細資料
### <a name="scripts-with-pseditionsscriptscriptwithpseditionsupportmd"></a>[搭配 PSEditions 的指令碼](../script/scriptwithpseditionsupport.md)
### <a name="pseditions-support-on-powershellgallerypsgallerypsgallerypseditionsmd"></a>[PowerShellGallery 的 PSEditions 支援](../../psgallery/psgallery_pseditions.md)
### <a name="update-module-manifest-psgetupdate-modulemanifestmd"></a>[更新模組資訊清單] (./psget_update-modulemanifest.md)

