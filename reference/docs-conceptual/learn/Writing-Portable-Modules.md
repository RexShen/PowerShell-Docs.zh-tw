---
ms.date: 01/10/2020
keywords: powershell,cmdlet
title: 撰寫可移植的模組
ms.openlocfilehash: 124e6efadfd07b8c5214a5c0446b1589f7142388
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "76022251"
---
# <a name="portable-modules"></a><span data-ttu-id="9e97e-103">可移植的模組</span><span class="sxs-lookup"><span data-stu-id="9e97e-103">Portable Modules</span></span>

<span data-ttu-id="9e97e-104">Windows PowerShell 是針對 [.NET Framework][] 撰寫的，而 PowerShell Core 則是針對 [.NET Core][] 撰寫的。</span><span class="sxs-lookup"><span data-stu-id="9e97e-104">Windows PowerShell is written for [.NET Framework][] while PowerShell Core is written for [.NET Core][].</span></span> <span data-ttu-id="9e97e-105">可移植的模組是在 Windows PowerShell 和 PowerShell Core 中運作的模組。</span><span class="sxs-lookup"><span data-stu-id="9e97e-105">Portable modules are modules that work in both Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="9e97e-106">雖然 .NET Framework 和 .NET Core 高度相容，但兩者之間提供的 API 還是有所不同。</span><span class="sxs-lookup"><span data-stu-id="9e97e-106">While .NET Framework and .NET Core are highly compatible, there are differences in the available APIs between the two.</span></span> <span data-ttu-id="9e97e-107">Windows PowerShell 和 PowerShell Core 中提供的 API 也有一些差異。</span><span class="sxs-lookup"><span data-stu-id="9e97e-107">There are also differences in the APIs available in Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="9e97e-108">同時適用於兩個環境的模組必須注意這些差異。</span><span class="sxs-lookup"><span data-stu-id="9e97e-108">Modules intended to be used in both environments need to be aware of these differences.</span></span>

## <a name="porting-an-existing-module"></a><span data-ttu-id="9e97e-109">移植現有的模組</span><span class="sxs-lookup"><span data-stu-id="9e97e-109">Porting an Existing Module</span></span>

### <a name="porting-a-pssnapin"></a><span data-ttu-id="9e97e-110">移植 PSSnapIn</span><span class="sxs-lookup"><span data-stu-id="9e97e-110">Porting a PSSnapIn</span></span>

<span data-ttu-id="9e97e-111">PowerShell Core 並不支援 PowerShell [嵌入式管理單元](/powershell/scripting/developer/cmdlet/modules-and-snap-ins)。</span><span class="sxs-lookup"><span data-stu-id="9e97e-111">PowerShell [SnapIns](/powershell/scripting/developer/cmdlet/modules-and-snap-ins) aren't supported in PowerShell Core.</span></span> <span data-ttu-id="9e97e-112">但是也沒有必要將 PSSnapIn 轉換成 PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="9e97e-112">However, it's trivial to convert a PSSnapIn to a PowerShell module.</span></span> <span data-ttu-id="9e97e-113">一般而言，PSSnapIn 註冊程式碼是衍生自 [PSSnapIn][] 之類別的單一來源檔案。</span><span class="sxs-lookup"><span data-stu-id="9e97e-113">Typically, the PSSnapIn registration code is in a single source file of a class that derives from [PSSnapIn][].</span></span>
<span data-ttu-id="9e97e-114">請將此來源檔案從組建中移除，因為已經不再需要。</span><span class="sxs-lookup"><span data-stu-id="9e97e-114">Remove this source file from the build; it's no longer needed.</span></span>

<span data-ttu-id="9e97e-115">使用 [New-ModuleManifest][] 建立新的模組資訊清單，以取代需要 PSSnapIn 註冊程式碼的需求。</span><span class="sxs-lookup"><span data-stu-id="9e97e-115">Use [New-ModuleManifest][] to create a new module manifest that replaces the need for the PSSnapIn registration code.</span></span> <span data-ttu-id="9e97e-116">**PSSnapIn** 的某些值 (例如 [描述]  ) 可在模組資訊清單內重複使用。</span><span class="sxs-lookup"><span data-stu-id="9e97e-116">Some of the values from the **PSSnapIn** (such as **Description**) can be reused within the module manifest.</span></span>

<span data-ttu-id="9e97e-117">模組資訊清單中的 **RootModule** 屬性應設定為實作 Cmdlet 之組件 (dll) 的名稱。</span><span class="sxs-lookup"><span data-stu-id="9e97e-117">The **RootModule** property in the module manifest should be set to the name of the assembly (dll) implementing the cmdlets.</span></span>

### <a name="the-net-portability-analyzer-aka-apiport"></a><span data-ttu-id="9e97e-118">.NET Portability Analyzer (也稱為 APIPort)</span><span class="sxs-lookup"><span data-stu-id="9e97e-118">The .NET Portability Analyzer (aka APIPort)</span></span>

<span data-ttu-id="9e97e-119">若要移植為 Windows PowerShell 撰寫的模組以和 PowerShell Core 搭配運作，請從 [.NET Portability Analyzer][] 開始。</span><span class="sxs-lookup"><span data-stu-id="9e97e-119">To port modules written for Windows PowerShell to work with PowerShell Core, start with the [.NET Portability Analyzer][].</span></span> <span data-ttu-id="9e97e-120">針對您編譯的組件執行此工具，以判斷模組中使用的 .NET API 是否與 .NET Framework、.NET Core 和其他 .NET 執行階段相容。</span><span class="sxs-lookup"><span data-stu-id="9e97e-120">Run this tool against your compiled assembly to determine if the .NET APIs used in the module are compatible with .NET Framework, .NET Core, and other .NET runtimes.</span></span> <span data-ttu-id="9e97e-121">如果它們存在，工具會建議替代的 API。</span><span class="sxs-lookup"><span data-stu-id="9e97e-121">The tool suggests alternate APIs if they exist.</span></span> <span data-ttu-id="9e97e-122">否則，您可能需要新增[執行階段檢查][]，並限制特定執行階段中不適用的功能。</span><span class="sxs-lookup"><span data-stu-id="9e97e-122">Otherwise, you may need to add [runtime checks][] and restrict capabilities not available in specific runtimes.</span></span>

## <a name="creating-a-new-module"></a><span data-ttu-id="9e97e-123">建立新模組</span><span class="sxs-lookup"><span data-stu-id="9e97e-123">Creating a New Module</span></span>

<span data-ttu-id="9e97e-124">如果建立新的模組，建議使用 [.NET CLI][]。</span><span class="sxs-lookup"><span data-stu-id="9e97e-124">If creating a new module, the recommendation is to use the [.NET CLI][].</span></span>

### <a name="installing-the-powershell-standard-module-template"></a><span data-ttu-id="9e97e-125">安裝 PowerShell 標準模組範本</span><span class="sxs-lookup"><span data-stu-id="9e97e-125">Installing the PowerShell Standard Module Template</span></span>

<span data-ttu-id="9e97e-126">安裝 .NET CLI 之後，請安裝範本程式庫以產生簡單的 PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="9e97e-126">Once the .NET CLI is installed, install a template library to generate a simple PowerShell module.</span></span>
<span data-ttu-id="9e97e-127">模組將會與 Windows PowerShell、PowerShell Core、Windows、Linux 和 macOS 相容。</span><span class="sxs-lookup"><span data-stu-id="9e97e-127">The module will be compatible with Windows PowerShell, PowerShell Core, Windows, Linux, and macOS.</span></span>

<span data-ttu-id="9e97e-128">下列範例顯示如何安裝範本：</span><span class="sxs-lookup"><span data-stu-id="9e97e-128">The following example shows how to install the template:</span></span>

```powershell
dotnet new -i Microsoft.PowerShell.Standard.Module.Template
```

```output
  Restoring packages for C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\restore.csproj...
  Installing Microsoft.PowerShell.Standard.Module.Template 0.1.3.
  Generating MSBuild file C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\obj\restore.csproj.nuget.g.props.
  Generating MSBuild file C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\obj\restore.csproj.nuget.g.targets.
  Restore completed in 1.66 sec for C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\restore.csproj.

Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.
  -n, --name          The name for the output being created. If no name is specified, the name of the current directory is used.
  -o, --output        Location to place the generated output.
  -i, --install       Installs a source or a template pack.
  -u, --uninstall     Uninstalls a source or a template pack.
  --nuget-source      Specifies a NuGet source to use during install.
  --type              Filters templates based on available types. Predefined values are "project", "item" or "other".
  --force             Forces content to be generated even if it would change existing files.
  -lang, --language   Filters templates based on language and specifies the language of the template to create.


Templates                                         Short Name         Language          Tags
----------------------------------------------------------------------------------------------------------------------------
Console Application                               console            [C#], F#, VB      Common/Console
Class library                                     classlib           [C#], F#, VB      Common/Library
PowerShell Standard Module                        psmodule           [C#]              Library/PowerShell/Module
...
```

### <a name="creating-a-new-module-project"></a><span data-ttu-id="9e97e-129">建立新模組專案</span><span class="sxs-lookup"><span data-stu-id="9e97e-129">Creating a New Module Project</span></span>

<span data-ttu-id="9e97e-130">安裝範本之後，就可以使用該範本建立新的 PowerShell 模組專案。</span><span class="sxs-lookup"><span data-stu-id="9e97e-130">After the template is installed, you can create a new PowerShell module project using that template.</span></span> <span data-ttu-id="9e97e-131">在此範例中，範例模組稱為 'myModule'。</span><span class="sxs-lookup"><span data-stu-id="9e97e-131">In this example, the sample module is called 'myModule'.</span></span>

```
PS> mkdir myModule

    Directory: C:\Users\Steve

Mode LastWriteTime Length Name
---- ------------- ------ ----
d----- 8/3/2018 2:41 PM myModule

PS> cd myModule
PS C:\Users\Steve\myModule> dotnet new psmodule

The template "PowerShell Standard Module" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\Users\Steve\myModule\myModule.csproj...
  Restoring packages for C:\Users\Steve\myModule\myModule.csproj...
  Installing PowerShellStandard.Library 5.1.0.
  Generating MSBuild file C:\Users\Steve\myModule\obj\myModule.csproj.nuget.g.props.
  Generating MSBuild file C:\Users\Steve\myModule\obj\myModule.csproj.nuget.g.targets.
  Restore completed in 1.76 sec for C:\Users\Steve\myModule\myModule.csproj.

Restore succeeded.
```

### <a name="building-the-module"></a><span data-ttu-id="9e97e-132">建置模組</span><span class="sxs-lookup"><span data-stu-id="9e97e-132">Building the Module</span></span>

<span data-ttu-id="9e97e-133">使用標準 .NET CLI 命令建置專案。</span><span class="sxs-lookup"><span data-stu-id="9e97e-133">Use standard .NET CLI commands to build the project.</span></span>

```powershell
dotnet build
```

```output
PS C:\Users\Steve\myModule> dotnet build
Microsoft (R) Build Engine version 15.7.179.6572 for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 76.85 ms for C:\Users\Steve\myModule\myModule.csproj.
  myModule -> C:\Users\Steve\myModule\bin\Debug\netstandard2.0\myModule.dll

Build succeeded.
    0 Warning(s)
    0 Error(s)

Time Elapsed 00:00:05.40
```

### <a name="testing-the-module"></a><span data-ttu-id="9e97e-134">測試模組</span><span class="sxs-lookup"><span data-stu-id="9e97e-134">Testing the Module</span></span>

<span data-ttu-id="9e97e-135">建置模組之後，可以將它匯入並執行範例 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9e97e-135">After building the module, you can import it and execute the sample cmdlet.</span></span>

```powershell
ipmo .\bin\Debug\netstandard2.0\myModule.dll
Test-SampleCmdlet -?
Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat
```

```output
PS C:\Users\Steve\myModule> ipmo .\bin\Debug\netstandard2.0\myModule.dll
PS C:\Users\Steve\myModule> Test-SampleCmdlet -?

NAME
    Test-SampleCmdlet

SYNTAX
    Test-SampleCmdlet [-FavoriteNumber] <int> [[-FavoritePet] {Cat | Dog | Horse}] [<CommonParameters>]


ALIASES
    None


REMARKS
    None


PS C:\Users\Steve\myModule> Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat

FavoriteNumber FavoritePet
-------------- -----------
             7 Cat
```

<span data-ttu-id="9e97e-136">以下各節詳細說明此範本的一些使用技巧。</span><span class="sxs-lookup"><span data-stu-id="9e97e-136">The following sections describe in detail some of the technologies used by this template.</span></span>

## <a name="net-standard-library"></a><span data-ttu-id="9e97e-137">.NET Standard 程式庫</span><span class="sxs-lookup"><span data-stu-id="9e97e-137">.NET Standard Library</span></span>

<span data-ttu-id="9e97e-138">[.NET Standard][] 是所有 .NET 實作中所提供之 .NET API 的正式規格。</span><span class="sxs-lookup"><span data-stu-id="9e97e-138">[.NET Standard][] is a formal specification of .NET APIs that are available in all .NET implementations.</span></span> <span data-ttu-id="9e97e-139">以 .NET Standard 為目標的受控程式碼可和與該版 .NET Standard 相容的 .NET Framework 和 .NET Core 版本搭配使用。</span><span class="sxs-lookup"><span data-stu-id="9e97e-139">Managed code targeting .NET Standard works with the .NET Framework and .NET Core versions that are compatible with that version of the .NET Standard.</span></span>

> [!NOTE]
> <span data-ttu-id="9e97e-140">雖然 .NET Standard 可能已經有 API 存在，但 .NET Core 中的 API 實作可能會在執行階段擲回 `PlatformNotSupportedException`，因此為了確認與 Windows PowerShell 和 PowerShell Core 的相容性，最好的方法是在兩個環境內針對模組執行測試。</span><span class="sxs-lookup"><span data-stu-id="9e97e-140">Although an API may exist in .NET Standard, the API implementation in .NET Core may throw a `PlatformNotSupportedException` at runtime, so to verify compatibility with Windows PowerShell and PowerShell Core, the best practice is to run tests for your module within both environments.</span></span>
> <span data-ttu-id="9e97e-141">如果模組要跨平台使用，也請在 Linux 和 macOS 中執行測試。</span><span class="sxs-lookup"><span data-stu-id="9e97e-141">Also run tests on Linux and macOS if your module is intended to be cross-platform.</span></span>

<span data-ttu-id="9e97e-142">以 .NET Standard 為目標有助於確保在模組發展過程中，不會突然出現不相容的 API。</span><span class="sxs-lookup"><span data-stu-id="9e97e-142">Targeting .NET Standard helps ensure that, as the module evolves, incompatible APIs don't accidentally get introduced into the module.</span></span> <span data-ttu-id="9e97e-143">因為在編譯時期就能發現不相容項目，而不是等到執行階段才發現。</span><span class="sxs-lookup"><span data-stu-id="9e97e-143">Incompatibilities are discovered at compile time instead of runtime.</span></span>

<span data-ttu-id="9e97e-144">但是只要使用相容的 API，就不需要將要與 Windows PowerShell 和 PowerShell Core 搭配使用的模組以 .NET Standard 為目標。</span><span class="sxs-lookup"><span data-stu-id="9e97e-144">However, it isn't required to target .NET Standard for a module to work with both Windows PowerShell and PowerShell Core, as long as you use compatible APIs.</span></span> <span data-ttu-id="9e97e-145">中繼語言 (IL) 在兩個執行階段之間是相容的。</span><span class="sxs-lookup"><span data-stu-id="9e97e-145">The Intermediate Language (IL) is compatible between the two runtimes.</span></span> <span data-ttu-id="9e97e-146">您能以 .NET Framework 4.6.1 為目標，它與 .NET Standard 2.0 相容。</span><span class="sxs-lookup"><span data-stu-id="9e97e-146">You can target .NET Framework 4.6.1, which is compatible with .NET Standard 2.0.</span></span> <span data-ttu-id="9e97e-147">如果沒有使用 .NET Standard 2.0 之外的 API，您的模組不需要重新編譯，就能與 PowerShell Core 6 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="9e97e-147">If you don't use APIs outside of .NET Standard 2.0, then your module works with PowerShell Core 6 without recompilation.</span></span>

## <a name="powershell-standard-library"></a><span data-ttu-id="9e97e-148">PowerShell Standard 程式庫</span><span class="sxs-lookup"><span data-stu-id="9e97e-148">PowerShell Standard Library</span></span>

<span data-ttu-id="9e97e-149">[PowerShell Standard][] 程式庫是版本大於或等於該標準版本的所有 PowerShell 版本中所提供 PowerShell API 的正式規格。</span><span class="sxs-lookup"><span data-stu-id="9e97e-149">The [PowerShell Standard][] library is a formal specification of PowerShell APIs available in all PowerShell versions greater than or equal to the version of that standard.</span></span>

<span data-ttu-id="9e97e-150">例如，[PowerShell Standard 5.1][] 與 Windows PowerShell 5.1 和 PowerShell Core 6.0 或更新版本相容。</span><span class="sxs-lookup"><span data-stu-id="9e97e-150">For example, [PowerShell Standard 5.1][] is compatible with both Windows PowerShell 5.1 and PowerShell Core 6.0 or newer.</span></span>

<span data-ttu-id="9e97e-151">我們建議您使用 PowerShell Standard 程式庫來編譯您的模組。</span><span class="sxs-lookup"><span data-stu-id="9e97e-151">We recommend you compile your module using PowerShell Standard Library.</span></span> <span data-ttu-id="9e97e-152">此程式庫可確保在 Windows PowerShell 和 PowerShell Core 6 中都已提供並實作 API。</span><span class="sxs-lookup"><span data-stu-id="9e97e-152">The library ensures the APIs are available and implemented in both Windows PowerShell and PowerShell Core 6.</span></span>
<span data-ttu-id="9e97e-153">PowerShell Standard 的設計旨在始終向下相容。</span><span class="sxs-lookup"><span data-stu-id="9e97e-153">PowerShell Standard is intended to always be forwards-compatible.</span></span> <span data-ttu-id="9e97e-154">使用 PowerShell Standard 程式庫 5.1 建置的模組一律會與未來的 PowerShell 版本相容。</span><span class="sxs-lookup"><span data-stu-id="9e97e-154">A module built using PowerShell Standard Library 5.1 will always be compatible with future versions of PowerShell.</span></span>

## <a name="module-manifest"></a><span data-ttu-id="9e97e-155">模組資訊清單</span><span class="sxs-lookup"><span data-stu-id="9e97e-155">Module Manifest</span></span>

### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a><span data-ttu-id="9e97e-156">指示與 Windows PowerShell 和 PowerShell Core 的相容性</span><span class="sxs-lookup"><span data-stu-id="9e97e-156">Indicating Compatibility With Windows PowerShell and PowerShell Core</span></span>

<span data-ttu-id="9e97e-157">驗證模組可與 Windows PowerShell 和 PowerShell Core 搭配使用之後，模組資訊清單應該使用 [CompatiblePSEditions][] 屬性明確指示相容性。</span><span class="sxs-lookup"><span data-stu-id="9e97e-157">After validating that your module works with both Windows PowerShell and PowerShell Core, the module manifest should explicitly indicate compatibility by using the [CompatiblePSEditions][] property.</span></span> <span data-ttu-id="9e97e-158">值為 `Desktop` 表示模組與 Windows PowerShell 相容，值為 `Core` 表示模組與 PowerShell Core 相容。</span><span class="sxs-lookup"><span data-stu-id="9e97e-158">A value of `Desktop` means that the module is compatible with Windows PowerShell, while a value of `Core` means that the module is compatible with PowerShell Core.</span></span> <span data-ttu-id="9e97e-159">同時包含 `Desktop` 與 `Core` 表示模組與 Windows PowerShell 和 PowerShell Core 相容。</span><span class="sxs-lookup"><span data-stu-id="9e97e-159">Including both `Desktop` and `Core` means that the module is compatible with both Windows PowerShell and PowerShell Core.</span></span>

> [!NOTE]
> <span data-ttu-id="9e97e-160">`Core` 不會自動表示模組與 Windows、Linux 和 macOS 相容。</span><span class="sxs-lookup"><span data-stu-id="9e97e-160">`Core` does not automatically mean that the module is compatible with Windows, Linux, and macOS.</span></span>
> <span data-ttu-id="9e97e-161">PowerShell v5 中已經引進 **CompatiblePSEditions** 屬性。</span><span class="sxs-lookup"><span data-stu-id="9e97e-161">The **CompatiblePSEditions** property was introduced in PowerShell v5.</span></span> <span data-ttu-id="9e97e-162">使用 **CompatiblePSEditions** 屬性的模組資訊清單無法載入至 PowerShell v5 之前的版本中。</span><span class="sxs-lookup"><span data-stu-id="9e97e-162">Module manifests that use the **CompatiblePSEditions** property fail to load in versions prior to PowerShell v5.</span></span>

### <a name="indicating-os-compatibility"></a><span data-ttu-id="9e97e-163">指示作業系統相容性</span><span class="sxs-lookup"><span data-stu-id="9e97e-163">Indicating OS Compatibility</span></span>

<span data-ttu-id="9e97e-164">首先，請驗證您的模組可在 Linux 和 macOS 上運作。</span><span class="sxs-lookup"><span data-stu-id="9e97e-164">First, validate that your module works on Linux and macOS.</span></span> <span data-ttu-id="9e97e-165">接下來，在模組資訊清單中指示與那些作業系統相容。</span><span class="sxs-lookup"><span data-stu-id="9e97e-165">Next, indicate compatibility with those operating systems in the module manifest.</span></span> <span data-ttu-id="9e97e-166">這可在將模組發佈至 [PowerShell 資源庫][]時，讓使用者更容易地為他們的作業系統找到您的模組。</span><span class="sxs-lookup"><span data-stu-id="9e97e-166">This makes it easier for users to find your module for their operating system when published to the [PowerShell Gallery][].</span></span>

<span data-ttu-id="9e97e-167">在模組資訊清單內，`PrivateData` 屬性具有 `PSData` 子屬性。</span><span class="sxs-lookup"><span data-stu-id="9e97e-167">Within the module manifest, the `PrivateData` property has a `PSData` sub-property.</span></span> <span data-ttu-id="9e97e-168">`PSData` 的選擇性 `Tags` 屬性接受 PowerShell 資源庫中顯示的值陣列。</span><span class="sxs-lookup"><span data-stu-id="9e97e-168">The optional `Tags` property of `PSData` takes an array of values that show up in PowerShell Gallery.</span></span> <span data-ttu-id="9e97e-169">PowerShell 資源庫支援下列相容性值：</span><span class="sxs-lookup"><span data-stu-id="9e97e-169">The PowerShell Gallery supports the following compatibility values:</span></span>

| <span data-ttu-id="9e97e-170">Tag</span><span class="sxs-lookup"><span data-stu-id="9e97e-170">Tag</span></span>               | <span data-ttu-id="9e97e-171">描述</span><span class="sxs-lookup"><span data-stu-id="9e97e-171">Description</span></span>                                |
|-------------------|--------------------------------------------|
| <span data-ttu-id="9e97e-172">PSEdition_Core</span><span class="sxs-lookup"><span data-stu-id="9e97e-172">PSEdition_Core</span></span>    | <span data-ttu-id="9e97e-173">與 PowerShell Core 6 相容</span><span class="sxs-lookup"><span data-stu-id="9e97e-173">Compatible with PowerShell Core 6</span></span>          |
| <span data-ttu-id="9e97e-174">PSEdition_Desktop</span><span class="sxs-lookup"><span data-stu-id="9e97e-174">PSEdition_Desktop</span></span> | <span data-ttu-id="9e97e-175">與 Windows PowerShell 相容</span><span class="sxs-lookup"><span data-stu-id="9e97e-175">Compatible with Windows PowerShell</span></span>         |
| <span data-ttu-id="9e97e-176">Windows</span><span class="sxs-lookup"><span data-stu-id="9e97e-176">Windows</span></span>           | <span data-ttu-id="9e97e-177">與 Windows 相容</span><span class="sxs-lookup"><span data-stu-id="9e97e-177">Compatible with Windows</span></span>                    |
| <span data-ttu-id="9e97e-178">Linux</span><span class="sxs-lookup"><span data-stu-id="9e97e-178">Linux</span></span>             | <span data-ttu-id="9e97e-179">與 Linux (不限特定散發版本) 相容</span><span class="sxs-lookup"><span data-stu-id="9e97e-179">Compatible with Linux (no specific distro)</span></span> |
| <span data-ttu-id="9e97e-180">macOS</span><span class="sxs-lookup"><span data-stu-id="9e97e-180">macOS</span></span>             | <span data-ttu-id="9e97e-181">與 macOS 相容</span><span class="sxs-lookup"><span data-stu-id="9e97e-181">Compatible with macOS</span></span>                      |

<span data-ttu-id="9e97e-182">範例：</span><span class="sxs-lookup"><span data-stu-id="9e97e-182">Example:</span></span>

```powershell
@{
    GUID = "4ae9fd46-338a-459c-8186-07f910774cb8"
    Author = "Microsoft Corporation"
    CompanyName = "Microsoft Corporation"
    Copyright = "(C) Microsoft Corporation. All rights reserved."
    HelpInfoUri = "https://go.microsoft.com/fwlink/?linkid=855962"
    ModuleVersion = "1.2.4"
    PowerShellVersion = "3.0"
    ClrVersion = "4.0"
    RootModule = "PackageManagement.psm1"
    Description = 'PackageManagement (a.k.a. OneGet) is a new way to discover and install software packages from around the web.
 It is a manager or multiplexer of existing package managers (also called package providers) that unifies Windows package management with a single Windows PowerShell interface. With PackageManagement, you can do the following.
  - Manage a list of software repositories in which packages can be searched, acquired and installed
  - Discover software packages
  - Seamlessly install, uninstall, and inventory packages from one or more software repositories'

    CmdletsToExport = @(
        'Find-Package',
        'Get-Package',
        'Get-PackageProvider',
        'Get-PackageSource',
        'Install-Package',
        'Import-PackageProvider'
        'Find-PackageProvider'
        'Install-PackageProvider'
        'Register-PackageSource',
        'Set-PackageSource',
        'Unregister-PackageSource',
        'Uninstall-Package'
        'Save-Package'
    )

    FormatsToProcess  = @('PackageManagement.format.ps1xml')

    PrivateData = @{
        PSData = @{
            Tags = @('PackageManagement', 'PSEdition_Core', 'PSEdition_Desktop', 'Windows', 'Linux', 'macOS')
            ProjectUri = 'https://oneget.org'
        }
    }
}
```

## <a name="dependency-on-native-libraries"></a><span data-ttu-id="9e97e-183">原生程式庫的相依性</span><span class="sxs-lookup"><span data-stu-id="9e97e-183">Dependency on Native Libraries</span></span>

<span data-ttu-id="9e97e-184">適用於不同作業系統或處理器架構的模組，可能相依於本身依賴某些原生程式庫的受控程式庫。</span><span class="sxs-lookup"><span data-stu-id="9e97e-184">Modules intended for use across different operating systems or processor architectures may depend on a managed library that itself depends on some native libraries.</span></span>

<span data-ttu-id="9e97e-185">在 PowerShell 7 之前，您必須有自訂程式碼，才能載入適當的原生 dll，以便受控程式庫正確地找到它。</span><span class="sxs-lookup"><span data-stu-id="9e97e-185">Prior to PowerShell 7, one would have to have custom code to load the appropriate native dll so that the managed library can find it correctly.</span></span>

<span data-ttu-id="9e97e-186">透過 PowerShell 7，可在受控程式庫的位置 (遵循 [.NET RID 目錄][]標記法的子集) 內的子資料夾中搜尋要載入的原生二進位檔。</span><span class="sxs-lookup"><span data-stu-id="9e97e-186">With PowerShell 7, native binaries to load are searched in sub-folders within the managed library's location following a subset of the [.NET RID Catalog][] notation.</span></span>

```
managed.dll folder
                |
                |--- 'win-x64' folder
                |       |--- native.dll
                |
                |--- 'win-x86' folder
                |       |--- native.dll
                |
                |--- 'win-arm' folder
                |       |--- native.dll
                |
                |--- 'win-arm64' folder
                |       |--- native.dll
                |
                |--- 'linux-x64' folder
                |       |--- native.so
                |
                |--- 'linux-x86' folder
                |       |--- native.so
                |
                |--- 'linux-arm' folder
                |       |--- native.so
                |
                |--- 'linux-arm64' folder
                |       |--- native.so
                |
                |--- 'osx-x64' folder
                |       |--- native.dylib
```

<!-- reference links -->
[.NET Framework]: /dotnet/framework/
[.NET Core]: /dotnet/core/
[PSSnapIn]: /dotnet/api/system.management.automation.pssnapin
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[執行階段檢查]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[runtime checks]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[.NET CLI]: /dotnet/core/tools/?tabs=netcore2x
[.NET Standard]: /dotnet/standard/net-standard
[PowerShell Standard]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[PowerShell 資源庫]: https://www.powershellgallery.com
[PowerShell Gallery]: https://www.powershellgallery.com
[.NET Portability Analyzer]: https://github.com/Microsoft/dotnet-apiport
[CompatiblePSEditions]: /powershell/scripting/gallery/concepts/module-psedition-support
[.NET RID 目錄]: https://docs.microsoft.com/dotnet/core/rid-catalog
[.NET RID Catalog]: https://docs.microsoft.com/dotnet/core/rid-catalog
