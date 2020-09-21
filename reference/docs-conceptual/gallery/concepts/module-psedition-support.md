---
ms.date: 06/10/2020
contributor: manikb
keywords: 資源庫,powershell,cmdlet,psget
title: 具有相容 PowerShell 版本的模組
ms.openlocfilehash: 522493714916e9fd21f67a6e7bc2cfb165041807
ms.sourcegitcommit: 4a283fe5419f47102e6c1de7060880a934842ee9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/10/2020
ms.locfileid: "84671405"
---
# <a name="modules-with-compatible-powershell-editions"></a><span data-ttu-id="71eca-103">具有相容 PowerShell 版本的模組</span><span class="sxs-lookup"><span data-stu-id="71eca-103">Modules with compatible PowerShell Editions</span></span>

<span data-ttu-id="71eca-104">PowerShell 自 5.1 版開始，提供代表各種功能集及平台合規性的不同版本。</span><span class="sxs-lookup"><span data-stu-id="71eca-104">Starting with version 5.1, PowerShell is available in different editions, which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="71eca-105">**Desktop Edition：** 在 .NET Framework 上建置，適用於 Windows PowerShell 4.0 和之前的版本，以及在 Windows Desktop、Windows Server、Windows Server Core 和其他大部分 Windows 版本上的 Windows PowerShell 5.1。</span><span class="sxs-lookup"><span data-stu-id="71eca-105">**Desktop Edition:** Built on .NET Framework, applies to Windows PowerShell v4.0 and below as well as Windows PowerShell 5.1 on Windows Desktop, Windows Server, Windows Server Core and most other Windows editions.</span></span>
- <span data-ttu-id="71eca-106">**Core Edition：** 在 .NET Core 上建置、適用於 PowerShell Core 6.0 和更新版本，以及在極精簡 Windows 版本 (例如 Windows IoT 和 Windows Nanoserver ) 上的 Windows PowerShell 5.1。</span><span class="sxs-lookup"><span data-stu-id="71eca-106">**Core Edition:** Built on .NET Core, applies to PowerShell Core 6.0 and above as well as Windows PowerShell 5.1 on reduced footprint Windows Editions such as Windows IoT and Windows Nanoserver.</span></span>

<span data-ttu-id="71eca-107">如需 PowerShell 版本的詳細資訊，請參閱 [about_PowerShell_Editions][]。</span><span class="sxs-lookup"><span data-stu-id="71eca-107">For more information on PowerShell editions, see [about_PowerShell_Editions][].</span></span>

## <a name="declaring-compatible-editions"></a><span data-ttu-id="71eca-108">宣告相容的版本</span><span class="sxs-lookup"><span data-stu-id="71eca-108">Declaring compatible editions</span></span>

<span data-ttu-id="71eca-109">模組作者可使用 `CompatiblePSEditions` 模組資訊清單金鑰來宣告其模組符合一或多個 PowerShell 版本的規範。</span><span class="sxs-lookup"><span data-stu-id="71eca-109">Module authors can declare their modules to be compatible with one or more PowerShell editions using the `CompatiblePSEditions` module manifest key.</span></span> <span data-ttu-id="71eca-110">僅限 PowerShell 5.1 或更新版本支援此金鑰。</span><span class="sxs-lookup"><span data-stu-id="71eca-110">This key is only supported on PowerShell 5.1 or later.</span></span>

> [!NOTE]
> <span data-ttu-id="71eca-111">模組資訊清單一經使用 `CompatiblePSEditions` 金鑰指定，或使用 `$PSEdition` 變數之後，即無法在 PowerShell 第 4 版或更低版本上匯入。</span><span class="sxs-lookup"><span data-stu-id="71eca-111">Once a module manifest is specified with the `CompatiblePSEditions` key or uses the `$PSEdition` variable, it can not be imported on PowerShell v4 or lower.</span></span>

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

<span data-ttu-id="71eca-112">取得可用的模組清單時，您可以依據 PowerShell 版本篩選該清單。</span><span class="sxs-lookup"><span data-stu-id="71eca-112">When getting a list of available modules, you can filter the list by PowerShell edition.</span></span>

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

<span data-ttu-id="71eca-113">PowerShell 從第 6 版開始，當從 `$env:windir\System32\WindowsPowerShell\v1.0\Modules` 匯入模組時，即會使用 `CompatiblePSEditions` 值來判斷模組是否合規。</span><span class="sxs-lookup"><span data-stu-id="71eca-113">Beginning in PowerShell 6, the `CompatiblePSEditions` value is used to decide if a module is compatible when modules are imported from `$env:windir\System32\WindowsPowerShell\v1.0\Modules`.</span></span>
<span data-ttu-id="71eca-114">此行為僅適用於 Windows。</span><span class="sxs-lookup"><span data-stu-id="71eca-114">This behavior only applies to Windows.</span></span> <span data-ttu-id="71eca-115">除此案例外，此值只會作為中繼資料使用。</span><span class="sxs-lookup"><span data-stu-id="71eca-115">Outside of this scenario, the value is only used as metadata.</span></span>

## <a name="finding-compatible-modules"></a><span data-ttu-id="71eca-116">尋找合規的模組</span><span class="sxs-lookup"><span data-stu-id="71eca-116">Finding compatible modules</span></span>

<span data-ttu-id="71eca-117">PowerShell 資源庫使用者可使用 **PSEdition_Desktop** 和 **PSEdition_Core** 標籤來尋找特定 PowerShell 版本支援的模組清單。</span><span class="sxs-lookup"><span data-stu-id="71eca-117">PowerShell Gallery users can find the list of modules supported on a specific PowerShell Edition using tags **PSEdition_Desktop** and **PSEdition_Core**.</span></span>

<span data-ttu-id="71eca-118">沒有 **PSEdition_Desktop** 和 **PSEdition_Core** 標籤的模組，在 PowerShell Desktop 上視為正常運作。</span><span class="sxs-lookup"><span data-stu-id="71eca-118">Modules without **PSEdition_Desktop** and **PSEdition_Core** tags are considered to work fine on PowerShell Desktop editions.</span></span>

```powershell
# Find modules supported on PowerShell Desktop edition
Find-Module -Tag PSEdition_Desktop

# Find modules supported on PowerShell Core editions
Find-Module -Tag PSEdition_Core
```

## <a name="targeting-multiple-editions"></a><span data-ttu-id="71eca-119">以多個版本為目標</span><span class="sxs-lookup"><span data-stu-id="71eca-119">Targeting multiple editions</span></span>

<span data-ttu-id="71eca-120">模組作者可以發行以其中一個 PowerShell 版本 (電腦版和 Core) 或兩者同時為目標的單一模組。</span><span class="sxs-lookup"><span data-stu-id="71eca-120">Module authors can publish a single module targeting to either or both PowerShell editions (Desktop and Core).</span></span>

<span data-ttu-id="71eca-121">單一模組在 Desktop 和 Core 版本上都可運作，但模組作者必須在 RootModule 中新增必要的邏輯，或在模組資訊清單中使用 `$PSEdition` 變數。</span><span class="sxs-lookup"><span data-stu-id="71eca-121">A single module can work on both Desktop and Core editions, in that module author has to add required logic in either RootModule or in the module manifest using `$PSEdition` variable.</span></span> <span data-ttu-id="71eca-122">模組可有兩組以 **CoreCLR** 和 **FullCLR** 為目標的編譯 DLL。</span><span class="sxs-lookup"><span data-stu-id="71eca-122">Modules can have two sets of compiled DLLs targeting both **CoreCLR** and **FullCLR**.</span></span> <span data-ttu-id="71eca-123">以下是載入適當 DLL 的邏輯封裝選項。</span><span class="sxs-lookup"><span data-stu-id="71eca-123">Here are the packaging options with logic for loading proper DLLs.</span></span>

### <a name="option-1-packaging-a-module-for-targeting-multiple-versions-and-multiple-editions-of-powershell"></a><span data-ttu-id="71eca-124">選項 1︰封裝將多個版本的 PowerShell 作為目標的模組</span><span class="sxs-lookup"><span data-stu-id="71eca-124">Option 1: Packaging a module for targeting multiple versions and multiple editions of PowerShell</span></span>

<span data-ttu-id="71eca-125">模組資料夾內容</span><span class="sxs-lookup"><span data-stu-id="71eca-125">Module folder contents</span></span>

- <span data-ttu-id="71eca-126">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="71eca-126">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="71eca-127">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="71eca-127">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="71eca-128">PSScriptAnalyzer.psd1</span><span class="sxs-lookup"><span data-stu-id="71eca-128">PSScriptAnalyzer.psd1</span></span>
- <span data-ttu-id="71eca-129">PSScriptAnalyzer.psm1</span><span class="sxs-lookup"><span data-stu-id="71eca-129">PSScriptAnalyzer.psm1</span></span>
- <span data-ttu-id="71eca-130">ScriptAnalyzer.format.ps1xml</span><span class="sxs-lookup"><span data-stu-id="71eca-130">ScriptAnalyzer.format.ps1xml</span></span>
- <span data-ttu-id="71eca-131">ScriptAnalyzer.types.ps1xml</span><span class="sxs-lookup"><span data-stu-id="71eca-131">ScriptAnalyzer.types.ps1xml</span></span>
- <span data-ttu-id="71eca-132">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="71eca-132">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="71eca-133">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="71eca-133">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="71eca-134">en-US\about_PSScriptAnalyzer.help.txt</span><span class="sxs-lookup"><span data-stu-id="71eca-134">en-US\about_PSScriptAnalyzer.help.txt</span></span>
- <span data-ttu-id="71eca-135">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span><span class="sxs-lookup"><span data-stu-id="71eca-135">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span></span>
- <span data-ttu-id="71eca-136">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="71eca-136">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="71eca-137">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="71eca-137">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="71eca-138">Settings\CmdletDesign.psd1</span><span class="sxs-lookup"><span data-stu-id="71eca-138">Settings\CmdletDesign.psd1</span></span>
- <span data-ttu-id="71eca-139">Settings\DSC.psd1</span><span class="sxs-lookup"><span data-stu-id="71eca-139">Settings\DSC.psd1</span></span>
- <span data-ttu-id="71eca-140">Settings\ScriptFunctions.psd1</span><span class="sxs-lookup"><span data-stu-id="71eca-140">Settings\ScriptFunctions.psd1</span></span>
- <span data-ttu-id="71eca-141">Settings\ScriptingStyle.psd1</span><span class="sxs-lookup"><span data-stu-id="71eca-141">Settings\ScriptingStyle.psd1</span></span>
- <span data-ttu-id="71eca-142">Settings\ScriptSecurity.psd1</span><span class="sxs-lookup"><span data-stu-id="71eca-142">Settings\ScriptSecurity.psd1</span></span>

<span data-ttu-id="71eca-143">`PSScriptAnalyzer.psd1` 檔案的內容</span><span class="sxs-lookup"><span data-stu-id="71eca-143">Contents of `PSScriptAnalyzer.psd1` file</span></span>

```powershell
@{

# Author of this module
Author = 'Microsoft Corporation'

# Script module or binary module file associated with this manifest.
RootModule = 'PSScriptAnalyzer.psm1'

# Version number of this module.
ModuleVersion = '1.6.1'

# ---
}
```

<span data-ttu-id="71eca-144">以下邏輯會載入必要的組件，視目前版本而定。</span><span class="sxs-lookup"><span data-stu-id="71eca-144">Below logic loads the required assemblies depending on the current edition or version.</span></span>

<span data-ttu-id="71eca-145">`PSScriptAnalyzer.psm1` 檔案的內容：</span><span class="sxs-lookup"><span data-stu-id="71eca-145">Contents of `PSScriptAnalyzer.psm1` file:</span></span>

```powershell
#
# Script module for module 'PSScriptAnalyzer'
#
Set-StrictMode -Version Latest

# Set up some helper variables to make it easier to work with the module
$PSModule = $ExecutionContext.SessionState.Module
$PSModuleRoot = $PSModule.ModuleBase

# Import the appropriate nested binary module based on the current PowerShell version
$binaryModuleRoot = $PSModuleRoot


if (($PSVersionTable.Keys -contains "PSEdition") -and ($PSVersionTable.PSEdition -ne 'Desktop')) {
    $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'coreclr'
}
else
{
    if ($PSVersionTable.PSVersion -lt [Version]'5.0')
    {
        $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'PSv3'
    }
}

$binaryModulePath = Join-Path -Path $binaryModuleRoot -ChildPath 'Microsoft.Windows.PowerShell.ScriptAnalyzer.dll'
$binaryModule = Import-Module -Name $binaryModulePath -PassThru

# When the module is unloaded, remove the nested binary module that was loaded with it
$PSModule.OnRemove = {
    Remove-Module -ModuleInfo $binaryModule
}
```

### <a name="option-2-use-psedition-variable-in-the-psd1-file-to-load-the-proper-dlls"></a><span data-ttu-id="71eca-146">選項 2：在 PSD1 檔案中使用 $PSEdition 變數，以載入適當的 DLL</span><span class="sxs-lookup"><span data-stu-id="71eca-146">Option 2: Use $PSEdition variable in the PSD1 file to load the proper DLLs</span></span>

<span data-ttu-id="71eca-147">在 PS 5.1 或更新版本的模組資訊清單檔案中允許 `$PSEdition` 全域變數。</span><span class="sxs-lookup"><span data-stu-id="71eca-147">In PS 5.1 or newer, `$PSEdition` global variable is allowed in the module manifest file.</span></span> <span data-ttu-id="71eca-148">模組作者可透過使用此變數，指定模組資訊清單檔案中的條件值。</span><span class="sxs-lookup"><span data-stu-id="71eca-148">Using this variable, module author can specify the conditional values in the module manifest file.</span></span> <span data-ttu-id="71eca-149">在限制的語言模式或 [資料] 區段中，可參考 `$PSEdition` 變數。</span><span class="sxs-lookup"><span data-stu-id="71eca-149">`$PSEdition` variable can be referenced in restricted language mode or a Data section.</span></span>

<span data-ttu-id="71eca-150">包含 `CompatiblePSEditions` 金鑰的範例模組資訊清單檔案。</span><span class="sxs-lookup"><span data-stu-id="71eca-150">Sample module manifest file with `CompatiblePSEditions` key.</span></span>

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

<span data-ttu-id="71eca-151">模組內容</span><span class="sxs-lookup"><span data-stu-id="71eca-151">Module contents</span></span>

- <span data-ttu-id="71eca-152">ModuleWithEditions\ModuleWithEditions.psd1</span><span class="sxs-lookup"><span data-stu-id="71eca-152">ModuleWithEditions\ModuleWithEditions.psd1</span></span>
- <span data-ttu-id="71eca-153">ModuleWithEditions\clr\MyFullClrNM1.dll</span><span class="sxs-lookup"><span data-stu-id="71eca-153">ModuleWithEditions\clr\MyFullClrNM1.dll</span></span>
- <span data-ttu-id="71eca-154">ModuleWithEditions\clr\MyFullClrNM2.dll</span><span class="sxs-lookup"><span data-stu-id="71eca-154">ModuleWithEditions\clr\MyFullClrNM2.dll</span></span>
- <span data-ttu-id="71eca-155">ModuleWithEditions\clr\MyFullClrRM.dll</span><span class="sxs-lookup"><span data-stu-id="71eca-155">ModuleWithEditions\clr\MyFullClrRM.dll</span></span>
- <span data-ttu-id="71eca-156">ModuleWithEditions\coreclr\MyCoreClrNM1.dll</span><span class="sxs-lookup"><span data-stu-id="71eca-156">ModuleWithEditions\coreclr\MyCoreClrNM1.dll</span></span>
- <span data-ttu-id="71eca-157">ModuleWithEditions\coreclr\MyCoreClrNM2.dll</span><span class="sxs-lookup"><span data-stu-id="71eca-157">ModuleWithEditions\coreclr\MyCoreClrNM2.dll</span></span>
- <span data-ttu-id="71eca-158">ModuleWithEditions\coreclr\MyCoreClrRM.dll</span><span class="sxs-lookup"><span data-stu-id="71eca-158">ModuleWithEditions\coreclr\MyCoreClrRM.dll</span></span>

## <a name="more-details"></a><span data-ttu-id="71eca-159">其他詳細資訊</span><span class="sxs-lookup"><span data-stu-id="71eca-159">More details</span></span>

[<span data-ttu-id="71eca-160">搭配 PSEditions 的指令碼</span><span class="sxs-lookup"><span data-stu-id="71eca-160">Scripts with PSEditions</span></span>](script-psedition-support.md)

[<span data-ttu-id="71eca-161">PowerShellGallery 的 PSEditions 支援</span><span class="sxs-lookup"><span data-stu-id="71eca-161">PSEditions support on PowerShellGallery</span></span>](../how-to/finding-packages/searching-by-compatibility.md)

[<span data-ttu-id="71eca-162">更新模組資訊清單</span><span class="sxs-lookup"><span data-stu-id="71eca-162">Update module manifest</span></span>](/powershell/module/powershellget/update-modulemanifest)

<span data-ttu-id="71eca-163">[about_PowerShell_Editions][]</span><span class="sxs-lookup"><span data-stu-id="71eca-163">[about_PowerShell_Editions][]</span></span>

[about_PowerShell_Editions]: /powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_Editions
