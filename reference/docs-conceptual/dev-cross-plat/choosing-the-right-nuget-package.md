---
title: 為 .NET 專案選擇正確的 PowerShell NuGet 套件
description: 除了與每個 PowerShell 版本一同發佈的可執行檔套件之外，PowerShell 小組也在 NuGet 上維護數個可用的套件。 這些套件允許在 .NET 中以 PowerShell 作為 API 平台。
ms.date: 06/25/2020
ms.custom: rjmholt
ms.openlocfilehash: 39369ed872faa76ad2c41d813da5e0a98cf1c078
ms.sourcegitcommit: d0461273abb6db099c5e784ef00f57fd551be4a6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85795256"
---
# <a name="choosing-the-right-powershell-nuget-package-for-your-net-project"></a><span data-ttu-id="93c45-104">為 .NET 專案選擇正確的 PowerShell NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="93c45-104">Choosing the right PowerShell NuGet package for your .NET project</span></span>

<span data-ttu-id="93c45-105">除了與每個 PowerShell 版本一同發佈的 `pwsh` 可執行檔套件之外，PowerShell 小組也在 [NuGet][] 上維護數個可用的套件。</span><span class="sxs-lookup"><span data-stu-id="93c45-105">Alongside the `pwsh` executable packages published with each PowerShell release, the PowerShell team also maintains several packages available on [NuGet][].</span></span> <span data-ttu-id="93c45-106">這些套件允許在 .NET 中以 PowerShell 作為 API 平台。</span><span class="sxs-lookup"><span data-stu-id="93c45-106">These packages allow targeting PowerShell as an API platform in .NET.</span></span>

<span data-ttu-id="93c45-107">作為提供 API 並預期載入實作自身 (二進位模組) .NET 程式庫的 .NET 應用程式，以 NuGet 的形式提供 PowerShell 非常重要。</span><span class="sxs-lookup"><span data-stu-id="93c45-107">As a .NET application that provides APIs and expects to load .NET libraries implementing its own (binary modules), it's essential that PowerShell be available in the form of a NuGet package.</span></span>

<span data-ttu-id="93c45-108">目前有數個 NuGet 套件呈現了一些 PowerShell API 的介面區。</span><span class="sxs-lookup"><span data-stu-id="93c45-108">Currently there are several NuGet packages that provide some representation of the PowerShell API surface area.</span></span> <span data-ttu-id="93c45-109">要針對特定專案使用哪一個套件不見得總是明確。</span><span class="sxs-lookup"><span data-stu-id="93c45-109">Which package to use with a particular project hasn't always been made clear.</span></span> <span data-ttu-id="93c45-110">本文揭示一些以 PowerShell 為目標的 .NET 專案常見案例，以及如何為以 PowerShell 為導向的 .NET 專案選擇正確 NuGet 套件作為目標。</span><span class="sxs-lookup"><span data-stu-id="93c45-110">This article sheds some light on a few common scenarios for PowerShell-targeting .NET projects and how to choose the right NuGet package to target for your PowerShell-oriented .NET project.</span></span>

## <a name="hosting-vs-referencing"></a><span data-ttu-id="93c45-111">主機與參考</span><span class="sxs-lookup"><span data-stu-id="93c45-111">Hosting vs referencing</span></span>

<span data-ttu-id="93c45-112">有些 .NET 專案會要求撰寫程式碼來將其載入已預先存在的 PowerShell 執行階段 (例如 `pwsh`、`powershell.exe`、PowerShell 整合式主控台或 ISE)，其他專案則可能會想要在其自身的應用程式內執行 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="93c45-112">Some .NET projects seek to write code to be loaded into a pre-existing PowerShell runtime (such as `pwsh`, `powershell.exe`, the PowerShell Integrated Console or the ISE), while others want to run PowerShell in their own applications.</span></span>

- <span data-ttu-id="93c45-113">**參考**指的是專案 (通常是模組) 旨在載入 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="93c45-113">**Referencing** is for when a project, usually a module, is intended to be loaded into PowerShell.</span></span>
  <span data-ttu-id="93c45-114">為了與 PowerShell 進行互動，其必須針對 PowerShell 提供的 API 編譯，但 PowerShell 實作是由載入該專案的 PowerShell 處理序提供的。</span><span class="sxs-lookup"><span data-stu-id="93c45-114">It must be compiled against the APIs that PowerShell provides in order to interact with it, but the PowerShell implementation is supplied by the PowerShell process loading it in.</span></span> <span data-ttu-id="93c45-115">針對參考，專案可使用[參考組件][]或實際的執行階段組件作為編譯目標，但必須確保其不會附帶任何編譯目標發佈其組建。</span><span class="sxs-lookup"><span data-stu-id="93c45-115">For referencing, a project can use [reference assemblies][] or the actual runtime assemblies as a compilation target, but must ensure that it does not publish any of these with its build.</span></span>
- <span data-ttu-id="93c45-116">**裝載**指的是專案需要其自身的 PowerShell 實作，通常是因為其為需要執行 PowerShell 的獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="93c45-116">**Hosting** is when a project needs its own implementation of PowerShell, usually because it is a standalone application that needs to run PowerShell.</span></span> <span data-ttu-id="93c45-117">在此情況下，即無法使用純參考組件。</span><span class="sxs-lookup"><span data-stu-id="93c45-117">In this case, pure reference assemblies cannot be used.</span></span> <span data-ttu-id="93c45-118">在此情況下，必須改為倚賴具體的 PowerShell 實作。</span><span class="sxs-lookup"><span data-stu-id="93c45-118">Instead, a concrete PowerShell implementation must be depended upon.</span></span> <span data-ttu-id="93c45-119">由於必須使用具體的 PowerShell 實作，因此必須針對裝載選擇特定的 PowerShell 版本；單一主機應用程式無法以多個 PowerShell 版本作為目標。</span><span class="sxs-lookup"><span data-stu-id="93c45-119">Because a concrete PowerShell implementation must be used, a specific version of PowerShell must be chosen for hosting; a single host application cannot multi-target PowerShell versions.</span></span>

### <a name="publishing-projects-that-target-powershell-as-a-reference"></a><span data-ttu-id="93c45-120">將以 PowerShell 為目標的專案作為參考發佈</span><span class="sxs-lookup"><span data-stu-id="93c45-120">Publishing projects that target PowerShell as a reference</span></span>

> [!NOTE]
> <span data-ttu-id="93c45-121">我們會在本文中使用**發佈**這個術語來表示執行 `dotnet publish`，這個命令會將 .NET 程式庫與其所有的相依性放入目錄中，準備就緒以供部署至特定的執行階段。</span><span class="sxs-lookup"><span data-stu-id="93c45-121">We use the term **publish** in this article to refer to running `dotnet publish`, which places a .NET library into a directory with all of its dependencies, ready for deployment to a particular runtime.</span></span>

<span data-ttu-id="93c45-122">為了避免發佈作為編譯參考目標使用的專案相依性，建議設定 [PrivateAssets 屬性][]：</span><span class="sxs-lookup"><span data-stu-id="93c45-122">In order to prevent publishing project dependencies that are just being used as compilation reference targets, it is recommended to set the [PrivateAssets attribute][]:</span></span>

```xml
<PackageReference Include="PowerShellStandard.Library" Version="5.1.0.0" PrivateAssets="all" />
```

<span data-ttu-id="93c45-123">若忘記執行這項操作，並使用參考組件作為目標，即可能會看到與使用參考組件預設實作相關的問題，而非實際的實作。</span><span class="sxs-lookup"><span data-stu-id="93c45-123">If you forget to do this and use a reference assembly as your target, you may see issues related to using the reference assembly's default implementation instead of the actual implementation.</span></span> <span data-ttu-id="93c45-124">其形式可能會是 `NullReferenceException`，因為參考組件通常會透過直接傳回 `null` 來模擬實作 API。</span><span class="sxs-lookup"><span data-stu-id="93c45-124">This may take the form of a `NullReferenceException`, since reference assemblies often mock the implementation API by simply returning `null`.</span></span>

## <a name="key-kinds-of-powershell-targeting-net-projects"></a><span data-ttu-id="93c45-125">以 PowerShell 為目標 .NET 專案的主要類型</span><span class="sxs-lookup"><span data-stu-id="93c45-125">Key kinds of PowerShell-targeting .NET projects</span></span>

<span data-ttu-id="93c45-126">雖然任何 .NET 程式庫或應用程式都可內嵌 PowerShell，仍然有些使用 PowerShell API 的常見案例：</span><span class="sxs-lookup"><span data-stu-id="93c45-126">While any .NET library or application can embed PowerShell, there are some common scenarios that use PowerShell APIs:</span></span>

- <span data-ttu-id="93c45-127">**實作 PowerShell 二進位模組**</span><span class="sxs-lookup"><span data-stu-id="93c45-127">**Implementing a PowerShell binary module**</span></span>

  <span data-ttu-id="93c45-128">PowerShell 二進位模組是由 PowerShell 載入的 .NET 程式庫，這些模組必須實作 [PSCmdlet][] 或 [CmdletProvider][] 類型等 PowerShell API，才能分別公開 Cmdlet 或提供者。</span><span class="sxs-lookup"><span data-stu-id="93c45-128">PowerShell binary modules are .NET libraries loaded by PowerShell that must implement PowerShell APIs like the [PSCmdlet][] or [CmdletProvider][] types in order to expose cmdlets or providers respectively.</span></span> <span data-ttu-id="93c45-129">因為會載入這些模組，這些模組會針對 PowerShell 的參考進行編譯，但不會在其組建中發佈任何參考。</span><span class="sxs-lookup"><span data-stu-id="93c45-129">Because they are loaded in, modules seek to compile against references to PowerShell without publishing it in their build.</span></span> <span data-ttu-id="93c45-130">模組也經常會想要支援多個 PowerShell 版本和平台，且最好是將磁碟空間、複雜度或重複實作的額外負荷降至最低。</span><span class="sxs-lookup"><span data-stu-id="93c45-130">It's also common for modules to want to support multiple PowerShell versions and platforms, ideally with a minimum of overhead of disk space, complexity, or repeated implementation.</span></span> <span data-ttu-id="93c45-131">請參閱 [about_Modules][] 以取得模組的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="93c45-131">See [about_Modules][] for more information about modules.</span></span>

- <span data-ttu-id="93c45-132">**實作 PowerShell 主機**</span><span class="sxs-lookup"><span data-stu-id="93c45-132">**Implementing a PowerShell Host**</span></span>

  <span data-ttu-id="93c45-133">PowerShell 主機提供 PowerShell 執行階段的互動層。</span><span class="sxs-lookup"><span data-stu-id="93c45-133">A PowerShell Host provides an interaction layer for the PowerShell runtime.</span></span> <span data-ttu-id="93c45-134">這是一種「裝載」的特定形式，其中 [PSHost][] 會作為 PowerShell 的新使用者介面實作。</span><span class="sxs-lookup"><span data-stu-id="93c45-134">It is a specific form of _hosting_, where a [PSHost][] is implemented as a new user interface to PowerShell.</span></span> <span data-ttu-id="93c45-135">例如，PowerShell ConsoleHost 提供適用於 PowerShell 可執行檔的終端使用者介面，PowerShell 編輯器服務主機和 ISE 主機則提供與編輯器整合的 PowerShell 部分圖形化使用者介面。</span><span class="sxs-lookup"><span data-stu-id="93c45-135">For example, the PowerShell ConsoleHost provides a terminal user interface for PowerShell executables, while the PowerShell Editor Services Host and the ISE Host both provide an editor-integrated partially graphical user interface around PowerShell.</span></span> <span data-ttu-id="93c45-136">雖然可將主機載入現有的 PowerShell 處理序，但將主機實作用作為轉散布 PowerShell 引擎的獨立 PowerShell 實作更為常見。</span><span class="sxs-lookup"><span data-stu-id="93c45-136">While it's possible to load a host onto an existing PowerShell process, it's much more common for a host implementation to act as a standalone PowerShell implementation that redistributes the PowerShell engine.</span></span>

- <span data-ttu-id="93c45-137">**從另一個 .NET 應用程式呼叫 PowerShell**</span><span class="sxs-lookup"><span data-stu-id="93c45-137">**Calling into PowerShell from another .NET application**</span></span>

  <span data-ttu-id="93c45-138">如同任何應用程式，可將 PowerShell 作為子流程呼叫來執行工作負載。</span><span class="sxs-lookup"><span data-stu-id="93c45-138">As with any application, PowerShell can be called as a subprocess to run workloads.</span></span> <span data-ttu-id="93c45-139">但是，作為 .NET 應用程式，也可以在處理序中叫用 PowerShell 來取回完整的 .NET 物件，以在呼叫的應用程式中使用。</span><span class="sxs-lookup"><span data-stu-id="93c45-139">However, as a .NET application, it's also possible to invoke PowerShell in-process to get back full .NET objects for use within the calling application.</span></span> <span data-ttu-id="93c45-140">這是更為一般的「裝載」形式，其中應用程式會保有其自身的 PowerShell 實作以供內部使用。</span><span class="sxs-lookup"><span data-stu-id="93c45-140">This is a more general form of _hosting_, where the application holds its own PowerShell implementation for internal use.</span></span> <span data-ttu-id="93c45-141">其範例可能是服務或是執行 PowerShell 來管理機器狀態的精靈，或根據要求執行 PowerShell 來執行如管理雲端部署等工作的 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="93c45-141">Examples of this might be a service or daemon running PowerShell to manage machine state or a web application that runs PowerShell on request to do something like manage cloud deployments.</span></span>

- <span data-ttu-id="93c45-142">**從 .NET 針對 PowerShell 模組進行單元測試**</span><span class="sxs-lookup"><span data-stu-id="93c45-142">**Unit testing PowerShell modules from .NET**</span></span>

  <span data-ttu-id="93c45-143">雖然模組和其他旨在向 PowerShell 公開功能的程式庫主要應在 PowerShell 內進行測試 (建議使用 [Pester][])，有時候還是必須從 .NET 針對為 PowerShell 模組撰寫的 API 進行單元測試。</span><span class="sxs-lookup"><span data-stu-id="93c45-143">While modules and other libraries designed to expose functionality to PowerShell should be primarily tested from PowerShell (we recommend [Pester][]), sometimes it's necessary to unit test APIs written for a PowerShell module from .NET.</span></span> <span data-ttu-id="93c45-144">這種情況涉及模組程式碼嘗試以多個 PowerShell 版本為目標，同時測試應在特定、具體的實作上執行該模組程式碼。</span><span class="sxs-lookup"><span data-stu-id="93c45-144">This situation involves the module code trying to target a number of PowerShell versions, while testing should run it on specific, concrete implementations.</span></span>

## <a name="powershell-nuget-packages-at-a-glance"></a><span data-ttu-id="93c45-145">PowerShell NuGet 套件一覽</span><span class="sxs-lookup"><span data-stu-id="93c45-145">PowerShell NuGet packages at a glance</span></span>

<span data-ttu-id="93c45-146">在本文中，我們會涵蓋公開 PowerShell API 的下列 NuGet 套件：</span><span class="sxs-lookup"><span data-stu-id="93c45-146">In this article, we'll cover the following NuGet packages that expose PowerShell APIs:</span></span>

- <span data-ttu-id="93c45-147">[PowerShellStandard.Library][]，這是一種參考組件，其可供建置可由多個 PowerShell 執行階段載入的單一組件。</span><span class="sxs-lookup"><span data-stu-id="93c45-147">[PowerShellStandard.Library][], a reference assembly that enables building a single assembly that can be loaded by multiple PowerShell runtimes.</span></span>
- <span data-ttu-id="93c45-148">[Microsoft.PowerShell.SDK][]，瞄準及重新裝載整個 PowerShell SDK 的方式</span><span class="sxs-lookup"><span data-stu-id="93c45-148">[Microsoft.PowerShell.SDK][], the way to target and rehost the whole PowerShell SDK</span></span>
- <span data-ttu-id="93c45-149">[System.Management.Automation][] 套件，這是核心 PowerShell 執行階段和引擎實作，在最少裝載實作以及以特定版本為目標的案例中相當實用。</span><span class="sxs-lookup"><span data-stu-id="93c45-149">The [System.Management.Automation][] package, the core PowerShell runtime and engine implementation, that can be useful in minimal hosted implementations and for version-specific targeting scenarios.</span></span>
- <span data-ttu-id="93c45-150">**Windows PowerShell 參考組件**，瞄準及有效重新裝載 Windows PowerShell (PowerShell 版本 5.1 及更早版本) 的方式。</span><span class="sxs-lookup"><span data-stu-id="93c45-150">The **Windows PowerShell reference assemblies**, the way to target and effectively rehost Windows PowerShell (PowerShell versions 5.1 and below).</span></span>

> [!NOTE]
> <span data-ttu-id="93c45-151">[PowerShell NuGet][] 套件完全不是 .NET 程式庫套件，但可提供 PowerShell dotnet 全域工具實作。</span><span class="sxs-lookup"><span data-stu-id="93c45-151">The [PowerShell NuGet][] package is not a .NET library package at all, but instead provides the PowerShell dotnet global tool implementation.</span></span> <span data-ttu-id="93c45-152">此項目不應由任何專案使用，因為其只提供可執行檔。</span><span class="sxs-lookup"><span data-stu-id="93c45-152">This should not be used by any projects, since it only provides an executable.</span></span>

## <a name="powershellstandardlibrary"></a><span data-ttu-id="93c45-153">PowerShellStandard.Library</span><span class="sxs-lookup"><span data-stu-id="93c45-153">PowerShellStandard.Library</span></span>

<span data-ttu-id="93c45-154">PowerShell Standard 程式庫是一種參考組件，其擷取 PowerShell 版本 7、6 及 5.1 API 的交集。</span><span class="sxs-lookup"><span data-stu-id="93c45-154">The PowerShell Standard library is a reference assembly that captures the intersection of the APIs of PowerShell versions 7, 6 and 5.1.</span></span> <span data-ttu-id="93c45-155">此提供編譯時間檢查 API 介面，以針對其編譯 .NET 程式碼，允許 .NET 專案以 PowerShell 版本 7、6 和 5.1 作為目標，而不會有呼叫不存在 API 的風險。</span><span class="sxs-lookup"><span data-stu-id="93c45-155">This provides a compile-time-checked API surface to compile .NET code against, allowing .NET projects to target PowerShell versions 7, 6 and 5.1 without risking calling an API that won't be there.</span></span>

<span data-ttu-id="93c45-156">PowerShell Standard 旨在適用於撰寫 PowerShell 模組，或其他僅旨在載入 PowerShell 處理序後執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="93c45-156">PowerShell Standard is intended for writing PowerShell modules, or other code only intended to be run after loading it into a PowerShell process.</span></span> <span data-ttu-id="93c45-157">由於其為參考組件，PowerShell Standard 本身不包含任何實作，因此不會提供任何標準應用程式的功能。</span><span class="sxs-lookup"><span data-stu-id="93c45-157">Because it is a reference assembly, PowerShell Standard contains no implementation itself, so provides no functionality for standalone applications.</span></span>

### <a name="using-powershell-standard-with-different-net-runtimes"></a><span data-ttu-id="93c45-158">搭配不同的 .NET 執行階段使用 PowerShell Standard</span><span class="sxs-lookup"><span data-stu-id="93c45-158">Using PowerShell Standard with different .NET runtimes</span></span>

<span data-ttu-id="93c45-159">PowerShell Standard 以 [.NET Standard 2.0][] 目標執行階段為目標，這是一種旨在提供 .NET Framework 和 .NET Core 通用介面區的外觀執行階段。</span><span class="sxs-lookup"><span data-stu-id="93c45-159">PowerShell Standard targets the [.NET Standard 2.0][] target runtime, which is a façade runtime designed to provide a common surface area shared by .NET Framework and .NET Core.</span></span> <span data-ttu-id="93c45-160">這會允許以單一執行階段作為目標，以產生可搭配多個 PowerShell 版本使用的單一組件，但會有下列結果：</span><span class="sxs-lookup"><span data-stu-id="93c45-160">This allows targeting a single runtime to produce a single assembly that will work with multiple PowerShell versions, but has the following consequences:</span></span>

- <span data-ttu-id="93c45-161">載入模組或程式庫的 PowerShell 至少必須執行 .NET 4.6.1，.NET 4.6 和 .NET 4.5.2 不支援 .NET Standard。</span><span class="sxs-lookup"><span data-stu-id="93c45-161">The PowerShell loading the module or library must be running a minimum of .NET 4.6.1; .NET 4.6 and .NET 4.5.2 do not support .NET Standard.</span></span> <span data-ttu-id="93c45-162">請注意，更新的 Windows PowerShell 版本並不等同於更新的 .NET Framework 版本；Windows PowerShell 5.1 可能會在 .NET 4.5.2 上執行。</span><span class="sxs-lookup"><span data-stu-id="93c45-162">Note that a newer Windows PowerShell version does not mean a newer .NET Framework version; Windows PowerShell 5.1 may run on .NET 4.5.2.</span></span>
- <span data-ttu-id="93c45-163">若要與執行 .NET Framework 4.7.1 或以下版本的 PowerShell 搭配使用，在較舊的 .NET Framework 版本中，需要 .NET 4.6.1 [NETStandard.Library][] 實作來提供 netstandard.dll 和其他填充碼組件。</span><span class="sxs-lookup"><span data-stu-id="93c45-163">In order to work with a PowerShell running .NET Framework 4.7.1 or below, the .NET 4.6.1 [NETStandard.Library][] implementation is required to provide the netstandard.dll and other shim assemblies in older .NET Framework versions.</span></span>

<span data-ttu-id="93c45-164">PowerShell 6 以上版本會提供其自身的填充碼組件，以將類型從 .NET Framework 4.6.1 (及更新版本) 轉送至 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="93c45-164">PowerShell 6+ provides its own shim assemblies for type forwarding from .NET Framework 4.6.1 (and above) to .NET Core.</span></span> <span data-ttu-id="93c45-165">這表示只要模組僅使用 .NET Core 中存在的 API，PowerShell 6 以上版本即可在為 .NET Framework 4.6.1 (`net461` 執行階段目標) 建置的情況下載入及執行。</span><span class="sxs-lookup"><span data-stu-id="93c45-165">This means that as long as a module uses only APIs that exist in .NET Core, PowerShell 6+ can load and run it when it has been built for .NET Framework 4.6.1 (the `net461` runtime target).</span></span>

<span data-ttu-id="93c45-166">這表示使用 PowerShell Standard，透過單一發佈的 DLL 以多個 PowerShell 版本為目標的二進位模組會有兩個選項：</span><span class="sxs-lookup"><span data-stu-id="93c45-166">This means that binary modules using PowerShell Standard to target multiple PowerShell versions with a single published DLL have two options:</span></span>

1. <span data-ttu-id="93c45-167">發佈為 `net461` 目標執行階段建置的組件。</span><span class="sxs-lookup"><span data-stu-id="93c45-167">Publishing an assembly built for the `net461` target runtime.</span></span> <span data-ttu-id="93c45-168">這包括：</span><span class="sxs-lookup"><span data-stu-id="93c45-168">This involves:</span></span>
   - <span data-ttu-id="93c45-169">為 `net461` 執行階段發佈專案</span><span class="sxs-lookup"><span data-stu-id="93c45-169">Publishing the project for the `net461` runtime</span></span>
   - <span data-ttu-id="93c45-170">同時針對 `netstandard2.0` 執行階段進行編譯 (不使用其建置輸出)，以確保所有使用的 API 也都存在於 .NET Core 中。</span><span class="sxs-lookup"><span data-stu-id="93c45-170">Also compiling against the `netstandard2.0` runtime (without using its build output) to ensure that all APIs used are also present in .NET Core.</span></span>

1. <span data-ttu-id="93c45-171">為 `netstandard2.0` 目標執行階段發佈組件的組建。</span><span class="sxs-lookup"><span data-stu-id="93c45-171">Publishing an assembly build for the `netstandard2.0` target runtime.</span></span> <span data-ttu-id="93c45-172">這需要：</span><span class="sxs-lookup"><span data-stu-id="93c45-172">This requires:</span></span>
   - <span data-ttu-id="93c45-173">為 `netstandard2.0` 執行階段發佈專案</span><span class="sxs-lookup"><span data-stu-id="93c45-173">Publishing the project for the `netstandard2.0` runtime</span></span>
   - <span data-ttu-id="93c45-174">取得 NETStandard.Library 的 `net461` 相依性，並將其複製到專案組件的發佈位置，以在 .NET Framework 中正確地針對組件進行類型轉送。</span><span class="sxs-lookup"><span data-stu-id="93c45-174">Taking the `net461` dependencies of NETStandard.Library and copying them into the project assembly's publish location so that the assembly is type-forwarded corrected in .NET Framework.</span></span>

<span data-ttu-id="93c45-175">若要建置以較舊 .NET Framework 版本為目標的 PowerShell 模組或程式庫，則建議以多個 .NET 執行階段作為目標。</span><span class="sxs-lookup"><span data-stu-id="93c45-175">To build PowerShell modules or libraries targeting older .NET Framework versions, it may be preferable to target multiple .NET runtimes.</span></span> <span data-ttu-id="93c45-176">這將會為每個目標執行階段發佈組件，且將需要在載入模組時載入正確的組件 (例如以小型的 psm1 作為根模組)。</span><span class="sxs-lookup"><span data-stu-id="93c45-176">This will publish an assembly for each target runtime, and the correct assembly will need to be loaded at module load time (for example with a small psm1 as the root module).</span></span>

### <a name="testing-powershell-standard-projects-in-net"></a><span data-ttu-id="93c45-177">在 .NET 中測試 PowerShell Standard 專案</span><span class="sxs-lookup"><span data-stu-id="93c45-177">Testing PowerShell Standard projects in .NET</span></span>

<span data-ttu-id="93c45-178">當想要在 xUnit 等 .NET 測試執行器中測試模組時，請記住編譯時間檢查能帶來的效果有限。</span><span class="sxs-lookup"><span data-stu-id="93c45-178">When it comes to testing your module in .NET test runners like xUnit, remember that compile-time checks can only go so far.</span></span> <span data-ttu-id="93c45-179">您必須針對相關的 PowerShell 平台測試模組。</span><span class="sxs-lookup"><span data-stu-id="93c45-179">You must test your module against the relevant PowerShell platforms.</span></span>

<span data-ttu-id="93c45-180">若要在 .NET 中測試針對 PowerShell Standard 建置的 API，建議新增 `Microsoft.Powershell.SDK` 作為 .NET Core 的測試相依性 (並將版本設為相符於所需 PowerShell 版本)，並針對 .NET Framework 新增適當的 Windows PowerShell 參考組件。</span><span class="sxs-lookup"><span data-stu-id="93c45-180">To test APIs built against PowerShell Standard in .NET, you should add `Microsoft.Powershell.SDK` as a testing dependency with .NET Core (with the version set to match the desired PowerShell version), and the appropriate Windows PowerShell reference assemblies with .NET Framework.</span></span>

<span data-ttu-id="93c45-181">如需 PowerShell Standard 的詳細資訊，以及使用其來撰寫可在多個 PowerShell 版本中運作的二進位模組詳細資訊，請參閱[此部落格文章][]。</span><span class="sxs-lookup"><span data-stu-id="93c45-181">For more information on PowerShell Standard and using it to write a binary module that works in multiple PowerShell versions, see [this blog post][].</span></span> <span data-ttu-id="93c45-182">另請參閱 GitHub 上的 [PowerShell Standard 存放庫][]。</span><span class="sxs-lookup"><span data-stu-id="93c45-182">Also see the [PowerShell Standard repository][] on GitHub.</span></span>

## <a name="microsoftpowershellsdk"></a><span data-ttu-id="93c45-183">Microsoft.PowerShell.SDK</span><span class="sxs-lookup"><span data-stu-id="93c45-183">Microsoft.PowerShell.SDK</span></span>

<span data-ttu-id="93c45-184">`Microsoft.PowerShell.SDK` 是一種中繼套件，這個套件將所有 PowerShell SDK 的元件組合成單一 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="93c45-184">`Microsoft.PowerShell.SDK` is a meta-package that pulls together all of the components of the PowerShell SDK into a single NuGet package.</span></span> <span data-ttu-id="93c45-185">獨立的 .NET 應用程式可使用 Microsoft PowerShell.SDK 來執行任意 PowerShell 功能，而無須依賴任何外部 PowerShell 安裝或程式庫。</span><span class="sxs-lookup"><span data-stu-id="93c45-185">A self-contained .NET application can use Microsoft.PowerShell.SDK to run arbitrary PowerShell functionality without depending on any external PowerShell installations or libraries.</span></span>

> [!NOTE]
> <span data-ttu-id="93c45-186">PowerShell SDK 會直接參考構成 PowerShell 的所有元件套件，以及可用於搭配 PowerShell 進行 .NET 開發的套件。</span><span class="sxs-lookup"><span data-stu-id="93c45-186">The PowerShell SDK just refers to all the component packages that make up PowerShell, and which can be used for .NET development with PowerShell.</span></span>

<span data-ttu-id="93c45-187">指定的 `Microsoft.Powershell.SDK` 版本包含相同版本 PowerShell 應用程式的具體實作；版本 7.0 包含 PowerShell 7.0 的實作，且使用其來執行命令或指令碼就如同在 PowerShell 7.0 中執行這些命令或指令碼。</span><span class="sxs-lookup"><span data-stu-id="93c45-187">A given `Microsoft.Powershell.SDK` version contains the concrete implementation of the same version of the PowerShell application; version 7.0 contains the implementation of PowerShell 7.0 and running commands or scripts with it will largely behave like running them in PowerShell 7.0.</span></span>

<span data-ttu-id="93c45-188">從 SDK 執行 PowerShell 命令大部分 (但不全是) 都和在 `pwsh` 中執行命令相同。</span><span class="sxs-lookup"><span data-stu-id="93c45-188">Running PowerShell commands from the SDK is mostly, but not totally, the same as running them from `pwsh`.</span></span> <span data-ttu-id="93c45-189">例如，[Start-Job][] 目前依賴可用的 `pwsh` 可執行檔，因此根據預設無法和 `Microsoft.Powershell.SDK` 搭配運作。</span><span class="sxs-lookup"><span data-stu-id="93c45-189">For example, [Start-Job][] currently depends on the `pwsh` executable being available, and so will not work with `Microsoft.Powershell.SDK` by default.</span></span>

<span data-ttu-id="93c45-190">從 .NET 應用程式以 `Microsoft.Powershell.SDK` 作為目標，可供和所有 PowerShell 的實作組件整合，例如 `System.Management.Automation`、`Microsoft.PowerShell.Management` 和其他模組組件。</span><span class="sxs-lookup"><span data-stu-id="93c45-190">Targeting `Microsoft.Powershell.SDK` from a .NET application allows you to integrate with all of PowerShell's implementation assemblies, such as `System.Management.Automation`, `Microsoft.PowerShell.Management`, and other module assemblies.</span></span>

<span data-ttu-id="93c45-191">發佈以 `Microsoft.Powershell.SDK` 作為目標的應用程式將會包含所有這些組件，以及任何 PowerShell 需要的相依性。</span><span class="sxs-lookup"><span data-stu-id="93c45-191">Publishing an application targeting `Microsoft.Powershell.SDK` will include all these assemblies, and any dependencies PowerShell requires.</span></span> <span data-ttu-id="93c45-192">這也會包含其他 PowerShell 在其組建中需要的資產，例如 `Microsoft.PowerShell.*` 模組的模組資訊清單，以及 [Add-Type][] 需要的 `ref` 目錄。</span><span class="sxs-lookup"><span data-stu-id="93c45-192">It will also include other assets that PowerShell required in its build, such as the module manifests for `Microsoft.PowerShell.*` modules and the `ref` directory required by [Add-Type][].</span></span>

<span data-ttu-id="93c45-193">基於 `Microsoft.Powershell.SDK` 的完整性，其最適合用於：</span><span class="sxs-lookup"><span data-stu-id="93c45-193">Given the completeness of `Microsoft.Powershell.SDK`, it's best suited for:</span></span>

- <span data-ttu-id="93c45-194">PowerShell 主機的實作。</span><span class="sxs-lookup"><span data-stu-id="93c45-194">Implementation of PowerShell hosts.</span></span>
- <span data-ttu-id="93c45-195">以 PowerShell 參考組件作為目標的程式庫 xUnit 測試。</span><span class="sxs-lookup"><span data-stu-id="93c45-195">xUnit testing of libraries targeting PowerShell reference assemblies.</span></span>
- <span data-ttu-id="93c45-196">從 .NET 應用程式的處理序中叫用 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="93c45-196">Invoking PowerShell in-process from a .NET application.</span></span>

<span data-ttu-id="93c45-197">`Microsoft.PowerShell.SDK` 也可以在 .NET 專案旨在用來作為模組，或會由 PowerShell 載入，但是依賴只存在於特定 PowerShell 版本中的 API 時，作為參考目標使用。</span><span class="sxs-lookup"><span data-stu-id="93c45-197">`Microsoft.PowerShell.SDK` may also be used as a reference target when a .NET project is intended to be used as a module or otherwise loaded by PowerShell, but depends on APIs only present in a particular version of PowerShell.</span></span> <span data-ttu-id="93c45-198">請注意，針對特定 `Microsoft.PowerShell.SDK` 版本所發佈組件只有在於該版本的 PowerShell 中載入及使用時才安全。</span><span class="sxs-lookup"><span data-stu-id="93c45-198">Note that an assembly published against a specific version of `Microsoft.PowerShell.SDK` will only be safe to load and use in that version of PowerShell.</span></span> <span data-ttu-id="93c45-199">若要以具備特定 API 的多個 PowerShell 版本作為目標，則需要多個組建，且每個組建都會以其自身的 `Microsoft.Powershell.SDK` 版本作為目標。</span><span class="sxs-lookup"><span data-stu-id="93c45-199">To target multiple PowerShell versions with specific APIs, multiple builds are required, each targeting their own version of `Microsoft.Powershell.SDK`.</span></span>

> [!NOTE]
> <span data-ttu-id="93c45-200">PowerShell SDK 僅提供 PowerShell 6 以上版本使用。</span><span class="sxs-lookup"><span data-stu-id="93c45-200">The PowerShell SDK is only available for PowerShell versions 6 and up.</span></span> <span data-ttu-id="93c45-201">若要透過 Windows PowerShell 提供相等的功能，請使用以下所述的 Windows PowerShell 參考組件。</span><span class="sxs-lookup"><span data-stu-id="93c45-201">To provide equivalent functionality with Windows PowerShell, use the Windows PowerShell reference assemblies described below.</span></span>

## <a name="systemmanagementautomation"></a><span data-ttu-id="93c45-202">System.Management.Automation</span><span class="sxs-lookup"><span data-stu-id="93c45-202">System.Management.Automation</span></span>

<span data-ttu-id="93c45-203">`System.Management.Automation` 套件是 PowerShell SDK 的核心。</span><span class="sxs-lookup"><span data-stu-id="93c45-203">The `System.Management.Automation` package is the heart of the PowerShell SDK.</span></span> <span data-ttu-id="93c45-204">其存在於 NuGet 上，主要作為 `Microsoft.Powershell.SDK` 提取的資產。</span><span class="sxs-lookup"><span data-stu-id="93c45-204">It exists on NuGet, primarily, as an asset for `Microsoft.Powershell.SDK` to pull in.</span></span> <span data-ttu-id="93c45-205">但是，其也可以直接用來作為較小裝載案例和瞄準版本模組的套件。</span><span class="sxs-lookup"><span data-stu-id="93c45-205">However, it can also be used directly as a package for smaller hosting scenarios and version-targeting modules.</span></span>

<span data-ttu-id="93c45-206">具體而言，`System.Management.Automation` 套件可能會是以下情況的偏好 PowerShell 功能提供者：</span><span class="sxs-lookup"><span data-stu-id="93c45-206">Specifically, the `System.Management.Automation` package may be a preferable provider of PowerShell functionality when:</span></span>

- <span data-ttu-id="93c45-207">您只想要使用 PowerShell 語言功能 (位於 `System.Management.Automation.Language` 命名空間)，例如 PowerShell 剖析器、AST，以及 AST 訪客 API (例如 PowerShell 的靜態分析)。</span><span class="sxs-lookup"><span data-stu-id="93c45-207">You're only looking to use PowerShell language functionality (in the `System.Management.Automation.Language` namespace) like the PowerShell parser, AST, and AST visitor APIs (for example for static analysis of PowerShell).</span></span>
- <span data-ttu-id="93c45-208">您只想要執行 `Microsoft.PowerShell.Core` 模組中的特定命令，且可在使用 [CreateDefault2][] Factory 方法建立的工作階段狀態中執行。</span><span class="sxs-lookup"><span data-stu-id="93c45-208">You only wish to execute specific commands from the `Microsoft.PowerShell.Core` module and can execute them in a session state created with the [CreateDefault2][] factory method.</span></span>

<span data-ttu-id="93c45-209">此外，`System.Management.Automation` 也是以下情況的實用參考組件：</span><span class="sxs-lookup"><span data-stu-id="93c45-209">Additionally, `System.Management.Automation` is a useful reference assembly when:</span></span>

- <span data-ttu-id="93c45-210">您想要以只在特定 PowerShell 版本中存在的 API 作為目標</span><span class="sxs-lookup"><span data-stu-id="93c45-210">You wish to target APIs that are only present within a specific PowerShell version</span></span>
- <span data-ttu-id="93c45-211">您不會依賴在 `System.Management.Automation` 組件外部發生的類型 (例如由 `Microsoft.PowerShell.*` 模組中 Cmdlet 匯出的類型)。</span><span class="sxs-lookup"><span data-stu-id="93c45-211">You won't be depending on types occurring outside the `System.Management.Automation` assembly (for example, types exported by cmdlets in `Microsoft.PowerShell.*` modules).</span></span>

## <a name="windows-powershell-reference-assemblies"></a><span data-ttu-id="93c45-212">Windows PowerShell 參考組件</span><span class="sxs-lookup"><span data-stu-id="93c45-212">Windows PowerShell reference assemblies</span></span>

<span data-ttu-id="93c45-213">針對 PowerShell 版本 5.1 及更早版本 (Windows PowerShell)，沒有 SDK 提供 PowerShell 的實作，因為 Windows PowerShell 的實作是 Windows 的一部分。</span><span class="sxs-lookup"><span data-stu-id="93c45-213">For PowerShell versions 5.1 and older (Windows PowerShell), there is no SDK to provide an implementation of PowerShell, since Windows PowerShell's implementation is a part of Windows.</span></span>

<span data-ttu-id="93c45-214">相反地，Windows PowerShell 參考組件提供參考目標以及重新裝載 Windows PowerShell 的方式，其運作方式與 PowerShell SDK 為版本 6 及更新版本執行的工作相同。</span><span class="sxs-lookup"><span data-stu-id="93c45-214">Instead, the Windows PowerShell reference assemblies provide both reference targets and a way to rehost Windows PowerShell, acting the same as the PowerShell SDK does for versions 6 and up.</span></span>

<span data-ttu-id="93c45-215">Windows PowerShell 參考組件針對每個 Windows PowerShell 版本皆有不同的套件，而非以版本進行區別：</span><span class="sxs-lookup"><span data-stu-id="93c45-215">Rather than being differentiated by version, Windows PowerShell reference assemblies have a different package for each version of Windows PowerShell:</span></span>

- [<span data-ttu-id="93c45-216">PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="93c45-216">PowerShell 5.1</span></span>](https://www.nuget.org/packages/Microsoft.PowerShell.5.ReferenceAssemblies/)
- [<span data-ttu-id="93c45-217">PowerShell 4</span><span class="sxs-lookup"><span data-stu-id="93c45-217">PowerShell 4</span></span>](https://www.nuget.org/packages/Microsoft.PowerShell.4.ReferenceAssemblies/)
- [<span data-ttu-id="93c45-218">PowerShell 3</span><span class="sxs-lookup"><span data-stu-id="93c45-218">PowerShell 3</span></span>](https://www.nuget.org/packages/Microsoft.PowerShell.3.ReferenceAssemblies/)

<span data-ttu-id="93c45-219">您可在 [Windows PowerShell SDK][] 中找到如何使用 Windows PowerShell 參考組件的資訊。</span><span class="sxs-lookup"><span data-stu-id="93c45-219">Information on how to use the Windows PowerShell reference assemblies can be found in the [Windows PowerShell SDK][].</span></span>

## <a name="real-world-examples-using-these-nuget-packages"></a><span data-ttu-id="93c45-220">使用這些 NuGet 套件的真實世界範例</span><span class="sxs-lookup"><span data-stu-id="93c45-220">Real-world examples using these NuGet packages</span></span>

<span data-ttu-id="93c45-221">取決於其需求，不同的 PowerShell 工具專案會以不同 PowerShell NuGet 套件作為目標。</span><span class="sxs-lookup"><span data-stu-id="93c45-221">Different PowerShell tooling projects target different PowerShell NuGet packages depending on their needs.</span></span> <span data-ttu-id="93c45-222">以下列出的是一些知名範例。</span><span class="sxs-lookup"><span data-stu-id="93c45-222">Listed here are some notable examples.</span></span>

### <a name="psreadline"></a><span data-ttu-id="93c45-223">PSReadLine</span><span class="sxs-lookup"><span data-stu-id="93c45-223">PSReadLine</span></span>

<span data-ttu-id="93c45-224">[PSReadLine][] 是一種 PowerShell 模組，其提供許多 PowerShell 的豐富主控台體驗，以 PowerShell Standard 而非特定 PowerShell 版本作為相依性，並在其 [csproj][] 中以 `net461` .NET 執行階段作為目標。</span><span class="sxs-lookup"><span data-stu-id="93c45-224">[PSReadLine][], the PowerShell module that provides much of PowerShell's rich console experience, targets PowerShell Standard as a dependency rather than a specific PowerShell version, and targets the `net461` .NET runtime in its [csproj][].</span></span>

<span data-ttu-id="93c45-225">PowerShell 6 以上版本會提供其自身的填充碼組件，允許以 `net461` 執行階段作為目標的 DLL 在載入時「正常運作」(其方式為將 .NET Framework `mscorlib.dll` 的繫結重新導向到相關的 .NET Core 組件)。</span><span class="sxs-lookup"><span data-stu-id="93c45-225">PowerShell 6+ supplies its own shim assemblies that allow a DLL targeting the `net461` runtime to "just work" when loaded in (by redirecting binding to .NET Framework's `mscorlib.dll` to the relevant .NET Core assembly).</span></span>

<span data-ttu-id="93c45-226">這大幅簡化 PSReadLine 模組的配置和傳遞，因為 PowerShell Standard 會確保使用的 API 都存在於 Power 5.1 和 PowerShell 6.0，同時也允許僅透過單一組件來傳遞模組。</span><span class="sxs-lookup"><span data-stu-id="93c45-226">This simplifies PSReadLine's module layout and delivery significantly, since PowerShell Standard ensures the only APIs used will be present in both PowerShell 5.1 and PowerShell 6+, while also allowing the module to ship with only a single assembly.</span></span>

<span data-ttu-id="93c45-227">雖然 .NET 4.6.1 目標表示其不支援在 .NET 4.5.2 和 .NET 4.6 上執行的 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="93c45-227">The .NET 4.6.1 target does mean that Windows PowerShell running on .NET 4.5.2 and .NET 4.6 is not supported though.</span></span>

### <a name="powershell-editor-services"></a><span data-ttu-id="93c45-228">PowerShell 編輯器服務</span><span class="sxs-lookup"><span data-stu-id="93c45-228">PowerShell Editor Services</span></span>

<span data-ttu-id="93c45-229">[PowerShell 編輯器服務][] (PSES) 是 [Visual Studio Code][] [PowerShell 延伸模組][]的後端，其實際上是一種由 PowerShell 可執行檔載入，並接管該處理序來在其內部重新裝載 PowerShell，同時提供語言服務通訊協定及偵錯配接器功能的 PowerShell 模組形式。</span><span class="sxs-lookup"><span data-stu-id="93c45-229">[PowerShell Editor Services][] (PSES) is the backend for the [PowerShell extension][] for [Visual Studio Code][], and is actually a form of PowerShell module that gets loaded by a PowerShell executable and then takes over that process to rehost PowerShell within itself while also providing Language Service Protocol and Debug Adapter features.</span></span>

<span data-ttu-id="93c45-230">PSES 提供 `netcoreapp2.1` 的具體實作目標來以 PowerShell 6 以上版本作為目標 (因為 PowerShell 7 的 `netcoreapp3.1` 執行階段具備回溯相容性)，並提供 `net461` 來以 Windows PowerShell 5.1 作為目標，但在第二個以 `netstandard2.0` 和 PowerShell Standard 作為目標的組件中包含大多數的邏輯。</span><span class="sxs-lookup"><span data-stu-id="93c45-230">PSES provides concrete implementation targets for `netcoreapp2.1` to target PowerShell 6+ (since PowerShell 7's `netcoreapp3.1` runtime is backwards compatible) and `net461` to target Windows PowerShell 5.1, but contains most of its logic in a second assembly that targets `netstandard2.0` and PowerShell Standard.</span></span> <span data-ttu-id="93c45-231">這可讓其提取 .NET Core 和 .NET Framework 平台需要的相依性，同時透過統一的抽象化來簡化大多數程式碼基底。</span><span class="sxs-lookup"><span data-stu-id="93c45-231">This allows it to pull in dependencies required for .NET Core and .NET Framework platforms, while still simplifying most of the codebase behind a uniform abstraction.</span></span>

<span data-ttu-id="93c45-232">由於其是針對 PowerShell Standard 所建置，因此 PSES 需要 PowerShell 的執行階段實作，才能正確地進行測試。</span><span class="sxs-lookup"><span data-stu-id="93c45-232">Because it is built against PowerShell Standard, PSES requires a runtime implementation of PowerShell in order to be tested correctly.</span></span> <span data-ttu-id="93c45-233">為了執行這項操作，[PSES 的 xUnit][] 測試會提取 `Microsoft.PowerShell.SDK` 和 `Microsoft.PowerShell.5.ReferenceAssemblies`，來在測試環境中提供 PowerShell 實作。</span><span class="sxs-lookup"><span data-stu-id="93c45-233">To do this, [PSES's xUnit][] tests pull in `Microsoft.PowerShell.SDK` and `Microsoft.PowerShell.5.ReferenceAssemblies` in order to provide a PowerShell implementation in the test environment.</span></span>

<span data-ttu-id="93c45-234">如同 PSReadLine，PSES 無法支援 .NET 4.6 及更早版本，但其會在呼叫任何可能會在較低 .NET Framework 執行階段中造成損毀的 API 之前，於執行階段[執行檢查][]。</span><span class="sxs-lookup"><span data-stu-id="93c45-234">As with PSReadLine, PSES cannot support .NET 4.6 and below, but it [performs a check][] at runtime before calling any of the APIs that could cause a crash on the lower .NET Framework runtimes.</span></span>

### <a name="psscriptanalyzer"></a><span data-ttu-id="93c45-235">PSScriptAnalyzer</span><span class="sxs-lookup"><span data-stu-id="93c45-235">PSScriptAnalyzer</span></span>

<span data-ttu-id="93c45-236">[PSScriptAnalyzer][]是 PowerShell 的 Linter，其必須以在特定 PowerShell 版本中引進的語法項目作為目標。</span><span class="sxs-lookup"><span data-stu-id="93c45-236">[PSScriptAnalyzer][], the linter for PowerShell, must target syntactic elements only introduced in certain versions of PowerShell.</span></span> <span data-ttu-id="93c45-237">由於識別這些語法項目的方式是透過實作 [AstVisitor2][]，因此其無法在使用 PowerShellStandard 的同時為 PowerShell 較新語法實作 AST 訪客方法。</span><span class="sxs-lookup"><span data-stu-id="93c45-237">Because recognition of these syntactic elements is accomplished by implementing an [AstVisitor2][], it's not possible to use PowerShellStandard and also implement AST visitor methods for newer PowerShell syntaxes.</span></span>

<span data-ttu-id="93c45-238">相反地，PSScriptAnalyzer 的組建組態[會以每個 PowerShell 版本作為目標][]，並為每個版本產生個別的 DLL。</span><span class="sxs-lookup"><span data-stu-id="93c45-238">Instead, PSScriptAnalyzer [targets each PowerShell version][] as a build configuration, and produces a separate DLL for each of them.</span></span> <span data-ttu-id="93c45-239">這會增加組建的大小和複雜度，但允許：</span><span class="sxs-lookup"><span data-stu-id="93c45-239">This increases build size and complexity, but allows:</span></span>

- <span data-ttu-id="93c45-240">以特定版本的 API 作為目標</span><span class="sxs-lookup"><span data-stu-id="93c45-240">Version-specific API targeting</span></span>
- <span data-ttu-id="93c45-241">在基本上沒有任何執行階段成本的情況下實作版本特定功能</span><span class="sxs-lookup"><span data-stu-id="93c45-241">Version-specific functionality to be implemented with essentially no runtime cost</span></span>
- <span data-ttu-id="93c45-242">直到 Windows PowerShell 到 .NET Framework 4.5.2 的整體支援</span><span class="sxs-lookup"><span data-stu-id="93c45-242">Total support for Windows PowerShell all the way down to .NET Framework 4.5.2</span></span>

## <a name="summary"></a><span data-ttu-id="93c45-243">摘要</span><span class="sxs-lookup"><span data-stu-id="93c45-243">Summary</span></span>

<span data-ttu-id="93c45-244">在本文中，我們已列出和討論了作為目標的 NuGet 套件 (在實作使用 PowerShell 的 .NET 專案時)，以及您可能會使用其中一個套件而非另一個套件的原因。</span><span class="sxs-lookup"><span data-stu-id="93c45-244">In this article, we've listed and discussed the NuGet packages available to target when implementing a .NET project that uses PowerShell, and the reasons you might have for using one over another.</span></span>

<span data-ttu-id="93c45-245">若您已跳到摘要，一些廣義的建議包括：</span><span class="sxs-lookup"><span data-stu-id="93c45-245">If you've skipped to the summary, some broad recommendations are:</span></span>

- <span data-ttu-id="93c45-246">PowerShell **模組**如果只需要不同 PowerShell 版本通用的 API，則應針對 PowerShell Standard 進行編譯。</span><span class="sxs-lookup"><span data-stu-id="93c45-246">PowerShell **modules** should compile against PowerShell Standard if they only require APIs common to different PowerShell versions.</span></span>
- <span data-ttu-id="93c45-247">需要在內部執行 PowerShell 的 PowerShell **主機和應用程式**，其應針對 PowerShell 6 以上版本以 PowerShell SDK 作為目標，或針對 Windows PowerShell 以相關 Windows PowerShell 參考組件作為目標。</span><span class="sxs-lookup"><span data-stu-id="93c45-247">PowerShell **hosts and applications** that need to run PowerShell internally should target the PowerShell SDK for PowerShell 6+ or the relevant Windows PowerShell reference assemblies for Windows PowerShell.</span></span>
- <span data-ttu-id="93c45-248">需要**版本特定 API** 的 PowerShell 模組應針對 PowerShell 必要版本，以 PowerShell SDK 或 Windows PowerShell 參考組件作為目標 (將其作為參考組件使用，即不發佈 PowerShell 相依性)。</span><span class="sxs-lookup"><span data-stu-id="93c45-248">PowerShell modules that need **version-specific APIs** should target the PowerShell SDK or Windows PowerShell reference assemblies for the required PowerShell versions, using them as reference assemblies (that is, not publishing the PowerShell dependencies).</span></span>

<!--link references -->

[.NET Standard 2.0]: /dotnet/standard/net-standard
[about_Modules]: /powershell/module/microsoft.powershell.core/about/about_modules
[Add-Type]: /powershell/module/microsoft.powershell.utility/add-type
[AstVisitor2]: /dotnet/api/system.management.automation.language.astvisitor2
[CmdletProvider]: /dotnet/api/system.management.automation.provider.cmdletprovider
[CreateDefault2]: /dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2
[csproj]: https://github.com/PowerShell/PSReadLine/blob/master/PSReadLine/PSReadLine.csproj
[Microsoft.PowerShell.SDK]: https://www.nuget.org/packages/Microsoft.PowerShell.SDK/
[NETStandard.Library]: https://www.nuget.org/packages/NETStandard.Library/
[NuGet]: https://www.nuget.org/
[執行檢查]: https://github.com/PowerShell/PowerShellEditorServices/blob/8c500ee1752201d3c1cc2e5d90f1a2af3b1eb15d/src/PowerShellEditorServices.Hosting/EditorServicesLoader.cs#L231-L251
[performs a check]: https://github.com/PowerShell/PowerShellEditorServices/blob/8c500ee1752201d3c1cc2e5d90f1a2af3b1eb15d/src/PowerShellEditorServices.Hosting/EditorServicesLoader.cs#L231-L251
[Pester]: https://github.com/Pester/Pester
[PowerShell 編輯器服務]: https://github.com/PowerShell/PowerShellEditorServices/
[PowerShell Editor Services]: https://github.com/PowerShell/PowerShellEditorServices/
[PowerShell 延伸模組]: https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell
[PowerShell extension]: https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell
[PowerShell NuGet]: https://www.nuget.org/packages/PowerShell/
[PowerShell Standard 存放庫]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard repository]: https://github.com/PowerShell/PowerShellStandard
[PowerShellStandard.Library]: https://www.nuget.org/packages/PowerShellStandard.Library/
[PSCmdlet]: /dotnet/api/system.management.automation.pscmdlet
[PSES 的 xUnit]: https://github.com/PowerShell/PowerShellEditorServices/blob/8c500ee1752201d3c1cc2e5d90f1a2af3b1eb15d/test/PowerShellEditorServices.Test/PowerShellEditorServices.Test.csproj#L15-L20
[PSES's xUnit]: https://github.com/PowerShell/PowerShellEditorServices/blob/8c500ee1752201d3c1cc2e5d90f1a2af3b1eb15d/test/PowerShellEditorServices.Test/PowerShellEditorServices.Test.csproj#L15-L20
[PSHost]: /dotnet/api/system.management.automation.host.pshost
[PrivateAssets 屬性]: /dotnet/core/tools/csproj#packagereference
[PrivateAssets attribute]: /dotnet/core/tools/csproj#packagereference
[PSReadLine]: https://github.com/PowerShell/PSReadLine
[PSScriptAnalyzer]: https://github.com/powershell/psscriptanalyzer
[參考組件]: https://github.com/dotnet/standard/blob/master/docs/history/evolution-of-design-time-assemblies.md#definitions
[reference assemblies]: https://github.com/dotnet/standard/blob/master/docs/history/evolution-of-design-time-assemblies.md#definitions
[Start-Job]: /powershell/module/microsoft.powershell.core/start-job
[System.Management.Automation]: https://www.nuget.org/packages/System.Management.Automation/
[以每個 PowerShell 版本作為目標]: https://github.com/PowerShell/PSScriptAnalyzer/blob/master/Engine/Engine.csproj
[targets each PowerShell version]: https://github.com/PowerShell/PSScriptAnalyzer/blob/master/Engine/Engine.csproj
[此部落格文章]: https://devblogs.microsoft.com/powershell/powershell-standard-library-build-single-module-that-works-across-windows-powershell-and-powershell-core/
[this blog post]: https://devblogs.microsoft.com/powershell/powershell-standard-library-build-single-module-that-works-across-windows-powershell-and-powershell-core/
[Visual Studio Code]: https://code.visualstudio.com/
[Windows PowerShell SDK]: /powershell/scripting/developer/windows-powershell
