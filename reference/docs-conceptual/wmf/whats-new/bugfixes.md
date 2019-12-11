---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,設定
title: WMF 5.1 的 Bug 修正
ms.openlocfilehash: 8edf295eb6304dc04de2fa5d3792b1c2fc4b01f3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "71147848"
---
# <a name="bug-fixes-in-wmf-51"></a><span data-ttu-id="3ef1e-103">WMF 5.1 的 Bug 修正</span><span class="sxs-lookup"><span data-stu-id="3ef1e-103">Bug Fixes in WMF 5.1</span></span>

## <a name="bug-fixes"></a><span data-ttu-id="3ef1e-104">Bug 修正</span><span class="sxs-lookup"><span data-stu-id="3ef1e-104">Bug fixes</span></span>

<span data-ttu-id="3ef1e-105">WMF 5.1 已修正下列重大 Bug︰</span><span class="sxs-lookup"><span data-stu-id="3ef1e-105">The following notable bugs are fixed in WMF 5.1:</span></span>

### <a name="module-auto-discovery-fully-honors-psmodulepath"></a><span data-ttu-id="3ef1e-106">完全接受模組自動探索 PSModulePath</span><span class="sxs-lookup"><span data-stu-id="3ef1e-106">Module auto-discovery fully honors PSModulePath</span></span>

<span data-ttu-id="3ef1e-107">WMF 3 中引進了模組自動探索 (呼叫命令時自動載入模組，不需要明確的 Import-Module)。</span><span class="sxs-lookup"><span data-stu-id="3ef1e-107">Module auto-discovery (loading modules automatically without an explicit Import-Module when calling a command) was introduced in WMF 3.</span></span> <span data-ttu-id="3ef1e-108">當初引入後，PowerShell 會先檢查 `$PSHome\Modules` 中有沒有命令，再使用 `$env:PSModulePath`。</span><span class="sxs-lookup"><span data-stu-id="3ef1e-108">When introduced, PowerShell checked for commands in `$PSHome\Modules` before using `$env:PSModulePath`.</span></span>

<span data-ttu-id="3ef1e-109">WMF 5.1 將此行為變更為完全接受 `$env:PSModulePath`。</span><span class="sxs-lookup"><span data-stu-id="3ef1e-109">WMF 5.1 changes this behavior to honor `$env:PSModulePath` completely.</span></span> <span data-ttu-id="3ef1e-110">這讓使用者撰寫之定義 PowerShell 所提供命令的模組 (例如 `Get-ChildItem`) 自動載入並正確覆寫內建的命令。</span><span class="sxs-lookup"><span data-stu-id="3ef1e-110">This allows for a user-authored module that defines commands provided by PowerShell (e.g. `Get-ChildItem`) to be auto-loaded and correctly overriding the built-in command.</span></span>

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a><span data-ttu-id="3ef1e-111">檔案重新導向不再硬式編碼 -Encoding Unicode</span><span class="sxs-lookup"><span data-stu-id="3ef1e-111">File redirection no longer hard-codes -Encoding Unicode</span></span>

<span data-ttu-id="3ef1e-112">在所有舊版的 PowerShell 中，都無法控制檔案重新導向運算子所使用的檔案編碼。</span><span class="sxs-lookup"><span data-stu-id="3ef1e-112">In all previous versions of PowerShell, it was impossible to control the file encoding used by the file redirection operator.</span></span>

<span data-ttu-id="3ef1e-113">但從 WMF 5.1 開始，您可以設定 `$PSDefaultParameterValues` 來變更重新導向的檔案編碼方式︰</span><span class="sxs-lookup"><span data-stu-id="3ef1e-113">Starting with WMF 5.1, you can now change the file encoding of redirection by setting `$PSDefaultParameterValues`:</span></span>

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a><span data-ttu-id="3ef1e-114">已修正存取 System.Reflection.TypeInfo 成員的迴歸</span><span class="sxs-lookup"><span data-stu-id="3ef1e-114">Fixed a regression in accessing members of System.Reflection.TypeInfo</span></span>

<span data-ttu-id="3ef1e-115">WMF 5.0 中引進的迴歸會中斷存取 `System.Reflection.RuntimeType` 的成員，例如 `[int].ImplementedInterfaces`。</span><span class="sxs-lookup"><span data-stu-id="3ef1e-115">A regression introduced in WMF 5.0 broke accessing members of `System.Reflection.RuntimeType`, for example, `[int].ImplementedInterfaces`.</span></span> <span data-ttu-id="3ef1e-116">WMF 5.1 已修正這個 Bug。</span><span class="sxs-lookup"><span data-stu-id="3ef1e-116">This bug has been fixed in WMF 5.1.</span></span>

### <a name="fixed-some-issues-with-com-objects"></a><span data-ttu-id="3ef1e-117">修正 COM 物件的一些問題</span><span class="sxs-lookup"><span data-stu-id="3ef1e-117">Fixed some issues with COM objects</span></span>

<span data-ttu-id="3ef1e-118">WMF 5.0 引入新的 COM 繫結器，可對 COM 物件叫用方法以及存取 COM 物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="3ef1e-118">WMF 5.0 introduced a new COM binder for invoking methods on COM objects and accessing properties of COM objects.</span></span> <span data-ttu-id="3ef1e-119">此新的繫結器大幅改善了效能，卻也造成了一些 Bug，WMF5.1 已加以修正。</span><span class="sxs-lookup"><span data-stu-id="3ef1e-119">This new binder improved performance significantly but also introduced some bugs which have been fixed in WMF 5.1.</span></span>

#### <a name="argument-conversions-were-not-always-performed-correctly"></a><span data-ttu-id="3ef1e-120">不一定會正確執行引數轉換</span><span class="sxs-lookup"><span data-stu-id="3ef1e-120">Argument conversions were not always performed correctly</span></span>

<span data-ttu-id="3ef1e-121">在下例中︰</span><span class="sxs-lookup"><span data-stu-id="3ef1e-121">In the following example:</span></span>

```powershell
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

<span data-ttu-id="3ef1e-122">**SendKeys** 方法預期的是字串，但 PowerShell 並未將字元轉換成字串，將轉換延後至 **IDispatch::Invoke**，其使用 **VariantChangeType** 進行轉換。</span><span class="sxs-lookup"><span data-stu-id="3ef1e-122">The **SendKeys** method expects a string, but PowerShell did not convert the char to a string, deferring the conversion to **IDispatch::Invoke**, which uses **VariantChangeType** to do the conversion.</span></span> <span data-ttu-id="3ef1e-123">在此範例中，這導致所傳送的是索引鍵 '1'、'7' 和 '3'，而非預期的 **Volume.Mute** 索引鍵。</span><span class="sxs-lookup"><span data-stu-id="3ef1e-123">In this example, this resulted in sending the keys '1', '7', and '3' instead of the expected **Volume.Mute** key.</span></span>

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a><span data-ttu-id="3ef1e-124">不一定會正確處理可列舉的 COM 物件</span><span class="sxs-lookup"><span data-stu-id="3ef1e-124">Enumerable COM objects not always handled correctly</span></span>

<span data-ttu-id="3ef1e-125">PowerShell 通常會列舉大部分可列舉的物件，但 WMF 5.0 引入的迴歸卻阻擋了列舉實作 IEnumerable 的 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="3ef1e-125">PowerShell normally enumerates most enumerable objects, but a regression introduced in WMF 5.0 prevented the enumeration of COM objects that implement IEnumerable.</span></span> <span data-ttu-id="3ef1e-126">例如：</span><span class="sxs-lookup"><span data-stu-id="3ef1e-126">For example:</span></span>

```powershell
function Get-COMDictionary
{
    $d = New-Object -ComObject Scripting.Dictionary
    $d.Add('a', 2)
    $d.Add('b', 2)
    return $d
}

$x = Get-COMDictionary
```

<span data-ttu-id="3ef1e-127">在上例中，WMF 5.0 誤將 **Scripting.Dictionary** 寫入至管線，而不是列舉索引鍵/值組。</span><span class="sxs-lookup"><span data-stu-id="3ef1e-127">In the above example, WMF 5.0 incorrectly wrote the **Scripting.Dictionary** to the pipeline instead of enumerating the key/value pairs.</span></span>

### <a name="ordered-was-not-allowed-inside-classes"></a><span data-ttu-id="3ef1e-128">類別內不允許 [ordered]</span><span class="sxs-lookup"><span data-stu-id="3ef1e-128">[ordered] was not allowed inside classes</span></span>

<span data-ttu-id="3ef1e-129">WMF 5.0 引入了類別，其具有類別所用的類型常值驗證。</span><span class="sxs-lookup"><span data-stu-id="3ef1e-129">WMF 5.0 introduced classes with validation of type literals used in classes.</span></span> <span data-ttu-id="3ef1e-130">`[ordered]` 看起來像類型常值，卻不是真正的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="3ef1e-130">`[ordered]` looks like a type literal but is not a true .NET type.</span></span> <span data-ttu-id="3ef1e-131">WMF 5.0 誤報類別內發生 `[ordered]` 錯誤︰</span><span class="sxs-lookup"><span data-stu-id="3ef1e-131">WMF 5.0 incorrectly reported an error on `[ordered]` inside a class:</span></span>

```powershell
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```

### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a><span data-ttu-id="3ef1e-132">多版本的說明主題無法運作</span><span class="sxs-lookup"><span data-stu-id="3ef1e-132">Help on About topics with multiple versions does not work</span></span>

<span data-ttu-id="3ef1e-133">在 WMF 5.1 以前，如果安裝了多個版本的模組，而它們都共用一個說明主題，例如，about_PSReadline，則 `help about_PSReadline` 會傳回多個主題，但沒有明確的方法可以檢視實際的說明。</span><span class="sxs-lookup"><span data-stu-id="3ef1e-133">Before WMF 5.1, if you had multiple versions of a module installed and they all shared a help topic, for example, about_PSReadline, `help about_PSReadline` would return multiple topics with no obvious way to view the real help.</span></span>

<span data-ttu-id="3ef1e-134">WMF 5.1 藉由傳回最新版本的說明主題，以修正此問題。</span><span class="sxs-lookup"><span data-stu-id="3ef1e-134">WMF 5.1 fixes this by returning the help for the latest version of the topic.</span></span>

<span data-ttu-id="3ef1e-135">`Get-Help` 不提供指定所需說明版本的方法。</span><span class="sxs-lookup"><span data-stu-id="3ef1e-135">`Get-Help` does not provide a way to specify which version you want help for.</span></span> <span data-ttu-id="3ef1e-136">若要解決這個問題，請瀏覽到模組目錄，直接使用您偏好的編輯器等工具檢視說明。</span><span class="sxs-lookup"><span data-stu-id="3ef1e-136">To work around this, navigate to the modules directory and view the help directly with a tool like your favorite editor.</span></span>

### <a name="powershellexe-reading-from-stdin-stopped-working"></a><span data-ttu-id="3ef1e-137">從 STDIN 讀取的 powershell.exe 停止運作</span><span class="sxs-lookup"><span data-stu-id="3ef1e-137">powershell.exe reading from STDIN stopped working</span></span>

<span data-ttu-id="3ef1e-138">客戶使用原生應用程式的 `powershell -command -` 來執行透過 STDIN 在指令碼中傳遞的 PowerShell，可惜的是，這已因為主控台主機的其他變更而無法運作。</span><span class="sxs-lookup"><span data-stu-id="3ef1e-138">Customers use `powershell -command -` from native apps to execute PowerShell passing in the script via STDIN unfortunately this was broken by other changes in the console host.</span></span>

<span data-ttu-id="3ef1e-139">這已針對 Windows 10 年度更新版中的 5.1 版加以修正。</span><span class="sxs-lookup"><span data-stu-id="3ef1e-139">This is fixed for version 5.1 in the Windows 10 Anniversary Update.</span></span>

### <a name="powershellexe-creates-spike-in-cpu-usage-on-startup"></a><span data-ttu-id="3ef1e-140">powershell.exe 在啟動時會造成 CPU 使用量突然增加</span><span class="sxs-lookup"><span data-stu-id="3ef1e-140">powershell.exe creates spike in CPU usage on startup</span></span>

<span data-ttu-id="3ef1e-141">PowerShell 會使用 WMI 查詢來檢查它是否透過「群組原則」啟動，以避免造成登入時的延遲。</span><span class="sxs-lookup"><span data-stu-id="3ef1e-141">PowerShell uses a WMI query to check if it was started via Group Policy to avoid causing delay in login.</span></span> <span data-ttu-id="3ef1e-142">WMI 查詢最後會將 tzres.mui.dll 插入至系統上的每一個處理序，因為 **WMI Win32_Process** 類別會嘗試擷取本地時區資訊。</span><span class="sxs-lookup"><span data-stu-id="3ef1e-142">The WMI query ends up injecting tzres.mui.dll into every process on the system since the WMI **Win32_Process** class attempts to retrieve local timezone information.</span></span> <span data-ttu-id="3ef1e-143">這導致 **wmiprvse** (WMI 提供者主機) 中出現大量的 CPU 使用量。</span><span class="sxs-lookup"><span data-stu-id="3ef1e-143">This results in a large CPU spike in **wmiprvse** (the WMI provider host).</span></span> <span data-ttu-id="3ef1e-144">修正方法是以 Win32 API 呼叫取代 WMI 來取得相同的資訊。</span><span class="sxs-lookup"><span data-stu-id="3ef1e-144">Fix is to use Win32 API calls to get the same information instead of using WMI.</span></span>
