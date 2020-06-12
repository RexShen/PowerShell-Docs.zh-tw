---
title: 如何建立標準程式庫的二進位模組
description: PowerShell 標準程式庫可讓我們建立跨平台模組，以便在 PowerShell Core 和 Windows PowerShell 5.1 中使用。
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 51734fd9232e7c33b11c6c5a6abddbcc1f28413c
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149411"
---
# <a name="how-to-create-a-standard-library-binary-module"></a><span data-ttu-id="4021d-103">如何建立標準程式庫的二進位模組</span><span class="sxs-lookup"><span data-stu-id="4021d-103">How to create a Standard Library binary module</span></span>

<span data-ttu-id="4021d-104">我最近已瞭解要實作為二進位模組的模組。</span><span class="sxs-lookup"><span data-stu-id="4021d-104">I recently had an idea for module that I wanted to implement as a binary module.</span></span> <span data-ttu-id="4021d-105">我還得使用 [PowerShell 標準程式庫][]來建立一個模組，因此這會是一個很好的機會。</span><span class="sxs-lookup"><span data-stu-id="4021d-105">I have yet to create one using the [PowerShell Standard Library][] so this felt like a good opportunity.</span></span> <span data-ttu-id="4021d-106">我使用[建立跨平台二進位模組][]指南來建立此模組，不會有任何障礙。</span><span class="sxs-lookup"><span data-stu-id="4021d-106">I used the [Creating a cross-platform binary module][] guide to create this module without any roadblocks.</span></span>
<span data-ttu-id="4021d-107">我們將逐步介紹相同的流程，並在過程中新增一些額外的評論。</span><span class="sxs-lookup"><span data-stu-id="4021d-107">We're going to walk that same process and I'll add a little extra commentary along the way.</span></span>

> [!NOTE]
> <span data-ttu-id="4021d-108">本文的[原始版本][]出自 [@KevinMarquette][] 所撰寫的部落格。</span><span class="sxs-lookup"><span data-stu-id="4021d-108">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="4021d-109">PowerShell 小組感謝 Kevin 分享的內容。</span><span class="sxs-lookup"><span data-stu-id="4021d-109">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="4021d-110">請前往 [PowerShellExplained.com][] 瀏覽他的部落格。</span><span class="sxs-lookup"><span data-stu-id="4021d-110">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="what-is-the-powershell-standard-library"></a><span data-ttu-id="4021d-111">什麼是 PowerShell 標準程式庫？</span><span class="sxs-lookup"><span data-stu-id="4021d-111">What is the PowerShell Standard Library?</span></span>

<span data-ttu-id="4021d-112">PowerShell 標準程式庫可讓我們建立跨平台模組，以便在 PowerShell Core 和 Windows PowerShell 5.1 (或 3.0) 中使用。</span><span class="sxs-lookup"><span data-stu-id="4021d-112">The PowerShell Standard Library allows us to create cross platform modules that work in both PowerShell Core and with Windows PowerShell 5.1 (or 3.0).</span></span>

## <a name="planning-our-module"></a><span data-ttu-id="4021d-113">規劃我們的模組</span><span class="sxs-lookup"><span data-stu-id="4021d-113">Planning our module</span></span>

<span data-ttu-id="4021d-114">此模組的規劃是針對 C# 程式碼建立 `src` 資料夾 ，並針對指令碼模組建立其餘部分的架構，如同我即將執行的作業。</span><span class="sxs-lookup"><span data-stu-id="4021d-114">The plan for this module is to create a `src` folder for the C# code and structure the rest like I would for a script module.</span></span> <span data-ttu-id="4021d-115">這包括使用組建指令碼將所有內容編譯在 `output` 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="4021d-115">This includes using a build script to compile everything into an `output` folder.</span></span> <span data-ttu-id="4021d-116">資料夾結構如下所示：</span><span class="sxs-lookup"><span data-stu-id="4021d-116">The folder structure looks like this:</span></span>

```
MyModule
├───src
├───Output
│   └───MyModule
├───MyModule
│   ├───Data
│   ├───Private
│   └───Public
└───Tests
```

## <a name="getting-started"></a><span data-ttu-id="4021d-117">開始使用</span><span class="sxs-lookup"><span data-stu-id="4021d-117">Getting Started</span></span>

<span data-ttu-id="4021d-118">我通常會使用 Plaster 範本，但目前的範本尚未提供任何二進位模組支援。</span><span class="sxs-lookup"><span data-stu-id="4021d-118">I normally use a Plaster template but my current template doesn't have any binary module support yet.</span></span> <span data-ttu-id="4021d-119">不過，這沒什麼大不了的。</span><span class="sxs-lookup"><span data-stu-id="4021d-119">Not a big deal.</span></span> <span data-ttu-id="4021d-120">我現在就能馬上手動建立一個。</span><span class="sxs-lookup"><span data-stu-id="4021d-120">I'll create this one by hand this time.</span></span>

<span data-ttu-id="4021d-121">首先我需要建立資料夾，並建立 git 存放庫。</span><span class="sxs-lookup"><span data-stu-id="4021d-121">First I need to create the folder and create the git repo.</span></span> <span data-ttu-id="4021d-122">我使用 `$module` 做為模組名稱的預留位置。</span><span class="sxs-lookup"><span data-stu-id="4021d-122">I'm using `$module` as a placeholder for the module name.</span></span> <span data-ttu-id="4021d-123">若有需要，這應該可讓您更輕鬆地重複使用這些範例。</span><span class="sxs-lookup"><span data-stu-id="4021d-123">This should make it easier for you to reuse these examples if needed.</span></span>

```powershell
$module = 'MyModule'
New-Item -Path $module -Type Directory
Set-Location $module
git init
```

<span data-ttu-id="4021d-124">然後建立根層級資料夾。</span><span class="sxs-lookup"><span data-stu-id="4021d-124">Then create the root level folders.</span></span>

```powershell
New-Item -Path 'src' -Type Directory
New-Item -Path 'Output' -Type Directory
New-Item -Path 'Tests' -Type Directory
New-Item -Path $module -Type Directory
```

### <a name="binary-module-setup"></a><span data-ttu-id="4021d-125">二進位模組設定</span><span class="sxs-lookup"><span data-stu-id="4021d-125">Binary module setup</span></span>

<span data-ttu-id="4021d-126">本文內容著重在二進位模組，因此我們將從這裡開始。</span><span class="sxs-lookup"><span data-stu-id="4021d-126">This article os focused on the binary module so that is where we'll start.</span></span> <span data-ttu-id="4021d-127">本節會從[建立跨平台二進位模組][]指南中舉例說明。</span><span class="sxs-lookup"><span data-stu-id="4021d-127">This section pulls examples from the [Creating a cross-platform binary module][] guide.</span></span> <span data-ttu-id="4021d-128">如果您需要更多詳細資料或有任何問題，請參閱該指南。</span><span class="sxs-lookup"><span data-stu-id="4021d-128">Review that guide if you need more details or have any issues.</span></span>

<span data-ttu-id="4021d-129">我們首先要做的，就是檢查我們所安裝的 [dotnet core SDK][] 版本。</span><span class="sxs-lookup"><span data-stu-id="4021d-129">First thing we want to do is check the version of the [dotnet core SDK][] that we installed.</span></span> <span data-ttu-id="4021d-130">我使用的是 2.1.4，但您應該先擁有 2.0.0 或更新版本，才能繼續進行。</span><span class="sxs-lookup"><span data-stu-id="4021d-130">I'm using 2.1.4, but you should have 2.0.0 or newer before continuing.</span></span>

```powershell
PS> dotnet --version
2.1.4
```

<span data-ttu-id="4021d-131">我正在處理本節所述的 `src` 資料夾。</span><span class="sxs-lookup"><span data-stu-id="4021d-131">I'm working out of the `src` folder for this section.</span></span>

```powershell
Set-Location 'src'
```

<span data-ttu-id="4021d-132">使用 dotnet 命令建立新的類別庫。</span><span class="sxs-lookup"><span data-stu-id="4021d-132">Using the dotnet command, create a new class library.</span></span>

```powershell
dotnet new classlib --name $module
```

<span data-ttu-id="4021d-133">這會在子資料夾中建立程式庫專案，但我不想要這個額外的嵌套層級。</span><span class="sxs-lookup"><span data-stu-id="4021d-133">This created the library project in a subfolder but I don't want that extra level of nesting.</span></span> <span data-ttu-id="4021d-134">我要將這些檔案往上移一層。</span><span class="sxs-lookup"><span data-stu-id="4021d-134">I'm going to move those files up a level.</span></span>

```powershell
Move-Item -Path .\$module\* -Destination .\
Remove-Item $module -Recurse
```

<span data-ttu-id="4021d-135">設定專案的 .NET core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="4021d-135">Set the .NET core SDK version for the project.</span></span> <span data-ttu-id="4021d-136">我有 2.1 SDK，所以我要指定 2.1.0。</span><span class="sxs-lookup"><span data-stu-id="4021d-136">I have the 2.1 SDK so I'm going to specify 2.1.0.</span></span>
<span data-ttu-id="4021d-137">如果您使用的是 2.0 SDK，請使用 2.0.0。</span><span class="sxs-lookup"><span data-stu-id="4021d-137">Use 2.0.0 if you're using the 2.0 SDK.</span></span>

```powershell
dotnet new globaljson --sdk-version 2.1.0
```

<span data-ttu-id="4021d-138">將 PowerShell Standard 程式庫 [ NuGet 套件][] 新增至專案。</span><span class="sxs-lookup"><span data-stu-id="4021d-138">Add the PowerShell Standard Library [NuGet package][] to the project.</span></span> <span data-ttu-id="4021d-139">請確定您使用的是最新版本，以取得您所需的相容性層級。</span><span class="sxs-lookup"><span data-stu-id="4021d-139">Make sure you use the most recent version available for the level of compatibility that you need.</span></span> <span data-ttu-id="4021d-140">我會預設為最新版本，但我不認為此模組會利用比 PowerShell 3.0 還新的任何功能。</span><span class="sxs-lookup"><span data-stu-id="4021d-140">I would default to the latest version but I don't think this module leverages any features newer than PowerShell 3.0.</span></span>

```powershell
dotnet add package PowerShellStandard.Library --version 7.0.0-preview.1
```

<span data-ttu-id="4021d-141">我們應該會有一個 src 資料夾，如下所示：</span><span class="sxs-lookup"><span data-stu-id="4021d-141">We should have a src folder that looks like this:</span></span>

```powershell
PS> Get-ChildItem
    Directory: \MyModule\src

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        7/14/2018   9:51 PM                obj
-a----        7/14/2018   9:51 PM             86 Class1.cs
-a----        7/14/2018  10:03 PM            259 MyModule.csproj
-a----        7/14/2018  10:05 PM             45 global.json
```

<span data-ttu-id="4021d-142">現在我們已經準備好將自己的程式碼加入專案中。</span><span class="sxs-lookup"><span data-stu-id="4021d-142">Now we're ready to add our own code to the project.</span></span>

### <a name="building-a-binary-cmdlet"></a><span data-ttu-id="4021d-143">建立二進位 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4021d-143">Building a binary cmdlet</span></span>

<span data-ttu-id="4021d-144">我們需要更新 `src\Class1.cs` 以包含此入門 Cmdlet：</span><span class="sxs-lookup"><span data-stu-id="4021d-144">We need to update the `src\Class1.cs` to contain this starter cmdlet:</span></span>

```csharp
using System;
using System.Management.Automation;

namespace MyModule
{
    [Cmdlet( VerbsDiagnostic.Resolve , "MyCmdlet")]
    public class ResolveMyCmdletCommand : PSCmdlet
    {
        [Parameter(Position=0)]
        public Object InputObject { get; set; }

        protected override void EndProcessing()
        {
            this.WriteObject(this.InputObject);
            base.EndProcessing();
        }
    }
}
```

<span data-ttu-id="4021d-145">將檔案重新命名以符合類別名稱。</span><span class="sxs-lookup"><span data-stu-id="4021d-145">Rename the file to match the class name.</span></span>

```powershell
Rename-Item .\Class1.cs .\ResolveMyCmdletCommand.cs
```

<span data-ttu-id="4021d-146">然後我們可以建立自己的模組。</span><span class="sxs-lookup"><span data-stu-id="4021d-146">Then we can build our module.</span></span>

```powershell
PS> dotnet build

Microsoft (R) Build Engine version 15.5.180.51428 for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

Restore completed in 18.19 ms for C:\workspace\MyModule\src\MyModule.csproj.
MyModule -> C:\workspace\MyModule\src\bin\Debug\netstandard2.0\MyModule.dll

Build succeeded.
    0 Warning(s)
    0 Error(s)

Time Elapsed 00:00:02.19
```

<span data-ttu-id="4021d-147">我們可以在新的 dll 上呼叫 `Import-Module`，載入新的 CMDlet。</span><span class="sxs-lookup"><span data-stu-id="4021d-147">We can call `Import-Module` on the new dll to load our new CMDlet.</span></span>

```powershell
PS> Import-Module .\bin\Debug\netstandard2.0\$module.dll
PS> Get-Command -Module $module

CommandType Name                    Version Source
----------- ----                    ------- ------
Cmdlet      Resolve-MyCmdlet        1.0.0.0 MyModule
```

<span data-ttu-id="4021d-148">如果您的系統匯入失敗，請嘗試將 .NET 更新為 4.7.1 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="4021d-148">If the import fails on your system, try updating .NET to 4.7.1 or newer.</span></span> <span data-ttu-id="4021d-149">[建立跨平台二進位模組][]指南會進一步探討 .NET 支援和舊版 .NET 的相容性。</span><span class="sxs-lookup"><span data-stu-id="4021d-149">The [Creating a cross-platform binary module][] guide goes into more details on .NET support and compatibility for older versions of .NET.</span></span>

### <a name="module-manifest"></a><span data-ttu-id="4021d-150">模組資訊清單</span><span class="sxs-lookup"><span data-stu-id="4021d-150">Module manifest</span></span>

<span data-ttu-id="4021d-151">很棒的是，我們可以匯入 dll 並擁有一個有效的模組。</span><span class="sxs-lookup"><span data-stu-id="4021d-151">It's cool that we can import the dll and have a working module.</span></span> <span data-ttu-id="4021d-152">我想要繼續使用它，並建立模組資訊清單。</span><span class="sxs-lookup"><span data-stu-id="4021d-152">I like to keep going with it and create a module manifest.</span></span> <span data-ttu-id="4021d-153">如果想要稍後發行至 PSGallery，我們需要資訊清單。</span><span class="sxs-lookup"><span data-stu-id="4021d-153">We need the manifest if we want to publish to the PSGallery later.</span></span>

<span data-ttu-id="4021d-154">從專案的根目錄，我們可以執行此命令以建立所需的模組資訊清單。</span><span class="sxs-lookup"><span data-stu-id="4021d-154">From the root of our project, we can run this command to create the module manifest that we need.</span></span>

```powershell
$manifestSplat = @{
    Path              = ".\$module\$module.psd1"
    Author            = 'Kevin Marquette'
    NestedModules     = @('bin\MyModule.dll')
    RootModule        = "$module.psm1"
    FunctionsToExport = @('Resolve-MyCmdlet')
}
New-ModuleManifest @manifestSplat
```

<span data-ttu-id="4021d-155">我也會建立一個空的根模組，供未來的 PowerShell 函式使用。</span><span class="sxs-lookup"><span data-stu-id="4021d-155">I'm also going to create an empty root module for future PowerShell functions.</span></span>

```powershell
Set-Content -Value '' -Path ".\$module\$module.psm1"
```

<span data-ttu-id="4021d-156">這可讓我在同一個專案中混合使用一般的 PowerShell 函式與二進位 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4021d-156">This allows me to mix both normal PowerShell functions and binary Cmdlets in the same project.</span></span>

### <a name="building-the-full-module"></a><span data-ttu-id="4021d-157">建置完整的模組</span><span class="sxs-lookup"><span data-stu-id="4021d-157">Building the full module</span></span>

<span data-ttu-id="4021d-158">我將所有專案編譯成輸出資料夾。</span><span class="sxs-lookup"><span data-stu-id="4021d-158">I compile everything together into an output folder.</span></span> <span data-ttu-id="4021d-159">我們需要建立組建指令碼以執行此動作。</span><span class="sxs-lookup"><span data-stu-id="4021d-159">We need to create a build script to do that.</span></span> <span data-ttu-id="4021d-160">我通常會將此程式碼新增至 `Invoke-Build` 指令碼，但在此範例中，我們可以將它簡化。</span><span class="sxs-lookup"><span data-stu-id="4021d-160">I would normally add this to an `Invoke-Build` script, but we can keep it simple for this example.</span></span> <span data-ttu-id="4021d-161">將此加入至專案根目錄的 `build.ps1`。</span><span class="sxs-lookup"><span data-stu-id="4021d-161">Add this to a `build.ps1` at the root of the project.</span></span>

```powershell
$module = 'MyModule'
Push-Location $PSScriptRoot

dotnet build $PSScriptRoot\src -o $PSScriptRoot\output\$module\bin
Copy-Item "$PSScriptRoot\$module\*" "$PSScriptRoot\output\$module" -Recurse -Force

Import-Module "$PSScriptRoot\Output\$module\$module.psd1"
Invoke-Pester "$PSScriptRoot\Tests"
```

<span data-ttu-id="4021d-162">這些命令會建立 DLL，並將其放入我們的 `output\$module\bin` 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="4021d-162">These commands build our DLL and place it into our `output\$module\bin` folder.</span></span> <span data-ttu-id="4021d-163">然後，它會將其他模組檔案複製到定位。</span><span class="sxs-lookup"><span data-stu-id="4021d-163">It then copies the other module files into place.</span></span>

```
Output
└───MyModule
    │   MyModule.psd1
    │   MyModule.psm1
    │
    └───bin
            MyModule.deps.json
            MyModule.dll
            MyModule.pdb
```

<span data-ttu-id="4021d-164">此時，我們可以使用 psd1 檔案匯入模組。</span><span class="sxs-lookup"><span data-stu-id="4021d-164">At this point, we can import our module with the psd1 file.</span></span>

```powershell
Import-Module ".\Output\$module\$module.psd1"
```

<span data-ttu-id="4021d-165">在這裡，我們可以將 `.\Output\$module` 資料夾放入我們的 `$env:PSModulePath` 目錄中，並在需要時該資料夾會自動載入我們的命令。</span><span class="sxs-lookup"><span data-stu-id="4021d-165">From here, we can drop the `.\Output\$module` folder into our `$env:PSModulePath` directory and it autoloads our command whenever we need it.</span></span>

### <a name="update-dotnet-new-psmodule"></a><span data-ttu-id="4021d-166">更新： dotnet 新的 PSModule</span><span class="sxs-lookup"><span data-stu-id="4021d-166">Update: dotnet new PSModule</span></span>

<span data-ttu-id="4021d-167">我瞭解 `dotnet` 工具具有 `PSModule` 範本。</span><span class="sxs-lookup"><span data-stu-id="4021d-167">I learned that the `dotnet` tool has a `PSModule` template.</span></span>

<span data-ttu-id="4021d-168">上面所述的所有步驟仍然有效，但此範本會減少了許多證明作業。它仍然是一個非常新的範本，仍然有待進一步完善。</span><span class="sxs-lookup"><span data-stu-id="4021d-168">All the steps that I outlined above are still valid, but this template cuts many pf them out. It's still a fairly new template that is still getting some polish placed on it.</span></span> <span data-ttu-id="4021d-169">期待它此後會日益完善。</span><span class="sxs-lookup"><span data-stu-id="4021d-169">Expect it to keep getting better from here.</span></span>

<span data-ttu-id="4021d-170">這是您使用 install 和使用 PSModule 範本的方式。</span><span class="sxs-lookup"><span data-stu-id="4021d-170">This is how you use install and use the PSModule template.</span></span>

```powershell
dotnet new -i Microsoft.PowerShell.Standard.Module.Template
dotnet new psmodule
dotnet build
Import-Module "bin\Debug\netstandard2.0\$module.dll"
Get-Module $module
```

<span data-ttu-id="4021d-171">這個最低可行的範本會負責新增 .NET SDK、PowerShell 標準程式庫，並在專案中建立範例類別。</span><span class="sxs-lookup"><span data-stu-id="4021d-171">This minimally-viable template takes care of adding the .NET SDK, PowerShell Standard Library, and creates an example class in the project.</span></span> <span data-ttu-id="4021d-172">您可以建立範本並立即加以執行。</span><span class="sxs-lookup"><span data-stu-id="4021d-172">You can build it and run it right away.</span></span>

## <a name="important-details"></a><span data-ttu-id="4021d-173">重要詳細資料</span><span class="sxs-lookup"><span data-stu-id="4021d-173">Important details</span></span>

<span data-ttu-id="4021d-174">在本文結束之前，這裡有一些值得一提的其他詳細資料。</span><span class="sxs-lookup"><span data-stu-id="4021d-174">Before we end this article, here are a few other details worth mentioning.</span></span>

### <a name="unloading-dlls"></a><span data-ttu-id="4021d-175">卸載 DLL</span><span class="sxs-lookup"><span data-stu-id="4021d-175">Unloading DLLs</span></span>

<span data-ttu-id="4021d-176">載入二進位模組之後，您就無法真正將其卸載。</span><span class="sxs-lookup"><span data-stu-id="4021d-176">Once a binary module is loaded, you can't really unload it.</span></span> <span data-ttu-id="4021d-177">系統會鎖定 DLL 檔案，直到其卸載為止。</span><span class="sxs-lookup"><span data-stu-id="4021d-177">The DLL file is locked until you unload it.</span></span> <span data-ttu-id="4021d-178">這可能會在開發時造成困擾，因為每當您進行變更並想要加以建置時，檔案常常會遭到鎖定。</span><span class="sxs-lookup"><span data-stu-id="4021d-178">This can be annoying when developing because every time you make a change and want to build it, the file is often locked.</span></span> <span data-ttu-id="4021d-179">解決此問題的唯一可靠方式，就是關閉載入 DLL 的 PowerShell 工作階段。</span><span class="sxs-lookup"><span data-stu-id="4021d-179">The only reliable way to resolve this is to close the PowerShell session that loaded the DLL.</span></span>

### <a name="vs-code-reload-window-action"></a><span data-ttu-id="4021d-180">VS Code 重載視窗動作</span><span class="sxs-lookup"><span data-stu-id="4021d-180">VS Code reload window action</span></span>

<span data-ttu-id="4021d-181">我大部分的 PowerShell 開發工作都是在 [VS 程式碼][] 中執行。</span><span class="sxs-lookup"><span data-stu-id="4021d-181">I do most of my PowerShell dev work in [VS Code][].</span></span> <span data-ttu-id="4021d-182">當我使用二進位模組 (或具有類別的模組) 時，我已經養成在每次建立時都重載 VS Code 的習慣。</span><span class="sxs-lookup"><span data-stu-id="4021d-182">When I'm working on a binary module (or a module with classes), I've gotten into the habit of reloading VS Code every time I build.</span></span>
<span data-ttu-id="4021d-183"><kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> 會使命令視窗隨即開啟，而 `Reload Window` 則一律位於清單頂端。</span><span class="sxs-lookup"><span data-stu-id="4021d-183"><kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> pops the command window and `Reload Window` is always at the top of my list.</span></span>

### <a name="nested-powershell-sessions"></a><span data-ttu-id="4021d-184">嵌套的 PowerShell 工作階段</span><span class="sxs-lookup"><span data-stu-id="4021d-184">Nested PowerShell sessions</span></span>

<span data-ttu-id="4021d-185">另一個選項是使用良好的 Pester 測試涵蓋範圍。</span><span class="sxs-lookup"><span data-stu-id="4021d-185">One other option is to have good Pester test coverage.</span></span> <span data-ttu-id="4021d-186">接著，您可以調整 build.ps1 指令碼來啟動新的 PowerShell 工作階段、執行組建、執行測試，然後關閉工作階段。</span><span class="sxs-lookup"><span data-stu-id="4021d-186">Then you can adjust the build.ps1 script to start a new PowerShell session, perform the build, run the tests, and close the session.</span></span>

### <a name="updating-installed-modules"></a><span data-ttu-id="4021d-187">更新已安裝的模組</span><span class="sxs-lookup"><span data-stu-id="4021d-187">Updating installed modules</span></span>

<span data-ttu-id="4021d-188">嘗試更新您在本機安裝的模組時，這種鎖定可能會造成困擾。</span><span class="sxs-lookup"><span data-stu-id="4021d-188">This locking can be annoying when trying to update your locally installed module.</span></span> <span data-ttu-id="4021d-189">如果有任何工作階段將其載入，您就必須將向下搜尋它並加以關閉。</span><span class="sxs-lookup"><span data-stu-id="4021d-189">If any session has it loaded, you have to go hunt it down and close it.</span></span> <span data-ttu-id="4021d-190">從 PSGallery 安裝時，這種問題比較少出現，因為模組版本設定會將新的設定放在不同的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="4021d-190">This is less of an issue when installing from a PSGallery because module versioning places the new one in a different folder.</span></span>

<span data-ttu-id="4021d-191">您可以設定本機 PSGallery，並將其發佈以做為組建的一部分。</span><span class="sxs-lookup"><span data-stu-id="4021d-191">You can set up a local PSGallery and publish to that as part of your build.</span></span> <span data-ttu-id="4021d-192">然後從該 PSGallery 進行本機安裝。</span><span class="sxs-lookup"><span data-stu-id="4021d-192">Then do your local install from that PSGallery.</span></span> <span data-ttu-id="4021d-193">這聽起來似乎頗為繁瑣，不過這就像啟動 docker 容器一樣簡單。</span><span class="sxs-lookup"><span data-stu-id="4021d-193">This sounds like a lot of work, but this can be as simple as starting a docker container.</span></span> <span data-ttu-id="4021d-194">我在 [使用適用於 PSRepository 的 NuGet 伺服器][] (英文) 文章中，介紹了執行這項操作的方法。</span><span class="sxs-lookup"><span data-stu-id="4021d-194">I cover a way to do that in my post on [Using a NuGet server for a PSRepository][].</span></span>

## <a name="why-binary-modules"></a><span data-ttu-id="4021d-195">為何要選擇二進位模組？</span><span class="sxs-lookup"><span data-stu-id="4021d-195">Why binary modules?</span></span>

<span data-ttu-id="4021d-196">我直接跳到如何製作二進位模組，卻沒有提及您為什麼要製作。</span><span class="sxs-lookup"><span data-stu-id="4021d-196">I jumped right into how to make a binary module and didn't mention why you want to make one.</span></span> <span data-ttu-id="4021d-197">實際上，您正在撰寫 C# 並且讓您輕鬆地存取 PowerShell Cmdlet 和函式。</span><span class="sxs-lookup"><span data-stu-id="4021d-197">In reality, you are writing C# and give up easy access to PowerShell Cmdlets and functions.</span></span> <span data-ttu-id="4021d-198">這是我未搶先移至二進位模組的主要原因。</span><span class="sxs-lookup"><span data-stu-id="4021d-198">That is the main reason why I have not shifted to binary modules sooner.</span></span>

<span data-ttu-id="4021d-199">不過，如果您要建立的模組並不依賴許多其他 PowerShell 命令，便可以在效能方面產生巨大優勢。</span><span class="sxs-lookup"><span data-stu-id="4021d-199">But if you are creating a module that doesn't depend on a lot of other PowerShell commands, the performance benefit can be significant.</span></span> <span data-ttu-id="4021d-200">藉由將放入 C# ，您就可以擺脫 PowerShell 新增的負荷。</span><span class="sxs-lookup"><span data-stu-id="4021d-200">By dropping into C#, you get to shed the overhead added by PowerShell.</span></span> <span data-ttu-id="4021d-201">PowerShell 已針對系統管理員 (而不是電腦) 進行最佳化，因而增加了一些負荷。</span><span class="sxs-lookup"><span data-stu-id="4021d-201">PowerShell was optimized for the administrator, not the computer, and that adds a little overhead.</span></span>

<span data-ttu-id="4021d-202">在工作時，我們有一個非常重要的流程，其中會使用 JSON 和雜湊表執行許多工作。</span><span class="sxs-lookup"><span data-stu-id="4021d-202">At work, we have a critical process that does a lot of work with JSON and Hashtables.</span></span> <span data-ttu-id="4021d-203">儘管我們已經盡可能將 PowerShell 最佳化，但此流程仍需要執行 12 分鐘。</span><span class="sxs-lookup"><span data-stu-id="4021d-203">We optimized the PowerShell as much as we could but this process was still running for 12 minutes.</span></span> <span data-ttu-id="4021d-204">模組已包含許多 C# 樣式的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="4021d-204">The module already contained a lot of C# style PowerShell.</span></span> <span data-ttu-id="4021d-205">這使得轉換成二進位模組變得簡單俐落，而且容易執行。</span><span class="sxs-lookup"><span data-stu-id="4021d-205">This made the conversion to a binary module clean and easy to do.</span></span> <span data-ttu-id="4021d-206">我們的轉換會將流程從12分鐘縮短至 4 分鐘以內。</span><span class="sxs-lookup"><span data-stu-id="4021d-206">Our conversion cut that process down from over 12 minutes to under four minutes.</span></span>

### <a name="hybrid-modules"></a><span data-ttu-id="4021d-207">混合式模組</span><span class="sxs-lookup"><span data-stu-id="4021d-207">Hybrid modules</span></span>

<span data-ttu-id="4021d-208">您可以混合使用二進位 Cmdlet 與 PowerShell 進階函式。</span><span class="sxs-lookup"><span data-stu-id="4021d-208">You can mix binary Cmdlets with PowerShell advanced functions.</span></span> <span data-ttu-id="4021d-209">這正是我在本指南中執行的動作。</span><span class="sxs-lookup"><span data-stu-id="4021d-209">That is exactly what I'm doing in this guide.</span></span> <span data-ttu-id="4021d-210">關於指令碼模組，您所知的一切，也全都以相同的方式適用。</span><span class="sxs-lookup"><span data-stu-id="4021d-210">You can take everything you know about script modules and it all applies the same way.</span></span>
<span data-ttu-id="4021d-211">我今天所建立的空白 `psm1` 檔案，就是您稍後可以放入其他 PowerShell 函式的位置。</span><span class="sxs-lookup"><span data-stu-id="4021d-211">The empty `psm1` file that I created today is there just so you can drop in other PowerShell functions later.</span></span>

<span data-ttu-id="4021d-212">幾乎我們所建立的所有經過編譯的 Cmdlet，都是先以 PowerShell 函式的方式開始的。</span><span class="sxs-lookup"><span data-stu-id="4021d-212">Almost all of the compiled cmdlets that we created started out as a PowerShell function first.</span></span> <span data-ttu-id="4021d-213">我們所有的二進位模組都是混合式模組。</span><span class="sxs-lookup"><span data-stu-id="4021d-213">All of our binary modules are really hybrid modules.</span></span>

### <a name="build-scripts"></a><span data-ttu-id="4021d-214">組建指令碼</span><span class="sxs-lookup"><span data-stu-id="4021d-214">Build scripts</span></span>

<span data-ttu-id="4021d-215">我在此將簡化組建指令碼。</span><span class="sxs-lookup"><span data-stu-id="4021d-215">I kept the build script simple here.</span></span> <span data-ttu-id="4021d-216">我通常會使用大型的 `Invoke-Build` 指令碼做為 CI/CD 管道的一部分。</span><span class="sxs-lookup"><span data-stu-id="4021d-216">I generally use a large `Invoke-Build` script as part of my CI/CD pipeline.</span></span> <span data-ttu-id="4021d-217">執行 Pester 測試、執行 PSScriptAnalyzer、管理版本控制，以及發行至 PSGallery 等，都能發揮更大的神奇效用。</span><span class="sxs-lookup"><span data-stu-id="4021d-217">It does more magic like running Pester tests, running PSScriptAnalyzer, managing versioning, and publishing to the PSGallery.</span></span> <span data-ttu-id="4021d-218">當我開始針對模組使用組建指令碼之後，我就可以找到要新增至模組的許多內容。</span><span class="sxs-lookup"><span data-stu-id="4021d-218">Once I started using a build script for my modules, I was able to find lots of things to add to it.</span></span>

## <a name="final-thoughts"></a><span data-ttu-id="4021d-219">最後的想法</span><span class="sxs-lookup"><span data-stu-id="4021d-219">Final thoughts</span></span>

<span data-ttu-id="4021d-220">二進位模組很容易建立。</span><span class="sxs-lookup"><span data-stu-id="4021d-220">Binary modules are easy to create.</span></span> <span data-ttu-id="4021d-221">建立 Cmdlet，我並未採用 C# 語法，不過 [Windows PowerShell SDK][] 中有許多相關文件。</span><span class="sxs-lookup"><span data-stu-id="4021d-221">I didn't touch on the C# syntax for creating a Cmdlet, but there is plenty of documentation on it in the [Windows PowerShell SDK][].</span></span> <span data-ttu-id="4021d-222">這種作法絕對值得一試，可做為更嚴謹的 C# 的跳板。</span><span class="sxs-lookup"><span data-stu-id="4021d-222">It is definitely something worth experimenting with as a stepping stone into more serious C#.</span></span>

<!-- link references -->
[原始版本]: https://powershellexplained.com/2018-08-04-Powershell-Standard-Library-Binary-Module/
[original version]: https://powershellexplained.com/2018-08-04-Powershell-Standard-Library-Binary-Module/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[PowerShell 標準程式庫]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard Library]: https://github.com/PowerShell/PowerShellStandard
[建立跨平台二進位模組]: https://github.com/PowerShell/PowerShell/blob/master/docs/cmdlet-example/command-line-simple-example.md
[Creating a cross-platform binary module]: https://github.com/PowerShell/PowerShell/blob/master/docs/cmdlet-example/command-line-simple-example.md
[dotnet core SDK]: https://www.microsoft.com/net/download/core
[使用適用於 PSRepository 的 NuGet 伺服器]: https://powershellexplained.com/2018-03-03-Powershell-Using-a-NuGet-server-for-a-PSRepository/
[Using a NuGet server for a PSRepository]: https://powershellexplained.com/2018-03-03-Powershell-Using-a-NuGet-server-for-a-PSRepository/
[Windows PowerShell SDK]: /powershell/scripting/developer/windows-powershell-reference
[VS 程式碼]: https://code.visualstudio.com
[VS Code]: https://code.visualstudio.com
[ NuGet 套件]: https://www.nuget.org/packages/PowerShellStandard.Library/
[nuget package]: https://www.nuget.org/packages/PowerShellStandard.Library/
