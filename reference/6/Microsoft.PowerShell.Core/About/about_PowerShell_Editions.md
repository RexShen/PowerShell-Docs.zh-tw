---
description: 不同的 PowerShell 版本會在不同的基礎執行時間上執行。
Locale: en-US
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_editions?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PowerShell_Editions
ms.openlocfilehash: 4649c1b47a69423eb2f11a119583f441191882dd
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206975"
---
# <a name="about-powershell-editions"></a><span data-ttu-id="761ea-103">關於 PowerShell 版本</span><span class="sxs-lookup"><span data-stu-id="761ea-103">About PowerShell Editions</span></span>

## <a name="short-description"></a><span data-ttu-id="761ea-104">簡短描述</span><span class="sxs-lookup"><span data-stu-id="761ea-104">Short Description</span></span>
<span data-ttu-id="761ea-105">不同的 PowerShell 版本會在不同的基礎執行時間上執行。</span><span class="sxs-lookup"><span data-stu-id="761ea-105">Different editions of PowerShell run on different underlying runtimes.</span></span>

## <a name="long-description"></a><span data-ttu-id="761ea-106">完整描述</span><span class="sxs-lookup"><span data-stu-id="761ea-106">Long Description</span></span>

<span data-ttu-id="761ea-107">從 PowerShell 5.1 開始，有多個 PowerShell _版本_ 可在不同的 .net 執行時間上執行。</span><span class="sxs-lookup"><span data-stu-id="761ea-107">From PowerShell 5.1, there are multiple _editions_ of PowerShell that each run on a different .NET runtime.</span></span> <span data-ttu-id="761ea-108">從 PowerShell 6.2 版來的 PowerShell 有兩種版本：</span><span class="sxs-lookup"><span data-stu-id="761ea-108">As of PowerShell 6.2 there are two editions of PowerShell:</span></span>

- <span data-ttu-id="761ea-109">在 .NET Framework 上執行的 **桌面** 。</span><span class="sxs-lookup"><span data-stu-id="761ea-109">**Desktop** , which runs on .NET Framework.</span></span> <span data-ttu-id="761ea-110">PowerShell 4 和以下版本，以及 Windows 桌面、Windows Server、Windows Server Core 和大部分其他 Windows 作業系統等完整功能的 Windows 版本上的 PowerShell 5.1 都是 Desktop edition。</span><span class="sxs-lookup"><span data-stu-id="761ea-110">PowerShell 4 and below, as well as PowerShell 5.1 on full-featured Windows editions like Windows Desktop, Windows Server, Windows Server Core and most other Windows operating systems are Desktop edition.</span></span> <span data-ttu-id="761ea-111">這是原始的 PowerShell 版本。</span><span class="sxs-lookup"><span data-stu-id="761ea-111">This is the original PowerShell edition.</span></span>
- <span data-ttu-id="761ea-112">**Core** ，可在 .net Core 上執行。</span><span class="sxs-lookup"><span data-stu-id="761ea-112">**Core** , which runs on .NET Core.</span></span> <span data-ttu-id="761ea-113">PowerShell 6.0 （含）以上版本，以及 PowerShell 5.1，在某些降低使用量的 Windows 版本（例如 Windows Nano Server 和 Windows IoT）上無法使用 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="761ea-113">PowerShell 6.0 and above, as well as PowerShell 5.1 on some reduced-footprint Windows editions such as Windows Nano Server and Windows IoT where .NET Framework is unavailable.</span></span>

<span data-ttu-id="761ea-114">因為 PowerShell 的版本對應至其 .NET 執行時間，所以它是 .NET API 和 PowerShell 模組相容性的主要指標。某些 .NET Api、類型或方法在 .NET 執行時間中無法使用，而這會影響依賴它們的 PowerShell 腳本和模組。</span><span class="sxs-lookup"><span data-stu-id="761ea-114">Because the edition of PowerShell corresponds to its .NET runtime, it is the primary indicator of .NET API and PowerShell module compatibility; some .NET APIs, types or methods are not available in both .NET runtimes and this affects PowerShell scripts and modules that depend on them.</span></span>

## <a name="the-psedition-automatic-variable"></a><span data-ttu-id="761ea-115">`$PSEdition`自動變數</span><span class="sxs-lookup"><span data-stu-id="761ea-115">The `$PSEdition` automatic variable</span></span>

<span data-ttu-id="761ea-116">在 PowerShell 5.1 和更新版本中，您可以使用自動變數找出您正在 `$PSEdition` 執行的版本：</span><span class="sxs-lookup"><span data-stu-id="761ea-116">In PowerShell 5.1 and above, you can find out what edition you are running with the `$PSEdition` automatic variable:</span></span>

```powershell
$PSEdition
```

```Output
Core
```

<span data-ttu-id="761ea-117">在 PowerShell 4 和以下的中，此變數不存在。</span><span class="sxs-lookup"><span data-stu-id="761ea-117">In PowerShell 4 and below, this variable does not exist.</span></span> <span data-ttu-id="761ea-118">`$PSEdition` null 應該視為具有值的相同值 `Desktop` 。</span><span class="sxs-lookup"><span data-stu-id="761ea-118">`$PSEdition` being null should be treated as the same as having the value `Desktop`.</span></span>

### <a name="edition-in-psversiontable"></a><span data-ttu-id="761ea-119">版 `$PSVersionTable`</span><span class="sxs-lookup"><span data-stu-id="761ea-119">Edition in `$PSVersionTable`</span></span>

<span data-ttu-id="761ea-120">`$PSVersionTable`自動變數在 PowerShell 5.1 和更新版本中也有版本資訊：</span><span class="sxs-lookup"><span data-stu-id="761ea-120">The `$PSVersionTable` automatic variable also has edition information in PowerShell 5.1 and above:</span></span>

```powershell
$PSVersionTable
```

```Output
Name                           Value
----                           -----
PSVersion                      6.2.0-rc.1
PSEdition                      Core           # <-- Edition information
GitCommitId                    6.2.0-rc.1
OS                             Microsoft Windows 10.0.18865
Platform                       Win32NT
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
WSManStackVersion              3.0
```

<span data-ttu-id="761ea-121">`PSEdition`欄位將具有與自動變數相同的值 `$PSEdition` 。</span><span class="sxs-lookup"><span data-stu-id="761ea-121">The `PSEdition` field will have the same value as the `$PSEdition` automatic variable.</span></span>

## <a name="the-compatiblepseditions-module-manifest-field"></a><span data-ttu-id="761ea-122">`CompatiblePSEditions`模組資訊清單欄位</span><span class="sxs-lookup"><span data-stu-id="761ea-122">The `CompatiblePSEditions` module manifest field</span></span>

<span data-ttu-id="761ea-123">PowerShell 模組可以使用模組資訊清單的欄位，宣告與它們相容的 PowerShell 版本 `CompatiblePSEditions` 。</span><span class="sxs-lookup"><span data-stu-id="761ea-123">PowerShell modules can declare what editions of PowerShell they are compatible with using the `CompatiblePSEditions` field of the module manifest.</span></span>

<span data-ttu-id="761ea-124">例如，宣告與 `Desktop` 和 PowerShell 版本相容的模組資訊清單 `Core` ：</span><span class="sxs-lookup"><span data-stu-id="761ea-124">For example, a module manifest declaring compatibility with both `Desktop` and `Core` editions of PowerShell:</span></span>

```powershell
@{
    ModuleVersion = '1.0'
    FunctionsToExport = @('Test-MyModule')
    CompatiblePSEditions = @('Desktop', 'Core')
}
```

<span data-ttu-id="761ea-125">只有相容性的模組資訊清單範例 `Desktop` ：</span><span class="sxs-lookup"><span data-stu-id="761ea-125">An example of a module manifest with only `Desktop` compatibility:</span></span>

```powershell
@{
    ModuleVersion = '1.0'
    FunctionsToExport = @('Test-MyModule')
    CompatiblePSEditions = @('Desktop')
}
```

<span data-ttu-id="761ea-126">略 `CompatiblePSEditions` 過模組資訊清單中的欄位將會有與將它設定為相同的效果 `Desktop` ，因為引進這個欄位之前建立的模組是針對此版本隱含撰寫的。</span><span class="sxs-lookup"><span data-stu-id="761ea-126">Omitting the `CompatiblePSEditions` field from a module manifest will have the same effect as setting it to `Desktop`, since modules created before this field was introduced were implicitly written for this edition.</span></span>

<span data-ttu-id="761ea-127">針對未隨附于 Windows 的模組 (例如您從資源庫) 撰寫或安裝的模組，此欄位僅供參考。PowerShell 不會根據欄位變更行為 `CompatiblePSEditions` ，但會對 `PSModuleInfo` 您自己的邏輯) 所傳回的物件 (公開它 `Get-Module` ：</span><span class="sxs-lookup"><span data-stu-id="761ea-127">For modules not shipped as part of Windows (i.e. modules you write or install from the gallery), this field is informational only; PowerShell does not change behavior based on the `CompatiblePSEditions` field, but does expose it on the `PSModuleInfo` object (returned by `Get-Module`) for your own logic:</span></span>

```powershell
New-ModuleManifest -Path .\TestModuleWithEdition.psd1 -CompatiblePSEditions Desktop,Core -PowerShellVersion '5.1'
$ModuleInfo = Test-ModuleManifest -Path .\TestModuleWithEdition.psd1
$ModuleInfo.CompatiblePSEditions
```

```Output
Desktop
Core
```

> [!NOTE]
> <span data-ttu-id="761ea-128">`CompatiblePSEditions`模組欄位只與 PowerShell 5.1 和更新版本相容。</span><span class="sxs-lookup"><span data-stu-id="761ea-128">The `CompatiblePSEditions` module field is only compatible with PowerShell 5.1 and above.</span></span> <span data-ttu-id="761ea-129">包含此欄位將會導致模組與 PowerShell 4 和以下模組不相容。</span><span class="sxs-lookup"><span data-stu-id="761ea-129">Including this field will cause a module to be incompatible with PowerShell 4 and below.</span></span> <span data-ttu-id="761ea-130">因為欄位純粹是資訊，所以可以在稍後的 PowerShell 版本中安全地省略。</span><span class="sxs-lookup"><span data-stu-id="761ea-130">Since the field is purely informational, it can be safely omitted in later PowerShell versions.</span></span>

<span data-ttu-id="761ea-131">在 PowerShell 6.1 中， `Get-Module -ListAvailable` 已更新其格式器以顯示每個模組的版本相容性：</span><span class="sxs-lookup"><span data-stu-id="761ea-131">In PowerShell 6.1, `Get-Module -ListAvailable` has had its formatter updated to display the edition-compatibility of each module:</span></span>

```PowerShell
Get-Module -ListAvailable
```

```Output

    Directory: C:\Users\me\Documents\PowerShell\Modules

ModuleType Version    Name                   PSEdition ExportedCommands
---------- -------    ----                   --------- ----------------
Script     1.4.0      Az                     Core,Desk
Script     1.3.1      Az.Accounts            Core,Desk {Disable-AzDataCollection, Disable-AzContextAutosave, E...
Script     1.0.1      Az.Aks                 Core,Desk {Get-AzAks, New-AzAks, Remove-AzAks, Import-AzAksCreden...

...

Script     4.4.0      Pester                 Desk      {Describe, Context, It, Should...}
Script     1.18.0     PSScriptAnalyzer       Desk      {Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer, Invoke-...
Script     1.0.0      WindowsCompatibility   Core      {Initialize-WinSession, Add-WinFunction, Invoke-WinComm...

```

## <a name="edition-compatibility-for-modules-that-ship-as-part-of-windows"></a><span data-ttu-id="761ea-132">版本相容于 Windows 隨附的模組</span><span class="sxs-lookup"><span data-stu-id="761ea-132">Edition-compatibility for modules that ship as part of Windows</span></span>

<span data-ttu-id="761ea-133">如果模組是 Windows (的一部分，或安裝為角色或功能) 的一部分，則 PowerShell 6.1 和更新版本會 `CompatiblePSEditions` 以不同方式來處理欄位。</span><span class="sxs-lookup"><span data-stu-id="761ea-133">For modules that come as part of Windows (or are installed as part of a role or feature), PowerShell 6.1 and above treat the `CompatiblePSEditions` field differently.</span></span> <span data-ttu-id="761ea-134">這類別模組可在 Windows PowerShell 系統模組目錄 () 中找到 `%windir%\System\WindowsPowerShell\v1.0\Modules` 。</span><span class="sxs-lookup"><span data-stu-id="761ea-134">Such modules are found in the Windows PowerShell system modules directory (`%windir%\System\WindowsPowerShell\v1.0\Modules`).</span></span>

<span data-ttu-id="761ea-135">針對從這個目錄載入或找到的模組，PowerShell 6.1 和 `CompatiblePSEditions` 更新版本會使用欄位來判斷模組是否與目前的會話相容，並據以運作。</span><span class="sxs-lookup"><span data-stu-id="761ea-135">For modules loaded from or found in this directory, PowerShell 6.1 and above uses the `CompatiblePSEditions` field to determine whether the module will be compatible with the current session and behaves accordingly.</span></span>

<span data-ttu-id="761ea-136">`Import-Module`使用時，不會匯入不含 in 的模組， `Core` `CompatiblePSEditions` 而且會顯示錯誤：</span><span class="sxs-lookup"><span data-stu-id="761ea-136">When `Import-Module` is used, a module without `Core` in `CompatiblePSEditions` will not be imported and an error will be displayed:</span></span>

```powershell
Import-Module BitsTransfer
```

```Output
Import-Module : Module 'C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\BitsT
ransfer\BitsTransfer.psd1' does not support current PowerShell edition 'Core'.
Its supported editions are 'Desktop'. Use 'Import-Module -SkipEditionCheck' to i
gnore the compatibility of this module.
At line:1 char:1
+ Import-Module BitsTransfer
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : ResourceUnavailable: (C:\WINDOWS\system32\u2026r\BitsT
ransfer.psd1:String) [Import-Module], InvalidOperationException
+ FullyQualifiedErrorId : Modules_PSEditionNotSupported,Microsoft.PowerShell.Com
mands.ImportModuleCommand
```

<span data-ttu-id="761ea-137">`Get-Module -ListAvailable`使用時，不會顯示不含 `Core` in 的模組 `CompatiblePSEditions` ：</span><span class="sxs-lookup"><span data-stu-id="761ea-137">When `Get-Module -ListAvailable` is used, modules without `Core` in `CompatiblePSEditions` will not be displayed:</span></span>

```powershell
Get-Module -ListAvailable BitsTransfer
```

```Output
# No output
```

<span data-ttu-id="761ea-138">在這兩種情況下， `-SkipEditionCheck` switch 參數都可以用來覆寫此行為：</span><span class="sxs-lookup"><span data-stu-id="761ea-138">In both cases, the `-SkipEditionCheck` switch parameter can be used to override this behavior:</span></span>

```powershell
Get-Module -ListAvailable -SkipEditionCheck BitsTransfer
```

```Output
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name             PSEdition ExportedCommands
---------- -------    ----             --------- ----------------
Manifest   2.0.0.0    BitsTransfer     Desk      {Add-BitsFile, Complete-BitsTransfer, Get-BitsTransfer,...
```

> [!WARNING]
> <span data-ttu-id="761ea-139">`Import-Module -SkipEditionCheck` 模組的外觀可能會成功，但使用該模組會在稍後遇到不相容的風險。載入模組一開始會成功，稍後命令可能會呼叫不相容的 API，並自發地失敗。</span><span class="sxs-lookup"><span data-stu-id="761ea-139">`Import-Module -SkipEditionCheck` may appear to succeed for a module, but using that module runs the risk of encountering an incompatibility later on; while loading the module initially succeeds, a command may later call an incompatible API and fail spontaneously.</span></span>

## <a name="authoring-powershell-modules-for-edition-cross-compatibility"></a><span data-ttu-id="761ea-140">撰寫適用于版本的 PowerShell 模組跨相容性</span><span class="sxs-lookup"><span data-stu-id="761ea-140">Authoring PowerShell modules for edition cross-compatibility</span></span>

<span data-ttu-id="761ea-141">撰寫 PowerShell 模組以將 PowerShell 模組設為目標時 `Desktop` `Core` ，您可以進行一些動作，以確保跨版本的相容性。</span><span class="sxs-lookup"><span data-stu-id="761ea-141">When writing a PowerShell module to target both `Desktop` and `Core` editions of PowerShell, there are things you can do to ensure cross-edition compatibility.</span></span>

<span data-ttu-id="761ea-142">唯一確認並持續驗證相容性的唯一方法，就是為您的腳本或模組撰寫測試，並在您需要相容性的所有 PowerShell 版本和版本上執行測試。</span><span class="sxs-lookup"><span data-stu-id="761ea-142">The only true way to confirm and continually validate compatibility however is to write tests for your script or module and run them on all versions and editions of PowerShell you need compatibility with.</span></span> <span data-ttu-id="761ea-143">建議的測試架構為 [Pester][]。</span><span class="sxs-lookup"><span data-stu-id="761ea-143">A recommended testing framework for this is [Pester][].</span></span>

### <a name="powershell-script"></a><span data-ttu-id="761ea-144">PowerShell 指令碼</span><span class="sxs-lookup"><span data-stu-id="761ea-144">PowerShell script</span></span>

<span data-ttu-id="761ea-145">PowerShell 是一種語言，在各版本之間的運作方式相同;它是您所使用且受版本相容性影響的 Cmdlet、模組和 .NET Api。</span><span class="sxs-lookup"><span data-stu-id="761ea-145">As a language, PowerShell works the same between editions; it is the cmdlets, modules and .NET APIs you use that are affected by edition compatibility.</span></span>

<span data-ttu-id="761ea-146">一般而言，在 PowerShell 6.1 和更新版本中運作的腳本將會與 Windows PowerShell 5.1 搭配運作，但有一些例外狀況。</span><span class="sxs-lookup"><span data-stu-id="761ea-146">Generally, scripts that work in PowerShell 6.1 and above will work with Windows PowerShell 5.1, but there are some exceptions.</span></span>

<span data-ttu-id="761ea-147">Version 1.18.0 [PSScriptAnalyzer][] 模組的規則如 [PSUseCompatibleCommands][] 和 [PSUseCompatibleTypes][] ，可以偵測 PowerShell 腳本中可能不相容的命令和 .net api 使用方式。</span><span class="sxs-lookup"><span data-stu-id="761ea-147">Version 1.18.0 [PSScriptAnalyzer][] module has rules like [PSUseCompatibleCommands][] and [PSUseCompatibleTypes][] that are able to detect possibly incompatible usage of commands and .NET APIs in PowerShell scripts.</span></span>

### <a name="net-assemblies"></a><span data-ttu-id="761ea-148">.NET 組件</span><span class="sxs-lookup"><span data-stu-id="761ea-148">.NET assemblies</span></span>

<span data-ttu-id="761ea-149">如果您要撰寫的二進位模組或模組包含 .NET 元件 (Dll) 從原始程式碼產生，您應該針對 .NET 和 PowerShell API 相容性的編譯時間相容性驗證，以 [.NET Standard][] 和 [powershell 標準][] 進行編譯。</span><span class="sxs-lookup"><span data-stu-id="761ea-149">If you are writing a binary module or a module that incorporates .NET assemblies (DLLs) generated from source code, you should compile against [.NET Standard][] and [PowerShell Standard][] for compile-time compatibility validation of .NET and PowerShell API compatibility.</span></span>

<span data-ttu-id="761ea-150">雖然這些程式庫可以在編譯時期檢查某些相容性，但是它們無法攔截版本之間可能的行為差異。</span><span class="sxs-lookup"><span data-stu-id="761ea-150">Although these libraries are able to check some compatibility at compile time, they won't be able to catch possible behavioral differences between editions.</span></span>
<span data-ttu-id="761ea-151">針對這一點，您仍然必須撰寫測試。</span><span class="sxs-lookup"><span data-stu-id="761ea-151">For this you must still write tests.</span></span>

## <a name="see-also"></a><span data-ttu-id="761ea-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="761ea-152">See also</span></span>

- [<span data-ttu-id="761ea-153">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="761ea-153">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)
- [<span data-ttu-id="761ea-154">Import-Module</span><span class="sxs-lookup"><span data-stu-id="761ea-154">Import-Module</span></span>](xref:Microsoft.PowerShell.Core.Import-Module)
- [<span data-ttu-id="761ea-155">Get-Module</span><span class="sxs-lookup"><span data-stu-id="761ea-155">Get-Module</span></span>](xref:Microsoft.PowerShell.Core.Get-Module)
- [<span data-ttu-id="761ea-156">具有相容 PowerShell 版本的模組</span><span class="sxs-lookup"><span data-stu-id="761ea-156">Modules with compatible PowerShell Editions</span></span>](/powershell/scripting/gallery/concepts/module-psedition-support)

[Pester]: https://github.com/pester/Pester/wiki/Pester
[PSScriptAnalyzer]: https://github.com/PowerShell/PSScriptAnalyzer
[PSUseCompatibleCommands]: https://github.com/PowerShell/PSScriptAnalyzer/blob/master/RuleDocumentation/UseCompatibleCommands.md
[PSUseCompatibleTypes]: https://github.com/PowerShell/PSScriptAnalyzer/blob/master/RuleDocumentation/UseCompatibleTypes.md
[.NET Standard]: /dotnet/standard/net-standard
[PowerShell Standard]: https://devblogs.microsoft.com/powershell/powershell-standard-library-build-single-module-that-works-across-windows-powershell-and-powershell-core/
