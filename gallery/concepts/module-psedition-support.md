---
ms.date: 06/12/2017
contributor: manikb
keywords: 資源庫,powershell,cmdlet,psget
title: 具有相容 PowerShell 版本的模組
ms.openlocfilehash: fbbfda2f913d54c3e69c0724fea4d977923279c1
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189511"
---
# <a name="modules-with-compatible-powershell-editions"></a><span data-ttu-id="cb753-103">具有相容 PowerShell 版本的模組</span><span class="sxs-lookup"><span data-stu-id="cb753-103">Modules with compatible PowerShell Editions</span></span>

<span data-ttu-id="cb753-104">從 5.1 版開始，PowerShell 提供代表各種功能集及平台相容性的不同版本。</span><span class="sxs-lookup"><span data-stu-id="cb753-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="cb753-105">**Desktop Edition︰** 建置在 .NET Framework 上，與在完整使用量的 Windows 版本 (如 Server Core 和 Windows Desktop) 上執行之 PowerShell 版本的指令碼和模組相容。</span><span class="sxs-lookup"><span data-stu-id="cb753-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="cb753-106">**Core Edition︰** 建置在 .NET Core 上，與在降低使用量的 Windows 版本 (如 Nano Server 和 Windows IoT) 上執行之 PowerShell 版本的指令碼和模組相容。</span><span class="sxs-lookup"><span data-stu-id="cb753-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

## <a name="the-running-edition-of-powershell-is-shown-in-the-psedition-property-of-psversiontable"></a><span data-ttu-id="cb753-107">$PSVersionTable 的 PSEdition 屬性會顯示正在執行的 PowerShell 版本。</span><span class="sxs-lookup"><span data-stu-id="cb753-107">The running edition of PowerShell is shown in the PSEdition property of $PSVersionTable.</span></span>

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

## <a name="module-authors-can-declare-their-modules-to-be-compatible-with-one-or-more-powershell-editions-using-the-compatiblepseditions-module-manifest-key-this-key-is-only-supported-on-powershell-51-or-later"></a><span data-ttu-id="cb753-108">模組作者可以使用 CompatiblePSEditions 模組資訊清單金鑰，宣告其模組與一或多個 PowerShell 版本相容。</span><span class="sxs-lookup"><span data-stu-id="cb753-108">Module authors can declare their modules to be compatible with one or more PowerShell editions using the CompatiblePSEditions module manifest key.</span></span> <span data-ttu-id="cb753-109">僅限 PowerShell 5.1 或更新版本支援此金鑰。</span><span class="sxs-lookup"><span data-stu-id="cb753-109">This key is only supported on PowerShell 5.1 or later.</span></span>

<span data-ttu-id="cb753-110">「請注意」一旦使用 CompatiblePSEditions 金鑰指定模組資訊清單，就無法在較低版本的 PowerShell 上進行匯入。</span><span class="sxs-lookup"><span data-stu-id="cb753-110">*NOTE* Once a module manifest is specified with the CompatiblePSEditions key, it can not be imported on lower versions of PowerShell.</span></span>

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

<span data-ttu-id="cb753-111">取得可用的模組清單時，您可以依據 PowerShell 版本篩選該清單。</span><span class="sxs-lookup"><span data-stu-id="cb753-111">When getting a list of available modules, you can filter the list by PowerShell edition.</span></span>

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

## <a name="module-authors-can-publish-a-single-module-targeting-to-either-or-both-powershell-editions-desktop-and-core"></a><span data-ttu-id="cb753-112">模組作者可以發行以其中一個 PowerShell 版本 (桌面和核心) 或兩者同時為目標的單一模組</span><span class="sxs-lookup"><span data-stu-id="cb753-112">Module authors can publish a single module targeting to either or both PowerShell editions (Desktop and Core)</span></span>

<span data-ttu-id="cb753-113">單一模組可在桌面和核心版本上使用，作者需在該模組的 RootModule 中或使用 $PSEdition 變數的模組資訊清單中，新增必要的邏輯。</span><span class="sxs-lookup"><span data-stu-id="cb753-113">A single module can work on both Desktop and Core editions, in that module author has to add required logic in either RootModule or in the module manifest using $PSEdition variable.</span></span>
<span data-ttu-id="cb753-114">模組可以有兩組以 CoreCLR 和 FullCLR 為目標的編譯 DLL。</span><span class="sxs-lookup"><span data-stu-id="cb753-114">Modules can have two sets of compiled DLLs targeting both CoreCLR and FullCLR.</span></span>
<span data-ttu-id="cb753-115">以下幾個選項可用來將邏輯封裝至您的模組，以載入適當的 dll。</span><span class="sxs-lookup"><span data-stu-id="cb753-115">Here are the couple of options to package your module with logic for loading proper dlls.</span></span>

### <a name="option-1-packaging-a-module-for-targeting-multiple-versions-and-multiple-editions-of-powershell"></a><span data-ttu-id="cb753-116">選項 1︰封裝將多個版本的 PowerShell 作為目標的模組</span><span class="sxs-lookup"><span data-stu-id="cb753-116">Option 1: Packaging a module for targeting multiple versions and multiple editions of PowerShell</span></span>

#### <a name="module-folder-contents"></a><span data-ttu-id="cb753-117">模組資料夾內容</span><span class="sxs-lookup"><span data-stu-id="cb753-117">Module folder contents</span></span>

- <span data-ttu-id="cb753-118">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="cb753-118">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="cb753-119">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="cb753-119">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="cb753-120">PSScriptAnalyzer.psd1</span><span class="sxs-lookup"><span data-stu-id="cb753-120">PSScriptAnalyzer.psd1</span></span>
- <span data-ttu-id="cb753-121">PSScriptAnalyzer.psm1</span><span class="sxs-lookup"><span data-stu-id="cb753-121">PSScriptAnalyzer.psm1</span></span>
- <span data-ttu-id="cb753-122">ScriptAnalyzer.format.ps1xml</span><span class="sxs-lookup"><span data-stu-id="cb753-122">ScriptAnalyzer.format.ps1xml</span></span>
- <span data-ttu-id="cb753-123">ScriptAnalyzer.types.ps1xml</span><span class="sxs-lookup"><span data-stu-id="cb753-123">ScriptAnalyzer.types.ps1xml</span></span>
- <span data-ttu-id="cb753-124">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="cb753-124">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="cb753-125">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="cb753-125">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="cb753-126">en-US\about_PSScriptAnalyzer.help.txt</span><span class="sxs-lookup"><span data-stu-id="cb753-126">en-US\about_PSScriptAnalyzer.help.txt</span></span>
- <span data-ttu-id="cb753-127">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span><span class="sxs-lookup"><span data-stu-id="cb753-127">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span></span>
- <span data-ttu-id="cb753-128">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="cb753-128">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="cb753-129">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="cb753-129">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="cb753-130">Settings\CmdletDesign.psd1</span><span class="sxs-lookup"><span data-stu-id="cb753-130">Settings\CmdletDesign.psd1</span></span>
- <span data-ttu-id="cb753-131">Settings\DSC.psd1</span><span class="sxs-lookup"><span data-stu-id="cb753-131">Settings\DSC.psd1</span></span>
- <span data-ttu-id="cb753-132">Settings\ScriptFunctions.psd1</span><span class="sxs-lookup"><span data-stu-id="cb753-132">Settings\ScriptFunctions.psd1</span></span>
- <span data-ttu-id="cb753-133">Settings\ScriptingStyle.psd1</span><span class="sxs-lookup"><span data-stu-id="cb753-133">Settings\ScriptingStyle.psd1</span></span>
- <span data-ttu-id="cb753-134">Settings\ScriptSecurity.psd1</span><span class="sxs-lookup"><span data-stu-id="cb753-134">Settings\ScriptSecurity.psd1</span></span>

#### <a name="contents-of-psscriptanalyzerpsd1-file"></a><span data-ttu-id="cb753-135">PSScriptAnalyzer.psd1 檔案的內容</span><span class="sxs-lookup"><span data-stu-id="cb753-135">Contents of PSScriptAnalyzer.psd1 file</span></span>

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

#### <a name="contents-of-psscriptanalyzerpsm1-file"></a><span data-ttu-id="cb753-136">PSScriptAnalyzer.psm1 檔案的內容</span><span class="sxs-lookup"><span data-stu-id="cb753-136">Contents of PSScriptAnalyzer.psm1 file</span></span>

<span data-ttu-id="cb753-137">以下邏輯會載入必要的組件，視目前版本而定。</span><span class="sxs-lookup"><span data-stu-id="cb753-137">Below logic loads the required assemblies depending on the current edition or version.</span></span>

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

### <a name="option-2-use-psedition-variable-in-the-psd1-file-to-load-the-proper-dlls-and-nestedrequired-modules"></a><span data-ttu-id="cb753-138">選項 2︰在 PSD1 檔案中使用 $PSEdition 變數，以載入適當的 Dll 和巢狀/必要的模組</span><span class="sxs-lookup"><span data-stu-id="cb753-138">Option 2: Use $PSEdition variable in the PSD1 file to load the proper DLLs and Nested/Required modules</span></span>

<span data-ttu-id="cb753-139">PS 5.1 或更新版本的模組資訊清單檔案中允許 $PSEdition 全域變數。</span><span class="sxs-lookup"><span data-stu-id="cb753-139">In PS 5.1 or newer, $PSEdition global variable is allowed in the module manifest file.</span></span>
<span data-ttu-id="cb753-140">模組作者可透過使用此變數，指定模組資訊清單檔案中的條件值。</span><span class="sxs-lookup"><span data-stu-id="cb753-140">Using this variable, module author can specify the conditional values in the module manifest file.</span></span> <span data-ttu-id="cb753-141">在限制的語言模式或 [資料] 區段中，可以參考 $PSEdition 變數。</span><span class="sxs-lookup"><span data-stu-id="cb753-141">$PSEdition variable can be referenced in restricted language mode or a Data section.</span></span>

<span data-ttu-id="cb753-142">「請注意」一旦使用 CompatiblePSEditions 金鑰指定模組資訊清單，或使用 $PSEdition 變數，就無法在較低版本的 PowerShell 上進行匯入。</span><span class="sxs-lookup"><span data-stu-id="cb753-142">*NOTE* Once a module manifest is specified with the CompatiblePSEditions key or uses $PSEdition variable, it can not be imported on lower versions of PowerShell.</span></span>


#### <a name="sample-module-manifest-file-with-compatiblepseditions-key"></a><span data-ttu-id="cb753-143">使用 CompatiblePSEditions 金鑰的模組資訊清單檔案範例</span><span class="sxs-lookup"><span data-stu-id="cb753-143">Sample module manifest file with CompatiblePSEditions key</span></span>

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

#### <a name="module-contents"></a><span data-ttu-id="cb753-144">模組內容</span><span class="sxs-lookup"><span data-stu-id="cb753-144">Module contents</span></span>

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

## <a name="powershell-gallery-users-can-find-the-list-of-modules-supported-on-a-specific-powershell-edition-using-tags-pseditiondesktop-and-pseditioncore"></a><span data-ttu-id="cb753-145">PowerShell 資源庫使用者可以使用 PSEdition_Desktop 和 PSEdition_Core 標記，尋找特定 PowerShell 版本支援的模組清單。</span><span class="sxs-lookup"><span data-stu-id="cb753-145">PowerShell Gallery users can find the list of modules supported on a specific PowerShell Edition using tags PSEdition_Desktop and PSEdition_Core.</span></span>

<span data-ttu-id="cb753-146">模組若不具 PSEdition_Desktop 和 PSEdition_Core 標籤 ，則會視為在 PowerShell Desktop 上正常運作。</span><span class="sxs-lookup"><span data-stu-id="cb753-146">Modules without PSEdition_Desktop and PSEdition_Core tags are considered to work fine on PowerShell Desktop editions.</span></span>

```powershell

# Find modules supported on PowerShell Desktop edition
Find-Module -Tag PSEdition_Desktop

# Find modules supported on PowerShell Core editions
Find-Module -Tag PSEdition_Core

```


## <a name="more-details"></a><span data-ttu-id="cb753-147">更多詳細資料</span><span class="sxs-lookup"><span data-stu-id="cb753-147">More details</span></span>

- [<span data-ttu-id="cb753-148">搭配 PSEditions 的指令碼</span><span class="sxs-lookup"><span data-stu-id="cb753-148">Scripts with PSEditions</span></span>](script-psedition-support.md)
- [<span data-ttu-id="cb753-149">PowerShellGallery 的 PSEditions 支援</span><span class="sxs-lookup"><span data-stu-id="cb753-149">PSEditions support on PowerShellGallery</span></span>](../how-to/finding-items/searching-by-psedition.md)
- <span data-ttu-id="cb753-150">[更新模組資訊清單] (/powershell/module/powershellget/update-modulemanifest)</span><span class="sxs-lookup"><span data-stu-id="cb753-150">[Update module manifest] (/powershell/module/powershellget/update-modulemanifest)</span></span>