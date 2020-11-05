---
ms.date: 06/10/2020
title: 具有相容 PowerShell 版本的模組
description: 此文章說明 PowerShellGet Cmdlet 如何支援 Desktop 與 Core 版本的 PowerShell 模組。
ms.openlocfilehash: 530101590cf83a1f43cbb9ce32d07a7e0ec79253
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661487"
---
# <a name="modules-with-compatible-powershell-editions"></a>具有相容 PowerShell 版本的模組

PowerShell 自 5.1 版開始，提供代表各種功能集及平台合規性的不同版本。

- **Desktop Edition：** 在 .NET Framework 上建置，適用於 Windows PowerShell 4.0 和之前的版本，以及在 Windows Desktop、Windows Server、Windows Server Core 和其他大部分 Windows 版本上的 Windows PowerShell 5.1。
- **Core Edition：** 在 .NET Core 上建置、適用於 PowerShell Core 6.0 和更新版本，以及在極精簡 Windows 版本 (例如 Windows IoT 和 Windows Nanoserver ) 上的 Windows PowerShell 5.1。

如需 PowerShell 版本的詳細資訊，請參閱 [about_PowerShell_Editions][]。

## <a name="declaring-compatible-editions"></a>宣告相容的版本

模組作者可使用 `CompatiblePSEditions` 模組資訊清單金鑰來宣告其模組符合一或多個 PowerShell 版本的規範。 僅限 PowerShell 5.1 或更新版本支援此金鑰。

> [!NOTE]
> 模組資訊清單一經使用 `CompatiblePSEditions` 金鑰指定，或使用 `$PSEdition` 變數之後，即無法在 PowerShell 第 4 版或更低版本上匯入。

```powershell
New-ModuleManifest -Path .\TestModuleWithEdition.psd1 -CompatiblePSEditions Desktop,Core -PowerShellVersion 5.1
$ModuleInfo = Test-ModuleManifest -Path .\TestModuleWithEdition.psd1
$ModuleInfo.CompatiblePSEditions
```

```Output
Desktop
Core
```

```powershell
$ModuleInfo | Get-Member CompatiblePSEditions
```

```Output
   TypeName: System.Management.Automation.PSModuleInfo

Name                 MemberType Definition
----                 ---------- ----------
CompatiblePSEditions Property   System.Collections.Generic.IEnumerable[string] CompatiblePSEditions {get;}
```

取得可用的模組清單時，您可以依據 PowerShell 版本篩選該清單。

```powershell
Get-Module -ListAvailable -PSEdition Desktop
```

```Output
    Directory: C:\Program Files\WindowsPowerShell\Modules

ModuleType Version    Name                                ExportedCommands
---------- -------    ----                                ----------------
Manifest   1.0        ModuleWithPSEditions
```

```powershell
Get-Module -ListAvailable -PSEdition Core | % CompatiblePSEditions
```

```Output
Desktop
Core
```

PowerShell 從第 6 版開始，當從 `$env:windir\System32\WindowsPowerShell\v1.0\Modules` 匯入模組時，即會使用 `CompatiblePSEditions` 值來判斷模組是否合規。
此行為僅適用於 Windows。 除此案例外，此值只會作為中繼資料使用。

## <a name="finding-compatible-modules"></a>尋找合規的模組

PowerShell 資源庫使用者可使用 **PSEdition_Desktop** 和 **PSEdition_Core** 標籤來尋找特定 PowerShell 版本支援的模組清單。

沒有 **PSEdition_Desktop** 和 **PSEdition_Core** 標籤的模組，在 PowerShell Desktop 上視為正常運作。

```powershell
# Find modules supported on PowerShell Desktop edition
Find-Module -Tag PSEdition_Desktop

# Find modules supported on PowerShell Core editions
Find-Module -Tag PSEdition_Core
```

## <a name="targeting-multiple-editions"></a>以多個版本為目標

模組作者可以發行以其中一個 PowerShell 版本 (電腦版和 Core) 或兩者同時為目標的單一模組。

單一模組在 Desktop 和 Core 版本上都可運作，但模組作者必須在 RootModule 中新增必要的邏輯，或在模組資訊清單中使用 `$PSEdition` 變數。 模組可有兩組以 **CoreCLR** 和 **FullCLR** 為目標的編譯 DLL。 以下是載入適當 DLL 的邏輯封裝選項。

### <a name="option-1-packaging-a-module-for-targeting-multiple-versions-and-multiple-editions-of-powershell"></a>選項 1︰封裝將多個版本的 PowerShell 作為目標的模組

模組資料夾內容

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

`PSScriptAnalyzer.psd1` 檔案的內容

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

以下邏輯會載入必要的組件，視目前版本而定。

`PSScriptAnalyzer.psm1` 檔案的內容：

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
    if ($PSVersionTable.PSVersion -lt [Version]'5.0')
    {
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

### <a name="option-2-use-psedition-variable-in-the-psd1-file-to-load-the-proper-dlls"></a>選項 2：在 PSD1 檔案中使用 $PSEdition 變數，以載入適當的 DLL

在 PS 5.1 或更新版本的模組資訊清單檔案中允許 `$PSEdition` 全域變數。 模組作者可透過使用此變數，指定模組資訊清單檔案中的條件值。 在限制的語言模式或 [資料] 區段中，可參考 `$PSEdition` 變數。

包含 `CompatiblePSEditions` 金鑰的範例模組資訊清單檔案。

```powershell
@{
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
}
```

模組內容

- ModuleWithEditions\ModuleWithEditions.psd1
- ModuleWithEditions\clr\MyFullClrNM1.dll
- ModuleWithEditions\clr\MyFullClrNM2.dll
- ModuleWithEditions\clr\MyFullClrRM.dll
- ModuleWithEditions\coreclr\MyCoreClrNM1.dll
- ModuleWithEditions\coreclr\MyCoreClrNM2.dll
- ModuleWithEditions\coreclr\MyCoreClrRM.dll

## <a name="more-details"></a>其他詳細資訊

[搭配 PSEditions 的指令碼](script-psedition-support.md)

[PowerShellGallery 的 PSEditions 支援](../how-to/finding-packages/searching-by-compatibility.md)

[更新模組資訊清單](/powershell/module/powershellget/update-modulemanifest)

[about_PowerShell_Editions][]

[about_PowerShell_Editions]: /powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_Editions
