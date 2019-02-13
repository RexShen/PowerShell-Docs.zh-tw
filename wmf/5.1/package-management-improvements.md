---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,設定
contributor: jianyunt, quoctruong
title: WMF 5.1 中套件管理的改善
ms.openlocfilehash: adcddcc94022f4961f3dd23c2cd56f2a8720049b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55679217"
---
# <a name="improvements-to-package-management-in-wmf-51"></a><span data-ttu-id="52f49-103">WMF 5.1 中套件管理的改善#</span><span class="sxs-lookup"><span data-stu-id="52f49-103">Improvements to Package Management in WMF 5.1#</span></span>

## <a name="improvements-in-packagemanagement"></a><span data-ttu-id="52f49-104">封裝管理的改善</span><span class="sxs-lookup"><span data-stu-id="52f49-104">Improvements in PackageManagement</span></span> ##
<span data-ttu-id="52f49-105">以下是 WMF 5.1 中所做的修正︰</span><span class="sxs-lookup"><span data-stu-id="52f49-105">The following are the fixes made in the WMF 5.1:</span></span>

### <a name="version-alias"></a><span data-ttu-id="52f49-106">版本別名</span><span class="sxs-lookup"><span data-stu-id="52f49-106">Version Alias</span></span>

<span data-ttu-id="52f49-107">**案例**︰您的系統上若是安裝了 1.0 及 2.0 版的 P1 套件，而您想要解除安裝 1.0 版，可以執行 `Uninstall-Package -Name P1 -Version 1.0`。預期在執行 Cmdlet 之後，應會解除安裝 1.0 版，</span><span class="sxs-lookup"><span data-stu-id="52f49-107">**Scenario**: If you have version 1.0 and 2.0 of a package, P1, installed on your system, and you want to uninstall version 1.0, you would run `Uninstall-Package -Name P1 -Version 1.0` and expect version 1.0 to be uninstalled after running the cmdlet.</span></span> <span data-ttu-id="52f49-108">但卻解除安裝了 2.0 版。</span><span class="sxs-lookup"><span data-stu-id="52f49-108">However the result is that version 2.0 gets uninstalled.</span></span>

<span data-ttu-id="52f49-109">這是因為 `-Version` 參數是 `-MinimumVersion` 參數的別名。</span><span class="sxs-lookup"><span data-stu-id="52f49-109">This occurs because the `-Version` parameter is an alias of the `-MinimumVersion` parameter.</span></span> <span data-ttu-id="52f49-110">當 PackageManagement 在尋找符合資格的套件 (最低 1.0 版) 時，會傳回最新的版本。</span><span class="sxs-lookup"><span data-stu-id="52f49-110">When PackageManagement is looking for a qualified package with the minimum version of 1.0, it returns the latest version.</span></span> <span data-ttu-id="52f49-111">正常情況下會發生此行為，因為尋找最新版本通常是我們想要的結果。</span><span class="sxs-lookup"><span data-stu-id="52f49-111">This behavior is expected in normal cases because finding the latest version is usually the desired result.</span></span> <span data-ttu-id="52f49-112">但 `Uninstall-Package` 案例應不會發生此情況。</span><span class="sxs-lookup"><span data-stu-id="52f49-112">However, it should not apply to the `Uninstall-Package` case.</span></span>

<span data-ttu-id="52f49-113">**解決方法**︰將 `-Version` 從 PackageManagement (又稱為</span><span class="sxs-lookup"><span data-stu-id="52f49-113">**Solution**:removed `-Version` alias entirely in PackageManagement (a.k.a.</span></span> <span data-ttu-id="52f49-114">OneGet) 及 PowerShellGet 中完全移除。</span><span class="sxs-lookup"><span data-stu-id="52f49-114">OneGet) and PowerShellGet.</span></span>

### <a name="multiple-prompts-for-bootstrapping-the-nuget-provider"></a><span data-ttu-id="52f49-115">多次提示啟動載入 NuGet 提供者</span><span class="sxs-lookup"><span data-stu-id="52f49-115">Multiple prompts for bootstrapping the NuGet provider</span></span>

<span data-ttu-id="52f49-116">**案例**︰當您第一次在電腦上執行 `Find-Module`、`Install-Module` 或其他 PackageManagement Cmdlet 時，PackageManagement 會嘗試啟動 NuGet 提供者。</span><span class="sxs-lookup"><span data-stu-id="52f49-116">**Scenario**: When you run `Find-Module` or `Install-Module` or other PackageManagement cmdlets on your computer for the first time, PackageManagement tries to bootstrap the NuGet provider.</span></span> <span data-ttu-id="52f49-117">這是因為 PowerShellGet 提供者也使用 NuGet 提供者下載 PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="52f49-117">It does this because the PowerShellGet provider also uses the NuGet provider to download PowerShell modules.</span></span> <span data-ttu-id="52f49-118">PackageManagement 會提示使用者提供安裝 NuGet 提供者的權限。</span><span class="sxs-lookup"><span data-stu-id="52f49-118">PackageManagement then prompts the user for permission to install the NuGet provider.</span></span> <span data-ttu-id="52f49-119">在使用者選取 [是] 啟動載入之後，就會安裝最新版的 NuGet 提供者。</span><span class="sxs-lookup"><span data-stu-id="52f49-119">After the user selects "yes" for the bootstrapping, the latest version of the NuGet provider will be installed.</span></span>

<span data-ttu-id="52f49-120">但在某些情況下，您的電腦如有安裝舊版的 NuGet 提供者，有時候會先將舊版的 NuGet 載入 PowerShell 工作階段 (亦即 PackageManagement 會出現競爭狀況)。</span><span class="sxs-lookup"><span data-stu-id="52f49-120">However, in some cases, when you have an old version of NuGet provider installed on your computer, the older version of NuGet sometimes gets loaded first into the PowerShell session (that's the race condition in PackageManagement).</span></span> <span data-ttu-id="52f49-121">但因為 PowerShellGet 需要新版的 NuGet 提供者才能運作，所以 PowerShellGet 會要求 PackageManagement 重新啟動 NuGet 提供者。</span><span class="sxs-lookup"><span data-stu-id="52f49-121">However PowerShellGet requires the later version of the NuGet provider to work, so PowerShellGet asks PackageManagement to bootstrap the NuGet provider again.</span></span> <span data-ttu-id="52f49-122">以致多次提示啟動載入 NuGet 提供者。</span><span class="sxs-lookup"><span data-stu-id="52f49-122">This results in multiple prompts for bootstrapping the NuGet provider.</span></span>

<span data-ttu-id="52f49-123">**解決方案**：在 wmf 5.1 中，PackageManagement 會載入最新版的 NuGet 提供者，以避免多次提示啟動載入 NuGet 提供者。</span><span class="sxs-lookup"><span data-stu-id="52f49-123">**Solution**: In WMF5.1, PackageManagement loads the latest version of the NuGet provider to avoid multiple prompts for bootstrapping the NuGet provider.</span></span>

<span data-ttu-id="52f49-124">如果 $env: ProgramFiles\PackageManagement\ProviderAssemblies $env: LOCALAPPDATA\PackageManagement\ProviderAssemblies 有舊版的 NuGet 提供者，您也可以手動刪除舊版 (NuGet Anycpu.exe) 解決這個問題。</span><span class="sxs-lookup"><span data-stu-id="52f49-124">You could also work around this issue by manually deleting the old version of the NuGet provider (NuGet-Anycpu.exe) if exists from $env:ProgramFiles\PackageManagement\ProviderAssemblies $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies</span></span>


### <a name="support-for-packagemanagement-on-computers-with-intranet-access-only"></a><span data-ttu-id="52f49-125">只有可以存取內部網路的電腦才支援 PackageManagement</span><span class="sxs-lookup"><span data-stu-id="52f49-125">Support for PackageManagement on computers with Intranet access only</span></span>

<span data-ttu-id="52f49-126">**案例**︰在企業環境中，員工的工作環境通常無法存取網際網路，而只能存取內部網路。</span><span class="sxs-lookup"><span data-stu-id="52f49-126">**Scenario**: For the enterprise scenario, people are working under an environment where there is no Internet access but Intranet only.</span></span> <span data-ttu-id="52f49-127">在 WMF 5.0 中，PackageManagement 不支援此狀況。</span><span class="sxs-lookup"><span data-stu-id="52f49-127">PackageManagement did not support this case in WMF 5.0.</span></span>

<span data-ttu-id="52f49-128">**案例**︰在 WMF 5.0 中，PackageManagement 不支援只能存取內部網路 (無法存取網際網路) 的電腦。</span><span class="sxs-lookup"><span data-stu-id="52f49-128">**Scenario**: In WMF 5.0, PackageManagement did not support computers that have only Intranet (but not Internet) access.</span></span>

<span data-ttu-id="52f49-129">**解決方案**：在 WMF 5.1 中，您可以遵循這些步驟，才能允許內部網路電腦使用 PackageManagement:</span><span class="sxs-lookup"><span data-stu-id="52f49-129">**Solution**: In WMF 5.1, you can follow these steps to allow Intranet computers to use PackageManagement:</span></span>

1. <span data-ttu-id="52f49-130">利用其他可以連線到網際網路的電腦執行 `Install-PackageProvider -Name NuGet`，以下載 NuGet 提供者。</span><span class="sxs-lookup"><span data-stu-id="52f49-130">Download the NuGet provider using another computer that has an Internet connection by using `Install-PackageProvider -Name NuGet`.</span></span>

2. <span data-ttu-id="52f49-131">在 `$env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget` 或 `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget` 下尋找 NuGet 提供者。</span><span class="sxs-lookup"><span data-stu-id="52f49-131">Find the NuGet provider under either `$env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget`  or  `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget`.</span></span>

3. <span data-ttu-id="52f49-132">將二進位檔複製到內部網路電腦能夠存取的資料夾或網路共用位置，然後使用 `Install-PackageProvider -Name NuGet -Source <Path to folder>` 安裝 NuGet 提供者。</span><span class="sxs-lookup"><span data-stu-id="52f49-132">Copy the binaries to a folder or network share location that the Intranet computer can access, and then install the NuGet provider with `Install-PackageProvider -Name NuGet -Source <Path to folder>`.</span></span>


### <a name="event-logging-improvements"></a><span data-ttu-id="52f49-133">事件記錄的改善</span><span class="sxs-lookup"><span data-stu-id="52f49-133">Event logging improvements</span></span>

<span data-ttu-id="52f49-134">安裝封裝即是變更電腦的狀態。</span><span class="sxs-lookup"><span data-stu-id="52f49-134">When you install packages, you are changing the state of the computer.</span></span> <span data-ttu-id="52f49-135">現在在 WMF 5.1 中，PackageManagement 已會將事件記錄到 `Install-Package`、`Uninstall-Package` 及 `Save-Package` 活動的 Windows 事件記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="52f49-135">In WMF 5.1, PackageManagement now logs events to the Windows event log for `Install-Package`, `Uninstall-Package`, and `Save-Package` activities.</span></span> <span data-ttu-id="52f49-136">事件記錄檔與 PowerShell 相同，亦即 `Microsoft-Windows-PowerShell, Operational`。</span><span class="sxs-lookup"><span data-stu-id="52f49-136">The Event log  is the same as for PowerShell, that is, `Microsoft-Windows-PowerShell, Operational`.</span></span>

### <a name="support-for-basic-authentication"></a><span data-ttu-id="52f49-137">支援基本驗證</span><span class="sxs-lookup"><span data-stu-id="52f49-137">Support for basic authentication</span></span>

<span data-ttu-id="52f49-138">在 WMF 5.1 中，PackageManagement 可讓您從需要基本驗證的存放庫尋找及安裝套件。</span><span class="sxs-lookup"><span data-stu-id="52f49-138">In WMF 5.1, PackageManagement supports finding and installing packages from a repository that requires basic authentication.</span></span> <span data-ttu-id="52f49-139">您可以將您的認證提供給 `Find-Package` 及 `Install-Package` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="52f49-139">You can supply your credentials to the `Find-Package` and `Install-Package` cmdlets.</span></span> <span data-ttu-id="52f49-140">例如：</span><span class="sxs-lookup"><span data-stu-id="52f49-140">For example:</span></span>

``` PowerShell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```
### <a name="support-for-using-packagemanagement-behind-a-proxy"></a><span data-ttu-id="52f49-141">在 Proxy 後方使用 PackageManagement 的支援</span><span class="sxs-lookup"><span data-stu-id="52f49-141">Support for using PackageManagement behind a proxy</span></span>

<span data-ttu-id="52f49-142">現在在 WMF 5.1 l 中，PackageManagement 也接受新的 Proxy 參數 `-ProxyCredential` 及 `-Proxy`。</span><span class="sxs-lookup"><span data-stu-id="52f49-142">In WMF 5.1, PackageManagement now takes new proxy parameters `-ProxyCredential` and `-Proxy`.</span></span> <span data-ttu-id="52f49-143">您可以使用這些參數，在 PackageManagement Cmdlet 中指定 Proxy URL 及認證。</span><span class="sxs-lookup"><span data-stu-id="52f49-143">Using these parameters, you can specify the proxy URL and credentials to PackageManagement cmdlets.</span></span> <span data-ttu-id="52f49-144">預設使用系統 Proxy 設定。</span><span class="sxs-lookup"><span data-stu-id="52f49-144">By default, system proxy settings are used.</span></span> <span data-ttu-id="52f49-145">例如：</span><span class="sxs-lookup"><span data-stu-id="52f49-145">For example:</span></span>

``` PowerShell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```
