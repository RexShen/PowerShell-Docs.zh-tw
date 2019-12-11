---
ms.date: 03/28/2019
contributor: manikb
keywords: 資源庫,powershell,cmdlet,psget
title: 具有相容 PowerShell 版本的模組
ms.openlocfilehash: 425588c168a4f864fdc0c52aa53cfd748b80dc98
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "71328499"
---
# <a name="modules-with-compatible-powershell-editions"></a><span data-ttu-id="802e2-103">具有相容 PowerShell 版本的模組</span><span class="sxs-lookup"><span data-stu-id="802e2-103">Modules with compatible PowerShell Editions</span></span>

<span data-ttu-id="802e2-104">從 5.1 版開始，PowerShell 提供代表各種功能集及平台相容性的不同版本。</span><span class="sxs-lookup"><span data-stu-id="802e2-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="802e2-105">**Desktop Edition：** 在 .NET Framework 上建置，適用於 Windows PowerShell 4.0 和之前的版本，以及在 Windows Desktop、Windows Server、Windows Server Core 和其他大部分 Windows 版本上的 Windows PowerShell 5.1。</span><span class="sxs-lookup"><span data-stu-id="802e2-105">**Desktop Edition:** Built on .NET Framework, applies to Windows PowerShell v4.0 and below as well as Windows PowerShell 5.1 on Windows Desktop, Windows Server, Windows Server Core and most other Windows editions.</span></span>
- <span data-ttu-id="802e2-106">**Core Edition：** 在 .NET Core 上建置、適用於 PowerShell Core 6.0 和更新版本，以及在極精簡 Windows 版本 (例如 Windows IoT 和 Windows Nanoserver ) 上的 Windows PowerShell 5.1。</span><span class="sxs-lookup"><span data-stu-id="802e2-106">**Core Edition:** Built on .NET Core, applies to PowerShell Core 6.0 and above as well as Windows PowerShell 5.1 on reduced footprint Windows Editions such as Windows IoT and Windows Nanoserver.</span></span>

<span data-ttu-id="802e2-107">如需 PowerShell 版本的詳細資訊，請參閱 [about_PowerShell_Editions][]。</span><span class="sxs-lookup"><span data-stu-id="802e2-107">For more information on PowerShell editions, see [about_PowerShell_Editions][].</span></span>

## <a name="declaring-compatible-editions"></a><span data-ttu-id="802e2-108">宣告相容的版本</span><span class="sxs-lookup"><span data-stu-id="802e2-108">Declaring compatible editions</span></span>

<span data-ttu-id="802e2-109">模組作者可以使用 CompatiblePSEditions 模組資訊清單金鑰，宣告其模組與一或多個 PowerShell 版本相容。</span><span class="sxs-lookup"><span data-stu-id="802e2-109">Module authors can declare their modules to be compatible with one or more PowerShell editions using the CompatiblePSEditions module manifest key.</span></span> <span data-ttu-id="802e2-110">僅限 PowerShell 5.1 或更新版本支援此金鑰。</span><span class="sxs-lookup"><span data-stu-id="802e2-110">This key is only supported on PowerShell 5.1 or later.</span></span>

> [!NOTE]
> <span data-ttu-id="802e2-111">一旦使用 CompatiblePSEditions 金鑰指定模組資訊清單之後，就無法在 PowerShell 版本 4 和更舊版本上匯入。</span><span class="sxs-lookup"><span data-stu-id="802e2-111">Once a module manifest is specified with the CompatiblePSEditions key, it can not be imported on PowerShell versions 4 and below.</span></span>

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

<span data-ttu-id="802e2-112">取得可用的模組清單時，您可以依據 PowerShell 版本篩選該清單。</span><span class="sxs-lookup"><span data-stu-id="802e2-112">When getting a list of available modules, you can filter the list by PowerShell edition.</span></span>

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

## <a name="targeting-multiple-editions"></a><span data-ttu-id="802e2-113">以多個版本為目標</span><span class="sxs-lookup"><span data-stu-id="802e2-113">Targeting multiple editions</span></span>

<span data-ttu-id="802e2-114">模組作者可以發行以其中一個 PowerShell 版本 (電腦版和 Core) 或兩者同時為目標的單一模組。</span><span class="sxs-lookup"><span data-stu-id="802e2-114">Module authors can publish a single module targeting to either or both PowerShell editions (Desktop and Core).</span></span>

<span data-ttu-id="802e2-115">單一模組可在桌面和核心版本上使用，作者需在該模組的 RootModule 中或使用 $PSEdition 變數的模組資訊清單中，新增必要的邏輯。</span><span class="sxs-lookup"><span data-stu-id="802e2-115">A single module can work on both Desktop and Core editions, in that module author has to add required logic in either RootModule or in the module manifest using $PSEdition variable.</span></span> <span data-ttu-id="802e2-116">模組可以有兩組以 CoreCLR 和 FullCLR 為目標的編譯 DLL。</span><span class="sxs-lookup"><span data-stu-id="802e2-116">Modules can have two sets of compiled DLLs targeting both CoreCLR and FullCLR.</span></span> <span data-ttu-id="802e2-117">以下幾個選項可用來將邏輯封裝至您的模組，以載入適當的 dll。</span><span class="sxs-lookup"><span data-stu-id="802e2-117">Here are the couple of options to package your module with logic for loading proper dlls.</span></span>

### <a name="option-1-packaging-a-module-for-targeting-multiple-versions-and-multiple-editions-of-powershell"></a><span data-ttu-id="802e2-118">選項 1：封裝將多個版本的 PowerShell 作為目標的模組</span><span class="sxs-lookup"><span data-stu-id="802e2-118">Option 1: Packaging a module for targeting multiple versions and multiple editions of PowerShell</span></span>

<span data-ttu-id="802e2-119">模組資料夾內容</span><span class="sxs-lookup"><span data-stu-id="802e2-119">Module folder contents</span></span>

- <span data-ttu-id="802e2-120">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="802e2-120">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="802e2-121">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="802e2-121">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="802e2-122">PSScriptAnalyzer.psd1</span><span class="sxs-lookup"><span data-stu-id="802e2-122">PSScriptAnalyzer.psd1</span></span>
- <span data-ttu-id="802e2-123">PSScriptAnalyzer.psm1</span><span class="sxs-lookup"><span data-stu-id="802e2-123">PSScriptAnalyzer.psm1</span></span>
- <span data-ttu-id="802e2-124">ScriptAnalyzer.format.ps1xml</span><span class="sxs-lookup"><span data-stu-id="802e2-124">ScriptAnalyzer.format.ps1xml</span></span>
- <span data-ttu-id="802e2-125">ScriptAnalyzer.types.ps1xml</span><span class="sxs-lookup"><span data-stu-id="802e2-125">ScriptAnalyzer.types.ps1xml</span></span>
- <span data-ttu-id="802e2-126">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="802e2-126">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="802e2-127">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="802e2-127">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="802e2-128">en-US\about_PSScriptAnalyzer.help.txt</span><span class="sxs-lookup"><span data-stu-id="802e2-128">en-US\about_PSScriptAnalyzer.help.txt</span></span>
- <span data-ttu-id="802e2-129">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span><span class="sxs-lookup"><span data-stu-id="802e2-129">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span></span>
- <span data-ttu-id="802e2-130">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="802e2-130">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="802e2-131">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="802e2-131">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="802e2-132">Settings\CmdletDesign.psd1</span><span class="sxs-lookup"><span data-stu-id="802e2-132">Settings\CmdletDesign.psd1</span></span>
- <span data-ttu-id="802e2-133">Settings\DSC.psd1</span><span class="sxs-lookup"><span data-stu-id="802e2-133">Settings\DSC.psd1</span></span>
- <span data-ttu-id="802e2-134">Settings\ScriptFunctions.psd1</span><span class="sxs-lookup"><span data-stu-id="802e2-134">Settings\ScriptFunctions.psd1</span></span>
- <span data-ttu-id="802e2-135">Settings\ScriptingStyle.psd1</span><span class="sxs-lookup"><span data-stu-id="802e2-135">Settings\ScriptingStyle.psd1</span></span>
- <span data-ttu-id="802e2-136">Settings\ScriptSecurity.psd1</span><span class="sxs-lookup"><span data-stu-id="802e2-136">Settings\ScriptSecurity.psd1</span></span>

<span data-ttu-id="802e2-137">PSScriptAnalyzer.psd1 檔案的內容</span><span class="sxs-lookup"><span data-stu-id="802e2-137">Contents of PSScriptAnalyzer.psd1 file</span></span>

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

<span data-ttu-id="802e2-138">以下邏輯會載入必要的組件，視目前版本而定。</span><span class="sxs-lookup"><span data-stu-id="802e2-138">Below logic loads the required assemblies depending on the current edition or version.</span></span>

<span data-ttu-id="802e2-139">PSScriptAnalyzer.psm1 檔案的內容：</span><span class="sxs-lookup"><span data-stu-id="802e2-139">Contents of PSScriptAnalyzer.psm1 file:</span></span>

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

### <a name="option-2-use-psedition-variable-in-the-psd1-file-to-load-the-proper-dlls-and-nestedrequired-modules"></a><span data-ttu-id="802e2-140">選項 2：在 PSD1 檔案中使用 $PSEdition 變數，以載入適當的 Dll 和巢狀/必要的模組</span><span class="sxs-lookup"><span data-stu-id="802e2-140">Option 2: Use $PSEdition variable in the PSD1 file to load the proper DLLs and Nested/Required modules</span></span>

<span data-ttu-id="802e2-141">PS 5.1 或更新版本的模組資訊清單檔案中允許 $PSEdition 全域變數。</span><span class="sxs-lookup"><span data-stu-id="802e2-141">In PS 5.1 or newer, $PSEdition global variable is allowed in the module manifest file.</span></span> <span data-ttu-id="802e2-142">模組作者可透過使用此變數，指定模組資訊清單檔案中的條件值。</span><span class="sxs-lookup"><span data-stu-id="802e2-142">Using this variable, module author can specify the conditional values in the module manifest file.</span></span> <span data-ttu-id="802e2-143">在限制的語言模式或 [資料] 區段中，可以參考 $PSEdition 變數。</span><span class="sxs-lookup"><span data-stu-id="802e2-143">$PSEdition variable can be referenced in restricted language mode or a Data section.</span></span>

> [!NOTE]
> <span data-ttu-id="802e2-144">一旦使用 CompatiblePSEditions 金鑰指定模組資訊清單，或使用 `$PSEdition` 變數之後，就無法在較低版本的 PowerShell 上匯入它。</span><span class="sxs-lookup"><span data-stu-id="802e2-144">Once a module manifest is specified with the CompatiblePSEditions key or uses `$PSEdition` variable, it can not be imported on lower versions of PowerShell.</span></span>

<span data-ttu-id="802e2-145">使用 CompatiblePSEditions 金鑰的模組資訊清單檔案範例</span><span class="sxs-lookup"><span data-stu-id="802e2-145">Sample module manifest file with CompatiblePSEditions key</span></span>

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

### <a name="module-contents"></a><span data-ttu-id="802e2-146">模組內容</span><span class="sxs-lookup"><span data-stu-id="802e2-146">Module contents</span></span>

```powershell
dir -Recurse
```

```Output
    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions

Mode           LastWriteTime   Length Name
----           -------------   ------ ----
d-----    7/5/2016   1:37 PM          clr
d-----    7/5/2016   1:36 PM          coreclr
-a----    7/5/2016   1:34 PM     4906 ModuleWithEditions.psd1

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\clr

Mode           LastWriteTime    Length Name
----           -------------    ------ ----
-a----    7/5/2016   1:35 PM         0 MyFullClrNM1.dll
-a----    7/5/2016   1:35 PM         0 MyFullClrNM2.dll
-a----    7/5/2016   1:35 PM         0 MyFullClrRM.dl

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\coreclr

Mode           LastWriteTime   Length Name
----           -------------   ------ ----
-a----    7/5/2016   1:35 PM        0 MyCoreClrNM1.dll
-a----    7/5/2016   1:35 PM        0 MyCoreClrNM2.dll
-a----    7/5/2016   1:35 PM        0 MyCoreClrRM.dl
```

<span data-ttu-id="802e2-147">PowerShell 資源庫使用者可以使用 PSEdition_Desktop 和 PSEdition_Core 標記，尋找特定 PowerShell 版本支援的模組清單。</span><span class="sxs-lookup"><span data-stu-id="802e2-147">PowerShell Gallery users can find the list of modules supported on a specific PowerShell Edition using tags PSEdition_Desktop and PSEdition_Core.</span></span>

<span data-ttu-id="802e2-148">模組若不具 PSEdition_Desktop 和 PSEdition_Core 標籤 ，則會視為在 PowerShell Desktop 上正常運作。</span><span class="sxs-lookup"><span data-stu-id="802e2-148">Modules without PSEdition_Desktop and PSEdition_Core tags are considered to work fine on PowerShell Desktop editions.</span></span>

```powershell
# Find modules supported on PowerShell Desktop edition
Find-Module -Tag PSEdition_Desktop

# Find modules supported on PowerShell Core editions
Find-Module -Tag PSEdition_Core
```

## <a name="more-details"></a><span data-ttu-id="802e2-149">更多詳細資料</span><span class="sxs-lookup"><span data-stu-id="802e2-149">More details</span></span>

[<span data-ttu-id="802e2-150">搭配 PSEditions 的指令碼</span><span class="sxs-lookup"><span data-stu-id="802e2-150">Scripts with PSEditions</span></span>](script-psedition-support.md)

[<span data-ttu-id="802e2-151">PowerShellGallery 的 PSEditions 支援</span><span class="sxs-lookup"><span data-stu-id="802e2-151">PSEditions support on PowerShellGallery</span></span>](../how-to/finding-packages/searching-by-compatibility.md)

[<span data-ttu-id="802e2-152">更新模組資訊清單</span><span class="sxs-lookup"><span data-stu-id="802e2-152">Update module manifest</span></span>](/powershell/module/powershellget/update-modulemanifest)

<span data-ttu-id="802e2-153">[about_PowerShell_Editions][]</span><span class="sxs-lookup"><span data-stu-id="802e2-153">[about_PowerShell_Editions][]</span></span>

[about_PowerShell_Editions]: /powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_Editions
