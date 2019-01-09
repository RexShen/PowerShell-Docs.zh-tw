---
ms.date: 12/14/2018
keywords: powershell,cmdlet
title: 撰寫可移植的模組
ms.openlocfilehash: 38a93b5b030d58784b91292e2cd060b3a2c19a00
ms.sourcegitcommit: d396d0e4cfe3d279f399c17e7337380a31d373ac
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2018
ms.locfileid: "53747716"
---
# <a name="portable-modules"></a><span data-ttu-id="0a1e4-103">可移植的模組</span><span class="sxs-lookup"><span data-stu-id="0a1e4-103">Portable Modules</span></span>

<span data-ttu-id="0a1e4-104">Windows PowerShell 針對撰寫[.NET Framework][]雖然 PowerShell Core 針對撰寫[.NET Core][]。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-104">Windows PowerShell is written for [.NET Framework][] while PowerShell Core is written for [.NET Core][].</span></span> <span data-ttu-id="0a1e4-105">可移植的模組是在 Windows PowerShell 和 PowerShell Core 中運作的模組。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-105">Portable modules are modules that work in both Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="0a1e4-106">雖然.NET Framework 及.NET Core 為高度相容，有可用的 api 兩者之間的差異。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-106">While .NET Framework and .NET Core are highly compatible, there are differences in the available APIs between the two.</span></span> <span data-ttu-id="0a1e4-107">另外還有 Api 中的差異可在 Windows PowerShell 和 PowerShell Core 中。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-107">There are also differences in the APIs available in Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="0a1e4-108">適用於兩個環境中的模組必須要注意這些差異。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-108">Modules intended to be used in both environments need to be aware of these differences.</span></span>

## <a name="porting-an-existing-module"></a><span data-ttu-id="0a1e4-109">移植現有的模組</span><span class="sxs-lookup"><span data-stu-id="0a1e4-109">Porting an Existing Module</span></span>

### <a name="porting-a-pssnapin"></a><span data-ttu-id="0a1e4-110">移植 PSSnapIn</span><span class="sxs-lookup"><span data-stu-id="0a1e4-110">Porting a PSSnapIn</span></span>

<span data-ttu-id="0a1e4-111">PowerShell Core 並不支援 PowerShell 嵌入式管理單元 (PSSnapIn)。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-111">PowerShell SnapIns (PSSnapIn) aren't supported in PowerShell Core.</span></span> <span data-ttu-id="0a1e4-112">不過，它是 trivial 將 PSSnapIn 轉換成 PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-112">However, it's trivial to convert a PSSnapIn to a PowerShell module.</span></span> <span data-ttu-id="0a1e4-113">一般而言，PSSnapIn 註冊程式碼是單一原始程式檔中的類別衍生自[PSSnapIn][]。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-113">Typically, the PSSnapIn registration code is in a single source file of a class that derives from [PSSnapIn][].</span></span> <span data-ttu-id="0a1e4-114">從組建; 移除這個原始程式檔不再需要。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-114">Remove this source file from the build; it's no longer needed.</span></span>

<span data-ttu-id="0a1e4-115">使用[New-modulemanifest][]來建立新的模組資訊清單，以取代需要 PSSnapIn 註冊程式碼。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-115">Use [New-ModuleManifest][] to create a new module manifest that replaces the need for the PSSnapIn registration code.</span></span> <span data-ttu-id="0a1e4-116">可重複使用的某些值 （例如描述） PSSnapIn 從模組資訊清單內。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-116">Some of the values from the PSSnapIn (such as Description) can be reused within the module manifest.</span></span>

<span data-ttu-id="0a1e4-117">`RootModule`模組資訊清單中的屬性應設為 實作指令程式的組件 (dll) 的名稱。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-117">The `RootModule` property in the module manifest should be set to the name of the assembly (dll) implementing the cmdlets.</span></span>

### <a name="the-net-portability-analyzer-aka-apiport"></a><span data-ttu-id="0a1e4-118">.NET Portability Analyzer (也稱為 APIPort)</span><span class="sxs-lookup"><span data-stu-id="0a1e4-118">The .NET Portability Analyzer (aka APIPort)</span></span>

<span data-ttu-id="0a1e4-119">若要撰寫適用於 Windows PowerShell 使用 PowerShell Core 時，開始使用的連接埠模組[.NET Portability Analyzer][]。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-119">To port modules written for Windows PowerShell to work with PowerShell Core, start with the [.NET Portability Analyzer][].</span></span> <span data-ttu-id="0a1e4-120">針對您編譯的組件，以判斷是否相容於.NET Framework、.NET Core 及其他.NET 執行階段模組中使用的.NET Api 中執行這項工具。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-120">Run this tool against your compiled assembly to determine if the .NET APIs used in the module are compatible with .NET Framework, .NET Core, and other .NET runtimes.</span></span> <span data-ttu-id="0a1e4-121">如果有的話，則工具會提供建議替代的 Api。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-121">The tool suggests alternate APIs if they exist.</span></span> <span data-ttu-id="0a1e4-122">否則，您可能必須加入[執行階段檢查][]並限制不適用於特定的執行階段的功能。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-122">Otherwise, you may need to add [runtime checks][] and restrict capabilities not available in specific runtimes.</span></span>

## <a name="creating-a-new-module"></a><span data-ttu-id="0a1e4-123">建立新的模組</span><span class="sxs-lookup"><span data-stu-id="0a1e4-123">Creating a New Module</span></span>

<span data-ttu-id="0a1e4-124">如果建立新的模組，是使用建議[.NET CLI][]。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-124">If creating a new module, the recommendation is to use the [.NET CLI][].</span></span>

### <a name="installing-the-powershell-standard-module-template"></a><span data-ttu-id="0a1e4-125">安裝 PowerShell 標準模組範本</span><span class="sxs-lookup"><span data-stu-id="0a1e4-125">Installing the PowerShell Standard Module Template</span></span>

<span data-ttu-id="0a1e4-126">.NET CLI 安裝之後，安裝的範本程式庫，以產生簡單的 PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-126">Once the .NET CLI is installed, install a template library to generate a simple PowerShell module.</span></span>
<span data-ttu-id="0a1e4-127">此模組會與 Windows PowerShell、 PowerShell Core、 Windows、 Linux 和 macOS 相容。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-127">The module will be compatible with Windows PowerShell, PowerShell Core, Windows, Linux, and macOS.</span></span>

<span data-ttu-id="0a1e4-128">下列範例示範如何安裝的範本：</span><span class="sxs-lookup"><span data-stu-id="0a1e4-128">The following example shows how to install the template:</span></span>

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

### <a name="creating-a-new-module-project"></a><span data-ttu-id="0a1e4-129">建立新的模組專案</span><span class="sxs-lookup"><span data-stu-id="0a1e4-129">Creating a New Module Project</span></span>

<span data-ttu-id="0a1e4-130">安裝範本之後，您可以建立新的 PowerShell 模組專案，使用該範本。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-130">After the template is installed, you can create a new PowerShell module project using that template.</span></span> <span data-ttu-id="0a1e4-131">在此範例中，範例模組稱為 'myModule'。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-131">In this example, the sample module is called 'myModule'.</span></span>

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

### <a name="building-the-module"></a><span data-ttu-id="0a1e4-132">建置模組</span><span class="sxs-lookup"><span data-stu-id="0a1e4-132">Building the Module</span></span>

<span data-ttu-id="0a1e4-133">使用標準的.NET CLI 命令來建置專案。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-133">Use standard .NET CLI commands to build the project.</span></span>

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

### <a name="testing-the-module"></a><span data-ttu-id="0a1e4-134">測試模組</span><span class="sxs-lookup"><span data-stu-id="0a1e4-134">Testing the Module</span></span>

<span data-ttu-id="0a1e4-135">在建置模組之後, 您可以將它匯入，並執行範例 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-135">After building the module, you can import it and execute the sample cmdlet.</span></span>

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

<span data-ttu-id="0a1e4-136">下列各節詳細說明一些使用此範本的技術。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-136">The following sections describe in detail some of the technologies used by this template.</span></span>

## <a name="net-standard-library"></a><span data-ttu-id="0a1e4-137">.NET 標準程式庫</span><span class="sxs-lookup"><span data-stu-id="0a1e4-137">.NET Standard Library</span></span>

<span data-ttu-id="0a1e4-138">[.NET standard][]是可用於所有.NET 實作的.NET api 正式規格。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-138">[.NET Standard][] is a formal specification of .NET APIs that are available in all .NET implementations.</span></span> <span data-ttu-id="0a1e4-139">Managed 程式碼以.NET Standard 搭配與該版.NET Standard 相容的.NET Framework 和.NET Core 版本為目標。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-139">Managed code targeting .NET Standard works with the .NET Framework and .NET Core versions that are compatible with that version of the .NET Standard.</span></span>

> [!NOTE]
> <span data-ttu-id="0a1e4-140">雖然 API 可能存在於.NET Standard，.NET Core 中的 API 實作可能會擲回`PlatformNotSupportedException`在執行階段，因此若要確認使用 Windows PowerShell 和 PowerShell Core 的相容性最佳做法是對您的模組，這兩種環境中執行測試。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-140">Although an API may exist in .NET Standard, the API implementation in .NET Core may throw a `PlatformNotSupportedException` at runtime, so to verify compatibility with Windows PowerShell and PowerShell Core, the best practice is to run tests for your module within both environments.</span></span>
> <span data-ttu-id="0a1e4-141">如果您的模組是跨平台，也執行 Linux 和 macOS 上測試。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-141">Also run tests on Linux and macOS if your module is intended to be cross-platform.</span></span>

<span data-ttu-id="0a1e4-142">目標.NET Standard，可協助確保，隨著模組的發展，不相容的 Api 不意外取得導入的模組。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-142">Targeting .NET Standard helps ensure that, as the module evolves, incompatible APIs don't accidentally get introduced into the module.</span></span> <span data-ttu-id="0a1e4-143">在編譯時期，而不是執行階段探索到不相容。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-143">Incompatibilities are discovered at compile time instead of runtime.</span></span>

<span data-ttu-id="0a1e4-144">不過，它不需要.NET 標準為目標的模組來使用 Windows PowerShell 和 PowerShell Core，只要您使用相容的 Api。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-144">However, it isn't required to target .NET Standard for a module to work with both Windows PowerShell and PowerShell Core, as long as you use compatible APIs.</span></span> <span data-ttu-id="0a1e4-145">Intermediate Language (IL) 是兩個執行階段之間相容。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-145">The Intermediate Language (IL) is compatible between the two runtimes.</span></span> <span data-ttu-id="0a1e4-146">您可以針對.NET Framework 4.6.1 中，這是與.NET Standard 2.0 相容。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-146">You can target .NET Framework 4.6.1, which is compatible with .NET Standard 2.0.</span></span> <span data-ttu-id="0a1e4-147">如果您不使用外部.NET Standard 2.0 的 Api，然後您的模組搭配 PowerShell Core 6 而不必重新編譯。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-147">If you don't use APIs outside of .NET Standard 2.0, then your module works with PowerShell Core 6 without recompilation.</span></span>

## <a name="powershell-standard-library"></a><span data-ttu-id="0a1e4-148">PowerShell 的標準程式庫</span><span class="sxs-lookup"><span data-stu-id="0a1e4-148">PowerShell Standard Library</span></span>

<span data-ttu-id="0a1e4-149">[PowerShell 標準][]程式庫是所有的 PowerShell 版本大於或等於該標準的版本中提供的 PowerShell Api 正式規格。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-149">The [PowerShell Standard][] library is a formal specification of PowerShell APIs available in all PowerShell versions greater than or equal to the version of that standard.</span></span>

<span data-ttu-id="0a1e4-150">例如， [PowerShell 標準 5.1][]相容於 Windows PowerShell 5.1 和 PowerShell Core 6.0 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-150">For example, [PowerShell Standard 5.1][] is compatible with both Windows PowerShell 5.1 and PowerShell Core 6.0 or newer.</span></span>

<span data-ttu-id="0a1e4-151">我們建議您編譯您使用 PowerShell 的標準程式庫的模組。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-151">We recommend you compile your module using PowerShell Standard Library.</span></span> <span data-ttu-id="0a1e4-152">程式庫可確保 Api 可供使用且在 Windows PowerShell 和 PowerShell Core 6 實作。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-152">The library ensures the APIs are available and implemented in both Windows PowerShell and PowerShell Core 6.</span></span>
<span data-ttu-id="0a1e4-153">PowerShell 標準被要總是轉送相容。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-153">PowerShell Standard is intended to always be forwards-compatible.</span></span> <span data-ttu-id="0a1e4-154">使用標準程式庫 5.1 PowerShell 所建置的模組一律會與未來的 PowerShell 版本相容。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-154">A module built using PowerShell Standard Library 5.1 will always be compatible with future versions of PowerShell.</span></span>

## <a name="module-manifest"></a><span data-ttu-id="0a1e4-155">模組資訊清單</span><span class="sxs-lookup"><span data-stu-id="0a1e4-155">Module Manifest</span></span>

### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a><span data-ttu-id="0a1e4-156">表示使用 Windows PowerShell 和 PowerShell Core 的相容性</span><span class="sxs-lookup"><span data-stu-id="0a1e4-156">Indicating Compatibility With Windows PowerShell and PowerShell Core</span></span>

<span data-ttu-id="0a1e4-157">驗證之後，與 Windows PowerShell 和 PowerShell Core 搭配使用您的模組，模組資訊清單應該明確表示相容性使用[CompatiblePSEditions][]屬性。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-157">After validating that your module works with both Windows PowerShell and PowerShell Core, the module manifest should explicitly indicate compatibility by using the [CompatiblePSEditions][] property.</span></span> <span data-ttu-id="0a1e4-158">值為`Desktop`表示模組會使用 Windows PowerShell 時的值相容`Core`表示模組與 PowerShell Core 相容。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-158">A value of `Desktop` means that the module is compatible with Windows PowerShell, while a value of `Core` means that the module is compatible with PowerShell Core.</span></span> <span data-ttu-id="0a1e4-159">包括`Desktop`和`Core`表示模組是與 Windows PowerShell 和 PowerShell Core 相容。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-159">Including both `Desktop` and `Core` means that the module is compatible with both Windows PowerShell and PowerShell Core.</span></span>

> [!NOTE]
> <span data-ttu-id="0a1e4-160">`Core` 不自動表示模組適用於 Windows、 Linux 和 macOS。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-160">`Core` does not automatically mean that the module is compatible with Windows, Linux, and macOS.</span></span>
> <span data-ttu-id="0a1e4-161">**CompatiblePSEditions** PowerShell v5 中引進了屬性。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-161">The **CompatiblePSEditions** property was introduced in PowerShell v5.</span></span> <span data-ttu-id="0a1e4-162">模組資訊清單使用**CompatiblePSEditions**屬性無法載入 PowerShell v5 之前的版本中。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-162">Module manifests that use the **CompatiblePSEditions** property fail to load in versions prior to PowerShell v5.</span></span>

### <a name="indicating-os-compatibility"></a><span data-ttu-id="0a1e4-163">指出作業系統相容性</span><span class="sxs-lookup"><span data-stu-id="0a1e4-163">Indicating OS Compatibility</span></span>

<span data-ttu-id="0a1e4-164">首先，請驗證您的模組，適用於 Linux 和 macOS 上。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-164">First, validate that your module works on Linux and macOS.</span></span> <span data-ttu-id="0a1e4-165">接下來，指出與這些模組資訊清單中的作業系統相容性。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-165">Next, indicate compatibility with those operating systems in the module manifest.</span></span> <span data-ttu-id="0a1e4-166">這可讓使用者更輕鬆地找到您的模組時發行至其作業系統[PowerShell 資源庫][]。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-166">This makes it easier for users to find your module for their operating system when published to the [PowerShell Gallery][].</span></span>

<span data-ttu-id="0a1e4-167">在模組資訊清單中，`PrivateData`屬性具有`PSData`子屬性。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-167">Within the module manifest, the `PrivateData` property has a `PSData` sub-property.</span></span> <span data-ttu-id="0a1e4-168">選擇性`Tags`屬性`PSData`接受 PowerShell 資源庫中顯示的值陣列。</span><span class="sxs-lookup"><span data-stu-id="0a1e4-168">The optional `Tags` property of `PSData` takes an array of values that show up in PowerShell Gallery.</span></span> <span data-ttu-id="0a1e4-169">「 PowerShell 資源庫支援下列相容性值：</span><span class="sxs-lookup"><span data-stu-id="0a1e4-169">The PowerShell Gallery supports the following compatibility values:</span></span>

| <span data-ttu-id="0a1e4-170">標籤</span><span class="sxs-lookup"><span data-stu-id="0a1e4-170">Tag</span></span>               | <span data-ttu-id="0a1e4-171">描述</span><span class="sxs-lookup"><span data-stu-id="0a1e4-171">Description</span></span>                                |
|-------------------|--------------------------------------------|
| <span data-ttu-id="0a1e4-172">PSEdition_Core</span><span class="sxs-lookup"><span data-stu-id="0a1e4-172">PSEdition_Core</span></span>    | <span data-ttu-id="0a1e4-173">與 PowerShell Core 6 相容</span><span class="sxs-lookup"><span data-stu-id="0a1e4-173">Compatible with PowerShell Core 6</span></span>          |
| <span data-ttu-id="0a1e4-174">PSEdition_Desktop</span><span class="sxs-lookup"><span data-stu-id="0a1e4-174">PSEdition_Desktop</span></span> | <span data-ttu-id="0a1e4-175">使用 Windows PowerShell 相容</span><span class="sxs-lookup"><span data-stu-id="0a1e4-175">Compatible with Windows PowerShell</span></span>         |
| <span data-ttu-id="0a1e4-176">Windows</span><span class="sxs-lookup"><span data-stu-id="0a1e4-176">Windows</span></span>           | <span data-ttu-id="0a1e4-177">與 Windows 相容性</span><span class="sxs-lookup"><span data-stu-id="0a1e4-177">Compatible with Windows</span></span>                    |
| <span data-ttu-id="0a1e4-178">Linux</span><span class="sxs-lookup"><span data-stu-id="0a1e4-178">Linux</span></span>             | <span data-ttu-id="0a1e4-179">與 Linux （沒有特定的散發版本） 相容</span><span class="sxs-lookup"><span data-stu-id="0a1e4-179">Compatible with Linux (no specific distro)</span></span> |
| <span data-ttu-id="0a1e4-180">macOS</span><span class="sxs-lookup"><span data-stu-id="0a1e4-180">macOS</span></span>             | <span data-ttu-id="0a1e4-181">MacOS 與相容性</span><span class="sxs-lookup"><span data-stu-id="0a1e4-181">Compatible with macOS</span></span>                      |

<span data-ttu-id="0a1e4-182">範例：</span><span class="sxs-lookup"><span data-stu-id="0a1e4-182">Example:</span></span>

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

<!-- reference links -->
[.NET Framework]: /dotnet/framework/
[.NET Core]: /dotnet/core/
[PSSnapIn]: /dotnet/api/system.management.automation.pssnapin
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[執行階段檢查]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[runtime checks]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[.NET CLI]: /dotnet/core/tools/?tabs=netcore2x
[.NET Standard]: /dotnet/standard/net-standard
[PowerShell 標準]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard]: https://github.com/PowerShell/PowerShellStandard
[PowerShell 標準 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[PowerShell Standard 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[PowerShell 資源庫]: https://www.powershellgallery.com
[PowerShell Gallery]: https://www.powershellgallery.com
[.NET portability Analyzer]: https://github.com/Microsoft/dotnet-apiport
[.NET Portability Analyzer]: https://github.com/Microsoft/dotnet-apiport
[CompatiblePSEditions]: /powershell/gallery/concepts/module-psedition-support
