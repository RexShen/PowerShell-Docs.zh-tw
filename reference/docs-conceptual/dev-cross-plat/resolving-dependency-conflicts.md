---
title: 解析 PowerShell 模組組件的相依性衝突
description: 使用 C# 撰寫二進位 PowerShell 模組時，為提供功能而相依於其他套件或程式庫是很自然的事。
ms.date: 06/25/2020
ms.custom: rjmholt
ms.openlocfilehash: 536bcfd1ced536faccde0d6c5bc483cdaf31ce68
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87775174"
---
# <a name="resolving-powershell-module-assembly-dependency-conflicts"></a><span data-ttu-id="02cb6-103">解析 PowerShell 模組組件的相依性衝突</span><span class="sxs-lookup"><span data-stu-id="02cb6-103">Resolving PowerShell module assembly dependency conflicts</span></span>

<span data-ttu-id="02cb6-104">使用 C# 撰寫二進位 PowerShell 模組時，為提供功能而相依於其他套件或程式庫是很自然的事。</span><span class="sxs-lookup"><span data-stu-id="02cb6-104">When writing a binary PowerShell module in C#, it's natural to take dependencies on other packages or libraries to provide functionality.</span></span> <span data-ttu-id="02cb6-105">為重複使用程式碼需要相依於其他程式庫。</span><span class="sxs-lookup"><span data-stu-id="02cb6-105">Taking dependencies on other libraries is desirable for code reuse.</span></span> <span data-ttu-id="02cb6-106">PowerShell 一律會將組件載入相同的內容中。</span><span class="sxs-lookup"><span data-stu-id="02cb6-106">PowerShell always loads assemblies into the same context.</span></span> <span data-ttu-id="02cb6-107">當模組的相依性與已載入 DLL 發生衝突，且會阻礙同一 PowerShell 工作階段使用其他兩個不相關的模組時，就會發生問題。</span><span class="sxs-lookup"><span data-stu-id="02cb6-107">This presents issues when a module's dependencies conflict with already-loaded DLLs and may prevent using two otherwise unrelated modules in the same PowerShell session.</span></span>

<span data-ttu-id="02cb6-108">如果遇到這個問題，即會看到類似下面的錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="02cb6-108">If you've had this problem, you've seen an error message like this:</span></span>

![組件載入衝突錯誤訊息](./media/resolving-dependency-conflicts/moduleconflict.png)

<span data-ttu-id="02cb6-110">本文會探討 PowerShell 發生相依性衝突的一些方式，以及減輕相依性衝突問題的方式。</span><span class="sxs-lookup"><span data-stu-id="02cb6-110">This article looks at some of the ways dependency conflicts occur in PowerShell and ways to mitigate dependency conflict issues.</span></span> <span data-ttu-id="02cb6-111">即使您不是模組作者，文中還是有一些訣竅可有助解析所用模組的相依性衝突。</span><span class="sxs-lookup"><span data-stu-id="02cb6-111">Even if you're not a module author, there are some tricks in here that might help you with dependency conflicts occurring in modules that you use.</span></span>

## <a name="why-do-dependency-conflicts-occur"></a><span data-ttu-id="02cb6-112">為何會發生相依性衝突？</span><span class="sxs-lookup"><span data-stu-id="02cb6-112">Why do dependency conflicts occur?</span></span>

<span data-ttu-id="02cb6-113">在 .NET 中，當兩個版本的相同組件載入至同一「組件載入內容」時，就會發生相依性衝突。</span><span class="sxs-lookup"><span data-stu-id="02cb6-113">In .NET, dependency conflicts occur when two versions of the same assembly are loaded into the same _Assembly Load Context_.</span></span> <span data-ttu-id="02cb6-114">這個字詞表示不同 .NET 平台上略微不同的東西，[後文](#powershell-and-net)會加以討論。</span><span class="sxs-lookup"><span data-stu-id="02cb6-114">This term means slightly different things on different .NET platforms, which is covered [later](#powershell-and-net).</span></span> <span data-ttu-id="02cb6-115">這是所有使用版本相依性的軟體其常見衝突。</span><span class="sxs-lookup"><span data-stu-id="02cb6-115">This conflict is a common problem that occurs in any software where versioned dependencies are used.</span></span> <span data-ttu-id="02cb6-116">因為沒有簡單的解決方案，而許多相依性解析架構都會使用不同的方式來嘗試解決問題，所以這種情況通常稱為「相依性地獄」。</span><span class="sxs-lookup"><span data-stu-id="02cb6-116">Because there are no simple solutions, and because many dependency-resolution frameworks try to solve the problem in different ways, this situation is often called "dependency hell".</span></span>

<span data-ttu-id="02cb6-117">衝突問題之所以複雜，是因為專案幾乎不會刻意或直接相依於兩個版本的同一相依性，</span><span class="sxs-lookup"><span data-stu-id="02cb6-117">Conflict issues are compounded by the fact that a project almost never deliberately or directly depends on two versions of the same dependency.</span></span> <span data-ttu-id="02cb6-118">而是專案有兩個或以上的相依性，各自又都需要不同版本的相同相依性。</span><span class="sxs-lookup"><span data-stu-id="02cb6-118">Instead, the project has two or more dependencies that each require a different version of the same dependency.</span></span>

<span data-ttu-id="02cb6-119">例如，假設 .NET 應用程式 `DuckBuilder` 引進兩個相依性來執行部分的功能，且看起來如下：</span><span class="sxs-lookup"><span data-stu-id="02cb6-119">For example, say your .NET application, `DuckBuilder`, brings in two dependencies, to perform parts of its functionality and looks like this:</span></span>

![DuckBuilder 其兩個相依性依賴不同版本的 Newtonsoft.Json](./media/resolving-dependency-conflicts/dep-conflict.jpg)

<span data-ttu-id="02cb6-121">因為 `Contoso.ZipTools` 和 `Fabrikam.FileHelpers` 都相依於不同版本的 `Newtonsoft.Json`，所以可能會有相依性衝突，視每個相依性的載入方式而定。</span><span class="sxs-lookup"><span data-stu-id="02cb6-121">Because `Contoso.ZipTools` and `Fabrikam.FileHelpers` both depend on different versions of `Newtonsoft.Json`, there may be a dependency conflict depending on how each dependency is loaded.</span></span>

### <a name="conflicting-with-powershells-dependencies"></a><span data-ttu-id="02cb6-122">與 PowerShell 的相依性發生衝突</span><span class="sxs-lookup"><span data-stu-id="02cb6-122">Conflicting with PowerShell's dependencies</span></span>

<span data-ttu-id="02cb6-123">在 PowerShell 中，相依性衝突問題會因為 PowerShell 模組和 PowerShell 本身的相依性載入至同一共用內容而放大。</span><span class="sxs-lookup"><span data-stu-id="02cb6-123">In PowerShell, the dependency conflict issue is magnified because PowerShell modules and PowerShell's own dependencies are loaded into the same shared context.</span></span> <span data-ttu-id="02cb6-124">這表示 PowerShell 引擎和所載入 PowerShell 全部模組絕不能有衝突的相依性。</span><span class="sxs-lookup"><span data-stu-id="02cb6-124">This means the PowerShell engine and all loaded PowerShell modules must not have conflicting dependencies.</span></span> <span data-ttu-id="02cb6-125">`Newtonsoft.Json` 即為典型的範例：</span><span class="sxs-lookup"><span data-stu-id="02cb6-125">A classic example of this is `Newtonsoft.Json`:</span></span>

![FictionalTools 模組相依於較新版的 Newtonsoft.Json，而不是 PowerShell](./media/resolving-dependency-conflicts/engine-conflict.jpg)

<span data-ttu-id="02cb6-127">在此範例中，模組 `FictionalTools` 相依於 `12.0.3` 版的 `Newtonsoft.Json`，這個 `Newtonsoft.Json` 版本比範例 PowerShell 所附的 `11.0.2` 版本更新。</span><span class="sxs-lookup"><span data-stu-id="02cb6-127">In this example, the module `FictionalTools` depends on `Newtonsoft.Json` version `12.0.3`, which is a newer version of `Newtonsoft.Json` than `11.0.2` that ships in the example PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="02cb6-128">此為範例，PowerShell 7 目前所附的版本為 `Newtonsoft.Json 12.0.3`。</span><span class="sxs-lookup"><span data-stu-id="02cb6-128">This is an example and PowerShell 7 currently ships with `Newtonsoft.Json 12.0.3`.</span></span>

<span data-ttu-id="02cb6-129">因為模組相依於較新版本的組件，所以不接受 PowerShell 已載入的版本。</span><span class="sxs-lookup"><span data-stu-id="02cb6-129">Because the module depends on a newer version of the assembly, it won't accept the version that PowerShell already has loaded.</span></span> <span data-ttu-id="02cb6-130">但因 PowerShell 已載入組件的某個版本，所以模組無法使用傳統載入機制來載入自己的版本。</span><span class="sxs-lookup"><span data-stu-id="02cb6-130">But because PowerShell has already loaded a version of the assembly, the module can't load its own version using the conventional load mechanism.</span></span>

### <a name="conflicting-with-another-modules-dependencies"></a><span data-ttu-id="02cb6-131">與另一個模組的相依性發生衝突</span><span class="sxs-lookup"><span data-stu-id="02cb6-131">Conflicting with another module's dependencies</span></span>

<span data-ttu-id="02cb6-132">PowerShell 中另一個常見案例就是所載入模組相依於組件的某個版本，但稍後另一個載入模組相依於該組件的不同版本。</span><span class="sxs-lookup"><span data-stu-id="02cb6-132">Another common scenario in PowerShell is that a module is loaded that depends on one version of an assembly, and then another module is loaded later that depends on a different version of that assembly.</span></span>

<span data-ttu-id="02cb6-133">通常看起來如下：</span><span class="sxs-lookup"><span data-stu-id="02cb6-133">This often looks like the following:</span></span>

![兩個 PowerShell 模組需要不同版本的 Microsoft.Extensions.Logging 相依性](./media/resolving-dependency-conflicts/mod-conflict.jpg)

<span data-ttu-id="02cb6-135">在本例中，`FictionalTools` 模組需要比 `FilesystemManager` 模組更新版本的 `Microsoft.Extensions.Logging`。</span><span class="sxs-lookup"><span data-stu-id="02cb6-135">In this case, the `FictionalTools` module requires a newer version of `Microsoft.Extensions.Logging` than the `FilesystemManager` module.</span></span>

<span data-ttu-id="02cb6-136">假設這些模組都將相依性組件和根模組組件放在相同的目錄中，以載入其相依性。</span><span class="sxs-lookup"><span data-stu-id="02cb6-136">Imagine these modules load their dependencies by placing the dependency assemblies in the same directory as the root module assembly.</span></span> <span data-ttu-id="02cb6-137">這會讓 .NET 毫無疑慮地依名稱載入這些組件。</span><span class="sxs-lookup"><span data-stu-id="02cb6-137">This allows .NET to implicitly load them by name.</span></span> <span data-ttu-id="02cb6-138">如果正在 .NET Core 3.1 上執行 PowerShell 7，則可載入並執行 `FictionalTools`，然後成功載入並執行 `FilesystemManager`。</span><span class="sxs-lookup"><span data-stu-id="02cb6-138">If we're running PowerShell 7 (on top of .NET Core 3.1), we can load and run `FictionalTools`, then load and run `FilesystemManager` without issue.</span></span> <span data-ttu-id="02cb6-139">但在新的工作階段中，如果我們載入並執行 `FilesystemManager`，然後載入 `FictionalTools`，就會從 `FictionalTools` 命令得到 `FileLoadException`，因為需要比所載入版本更新的 `Microsoft.Extensions.Logging`。</span><span class="sxs-lookup"><span data-stu-id="02cb6-139">However, in a new session, if we load and run `FilesystemManager`, then load `FictionalTools`, we get a `FileLoadException` from the `FictionalTools` command because it requires a newer version of `Microsoft.Extensions.Logging` than the one loaded.</span></span>
<span data-ttu-id="02cb6-140">`FictionalTools` 無法載入所需的版本，因為已經載入具有相同名稱的組件。</span><span class="sxs-lookup"><span data-stu-id="02cb6-140">`FictionalTools` can't load the version needed because an assembly of the same name has already been loaded.</span></span>

## <a name="powershell-and-net"></a><span data-ttu-id="02cb6-141">PowerShell 和 .Net</span><span class="sxs-lookup"><span data-stu-id="02cb6-141">PowerShell and .NET</span></span>

<span data-ttu-id="02cb6-142">PowerShell 會在 .NET 平台上執行。</span><span class="sxs-lookup"><span data-stu-id="02cb6-142">PowerShell runs on the .NET platform.</span></span> <span data-ttu-id="02cb6-143">因為最後是 NET 負責解析和載入組件相依性，所以我們必須了解 .NET 在這裡的運作方式，才能了解相依性衝突。</span><span class="sxs-lookup"><span data-stu-id="02cb6-143">NET is ultimately responsible for resolving and loading assembly dependencies, so we must understand how .NET operates here to understand dependency conflicts.</span></span>

<span data-ttu-id="02cb6-144">我們也必須面對在不同 .NET 實作中執行不同版本 PowerShell 的事實。</span><span class="sxs-lookup"><span data-stu-id="02cb6-144">We must also confront the fact that different versions of PowerShell run on different .NET implementations.</span></span> <span data-ttu-id="02cb6-145">PowerShell 5.1 和較低版本一般會在 .NET Framework 上執行，而 PowerShell 6 和更新版本則是在 .NET Core 上執行。</span><span class="sxs-lookup"><span data-stu-id="02cb6-145">In general, PowerShell 5.1 and below run on .NET Framework, while PowerShell 6 and above run on .NET Core.</span></span> <span data-ttu-id="02cb6-146">這兩種 .NET 載入和處理組件的實作方式不同。</span><span class="sxs-lookup"><span data-stu-id="02cb6-146">These two implementations of .NET load and handle assemblies differently.</span></span>
<span data-ttu-id="02cb6-147">這表示解析相依性衝突會隨基礎 .NET 平台而有所不同。</span><span class="sxs-lookup"><span data-stu-id="02cb6-147">This means that resolving dependency conflicts can vary depending on the underlying .NET platform.</span></span>

### <a name="assembly-load-contexts"></a><span data-ttu-id="02cb6-148">組件載入內容</span><span class="sxs-lookup"><span data-stu-id="02cb6-148">Assembly Load Contexts</span></span>

<span data-ttu-id="02cb6-149">在 .NET 中，「組件載入內容」(ALC) 是組件載入所在的執行階段命名空間。</span><span class="sxs-lookup"><span data-stu-id="02cb6-149">In .NET, an _Assembly Load Context_ (ALC) that is a runtime namespace into which assemblies are loaded.</span></span> <span data-ttu-id="02cb6-150">組件名稱必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="02cb6-150">The assemblies' names must be unique.</span></span> <span data-ttu-id="02cb6-151">這個概念可在每個 ALC 中，依名稱來唯一解析組件。</span><span class="sxs-lookup"><span data-stu-id="02cb6-151">This concept allows assemblies to be uniquely resolved by name in each ALC.</span></span>

### <a name="assembly-reference-loading-in-net"></a><span data-ttu-id="02cb6-152">.NET 中的組件參考載入</span><span class="sxs-lookup"><span data-stu-id="02cb6-152">Assembly reference loading in .NET</span></span>

<span data-ttu-id="02cb6-153">組件載入其語義取決於 .NET 實作 (.NET Core 與 .NET Framework) 和載入特定組件所用的 .NET API。</span><span class="sxs-lookup"><span data-stu-id="02cb6-153">The semantics of assembly loading depend on both the .NET implementation (.NET Core vs .NET Framework) and the .NET API used to load a particular assembly.</span></span> <span data-ttu-id="02cb6-154">[進階閱讀](#further-reading)一節中提供的連結，可供深入了解 .NET 組件載入在每個 .NET 實作中的運作方式，這裡不詳細說明。</span><span class="sxs-lookup"><span data-stu-id="02cb6-154">Rather than go into detail here, there are links in the [Further reading](#further-reading) section that go into great detail on how .NET assembly loading works in each .NET implementation.</span></span>

<span data-ttu-id="02cb6-155">本文會討論下列機制：</span><span class="sxs-lookup"><span data-stu-id="02cb6-155">In this article we'll refer to the following mechanisms:</span></span>

- <span data-ttu-id="02cb6-156">隱含組件載入 (有效率地 `Assembly.Load(AssemblyName)`)，當 .NET 嘗試從 .NET 程式碼的靜態組件參考中隱含地依名稱載入組件時。</span><span class="sxs-lookup"><span data-stu-id="02cb6-156">Implicit assembly loading (effectively `Assembly.Load(AssemblyName)`), when .NET implicitly tries to load an assembly by name from a static assembly reference in .NET code.</span></span>
- <span data-ttu-id="02cb6-157">`Assembly.LoadFrom()` 是外掛程式導向的載入 API，其會新增處理常式以解析所載入 DLL 的相依性。</span><span class="sxs-lookup"><span data-stu-id="02cb6-157">`Assembly.LoadFrom()`, a plugin-oriented loading API that adds handlers to resolve dependencies of the loaded DLL.</span></span> <span data-ttu-id="02cb6-158">這個方法可能無法以所要的方式來解析相依性。</span><span class="sxs-lookup"><span data-stu-id="02cb6-158">This method may not resolve dependencies the way we want.</span></span>
- <span data-ttu-id="02cb6-159">`Assembly.LoadFile()` 是基本的載入 API，僅用來載入所要求的組件，且不處理任何相依性。</span><span class="sxs-lookup"><span data-stu-id="02cb6-159">`Assembly.LoadFile()`, a basic loading API intended to load only the assembly asked for and does not handle any dependencies.</span></span>

### <a name="differences-in-net-framework-vs-net-core"></a><span data-ttu-id="02cb6-160">.NET Framework 與 .NET Core 的差異</span><span class="sxs-lookup"><span data-stu-id="02cb6-160">Differences in .NET Framework vs .NET Core</span></span>

<span data-ttu-id="02cb6-161">這些 API 的運作方式在 .NET Core 與 .NET Framework 之間有些許變化，因此值得您詳閱隨附的[連結](#further-reading)。</span><span class="sxs-lookup"><span data-stu-id="02cb6-161">The way these APIs work has changed in subtle ways between .NET Core and .NET Framework, so it's worth reading through the included [links](#further-reading).</span></span> <span data-ttu-id="02cb6-162">重要的是，組件載入內容及其他組件解析機制在 .NET Framework 和 .NET Core 之間已經變更。</span><span class="sxs-lookup"><span data-stu-id="02cb6-162">Importantly, Assembly Load Contexts and other assembly resolution mechanisms have changed between .NET Framework and .NET Core.</span></span>

<span data-ttu-id="02cb6-163">特別是 .NET Framework 具有下列功能：</span><span class="sxs-lookup"><span data-stu-id="02cb6-163">In particular, .NET Framework has the following features:</span></span>

- <span data-ttu-id="02cb6-164">全域組件快取，適用於整部電腦的組件解析</span><span class="sxs-lookup"><span data-stu-id="02cb6-164">The Global Assembly Cache, for machine-wide assembly resolution</span></span>
- <span data-ttu-id="02cb6-165">應用程式定義域，適用於隔離組件的半成品沙箱，但也會顯示要處理的序列化層</span><span class="sxs-lookup"><span data-stu-id="02cb6-165">Application Domains, which work like in-process sandboxes for assembly isolation, but also present a serialization layer to contend with</span></span>
- <span data-ttu-id="02cb6-166">有限的組件載入內容模型 ([這裡](/dotnet/framework/deployment/best-practices-for-assembly-loading)會詳加說明)，具有一組固定的組件載入內容，各有各的行為：</span><span class="sxs-lookup"><span data-stu-id="02cb6-166">A limited assembly load context model, explained in depth [here](/dotnet/framework/deployment/best-practices-for-assembly-loading), that has a fixed set of assembly load contexts, each with their own behavior:</span></span>
  - <span data-ttu-id="02cb6-167">預設的載入內容，其包含預設載入的組件</span><span class="sxs-lookup"><span data-stu-id="02cb6-167">The default load context, where assemblies are loaded by default</span></span>
  - <span data-ttu-id="02cb6-168">載入來源內容，以在執行階段手動載入組件</span><span class="sxs-lookup"><span data-stu-id="02cb6-168">The load-from context, for loading assemblies manually at runtime</span></span>
  - <span data-ttu-id="02cb6-169">僅限反映的內容，用於安全載入組件以讀取其中繼資料但不予以執行</span><span class="sxs-lookup"><span data-stu-id="02cb6-169">The reflection-only context, for safely loading assemblies to read their metadata without running them</span></span>
  - <span data-ttu-id="02cb6-170">組件以 `Assembly.LoadFile(string path)` 載入和 `Assembly.Load(byte[] asmBytes)` 所在位置的神秘 void</span><span class="sxs-lookup"><span data-stu-id="02cb6-170">The mysterious void that assemblies loaded with `Assembly.LoadFile(string path)` and `Assembly.Load(byte[] asmBytes)` live in</span></span>

<span data-ttu-id="02cb6-171">.NET Core (和 .NET 5+) 已使用更簡單的模型取代此複雜情況：</span><span class="sxs-lookup"><span data-stu-id="02cb6-171">.NET Core (and .NET 5+) has replaced this complexity with a simpler model:</span></span>

- <span data-ttu-id="02cb6-172">無全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="02cb6-172">No Global Assembly Cache.</span></span> <span data-ttu-id="02cb6-173">應用程式會攜帶自己所有的相依性。</span><span class="sxs-lookup"><span data-stu-id="02cb6-173">Applications bring all their own dependencies.</span></span> <span data-ttu-id="02cb6-174">這可排除應用程式相依性解析的外部因素，以更有機會重現相依性解析。</span><span class="sxs-lookup"><span data-stu-id="02cb6-174">This removes an external factor for dependency resolution in applications, making dependency resolution more reproducible.</span></span>
  <span data-ttu-id="02cb6-175">對模組而言，以 PowerShell 作為外掛程式主機，情況會稍微複雜一點。</span><span class="sxs-lookup"><span data-stu-id="02cb6-175">PowerShell, as the plugin host, complicates this slightly for modules.</span></span> <span data-ttu-id="02cb6-176">其在 `$PSHOME` 中的相依性會與所有模組共用。</span><span class="sxs-lookup"><span data-stu-id="02cb6-176">Its dependencies in `$PSHOME` are shared with all modules.</span></span>
- <span data-ttu-id="02cb6-177">只有一個應用程式定義域，且無法建立新的。</span><span class="sxs-lookup"><span data-stu-id="02cb6-177">Only one Application Domain, and no ability to create new ones.</span></span> <span data-ttu-id="02cb6-178">應用程式定義域概念是在 .NET Core 中維護，純為 .NET 程序的全域狀態。</span><span class="sxs-lookup"><span data-stu-id="02cb6-178">The Application Domain concept is maintained in .NET Core purely to be the global state of the .NET process.</span></span>
- <span data-ttu-id="02cb6-179">新的可延伸組件載入內容模型。</span><span class="sxs-lookup"><span data-stu-id="02cb6-179">A new, extensible Assembly Load Context model.</span></span> <span data-ttu-id="02cb6-180">將組件解析放入新的 ALC，可將其定義為命名空間。</span><span class="sxs-lookup"><span data-stu-id="02cb6-180">Assembly resolution can be namespaced by putting it in a new ALC.</span></span> <span data-ttu-id="02cb6-181">.NET Core 程序從單一預設 ALC 開始，直到載入所有組件。</span><span class="sxs-lookup"><span data-stu-id="02cb6-181">.NET Core processes begin with a single default ALC into which all assemblies are loaded.</span></span> <span data-ttu-id="02cb6-182">(以 `Assembly.LoadFile(string)` 和 `Assembly.Load(byte[])` 載入的除外) 但此程式可使用專屬載入邏輯來建立及定義自己的自訂 ALC。</span><span class="sxs-lookup"><span data-stu-id="02cb6-182">(except for those loaded with `Assembly.LoadFile(string)` and `Assembly.Load(byte[])`) But the process can create and define its own custom ALCs with its own loading logic.</span></span> <span data-ttu-id="02cb6-183">載入組件時，其載入的第一個 ALC 會負責解析其相依性。</span><span class="sxs-lookup"><span data-stu-id="02cb6-183">When an assembly is loaded, the first ALC it is loaded into is responsible for resolving its dependencies.</span></span> <span data-ttu-id="02cb6-184">這提供機會來實作功能強大的 .NET 外掛程式載入機制。</span><span class="sxs-lookup"><span data-stu-id="02cb6-184">This creates opportunities to implement powerful .NET plugin loading mechanisms.</span></span>

<span data-ttu-id="02cb6-185">這兩種實作都會延遲載入組件。</span><span class="sxs-lookup"><span data-stu-id="02cb6-185">In both implementations, assemblies are loaded lazily.</span></span> <span data-ttu-id="02cb6-186">這表示載入時，有方法要求其第一次執行時的類型。</span><span class="sxs-lookup"><span data-stu-id="02cb6-186">This means that they are loaded when a method requiring their type is run for the first time.</span></span>

<span data-ttu-id="02cb6-187">例如，下列兩個版本的相同程式碼在不同時間載入相依性。</span><span class="sxs-lookup"><span data-stu-id="02cb6-187">For example, here are two versions of the same code that load a dependency at different times.</span></span>

<span data-ttu-id="02cb6-188">呼叫 `Program.GetRange()` 時，第一個版本一律載入自己的相依性，因為相依性參考是以語彙方式呈現在方法中：</span><span class="sxs-lookup"><span data-stu-id="02cb6-188">The first always loads its dependency when `Program.GetRange()` is called, because the dependency reference is lexically present within the method:</span></span>

```csharp
using Dependency.Library;

public static class Program
{
    public static List<int> GetRange(int limit)
    {
        var list = new List<int>();
        for (int i = 0; i < limit; i++)
        {
            if (i >= 20)
            {
                // Dependency.Library will be loaded when GetRange is run
                // because the dependency call occurs directly within the method
                DependencyApi.Use();
            }

            list.Add(i);
        }
        return list;
    }
}
```

<span data-ttu-id="02cb6-189">而第二個版本只有在 `limit` 參數為 20 或以上時才會載入自己的相依性，因為是透過方法的內部間接取值：</span><span class="sxs-lookup"><span data-stu-id="02cb6-189">The second will load its dependency only if the `limit` parameter is 20 or more, because of the internal indirection through a method:</span></span>

```csharp
using Dependency.Library;

public static class Program
{
    public static List<int> GetNumbers(int limit)
    {
        var list = new List<int>();
        for (int i = 0; i < limit; i++)
        {
            if (i >= 20)
            {
                // Dependency.Library is only referenced within
                // the UseDependencyApi() method,
                // so will only be loaded when limit >= 20
                UseDependencyApi();
            }

            list.Add(i);
        }
        return list;
    }

    private static void UseDependencyApi()
    {
        // Once UseDependencyApi() is called, Dependency.Library is loaded
        DependencyApi.Use();
    }
}
```

<span data-ttu-id="02cb6-190">這是很好的做法，因為既可將記憶體和檔案系統 I/O 降到最低，又能更有效率地使用資源。</span><span class="sxs-lookup"><span data-stu-id="02cb6-190">This is a good practice since it minimizes the memory and filesystem I/O and uses the resources more efficiently.</span></span> <span data-ttu-id="02cb6-191">但其副作用是，不到嘗試載入組件的程式碼路徑，不會知道組件無法載入。</span><span class="sxs-lookup"><span data-stu-id="02cb6-191">The unfortunate a side effect of this is that we won't know that the assembly fails to load until we reach the code path that tries to load the assembly.</span></span>

<span data-ttu-id="02cb6-192">這也會建立組件載入衝突的計時條件。</span><span class="sxs-lookup"><span data-stu-id="02cb6-192">It can also create a timing condition for assembly load conflicts.</span></span> <span data-ttu-id="02cb6-193">如果同一個程式有兩個部分嘗試載入同一組件的不同版本，則第一次執行的程式碼路徑會決定所載入版本。</span><span class="sxs-lookup"><span data-stu-id="02cb6-193">If two parts of the same program try to load different versions of the same assembly, the version loaded depends on which code path is run first.</span></span>

<span data-ttu-id="02cb6-194">對 PowerShell 而言，這表示下列因素會影響組件載入衝突：</span><span class="sxs-lookup"><span data-stu-id="02cb6-194">For PowerShell, this means that the following factors can affect an assembly load conflict:</span></span>

- <span data-ttu-id="02cb6-195">首先載入哪一個模組？</span><span class="sxs-lookup"><span data-stu-id="02cb6-195">Which module was loaded first?</span></span>
- <span data-ttu-id="02cb6-196">執行了使用相依性程式庫的程式碼路徑嗎？</span><span class="sxs-lookup"><span data-stu-id="02cb6-196">Was the code path that uses the dependency library run?</span></span>
- <span data-ttu-id="02cb6-197">PowerShell 是在啟動時載入衝突的相依性，或只在特定程式碼路徑下才會載入衝突的相依性？</span><span class="sxs-lookup"><span data-stu-id="02cb6-197">Does PowerShell load a conflicting dependency at startup or only under certain code paths?</span></span>

## <a name="quick-fixes-and-their-limitations"></a><span data-ttu-id="02cb6-198">快速修正及其限制</span><span class="sxs-lookup"><span data-stu-id="02cb6-198">Quick fixes and their limitations</span></span>

<span data-ttu-id="02cb6-199">在某些情況下，您可微幅調整模組，並以最不費力的方式來修正問題。</span><span class="sxs-lookup"><span data-stu-id="02cb6-199">In some cases, it's possible to make small adjustments to your module and fix things with minimal effort.</span></span> <span data-ttu-id="02cb6-200">但這些解決方案通常會附帶一些注意事項。</span><span class="sxs-lookup"><span data-stu-id="02cb6-200">But these solutions tend to come with caveats.</span></span> <span data-ttu-id="02cb6-201">其也許可能適用於模組，卻不適用於所有模組。</span><span class="sxs-lookup"><span data-stu-id="02cb6-201">While they may apply to your module, they won't work for every module.</span></span>

### <a name="change-your-dependency-version"></a><span data-ttu-id="02cb6-202">變更相依性版本</span><span class="sxs-lookup"><span data-stu-id="02cb6-202">Change your dependency version</span></span>

<span data-ttu-id="02cb6-203">避免發生相依性衝突的最簡單方式就是同意相依性。</span><span class="sxs-lookup"><span data-stu-id="02cb6-203">The simplest way to avoid dependency conflicts is to agree on a dependency.</span></span> <span data-ttu-id="02cb6-204">可能的狀況如下：</span><span class="sxs-lookup"><span data-stu-id="02cb6-204">This may be possible when:</span></span>

- <span data-ttu-id="02cb6-205">衝突來自於模組的直接相依性，且您控制了版本。</span><span class="sxs-lookup"><span data-stu-id="02cb6-205">Your conflict is with a direct dependency of your module and you control the version.</span></span>
- <span data-ttu-id="02cb6-206">衝突來自於間接相依性，但您可設定直接相依性，令其使用可行的間接相依性版本。</span><span class="sxs-lookup"><span data-stu-id="02cb6-206">Your conflict is with an indirect dependency, but you can configure your direct dependencies to use a workable indirect dependency version.</span></span>
- <span data-ttu-id="02cb6-207">您知道發生衝突的版本，且依賴其的不變更。</span><span class="sxs-lookup"><span data-stu-id="02cb6-207">You know the conflicting version and can rely on it not changing.</span></span>

<span data-ttu-id="02cb6-208">`Newtonsoft.Json` 套件是最後一種情況的絕佳範例。</span><span class="sxs-lookup"><span data-stu-id="02cb6-208">The `Newtonsoft.Json` package is a good example of this last scenario.</span></span> <span data-ttu-id="02cb6-209">這是 PowerShell 6 及更新版本的相依性，不會用在 Windows PowerShell 中。</span><span class="sxs-lookup"><span data-stu-id="02cb6-209">This is a dependency of PowerShell 6 and above, and isn't used in Windows PowerShell.</span></span> <span data-ttu-id="02cb6-210">這表示解析版本控制衝突的簡單方法，就是在您希望作為目標的所有 PowerShell 版本中，以最低版本的 `Newtonsoft.Json` 為目標。</span><span class="sxs-lookup"><span data-stu-id="02cb6-210">Meaning a simple way to resolve versioning conflicts is to target the lowest version of `Newtonsoft.Json` across the PowerShell versions you wish to target.</span></span>

<span data-ttu-id="02cb6-211">例如，PowerShell 6.2.6 和 PowerShell 7.0.2 目前都使用 12.0.3 版的 `Newtonsoft.Json`。</span><span class="sxs-lookup"><span data-stu-id="02cb6-211">For example, PowerShell 6.2.6 and PowerShell 7.0.2 both currently use `Newtonsoft.Json` version 12.0.3.</span></span> <span data-ttu-id="02cb6-212">因此，若要建立以 Windows PowerShell、PowerShell 6 和 PowerShell 7 為目標的模組，則要使用 `Newtonsoft.Json 12.0.3` 作為相依性目標，並包含在建置模組中。</span><span class="sxs-lookup"><span data-stu-id="02cb6-212">So, to create a module targeting Windows PowerShell, PowerShell 6, and PowerShell 7, you would target `Newtonsoft.Json 12.0.3` as a dependency and include it in your built module.</span></span> <span data-ttu-id="02cb6-213">在 PowerShell 6 或 7 中載入模組時，即已載入 PowerShell 自己的 `Newtonsoft.Json` 組件。</span><span class="sxs-lookup"><span data-stu-id="02cb6-213">When the module is loaded in PowerShell 6 or 7, PowerShell's own `Newtonsoft.Json` assembly is already loaded.</span></span> <span data-ttu-id="02cb6-214">而且，至少是模組所需版本，所以解析成功。</span><span class="sxs-lookup"><span data-stu-id="02cb6-214">Also, it is at least the version required for your module, so resolution succeeds.</span></span> <span data-ttu-id="02cb6-215">在 Windows PowerShell 中，組件尚未出現在 PowerShell 中。</span><span class="sxs-lookup"><span data-stu-id="02cb6-215">In Windows PowerShell, the assembly isn't already present in PowerShell.</span></span> <span data-ttu-id="02cb6-216">所以會改從模組資料夾載入。</span><span class="sxs-lookup"><span data-stu-id="02cb6-216">So, it's loaded from your module folder instead.</span></span>

<span data-ttu-id="02cb6-217">一般以具體的 PowerShell 套件 (例如 `Microsoft.PowerShell.Sdk` 或 `System.Management.Automation`) 為目標時，NuGet 應該能夠解析所需的正確相依性版本。</span><span class="sxs-lookup"><span data-stu-id="02cb6-217">Generally, when targeting a concrete PowerShell package, like `Microsoft.PowerShell.Sdk` or `System.Management.Automation`, NuGet should be able to resolve the right dependency versions required.</span></span> <span data-ttu-id="02cb6-218">以 Windows PowerShell 和 PowerShell 6+ 為目標會更加困難，因為必須選擇以多個架構或以 `PowerShellStandard.Library` 為目標。</span><span class="sxs-lookup"><span data-stu-id="02cb6-218">Targeting both Windows PowerShell and PowerShell 6+ becomes more difficult because you must choose between targeting multiple frameworks or `PowerShellStandard.Library`.</span></span>

<span data-ttu-id="02cb6-219">無法釘選到通用相依性版本的情況包括：</span><span class="sxs-lookup"><span data-stu-id="02cb6-219">Circumstances where pinning to a common dependency version won't work include:</span></span>

- <span data-ttu-id="02cb6-220">衝突來自間接相依性，且所有相依性皆無法設定為使用通用版本。</span><span class="sxs-lookup"><span data-stu-id="02cb6-220">The conflict is with an indirect dependency, and none of your dependencies can be configured to use a common version.</span></span>
- <span data-ttu-id="02cb6-221">其他相依性版本可能經常變更，因此設定通用版本只能短期修正問題。</span><span class="sxs-lookup"><span data-stu-id="02cb6-221">The other dependency version is likely to change often, so settling on a common version is only a short-term fix.</span></span>

### <a name="add-an-assemblyresolve-event-handler-to-create-a-dynamic-binding-redirect"></a><span data-ttu-id="02cb6-222">新增 AssemblyResolve 事件處理常式以建立動態繫結重新導向</span><span class="sxs-lookup"><span data-stu-id="02cb6-222">Add an AssemblyResolve event handler to create a dynamic binding redirect</span></span>

<span data-ttu-id="02cb6-223">變更自己的相依性版本，有時不太可能或太難。</span><span class="sxs-lookup"><span data-stu-id="02cb6-223">Sometimes changing your own dependency version isn't possible or is too difficult.</span></span> <span data-ttu-id="02cb6-224">另一個選項是註冊 `AssemblyResolve` 事件的事件處理常式，以設定動態繫結重新導向。</span><span class="sxs-lookup"><span data-stu-id="02cb6-224">Another option is to set up a dynamic binding redirect by registering an event handler for the `AssemblyResolve` event.</span></span>

<span data-ttu-id="02cb6-225">和靜態繫結重新導向一樣，重點在於強制某個相依性的所有取用者都使用相同的實際組件。</span><span class="sxs-lookup"><span data-stu-id="02cb6-225">As with a static binding redirect, the point is to force all consumers of a dependency to use the same actual assembly.</span></span> <span data-ttu-id="02cb6-226">您要攔截載入相依性的呼叫，並將其一律重新導向至所要的版本。</span><span class="sxs-lookup"><span data-stu-id="02cb6-226">You intercept calls to load the dependency and always redirect them to the version you want.</span></span>

<span data-ttu-id="02cb6-227">看起來如下：</span><span class="sxs-lookup"><span data-stu-id="02cb6-227">This looks something like this:</span></span>

```csharp
// Register the event handler as early as you can in your code.
// A good option is to use the IModuleAssemblyInitializer interface
// that PowerShell provides to run code early on when your module is loaded.

// This class will be instantiated on module import and the OnImport() method run.
// Make sure that:
//  - the class is public
//  - the class has a public, parameterless constructor
//  - the class implements IModuleAssemblyInitializer
public class MyModuleInitializer : IModuleAssemblyInitializer
{
    public void OnImport()
    {
        AppDomain.CurrentDomain.AssemblyResolve += DependencyResolution.ResolveNewtonsoftJson;
    }
}

// Clean up the event handler when the the module is removed
// to prevent memory leaks.
//
// Like IModuleAssemblyInitializer, IModuleAssemblyCleanup allows
// you to register code to run when a module is removed (with Remove-Module).
// Make sure it is also public with a public parameterless contructor
// and implements IModuleAssemblyCleanup.
public class MyModuleCleanup : IModuleAssemblyCleanup
{
    public void OnRemove()
    {
        AppDomain.CurrentDomain.AssemblyResolve -= DependencyResolution.ResolveNewtonsoftJson;
    }
}

internal static class DependencyResolution
{
    private static readonly string s_modulePath = Path.GetDirectoryName(
        Assembly.GetExecutingAssembly().Location);

    public static Assembly ResolveNewtonsoftJson(object sender, ResolveEventArgs args)
    {
        // Parse the assembly name
        var assemblyName = new AssemblyName(args.Name);

        // We only want to handle the dependency we care about.
        // In this example it's Newtonsoft.Json.
        if (!assemblyName.Name.Equals("Newtonsoft.Json"))
        {
            return null;
        }

        // Generally the version of the dependency you want to load is the higher one,
        // since it's the most likely to be compatible with all dependent assemblies.
        // The logic here assumes our module always has the version we want to load.
        // Also note the use of Assembly.LoadFrom() here rather than Assembly.LoadFile().
        return Assembly.LoadFrom(Path.Combine(s_modulePath, "Newtonsoft.Json.dll"));
    }
}
```

<span data-ttu-id="02cb6-228">技術上，您可在 PowerShell 中註冊 ScriptBlock 以處理 `AssemblyResolve` 事件，但：</span><span class="sxs-lookup"><span data-stu-id="02cb6-228">You can technically register a scriptblock within PowerShell to handle an `AssemblyResolve` event, but:</span></span>

- <span data-ttu-id="02cb6-229">任何執行緒上都可能觸發 `AssemblyResolve` 事件，PowerShell 有時都無法處理。</span><span class="sxs-lookup"><span data-stu-id="02cb6-229">An `AssemblyResolve` event may be triggered on any thread, something that PowerShell will be unable to handle.</span></span>
- <span data-ttu-id="02cb6-230">即使在正確的執行緒上處理了事件，PowerShell 的範圍概念也表示必須謹慎寫入事件處理常式 ScriptBlock，而不要相依於在其外部定義的變數。</span><span class="sxs-lookup"><span data-stu-id="02cb6-230">Even when events are handled on the right thread, PowerShell's scoping concepts mean that the event handler scriptblock must be written carefully to not depend on variables defined outside it.</span></span>

<span data-ttu-id="02cb6-231">有時候，重新導向至通用版本無效：</span><span class="sxs-lookup"><span data-stu-id="02cb6-231">There are situations where redirecting to a common version won't work:</span></span>

- <span data-ttu-id="02cb6-232">當多個版本間的相依性出現重大變更時，或相依的程式碼若不依賴某個功能，即無法在所重新導向的版本中使用。</span><span class="sxs-lookup"><span data-stu-id="02cb6-232">When the dependency has made breaking changes between versions, or when dependent code relies on a functionality otherwise not available in the version you redirect to.</span></span>
- <span data-ttu-id="02cb6-233">先載入發生衝突的相依性，後載入模組時。</span><span class="sxs-lookup"><span data-stu-id="02cb6-233">When your module isn't loaded before the conflicting dependency.</span></span> <span data-ttu-id="02cb6-234">如果在載入相依性之後才註冊 `AssemblyResolve` 事件處理常式，則永遠不會引發。</span><span class="sxs-lookup"><span data-stu-id="02cb6-234">If you register an `AssemblyResolve` event handler after the dependency has been loaded, it will never be fired.</span></span> <span data-ttu-id="02cb6-235">如果嘗試避免與另一個模組發生相依性衝突，這可能會造成問題，因為其他模組可能已先行載入。</span><span class="sxs-lookup"><span data-stu-id="02cb6-235">If you're trying to prevent dependency conflicts with another module, this may be an issue, since the other module may be loaded first.</span></span>

### <a name="use-the-dependency-out-of-process"></a><span data-ttu-id="02cb6-236">在程序外使用相依性</span><span class="sxs-lookup"><span data-stu-id="02cb6-236">Use the dependency out of process</span></span>

<span data-ttu-id="02cb6-237">此解決方案更適合模組使用者，較不偏向模組作者。</span><span class="sxs-lookup"><span data-stu-id="02cb6-237">This solution is more for module users than module authors.</span></span> <span data-ttu-id="02cb6-238">當模組因現有相依性衝突而無法作用時，可使用此解決方案。</span><span class="sxs-lookup"><span data-stu-id="02cb6-238">This is a solution to use when confronted with a module that won't work due to an existing dependency conflict.</span></span>

<span data-ttu-id="02cb6-239">相依性衝突發生的原因，是在相同 .NET 程序中載入了兩個版本的相同組件。</span><span class="sxs-lookup"><span data-stu-id="02cb6-239">Dependency conflicts occur because two versions of the same assembly are loaded into the same .NET process.</span></span> <span data-ttu-id="02cb6-240">簡單的解決方法是將組件載入至不同程序，只要仍然可同時使用兩者的功能即可。</span><span class="sxs-lookup"><span data-stu-id="02cb6-240">A simple solution is to load them into different processes, as long as you can still use the functionality from both together.</span></span>

<span data-ttu-id="02cb6-241">PowerShell 中有數種方法可達到此目標：</span><span class="sxs-lookup"><span data-stu-id="02cb6-241">In PowerShell, there are several ways to achieve this:</span></span>

- <span data-ttu-id="02cb6-242">將 PowerShell 叫用為子程序</span><span class="sxs-lookup"><span data-stu-id="02cb6-242">Invoke PowerShell as a subprocess</span></span>

  <span data-ttu-id="02cb6-243">在目前程序外執行 PowerShell 命令的簡單方法，就是直接使用命令呼叫來啟動新的 PowerShell 程序：</span><span class="sxs-lookup"><span data-stu-id="02cb6-243">A simple way to run a PowerShell command out of the current process is to just start a new PowerShell process directly with the command call:</span></span>

  ```powershell
  pwsh -c 'Invoke-ConflictingCommand'
  ```

  <span data-ttu-id="02cb6-244">此方法的主要限制是重組結果可能更棘手，或比其他選項更容易發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="02cb6-244">The main limitation here is that restructuring the result can be trickier or more error prone than other options.</span></span>

- <span data-ttu-id="02cb6-245">PowerShell 工作系統</span><span class="sxs-lookup"><span data-stu-id="02cb6-245">The PowerShell job system</span></span>

  <span data-ttu-id="02cb6-246">PowerShell 工作系統也會將命令傳送至新的 PowerShell 程序並傳回結果，以在程序外執行命令：</span><span class="sxs-lookup"><span data-stu-id="02cb6-246">The PowerShell job system also runs commands out of process, by sending commands to a new PowerShell process and returning the results:</span></span>

  ```powershell
  $result = Start-Job { Invoke-ConflictingCommand } | Receive-Job -Wait
  ```

  <span data-ttu-id="02cb6-247">如此一來，您只需要確定所有變數和狀態皆已正確傳遞即可。</span><span class="sxs-lookup"><span data-stu-id="02cb6-247">In this case, you just need to be sure that any variables and state are passed in correctly.</span></span>

  <span data-ttu-id="02cb6-248">工作系統在執行小型命令時，也略為繁瑣。</span><span class="sxs-lookup"><span data-stu-id="02cb6-248">The job system can also be slightly cumbersome when running small commands.</span></span>

- <span data-ttu-id="02cb6-249">PowerShell 遠端</span><span class="sxs-lookup"><span data-stu-id="02cb6-249">PowerShell remoting</span></span>

  <span data-ttu-id="02cb6-250">當可用時，PowerShell 遠端是在程序外執行命令的實用方式。</span><span class="sxs-lookup"><span data-stu-id="02cb6-250">When it's available, PowerShell remoting can be a useful way to run commands out of process.</span></span> <span data-ttu-id="02cb6-251">您可透過遠端在新的程序中建立全新 **PSSession**、透過 PowerShell 遠端呼叫其命令，然後在本機使用結果及包含衝突相依性的其他模組。</span><span class="sxs-lookup"><span data-stu-id="02cb6-251">With remoting, you can create a fresh **PSSession** in a new process, call its commands over PowerShell remoting, then use the results locally with the other modules containing the conflicting dependencies.</span></span>

  <span data-ttu-id="02cb6-252">範例可能會如下：</span><span class="sxs-lookup"><span data-stu-id="02cb6-252">An example might look like this:</span></span>

  ```powershell
  # Create a local PowerShell session
  # where the module with conflicting assemblies will be loaded
  $s = New-PSSession

  # Import the module with the conflicting dependency via remoting,
  # exposing the commands locally
  Import-Module -PSSession $s -Name ConflictingModule

  # Run a command from the module with the conflicting dependencies
  Invoke-ConflictingCommand
  ```

- <span data-ttu-id="02cb6-253">Windows PowerShell 隱含的遠端功能</span><span class="sxs-lookup"><span data-stu-id="02cb6-253">Implicit remoting to Windows PowerShell</span></span>

  <span data-ttu-id="02cb6-254">PowerShell 7 還有另一個選項，是在 `Import-Module` 上使用 `-UseWindowsPowerShell` 旗標。</span><span class="sxs-lookup"><span data-stu-id="02cb6-254">Another option in PowerShell 7 is to use the `-UseWindowsPowerShell` flag on `Import-Module`.</span></span> <span data-ttu-id="02cb6-255">這會透過本機遠端工作階段將模組匯入 Windows PowerShell：</span><span class="sxs-lookup"><span data-stu-id="02cb6-255">This will import the module through a local remoting session into Windows PowerShell:</span></span>

  ```powershell
  Import-Module -Name ConflictingModule -UseWindowsPowerShell
  ```

  <span data-ttu-id="02cb6-256">請注意，模組可能無法配合 Windows PowerShell，或運作方式不同。</span><span class="sxs-lookup"><span data-stu-id="02cb6-256">Be aware that modules may not work with, or work differently with Windows PowerShell.</span></span>

#### <a name="when-out-of-process-invocation-should-not-be-used"></a><span data-ttu-id="02cb6-257">不應使用程序外叫用的情況</span><span class="sxs-lookup"><span data-stu-id="02cb6-257">When out-of-process invocation should not be used</span></span>

<span data-ttu-id="02cb6-258">身為模組作者，程序外命令調用很難併入模組中，且可能會有造成問題的邊緣案例。</span><span class="sxs-lookup"><span data-stu-id="02cb6-258">As a module author, out-of-process command invocation is difficult to bake into a module and may have edge cases that cause issues.</span></span> <span data-ttu-id="02cb6-259">特別是在模組需要運作的所有環境中，可能無法使用遠端功能和工作。</span><span class="sxs-lookup"><span data-stu-id="02cb6-259">In particular, remoting and jobs may not be available in all environments where your module needs to work.</span></span> <span data-ttu-id="02cb6-260">不過，將實作移出程序，允許 PowerShell 模組成為更精簡用戶端的一般原則，仍然適用。</span><span class="sxs-lookup"><span data-stu-id="02cb6-260">However, the general principle of moving the implementation out of process and allowing the PowerShell module to be a thinner client, may still be applicable.</span></span>

<span data-ttu-id="02cb6-261">身為模組使用者，有時候程序外叫用無法正常執行：</span><span class="sxs-lookup"><span data-stu-id="02cb6-261">As a module user, there are cases where out-of-process invocation won't work:</span></span>

- <span data-ttu-id="02cb6-262">因為您無權使用 PowerShell 遠端或其未啟用，以致無法使用時。</span><span class="sxs-lookup"><span data-stu-id="02cb6-262">When PowerShell remoting is unavailable because you don't have privileges to use it or it is not enabled.</span></span>
- <span data-ttu-id="02cb6-263">當需要輸出中特定 .NET 類型作為方法或其他命令的輸入時。</span><span class="sxs-lookup"><span data-stu-id="02cb6-263">When a particular .NET type is needed from output as input to a method or another command.</span></span>
  <span data-ttu-id="02cb6-264">透過 PowerShell 遠端所執行命令會發出還原序列化的物件，而不是強型別的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="02cb6-264">Commands running over PowerShell remoting emit deserialized objects rather than strongly-typed .NET objects.</span></span> <span data-ttu-id="02cb6-265">這表示方法呼叫和強型別 API 都不適用透過遠端匯入的命令輸出。</span><span class="sxs-lookup"><span data-stu-id="02cb6-265">This means that method calls and strongly typed APIs do not work with the output of commands imported over remoting.</span></span>

## <a name="more-robust-solutions"></a><span data-ttu-id="02cb6-266">更強大的解決方案</span><span class="sxs-lookup"><span data-stu-id="02cb6-266">More robust solutions</span></span>

<span data-ttu-id="02cb6-267">前述解決方案都有不適用的案例和模組。</span><span class="sxs-lookup"><span data-stu-id="02cb6-267">The previous solutions all had scenarios and modules that don't work.</span></span> <span data-ttu-id="02cb6-268">但其也都相當簡單，可正確實作。</span><span class="sxs-lookup"><span data-stu-id="02cb6-268">However, they also have the virtue of being relatively simple to implement correctly.</span></span> <span data-ttu-id="02cb6-269">下列解決方案較強大，但需要花費更多精力才能正確執行，且若撰寫不慎，可能會造成微小的錯誤。</span><span class="sxs-lookup"><span data-stu-id="02cb6-269">The following solutions are more robust, but require more effort to implement correctly and can introduce subtle bugs if not written carefully.</span></span>

### <a name="loading-through-net-core-assembly-load-contexts"></a><span data-ttu-id="02cb6-270">透過 .NET Core 組件載入內容載入</span><span class="sxs-lookup"><span data-stu-id="02cb6-270">Loading through .NET Core Assembly Load Contexts</span></span>

<span data-ttu-id="02cb6-271">[組件載入內容](/dotnet/api/system.runtime.loader.assemblyloadcontext) (ALC) 是可實作的 API，早在 .NET Core 1.0 中即已引入，專門用來處理將多個版本其相同組件載入同一執行階段的需求。</span><span class="sxs-lookup"><span data-stu-id="02cb6-271">[Assembly Load Contexts](/dotnet/api/system.runtime.loader.assemblyloadcontext) (ALCs) as an implementable API were introduced in .NET Core 1.0 to specifically address the need to load multiple versions of the same assembly into the same runtime.</span></span>

<span data-ttu-id="02cb6-272">.NET Core 和 .NET 5 為載入組件衝突版本的問題提供了強大解決方案。</span><span class="sxs-lookup"><span data-stu-id="02cb6-272">Within .NET Core and .NET 5, they offer the most robust solution to the problem of loading conflicting versions of an assembly.</span></span> <span data-ttu-id="02cb6-273">不過，.NET Framework 中無法使用自訂的 ALC。</span><span class="sxs-lookup"><span data-stu-id="02cb6-273">However, custom ALCs are not available in .NET Framework.</span></span> <span data-ttu-id="02cb6-274">這表示此解決方案僅適用於 PowerShell 6 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="02cb6-274">This means that this solution only works in PowerShell 6 and above.</span></span>

<span data-ttu-id="02cb6-275">目前，在 PowerShell 中使用 ALC 隔離相依性的最佳範例，是 PowerShell 編輯器服務中，適用於 Visual Studio Code 的 PowerShell 延伸模組的語言伺服器。</span><span class="sxs-lookup"><span data-stu-id="02cb6-275">Currently, the best example of using an ALC for dependency isolation in PowerShell is in PowerShell Editor Services, the language server for the PowerShell extension for Visual Studio Code.</span></span> <span data-ttu-id="02cb6-276">[ALC](https://github.com/PowerShell/PowerShellEditorServices/blob/master/src/PowerShellEditorServices.Hosting/Internal/PsesLoadContext.cs) 旨在防止 PowerShell 編輯器服務的自有相依性與 PowerShell 模組中相依性發生衝突。</span><span class="sxs-lookup"><span data-stu-id="02cb6-276">An [ALC is used](https://github.com/PowerShell/PowerShellEditorServices/blob/master/src/PowerShellEditorServices.Hosting/Internal/PsesLoadContext.cs) to prevent PowerShell Editor Services' own dependencies from clashing with those in PowerShell modules.</span></span>

<span data-ttu-id="02cb6-277">使用 ALC 實作模組相依性隔離，在概念上很困難，但我們會利用最基本的範例來逐步解說。</span><span class="sxs-lookup"><span data-stu-id="02cb6-277">Implementing module dependency isolation with an ALC is conceptually difficult, but we will work through a minimal example.</span></span> <span data-ttu-id="02cb6-278">假設我們有一個簡單模組，其僅適用於 PowerShell 7。</span><span class="sxs-lookup"><span data-stu-id="02cb6-278">Imagine we have a simple module that is only intended to work in PowerShell 7.</span></span>
<span data-ttu-id="02cb6-279">原始程式碼的組織方式如下：</span><span class="sxs-lookup"><span data-stu-id="02cb6-279">The source code is organized as follows:</span></span>

```
+ AlcModule.psd1
+ src/
    + TestAlcModuleCommand.cs
    + AlcModule.csproj
```

<span data-ttu-id="02cb6-280">Cmdlet 的實作看起來如下：</span><span class="sxs-lookup"><span data-stu-id="02cb6-280">The cmdlet implementation looks like this:</span></span>

```csharp
using Shared.Dependency;

namespace AlcModule
{
    [Cmdlet(VerbsDiagnostic.Test, "AlcModule")]
    public class TestAlcModuleCommand : Cmdlet
    {
        protected override void EndProcessing()
        {
            // Here's where our dependency gets used
            Dependency.Use();
            // Something trivial to make our cmdlet do *something*
            WriteObject("done!");
        }
    }
}
```

<span data-ttu-id="02cb6-281">(已大幅簡化的) 資訊清單看起來如下：</span><span class="sxs-lookup"><span data-stu-id="02cb6-281">The (heavily simplified) manifest, looks like this:</span></span>

```powershell
@{
    Author = 'Me'
    ModuleVersion = '0.0.1'
    RootModule = 'AlcModule.dll'
    CmdletsToExport = @('Test-AlcModule')
    PowerShellVersion = '7.0'
}
```

<span data-ttu-id="02cb6-282">`csproj` 看起來如下：</span><span class="sxs-lookup"><span data-stu-id="02cb6-282">And the `csproj` looks like this:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Shared.Dependency" Version="1.0.0" />
    <PackageReference Include="Microsoft.PowerShell.Sdk" Version="7.0.1" PrivateAssets="all" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="02cb6-283">當建置此模組時，所產生的輸出會有下列配置：</span><span class="sxs-lookup"><span data-stu-id="02cb6-283">When we build this module, the generated output has the following layout:</span></span>

```
AlcModule/
  + AlcModule.psd1
  + AlcModule.dll
  + Shared.Dependency.dll
```

<span data-ttu-id="02cb6-284">在此範例中，問題出在 `Shared.Dependency.dll` 組件，這是假想的衝突相依性。</span><span class="sxs-lookup"><span data-stu-id="02cb6-284">In this example, our problem is in the `Shared.Dependency.dll` assembly, which is our imaginary conflicting dependency.</span></span> <span data-ttu-id="02cb6-285">這個相依性需要放在 ALC 後面，以便使用模組特定版本。</span><span class="sxs-lookup"><span data-stu-id="02cb6-285">This is the dependency that we need to put behind an ALC so that we can use the module-specific version.</span></span>

<span data-ttu-id="02cb6-286">我們需要重新設計模組，以便：</span><span class="sxs-lookup"><span data-stu-id="02cb6-286">We need to re-engineer the module so that:</span></span>

- <span data-ttu-id="02cb6-287">模組相依性只會載入至自訂的 ALC，不會載入到 PowerShell 的 ALC，所以不會發生衝突。</span><span class="sxs-lookup"><span data-stu-id="02cb6-287">Module dependencies are only loaded into our custom ALC, and not into PowerShell's ALC, so there can be no conflict.</span></span> <span data-ttu-id="02cb6-288">此外，當在專案中新增更多相依性時，我們不希望為了讓載入保持運作而持續新增更多程式碼。</span><span class="sxs-lookup"><span data-stu-id="02cb6-288">Moreover, as we add more dependencies to our project, we don't want to continuously add more code to keep loading working.</span></span> <span data-ttu-id="02cb6-289">而是想要可重複使用的一般相依性解析邏輯。</span><span class="sxs-lookup"><span data-stu-id="02cb6-289">Instead, we want reusable, generic dependency resolution logic.</span></span>
- <span data-ttu-id="02cb6-290">載入模組仍可在 PowerShell 中如常運作。</span><span class="sxs-lookup"><span data-stu-id="02cb6-290">Loading the module still works as normal in PowerShell.</span></span> <span data-ttu-id="02cb6-291">PowerShell 模組系統所需 Cmdlet 和其他類型是在 PowerShell 專屬的 ALC 中定義。</span><span class="sxs-lookup"><span data-stu-id="02cb6-291">Cmdlets and other types that the PowerShell module system needs are defined within PowerShell's own ALC.</span></span>

<span data-ttu-id="02cb6-292">為協調這兩種需求，則必須將模組分成兩個組件：</span><span class="sxs-lookup"><span data-stu-id="02cb6-292">To mediate these two requirements, we must break up our module into two assemblies:</span></span>

- <span data-ttu-id="02cb6-293">Cmdlet 組件 `AlcModule.Cmdlets.dll`，包含 PowerShell 模組系統正確載入模組所需的所有類型定義。</span><span class="sxs-lookup"><span data-stu-id="02cb6-293">A cmdlets assembly, `AlcModule.Cmdlets.dll`, that contains definitions of all the types that PowerShell's module system needs to load our module correctly.</span></span> <span data-ttu-id="02cb6-294">亦即，`Cmdlet` 基底類別及實作 `IModuleAssemblyInitializer` 的類別其所有實作，會透過自訂的 ALC，將 `AssemblyLoadContext.Default.Resolving` 的事件處理常式設定為可正確載入 `AlcModule.Engine.dll`。</span><span class="sxs-lookup"><span data-stu-id="02cb6-294">Namely, any implementations of the `Cmdlet` base class and the class that implements `IModuleAssemblyInitializer`, which sets up the event handler for `AssemblyLoadContext.Default.Resolving` to properly load `AlcModule.Engine.dll` through our custom ALC.</span></span> <span data-ttu-id="02cb6-295">因為 PowerShell 7 刻意隱藏在其他 ALC 載入組件中所定義的類型，所以您也必須在這裡定義要向 PowerShell 公開的所有類型。</span><span class="sxs-lookup"><span data-stu-id="02cb6-295">Since PowerShell 7 deliberately hides types defined in assemblies loaded in other ALCs, any types that are meant to be publicly exposed to PowerShell must also be defined here.</span></span> <span data-ttu-id="02cb6-296">最後，我們必須在這個組件中定義自訂的 ALC 定義。</span><span class="sxs-lookup"><span data-stu-id="02cb6-296">Finally, our custom ALC definition needs to be defined in this assembly.</span></span> <span data-ttu-id="02cb6-297">此外，這個組件中應盡可能不要留存程式碼。</span><span class="sxs-lookup"><span data-stu-id="02cb6-297">Beyond that, as little code as possible should live in this assembly.</span></span>
- <span data-ttu-id="02cb6-298">引擎組件 `AlcModule.Engine.dll`，負責處理模組的實際實作。</span><span class="sxs-lookup"><span data-stu-id="02cb6-298">An engine assembly, `AlcModule.Engine.dll`, that handles the actual implementation of the module.</span></span>
  <span data-ttu-id="02cb6-299">PowerShell ALC 中可使用來自此組件的類型，但其一開始要透過自訂的 ALC 載入。</span><span class="sxs-lookup"><span data-stu-id="02cb6-299">Types from this are available in the PowerShell ALC, but it will initially be loaded through our custom ALC.</span></span> <span data-ttu-id="02cb6-300">其相依性只會載入自訂的 ALC。</span><span class="sxs-lookup"><span data-stu-id="02cb6-300">Its dependencies are only loaded into the custom ALC.</span></span> <span data-ttu-id="02cb6-301">實際上，這會成為兩個 ALC 之間的「橋樑」。</span><span class="sxs-lookup"><span data-stu-id="02cb6-301">Effectively, this becomes a _bridge_ between the two ALCs.</span></span>

<span data-ttu-id="02cb6-302">使用此橋接概念，新組件的情況會如下：</span><span class="sxs-lookup"><span data-stu-id="02cb6-302">Using this bridge concept, our new assembly situation looks like this:</span></span>

![AlcModule.Engine.dll 橋接兩個 ALC 的示意圖](./media/resolving-dependency-conflicts/alc-diagram.jpg)

<span data-ttu-id="02cb6-304">為確保預設 ALC 其相依性探查邏輯不會解析要載入到自訂 ALC 的相依性，我們必須將此模組的兩個部分放在不同目錄中。</span><span class="sxs-lookup"><span data-stu-id="02cb6-304">To make sure the default ALC's dependency probing logic does not resolve the dependencies to be loaded into the custom ALC, we need to separate these two parts of the module in different directories.</span></span> <span data-ttu-id="02cb6-305">新模組配置具有下列結構：</span><span class="sxs-lookup"><span data-stu-id="02cb6-305">The new module layout has the following structure:</span></span>

```
AlcModule/
  AlcModule.Cmdlets.dll
  AlcModule.psd1
  Dependencies/
  | + AlcModule.Engine.dll
  | + Shared.Dependency.dll
```

<span data-ttu-id="02cb6-306">為查看實作變更的方式，我們將從 `AlcModule.Engine.dll` 的實作開始：</span><span class="sxs-lookup"><span data-stu-id="02cb6-306">To see how the implementation changes, we'll start with the implementation of `AlcModule.Engine.dll`:</span></span>

```csharp
using Shared.Dependency;

namespace AlcModule.Engine
{
    public class AlcEngine
    {
        public static void Use()
        {
            Dependency.Use();
        }
    }
}
```

<span data-ttu-id="02cb6-307">`Shared.Dependency.dll` 是簡單的相依性容器，但應視為 PowerShell 其他組件換行 Cmdlet 功能的 .NET API。</span><span class="sxs-lookup"><span data-stu-id="02cb6-307">This is a simple container for the dependency, `Shared.Dependency.dll`, but you should think of it as the .NET API for your functionality that the cmdlets in the other assembly wrap for PowerShell.</span></span>

<span data-ttu-id="02cb6-308">`AlcModule.Cmdlets.dll` 中的 Cmdlet 看起來如下：</span><span class="sxs-lookup"><span data-stu-id="02cb6-308">The cmdlet in `AlcModule.Cmdlets.dll` looks like this:</span></span>

```csharp
// Reference our module's Engine implementation here
using AlcModule.Engine;

namespace AlcModule.Cmdlets
{
    [Cmdlet(VerbsDiagnostic.Test, "AlcModule")]
    public class TestAlcModuleCommand : Cmdlet
    {
        protected override void EndProcessing()
        {
            AlcEngine.Use();
            WriteObject("done!");
        }
    }
}
```

<span data-ttu-id="02cb6-309">此時，如果要載入 **AlcModule** 並執行 `Test-AlcModule`，則當預設 ALC 嘗試載入 `Alc.Engine.dll` 以執行 `EndProcessing()` 時，就會得到 `FileNotFoundException`。</span><span class="sxs-lookup"><span data-stu-id="02cb6-309">At this point, if we were to load **AlcModule** and run `Test-AlcModule`, we get a `FileNotFoundException` when the default ALC tries to load `Alc.Engine.dll` to run `EndProcessing()`.</span></span> <span data-ttu-id="02cb6-310">這很好，因為這表示預設 ALC 找不到我們想要隱藏的相依性。</span><span class="sxs-lookup"><span data-stu-id="02cb6-310">This is good, since it means the default ALC can't find the dependencies we want to hide.</span></span>

<span data-ttu-id="02cb6-311">現在，我們需要將程式碼新增至 `AlcModule.Cmdlets.dll`，以便其知道如何解析 `AlcModule.Engine.dll`。</span><span class="sxs-lookup"><span data-stu-id="02cb6-311">Now we need to add code to `AlcModule.Cmdlets.dll` so that it knows how to resolve `AlcModule.Engine.dll`.</span></span> <span data-ttu-id="02cb6-312">首先，我們必須定義會從模組其 `Dependencies` 目錄解析組件的自訂 ALC：</span><span class="sxs-lookup"><span data-stu-id="02cb6-312">First we must define our custom ALC that will resolve assemblies from our module's `Dependencies` directory:</span></span>

```csharp
namespace AlcModule.Cmdlets
{
    internal class AlcModuleAssemblyLoadContext : AssemblyLoadContext
    {
        private readonly string _dependencyDirPath;

        public AlcModuleAssemblyLoadContext(string dependencyDirPath)
        {
            _depdendencyDirPath = dependencyDirPath;
        }

        protected override Assembly Load(AssemblyName assemblyName)
        {
            // We do the simple logic here of
            // looking for an assembly of the given name
            // in the configured dependency directory
            string assemblyPath = Path.Combine(
                s_dependencyDirPath,
                $"{assemblyName.Name}.dll");

            // The ALC must use inherited methods to load assemblies
            // Assembly.Load*() won't work here
            return LoadFromAssemblyPath(assemblyPath);
        }
    }
}
```

<span data-ttu-id="02cb6-313">然後，我們需要將自訂 ALC 連接至預設 ALC 的 `Resolving` 事件，這是應用程式定義域中 `AssemblyResolve` 事件的 ALC 版本。</span><span class="sxs-lookup"><span data-stu-id="02cb6-313">Then we need to hook up our custom ALC to the default ALC's `Resolving` event, which is the ALC version of the `AssemblyResolve` event on Application Domains.</span></span> <span data-ttu-id="02cb6-314">當呼叫 `EndProcessing()` 時，就會引發此事件以尋找 `AlcModule.Engine.dll`。</span><span class="sxs-lookup"><span data-stu-id="02cb6-314">This event is fired to find `AlcModule.Engine.dll` when `EndProcessing()` is called.</span></span>

```csharp
namespace AlcModule.Cmdlets
{
    public class AlcModuleResolveEventHandler : IModuleAssemblyInitializer, IModuleAssemblyCleanup
    {
        // Get the path of the dependency directory.
        // In this case we find it relative to the AlcModule.Cmdlets.dll location
        private static readonly string s_dependencyDirPath = Path.GetFullPath(
            Path.Combine(
                Path.GetDirectoryName(Assembly.GetExecutingAssembly().Location),
                "Dependencies"));

        private static readonly AlcModuleAssemblyLoadContext s_dependencyAlc = new AlcModuleAssemblyLoadContext(s_dependencyDirPath);

        public void OnImport()
        {
            // Add the Resolving event handler here
            AssemblyLoadContext.Default.Resolving += ResolveAlcEngine;
        }

        public void OnRemove()
        {
          // Remove the Resolving event handler here
          AssemblyLoadContext.Default.Resolving -= ResolveAlcEngine;
        }

        private static Assembly ResolveAlcEngine(
            AssemblyLoadContext defaultAlc,
            AssemblyName assemblyToResolve)
        {
            // We only want to resolve the Alc.Engine.dll assembly here.
            // Because this will be loaded into the custom ALC,
            // all of *its* dependencies will be resolved
            // by the logic we defined for that ALC's implementation.
            //
            // Note that we are safe in our assumption that the name is enough
            // to distinguish our assembly here,
            // since it's unique to our module.
            // There should be no other AlcModule.Engine.dll on the system.
            if (!assemblyToResolve.Name.Equals("AlcModule.Engine"))
            {
                return null;
            }

            // Allow our ALC to handle the directory discovery concept
            //
            // This is where Alc.Engine.dll is loaded into our custom ALC
            // and then passed through into PowerShell's ALC,
            // becoming the bridge between both
            return s_dependencyAlc.LoadFromAssemblyName(assemblyToResolve);
        }
    }
}
```

<span data-ttu-id="02cb6-315">請藉由新的實作來查看載入模組並執行 `Test-AlcModule` 時所發生的呼叫順序：</span><span class="sxs-lookup"><span data-stu-id="02cb6-315">With the new implementation, take a look at the sequence of calls that occurs when the module is loaded and `Test-AlcModule` is run:</span></span>

![使用自訂 ALC 載入相依性的呼叫順序圖](./media/resolving-dependency-conflicts/alc-sequence.png)

<span data-ttu-id="02cb6-317">要點如下：</span><span class="sxs-lookup"><span data-stu-id="02cb6-317">Some points of interest are:</span></span>

- <span data-ttu-id="02cb6-318">當模組載入並設定 `Resolving` 事件時，會先執行 `IModuleAssemblyInitializer`。</span><span class="sxs-lookup"><span data-stu-id="02cb6-318">The `IModuleAssemblyInitializer` is run first when the module loads and sets the `Resolving` event.</span></span>
- <span data-ttu-id="02cb6-319">執行 `Test-AlcModule` 且呼叫其 `EndProcessing()` 方法後才會載入相依性。</span><span class="sxs-lookup"><span data-stu-id="02cb6-319">We don't load the dependencies until `Test-AlcModule` is run and its `EndProcessing()` method is called.</span></span>
- <span data-ttu-id="02cb6-320">呼叫 `EndProcessing()` 時，預設 ALC 會找不到 `AlcModule.Engine.dll`，並引發 `Resolving` 事件。</span><span class="sxs-lookup"><span data-stu-id="02cb6-320">When `EndProcessing()` is called, the default ALC fails to find `AlcModule.Engine.dll` and fires the `Resolving` event.</span></span>
- <span data-ttu-id="02cb6-321">事件處理常式會將自訂 ALC 連接至預設 ALC，並只載入 `AlcModule.Engine.dll`。</span><span class="sxs-lookup"><span data-stu-id="02cb6-321">Our event handler hooks up the custom ALC to the default ALC and loads `AlcModule.Engine.dll` only.</span></span>
- <span data-ttu-id="02cb6-322">在 `AlcModule.Engine.dll` 中呼叫 `AlcEngine.Use()` 時，自訂 ALC 會再次開始解決 `Shared.Dependency.dll`。</span><span class="sxs-lookup"><span data-stu-id="02cb6-322">When `AlcEngine.Use()` is called within `AlcModule.Engine.dll`, the custom ALC again kicks in to resolve `Shared.Dependency.dll`.</span></span> <span data-ttu-id="02cb6-323">具體而言，一律會載入`Shared.Dependency.dll`，因為其絕對不會與預設 ALC 中的任何內容發生衝突，且只會在 `Dependencies` 目錄中尋找。</span><span class="sxs-lookup"><span data-stu-id="02cb6-323">Specifically, it always loads _our_ `Shared.Dependency.dll` since it never conflicts with anything in the default ALC and only looks in our `Dependencies` directory.</span></span>

<span data-ttu-id="02cb6-324">組合實作時，新的原始程式碼配置看起來會如下：</span><span class="sxs-lookup"><span data-stu-id="02cb6-324">Assembling the implementation, our new source code layout looks like this:</span></span>

```
+ AlcModule.psd1
+ src/
  + AlcModule.Cmdlets/
  | + AlcModule.Cmdlets.csproj
  | + TestAlcModuleCommand.cs
  | + AlcModuleAssemblyLoadContext.cs
  | + AlcModuleInitializer.cs
  |
  + AlcModule.Engine/
  | + AlcModule.Engine.csproj
  | + AlcEngine.cs
```

<span data-ttu-id="02cb6-325">AlcModule.Cmdlets.csproj 看起來如下：</span><span class="sxs-lookup"><span data-stu-id="02cb6-325">AlcModule.Cmdlets.csproj looks like:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <ProjectReference Include="..\AlcModule.Engine\AlcModule.Engine.csproj" />
    <PackageReference Include="Microsoft.PowerShell.Sdk" Version="7.0.1" PrivateAssets="all" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="02cb6-326">AlcModule.Engine.csproj 看起來如下：</span><span class="sxs-lookup"><span data-stu-id="02cb6-326">AlcModule.Engine.csproj looks like this:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Shared.Dependency" Version="1.0.0" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="02cb6-327">因此，建置模組時，我們的策略是：</span><span class="sxs-lookup"><span data-stu-id="02cb6-327">So, when we build the module, our strategy is:</span></span>

- <span data-ttu-id="02cb6-328">建置 `AlcModule.Engine`</span><span class="sxs-lookup"><span data-stu-id="02cb6-328">Build `AlcModule.Engine`</span></span>
- <span data-ttu-id="02cb6-329">建置 `AlcModule.Cmdlets`</span><span class="sxs-lookup"><span data-stu-id="02cb6-329">Build `AlcModule.Cmdlets`</span></span>
- <span data-ttu-id="02cb6-330">將 `AlcModule.Engine` 所有的內容複製到 `Dependencies` 目錄，並記住所複製的內容</span><span class="sxs-lookup"><span data-stu-id="02cb6-330">Copy everything from `AlcModule.Engine` into the `Dependencies` directory, and remember what we copied</span></span>
- <span data-ttu-id="02cb6-331">將 `AlcModule.Engine` 中沒有的全部 `AlcModule.Cmdlets` 內容複製到基底模組目錄</span><span class="sxs-lookup"><span data-stu-id="02cb6-331">Copy everything from `AlcModule.Cmdlets` that wasn't in `AlcModule.Engine` into the base module directory</span></span>

<span data-ttu-id="02cb6-332">因為這裡的模組配置對分隔相依性很重要，所以要從來源根目錄使用建置指令碼：</span><span class="sxs-lookup"><span data-stu-id="02cb6-332">Since the module layout here is so crucial to dependency separation, here's a build script to use from the source root:</span></span>

```powershell
param(
    # The .NET build configuration
    [ValidateSet('Debug', 'Release')]
    [string]
    $Configuration = 'Debug'
)

# Convenient reusable constants
$mod = "AlcModule"
$netcore = "netcoreapp3.1"
$copyExtensions = @('.dll', '.pdb')

# Source code locations
$src = "$PSScriptRoot/src"
$engineSrc = "$src/$mod.Engine"
$cmdletsSrc = "$src/$mod.Cmdlets"

# Generated output locations
$outDir = "$PSScriptRoot/out/$mod"
$outDeps = "$outDir/Dependencies"

# Build AlcModule.Engine
Push-Location $engineSrc
dotnet publish -c $Configuration
Pop-Location

# Build AlcModule.Cmdlets
Push-Location $cmdletsSrc
dotnet publish -c $Configuration
Pop-Location

# Ensure out directory exists and is clean
Remove-Item -Path $outDir -Recurse -ErrorAction Ignore
New-Item -Path $outDir -ItemType Directory
New-Item -Path $outDeps -ItemType Directory

# Copy manifest
Copy-Item -Path "$PSScriptRoot/$mod.psd1"

# Copy each Engine asset and remember it
$deps = [System.Collections.Generic.Hashtable[string]]::new()
Get-ChildItem -Path "$engineSrc/bin/$Configuration/$netcore/publish/" |
    Where-Object { $_.Extension -in $copyExtensions } |
    ForEach-Object { [void]$deps.Add($_.Name); Copy-Item -Path $_.FullName -Destination $outDeps }

# Now copy each Cmdlets asset, not taking any found in Engine
Get-ChildItem -Path "$cmdletsSrc/bin/$Configuration/$netcore/publish/" |
    Where-Object { -not $deps.Contains($_.Name) -and $_.Extension -in $copyExtensions } |
    ForEach-Object { Copy-Item -Path $_.FullName -Destination $outDir }
```

<span data-ttu-id="02cb6-333">最後，我們有個可使用組件載入內容隔離模組其相依性的一般方法，其會隨著與時俱增的相依性保持穩定。</span><span class="sxs-lookup"><span data-stu-id="02cb6-333">Finally, we have a general way to use an Assembly Load Context to isolate our module's dependencies that remains robust over time as more dependencies are added.</span></span>

<span data-ttu-id="02cb6-334">如需更詳細的範例，請參閱此 [GitHub 存放庫](https://github.com/rjmholt/ModuleDependencyIsolationExample)。</span><span class="sxs-lookup"><span data-stu-id="02cb6-334">For a more detailed example, go to this [GitHub repository](https://github.com/rjmholt/ModuleDependencyIsolationExample).</span></span> <span data-ttu-id="02cb6-335">此範例會示範如何移轉模組以使用 ALC，同時讓該模組能在 .NET Framework 中繼續運作。</span><span class="sxs-lookup"><span data-stu-id="02cb6-335">This example demonstrates how to migrate a module to use an ALC, while keeping that module working in .NET Framework.</span></span> <span data-ttu-id="02cb6-336">其也會示範如何使用 .NET Standard 和 PowerShell Standard 來簡化核心實作。</span><span class="sxs-lookup"><span data-stu-id="02cb6-336">It also show how to use .NET Standard and PowerShell Standard to simplify the core implementation.</span></span>

### <a name="assembly-resolve-handler-for-side-by-side-loading-with-assemblyloadfile"></a><span data-ttu-id="02cb6-337">搭配 `Assembly.LoadFile()` 用於並存載入的組件解析處理常式</span><span class="sxs-lookup"><span data-stu-id="02cb6-337">Assembly resolve handler for side-by-side loading with `Assembly.LoadFile()`</span></span>

<span data-ttu-id="02cb6-338">另一個可能較容易達到載入並存組件的方法，是將 `AssemblyResolve` 事件連接到 `Assembly.LoadFile()`。</span><span class="sxs-lookup"><span data-stu-id="02cb6-338">Another, possibly simpler, way to achieve side-by-side assembly loading is to hook up an `AssemblyResolve` event to `Assembly.LoadFile()`.</span></span> <span data-ttu-id="02cb6-339">使用 `Assembly.LoadFile()` 的優點是，這是實作及使用 .NET Core 和 .NET Framework 的最簡單解決方案。</span><span class="sxs-lookup"><span data-stu-id="02cb6-339">Using `Assembly.LoadFile()` has the advantage of being the simplest solution to implement and works with both .NET Core and .NET Framework.</span></span>

<span data-ttu-id="02cb6-340">讓我們以一個快速的實作範例示範，其結合了動態繫結重新導向範例的想法，以及前文的組件載入內容範例。</span><span class="sxs-lookup"><span data-stu-id="02cb6-340">To show this, let's take a look at a quick example of an implementation that combines ideas from our dynamic binding redirect example, and the Assembly Load Context example above.</span></span>

<span data-ttu-id="02cb6-341">此模組稱為 **LoadFileModule**，其擁有一般的命令 `Test-LoadFile [-Path] <path>`。</span><span class="sxs-lookup"><span data-stu-id="02cb6-341">We'll call this module **LoadFileModule**, which has a trivial command `Test-LoadFile [-Path] <path>`.</span></span> <span data-ttu-id="02cb6-342">此模組相依於 `CsvHelper` 組件 (15.0.5 版)。</span><span class="sxs-lookup"><span data-stu-id="02cb6-342">This module takes a dependency on the `CsvHelper` assembly (version 15.0.5).</span></span>

<span data-ttu-id="02cb6-343">和 ALC 模組一樣，我們必須先將模組分為兩部分。</span><span class="sxs-lookup"><span data-stu-id="02cb6-343">As with the ALC module, we must first split up the module into two pieces.</span></span>

<span data-ttu-id="02cb6-344">第一個部分負責實際的實作，即 `LoadFileModule.Engine`：</span><span class="sxs-lookup"><span data-stu-id="02cb6-344">The first part does the actual implementation, `LoadFileModule.Engine`:</span></span>

```csharp
using CsvHelper;

namespace LoadFileModule.Engine
{
    public class Runner
    {
        public void Use(string path)
        {
            // Here's where we use the CsvHelper dependency
            using (var reader = new StreamReader(path))
            using (var csvReader = new CsvReader(reader, CultureInfo.InvariantCulture))
            {
                // Imagine we do something useful here...
            }
        }
    }
}
```

<span data-ttu-id="02cb6-345">第二個部分是 PowerShell 直接載入的內容，即 `LoadFileModule.Cmdlets`。</span><span class="sxs-lookup"><span data-stu-id="02cb6-345">The second part is what PowerShell loads directly, `LoadFileModule.Cmdlets`.</span></span> <span data-ttu-id="02cb6-346">我們使用的策略與 ALC 模組雷同，將相依性隔離在不同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="02cb6-346">We use a strategy similar to the ALC module, where we isolate dependencies in a separate directory.</span></span> <span data-ttu-id="02cb6-347">但是這一次，我們會載入所有包含解析事件的組件，而不僅是 `LoadFileModule.Engine.dll`。</span><span class="sxs-lookup"><span data-stu-id="02cb6-347">But this time, we load all assemblies in with a resolve event rather than just `LoadFileModule.Engine.dll`.</span></span>

```csharp
using LoadFileModule.Engine;

namespace LoadFileModule.Cmdlets
{
    // Actual cmdlet definition
    [Cmdlet(VerbsDiagnostic.Test, "LoadFile")]
    public class TestLoadFileCommand : Cmdlet
    {
        [Parameter(Mandatory = true)]
        public string Path { get; set; }

        protected override void EndProcessing()
        {
            // Here's where we use LoadFileModule.Engine
            new Runner().Use(Path);
        }
    }

    // This class controls our dependency resolution
    public class ModuleContextHandler : IModuleAssemblyInitializer, IModuleAssemblyCleanup
    {
        // We catalog our dependencies here to ensure we don't load anything else
        private static IReadOnlyDictionary<string, int> s_dependencies = new Dictionary<string, int>
        {
            { "CsvHelper", 15 },
        };

        // Set up the path to our dependency directory within the module
        private static string s_dependenciesDirPath = Path.GetFullPath(
            Path.Combine(
                Path.GetDirectoryName(Assembly.GetExecutingAssembly().Location),
                "Dependencies"));

        // This makes sure we only try to resolve dependencies when the module is loaded
        private static bool s_engineLoaded = false;

        public void OnImport()
          {
            // Set up our event when the module is loaded
            AppDomain.CurrentDomain.AssemblyResolve += HandleResolveEvent;
        }

        public void OnRemove(PSModuleInfo psModuleInfo)
        {
            // Unset the event when the module is unloaded
            AppDomain.CurrentDomain.AssemblyResolve -= HandleResolveEvent;
        }

        private static Assembly HandleResolveEvent(object sender, ResolveEventArgs args)
        {
            var asmName = new AssemblyName(args.Name);

            // First we want to know if this is the top-level assembly
            if (asmName.Name.Equals("LoadFileModule.Engine"))
            {
                s_engineLoaded = true;
                return Assembly.LoadFile(Path.Combine(s_dependenciesDirPath, "Unrelated.Engine.dll"));
            }

            // Otherwise, if that assembly has been loaded, we must try to resolve its dependencies too
            if (s_engineLoaded
                && s_dependencies.TryGetValue(asmName.Name, out int requiredMajorVersion)
                && asmName.Version.Major == requiredMajorVersion)
            {
                string asmPath = Path.Combine(s_dependenciesDirPath, $"{asmName.Name}.dll");
                return Assembly.LoadFile(asmPath);
            }

            return null;
        }
    }
}
```

<span data-ttu-id="02cb6-348">最後，模組的配置也與 ALC 模組雷同：</span><span class="sxs-lookup"><span data-stu-id="02cb6-348">Finally, the layout of the module is also similar to the ALC module:</span></span>

```
LoadFileModule/
  + LoadFileModule.Cmdlets.dll
  + LoadFileModule.psd1
  + Dependencies/
  |  + LoadFileModule.Engine.dll
  |  + CsvHelper.dll
```

<span data-ttu-id="02cb6-349">在此結構就緒後，**LoadFileModule** 現可支援與其他模組一起載入，且有 **CsvHelper** 相依性。</span><span class="sxs-lookup"><span data-stu-id="02cb6-349">With this structure in place, **LoadFileModule** now supports being loaded alongside other modules with a dependency on **CsvHelper**.</span></span>

<span data-ttu-id="02cb6-350">因為處理常式適用於整個應用程式定義域的**所有** `AssemblyResolve` 事件，所以我們必須在此設計一些特定選項：</span><span class="sxs-lookup"><span data-stu-id="02cb6-350">Because our handler applies to **all** `AssemblyResolve` events across the Application Domain, we need to make some specific design choices here:</span></span>

- <span data-ttu-id="02cb6-351">為縮小事件可能會干擾其他載入的時間範圍，我們只會在載入 `LoadFileModule.Engine.dll` 之後，再開始處理一般相依性載入。</span><span class="sxs-lookup"><span data-stu-id="02cb6-351">To narrow the window in which our event may interfere with other loading, we only start handling general dependency loading after `LoadFileModule.Engine.dll` has been loaded.</span></span>
- <span data-ttu-id="02cb6-352">我們會將 `LoadFileModule.Engine.dll` 推送至相依性目錄，使其由 `LoadFile()` 呼叫載入，而不是由 PowerShell 載入。</span><span class="sxs-lookup"><span data-stu-id="02cb6-352">We push `LoadFileModule.Engine.dll` out into the Dependencies directory, so that it's loaded by a `LoadFile()` call rather than by PowerShell.</span></span> <span data-ttu-id="02cb6-353">這表示它自己的相依性載入一律會引發 `AssemblyResolve` 事件，即使 PowerShell 中已載入另一個 (例如) `CsvHelper.dll`。</span><span class="sxs-lookup"><span data-stu-id="02cb6-353">This means its own dependency loads always raise an `AssemblyResolve` event, even if another `CsvHelper.dll` (for example) is loaded in PowerShell.</span></span>
  <span data-ttu-id="02cb6-354">這讓我們有機會找出正確的相依性。</span><span class="sxs-lookup"><span data-stu-id="02cb6-354">This gives us the opportunity to find the correct dependency.</span></span>
- <span data-ttu-id="02cb6-355">因為我們必須只解析模組的特定相依性，所以我們不得不將相依性名稱和版本的字典編碼成處理常式。</span><span class="sxs-lookup"><span data-stu-id="02cb6-355">Since we must only resolve the specific dependencies for our module, we're forced to code a dictionary of dependency names and versions into our handler.</span></span> <span data-ttu-id="02cb6-356">在特定情況下，可使用 `ResolveEventArgs.RequestingAssembly` 屬性來得知模組是否正在要求 `CsvHelper`。</span><span class="sxs-lookup"><span data-stu-id="02cb6-356">In our particular case, it would be possible to use the `ResolveEventArgs.RequestingAssembly` property to work out whether `CsvHelper` is being requested by our module.</span></span> <span data-ttu-id="02cb6-357">但這對相依性的相依性無效；例如，如果 `CsvHelper` 本身引發了 `AssemblyResolve` 事件。</span><span class="sxs-lookup"><span data-stu-id="02cb6-357">But this doesn't work for dependencies of dependencies; for example, if `CsvHelper` itself raised an `AssemblyResolve` event.</span></span> <span data-ttu-id="02cb6-358">還有其他更困難的方法可執行這項操作，例如比較要求的組件與 `Dependencies` 目錄中的組件中繼資料。</span><span class="sxs-lookup"><span data-stu-id="02cb6-358">There are other, harder ways to do this, such as comparing requested assemblies to the metadata of assemblies in the `Dependencies` directory.</span></span> <span data-ttu-id="02cb6-359">但是在此範例中，我們既醒目提示了問題又簡化了範例，讓這項檢查變得更明確。</span><span class="sxs-lookup"><span data-stu-id="02cb6-359">But, in this example, we've made this checking more explicit to both highlight the issue and simplify the example.</span></span>

<span data-ttu-id="02cb6-360">這是 `LoadFile()` 策略與 ALC 策略之間的主要差異：`AssemblyResolve` 事件必須為應用程式定義域中的所有載入提供服務，讓相依性解析變得更困難，以免與其他模組糾纏不休。</span><span class="sxs-lookup"><span data-stu-id="02cb6-360">This is the key difference between the `LoadFile()` strategy and the ALC strategy: the `AssemblyResolve` event must service all loads in the Application Domain, making it much harder to keep our dependency resolution from being tangled with other modules.</span></span> <span data-ttu-id="02cb6-361">不過，.NET Framework 中缺少 ALC 讓此選項更值得了解。</span><span class="sxs-lookup"><span data-stu-id="02cb6-361">However, the lack of ALCs in .NET Framework makes this option worth understanding.</span></span>

### <a name="custom-application-domains"></a><span data-ttu-id="02cb6-362">自訂的應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="02cb6-362">Custom Application Domains</span></span>

<span data-ttu-id="02cb6-363">組件隔離的最後一個，也是最極端的選項，是使用自訂的應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="02cb6-363">The final and most extreme option for assembly isolation is to use custom Application Domains.</span></span>
<span data-ttu-id="02cb6-364">應用程式定義域 (複數名詞) 只能在 .NET Framework 中使用。</span><span class="sxs-lookup"><span data-stu-id="02cb6-364">Application Domains (used in the plural) are only available in .NET Framework.</span></span> <span data-ttu-id="02cb6-365">其可用來半隔離 .NET 應用程式的各組件。</span><span class="sxs-lookup"><span data-stu-id="02cb6-365">They are used to provide in-process isolation between parts of a .NET application.</span></span> <span data-ttu-id="02cb6-366">其中一個用途是隔離同一程序中的組件載入。</span><span class="sxs-lookup"><span data-stu-id="02cb6-366">One of the uses is to isolate assembly loads from each other within the same process.</span></span>

<span data-ttu-id="02cb6-367">不過，應用程式定義域是序列化界限。</span><span class="sxs-lookup"><span data-stu-id="02cb6-367">However, Application Domains are serialization boundaries.</span></span> <span data-ttu-id="02cb6-368">一個應用程式定義域中物件無法直接參考及使用另一個應用程式定義域中的物件。</span><span class="sxs-lookup"><span data-stu-id="02cb6-368">Objects in one Application Domain can't be referenced and used directly by objects in another Application Domain.</span></span> <span data-ttu-id="02cb6-369">您可實作 `MarshalByRefObject` 以暫時解決這個問題。</span><span class="sxs-lookup"><span data-stu-id="02cb6-369">You can work around this by implementing `MarshalByRefObject`.</span></span> <span data-ttu-id="02cb6-370">但是若不控制類型，因為相依性常有這種情況，就無法在此強制實作。</span><span class="sxs-lookup"><span data-stu-id="02cb6-370">But when you don't control the types, as is often the case with dependencies, it's not possible to force an implementation here.</span></span> <span data-ttu-id="02cb6-371">大型架構化變更是唯一的解決之道。</span><span class="sxs-lookup"><span data-stu-id="02cb6-371">The only solution is to make large architectural changes.</span></span> <span data-ttu-id="02cb6-372">序列化界限也會對效能造成嚴重影響。</span><span class="sxs-lookup"><span data-stu-id="02cb6-372">The serialization boundary also has serious performance implications.</span></span>

<span data-ttu-id="02cb6-373">因為應用程式定義域具有這項重大限制，實作很複雜，且只在 .NET Framework 中有效，所以本文不舉例示範使用方法。</span><span class="sxs-lookup"><span data-stu-id="02cb6-373">Because Application Domains have this serious limitation, are complicated to implement, and only work in .NET Framework, we won't give an example of how you might use them here.</span></span> <span data-ttu-id="02cb6-374">雖然值得一提，但不建議這麼做。</span><span class="sxs-lookup"><span data-stu-id="02cb6-374">While they're worth mentioning as a possibility, they're not recommended.</span></span>

<span data-ttu-id="02cb6-375">如果想要嘗試使用自訂的應用程式定義域，下列連結可能會有所幫助：</span><span class="sxs-lookup"><span data-stu-id="02cb6-375">If you're interested in trying to use a custom Application Domain, the following links might help:</span></span>

- [<span data-ttu-id="02cb6-376">有關應用程式定義域概念的文件</span><span class="sxs-lookup"><span data-stu-id="02cb6-376">Conceptual documentation on Application Domains</span></span>](/dotnet/framework/app-domains/application-domains)
- [<span data-ttu-id="02cb6-377">使用應用程式定義域的範例</span><span class="sxs-lookup"><span data-stu-id="02cb6-377">Examples for using Application Domains</span></span>](/dotnet/framework/app-domains/use)

## <a name="solutions-for-dependency-conflicts-that-dont-work-for-powershell"></a><span data-ttu-id="02cb6-378">不適用於 PowerShell 的相依性衝突解決方案</span><span class="sxs-lookup"><span data-stu-id="02cb6-378">Solutions for dependency conflicts that don't work for PowerShell</span></span>

<span data-ttu-id="02cb6-379">最後，我們會討論在研究 .NET 的 .NET 相依性衝突時看起來很有希望的可能方案，但這些通常不適用於 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="02cb6-379">Finally, we'll address some possibilities that come up when researching .NET dependency conflicts in .NET that can look promising, but generally won't work for PowerShell.</span></span>

<span data-ttu-id="02cb6-380">這些解決方案的共同主題是，會變更您控制應用程式，甚至可能是整部電腦的環境部署組態。</span><span class="sxs-lookup"><span data-stu-id="02cb6-380">These solutions have the common theme that they are changes to deployment configurations for an environment where you control the application and possibly the entire machine.</span></span> <span data-ttu-id="02cb6-381">這些解決方案所適用案例為網頁伺服器和其他部署至伺服器環境的應用程式，此環境旨在裝載應用程式，且可供部署使用者自由設定。</span><span class="sxs-lookup"><span data-stu-id="02cb6-381">These solutions are oriented toward scenarios like web servers and other applications deployed to server environments, where the environment is intended to host the application and is free to be configured by the deploying user.</span></span> <span data-ttu-id="02cb6-382">其也非常適合 .NET Framework，這表示其不適用於 PowerShell 6 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="02cb6-382">They also tend to be very much .NET Framework oriented, meaning they do not work with PowerShell 6 or above.</span></span>

<span data-ttu-id="02cb6-383">如果確定模組僅用在您擁有完全控制權的 Windows PowerShell 5.1 環境中，則可嘗試其中一些方案。</span><span class="sxs-lookup"><span data-stu-id="02cb6-383">If you know that your module is only used in Windows PowerShell 5.1 environments that you have total control over, some of these may be options.</span></span> <span data-ttu-id="02cb6-384">不過，總而言之，**模組不應以此方式修改全域電腦狀態**。</span><span class="sxs-lookup"><span data-stu-id="02cb6-384">In general however, **modules should not modify global machine state like this**.</span></span> <span data-ttu-id="02cb6-385">這會中斷組態，導致 `powershell.exe`、其他模組，或造成模組以非預期方式失敗的其他相依應用程式發生問題。</span><span class="sxs-lookup"><span data-stu-id="02cb6-385">It can break configurations that cause problems in `powershell.exe`, other modules, or other dependent applications that cause your module to fail in unexpected ways.</span></span>

### <a name="static-binding-redirect-with-appconfig-to-force-using-the-same-dependency-version"></a><span data-ttu-id="02cb6-386">使用 app.config 重新導向靜態繫結，以強制使用相同的相依性版本</span><span class="sxs-lookup"><span data-stu-id="02cb6-386">Static binding redirect with app.config to force using the same dependency version</span></span>

<span data-ttu-id="02cb6-387">.NET Framework 應用程式可利用 `app.config` 檔案，以宣告方式設定應用程式的部分行為。</span><span class="sxs-lookup"><span data-stu-id="02cb6-387">.NET Framework applications can take advantage of an `app.config` file to configure some of the application's behaviors declaratively.</span></span> <span data-ttu-id="02cb6-388">您可撰寫 `app.config` 項目，將組件繫結設定為將組件載入重新導向至特定版本。</span><span class="sxs-lookup"><span data-stu-id="02cb6-388">It's possible to write an `app.config` entry that configures assembly binding to redirect assembly loading to a particular version.</span></span>

<span data-ttu-id="02cb6-389">PowerShell 有關這方面的兩個問題如下：</span><span class="sxs-lookup"><span data-stu-id="02cb6-389">Two issues with this for PowerShell are:</span></span>

- <span data-ttu-id="02cb6-390">.NET Core 不支援 `app.config`，所以此方案僅適用於 `powershell.exe`。</span><span class="sxs-lookup"><span data-stu-id="02cb6-390">.NET Core does not support `app.config`, so this solution only applies to `powershell.exe`.</span></span>
- <span data-ttu-id="02cb6-391">`powershell.exe` 是存在於 `System32` 目錄中的共用應用程式。</span><span class="sxs-lookup"><span data-stu-id="02cb6-391">`powershell.exe` is a shared application that lives in the `System32` directory.</span></span> <span data-ttu-id="02cb6-392">在許多系統上，模組很可能無法修改其內容。</span><span class="sxs-lookup"><span data-stu-id="02cb6-392">It's likely that your module won't be able to modify its contents on many systems.</span></span> <span data-ttu-id="02cb6-393">即使可以，修改 `app.config` 可能會中斷現有組態，或影響其他模組載入。</span><span class="sxs-lookup"><span data-stu-id="02cb6-393">Even if it can, modifying the `app.config` could break an existing configuration or affect the loading of other modules.</span></span>

### <a name="setting-codebase-with-appconfig"></a><span data-ttu-id="02cb6-394">使用 app.config 設定 `codebase`</span><span class="sxs-lookup"><span data-stu-id="02cb6-394">Setting `codebase` with app.config</span></span>

<span data-ttu-id="02cb6-395">基於相同的原因，嘗試在 `app.config` 中進行 `codebase` 設定在 PowerShell 模組中無效。</span><span class="sxs-lookup"><span data-stu-id="02cb6-395">For the same reasons, trying to configure the `codebase` setting in `app.config` is not going to work in PowerShell modules.</span></span>

### <a name="installing-dependencies-to-the-global-assembly-cache-gac"></a><span data-ttu-id="02cb6-396">將相依性安裝到全域組件快取 (GAC)</span><span class="sxs-lookup"><span data-stu-id="02cb6-396">Installing dependencies to the Global Assembly Cache (GAC)</span></span>

<span data-ttu-id="02cb6-397">解析 .NET Framework 相依性版本衝突的另一個方法是將相依性安裝到 GAC，以從 GAC 並存載入不同的版本。</span><span class="sxs-lookup"><span data-stu-id="02cb6-397">Another way to resolve dependency version conflicts in .NET Framework is to install dependencies to the GAC, so that different versions can be loaded side-by-side from the GAC.</span></span>

<span data-ttu-id="02cb6-398">再次說明，PowerShell 模組的主要問題是：</span><span class="sxs-lookup"><span data-stu-id="02cb6-398">Again, for PowerShell modules, the chief issues here are:</span></span>

- <span data-ttu-id="02cb6-399">GAC 僅適用於 .NET Framework，所以這對 PowerShell 6 和更新版本沒有幫助。</span><span class="sxs-lookup"><span data-stu-id="02cb6-399">The GAC only applies to .NET Framework, so this does not help in PowerShell 6 and above.</span></span>
- <span data-ttu-id="02cb6-400">將組件安裝到 GAC 會修改全域電腦狀態，且可能對其他應用程式或其他模組產生副作用。</span><span class="sxs-lookup"><span data-stu-id="02cb6-400">Installing assemblies to the GAC is a modification of global machine state and may cause side-effects in other applications or to other modules.</span></span> <span data-ttu-id="02cb6-401">即使模組具有必要的存取權限，也不容易正確執行。</span><span class="sxs-lookup"><span data-stu-id="02cb6-401">It may also be difficult to do correctly, even when your module has the required access privileges.</span></span> <span data-ttu-id="02cb6-402">如果發生錯誤，可能會造成其他 .NET 應用程式嚴重的全電腦問題。</span><span class="sxs-lookup"><span data-stu-id="02cb6-402">Getting it wrong could cause serious, machine-wide issues in other .NET applications.</span></span>

## <a name="further-reading"></a><span data-ttu-id="02cb6-403">進一步閱讀</span><span class="sxs-lookup"><span data-stu-id="02cb6-403">Further reading</span></span>

<span data-ttu-id="02cb6-404">.NET 組件版本相依性衝突還有許多內容值得了解。</span><span class="sxs-lookup"><span data-stu-id="02cb6-404">There's plenty more to read on .NET assembly version dependency conflicts.</span></span> <span data-ttu-id="02cb6-405">以下是一些不錯的起點：</span><span class="sxs-lookup"><span data-stu-id="02cb6-405">Here are some nice jumping off points:</span></span>

- [<span data-ttu-id="02cb6-406">.NET：.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="02cb6-406">.NET: Assemblies in .NET</span></span>](/dotnet/standard/assembly/)
- [<span data-ttu-id="02cb6-407">.NET Core：受控組件載入演算法</span><span class="sxs-lookup"><span data-stu-id="02cb6-407">.NET Core: The managed assembly loading algorithm</span></span>](/dotnet/core/dependency-loading/loading-managed)
- [<span data-ttu-id="02cb6-408">.NET Core：了解 System.Runtime.Loader.AssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="02cb6-408">.NET Core: Understanding System.Runtime.Loader.AssemblyLoadContext</span></span>](/dotnet/core/dependency-loading/understanding-assemblyloadcontext)
- [<span data-ttu-id="02cb6-409">.NET Core：討論有關並存組件載入的解決方案</span><span class="sxs-lookup"><span data-stu-id="02cb6-409">.NET Core: Discussion about side-by-side assembly loading solutions</span></span>](https://github.com/dotnet/runtime/issues/13471)
- [<span data-ttu-id="02cb6-410">.NET Framework：重新導向組件版本</span><span class="sxs-lookup"><span data-stu-id="02cb6-410">.NET Framework: Redirecting assembly versions</span></span>](/dotnet/framework/configure-apps/redirect-assembly-versions)
- [<span data-ttu-id="02cb6-411">.NET Framework：組件載入的最佳做法</span><span class="sxs-lookup"><span data-stu-id="02cb6-411">.NET Framework: Best practices for assembly loading</span></span>](/dotnet/framework/deployment/best-practices-for-assembly-loading)
- [<span data-ttu-id="02cb6-412">.NET Framework：執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="02cb6-412">.NET Framework: How the runtime locates assemblies</span></span>](/dotnet/framework/deployment/how-the-runtime-locates-assemblies)
- [<span data-ttu-id="02cb6-413">.NET Framework：解析組件載入</span><span class="sxs-lookup"><span data-stu-id="02cb6-413">.NET Framework: Resolve assembly loads</span></span>](/dotnet/standard/assembly/resolve-loads)
- <span data-ttu-id="02cb6-414">[StackOverflow：Assembly binding redirect, how and why?](https://stackoverflow.com/questions/43365736/assembly-binding-redirect-how-and-why) (組件繫結重新導向：方法及原因？)</span><span class="sxs-lookup"><span data-stu-id="02cb6-414">[StackOverflow: Assembly binding redirect, how and why?](https://stackoverflow.com/questions/43365736/assembly-binding-redirect-how-and-why)</span></span>
- [<span data-ttu-id="02cb6-415">PowerShell：討論如何實作 AssemblyLoadCoNtexts</span><span class="sxs-lookup"><span data-stu-id="02cb6-415">PowerShell: Discussion about implementing AssemblyLoadContexts</span></span>](https://github.com/PowerShell/PowerShell/issues/11571)
- [<span data-ttu-id="02cb6-416">PowerShell：`Assembly.LoadFile()` 不會載入至預設的 AssemblyLoadCoNtext</span><span class="sxs-lookup"><span data-stu-id="02cb6-416">PowerShell: `Assembly.LoadFile()` doesn't load into default AssemblyLoadContext</span></span>](https://github.com/PowerShell/PowerShell/issues/12052)
- <span data-ttu-id="02cb6-417">[Rick Strahl：When does a .NET assembly dependency get loaded?](https://weblog.west-wind.com/posts/2012/Nov/03/Back-to-Basics-When-does-a-NET-Assembly-Dependency-get-loaded) (何時會載入 .NET 組件相依性？)</span><span class="sxs-lookup"><span data-stu-id="02cb6-417">[Rick Strahl: When does a .NET assembly dependency get loaded?](https://weblog.west-wind.com/posts/2012/Nov/03/Back-to-Basics-When-does-a-NET-Assembly-Dependency-get-loaded)</span></span>
- [<span data-ttu-id="02cb6-418">Jon Skeet：.NET 的版本控制摘要</span><span class="sxs-lookup"><span data-stu-id="02cb6-418">Jon Skeet: Summary of versioning in .NET</span></span>](https://codeblog.jonskeet.uk/2019/06/30/versioning-limitations-in-net/)
- <span data-ttu-id="02cb6-419">[Nate McMaster：Deep dive into .NET Core primitives](https://natemcmaster.com/blog/2017/12/21/netcore-primitives/) (深入探討 .NET Core 的基本類型)</span><span class="sxs-lookup"><span data-stu-id="02cb6-419">[Nate McMaster: Deep dive into .NET Core primitives](https://natemcmaster.com/blog/2017/12/21/netcore-primitives/)</span></span>
