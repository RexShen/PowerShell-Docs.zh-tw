---
ms.date: 05/17/2018
keywords: powershell, core
title: PowerShell 6.0 的中斷性變更
ms.openlocfilehash: 60ce7a1676403bb08b57bf852ba725acde86a30c
ms.sourcegitcommit: 2d9cf1ccb9a653db7726a408ebcb65530dcb1522
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2018
---
# <a name="breaking-changes-for-powershell-60"></a><span data-ttu-id="76cbf-103">PowerShell 6.0 的中斷性變更</span><span class="sxs-lookup"><span data-stu-id="76cbf-103">Breaking Changes for PowerShell 6.0</span></span>

## <a name="features-no-longer-available-in-powershell-core"></a><span data-ttu-id="76cbf-104">PowerShell Core 中已不再提供的功能</span><span class="sxs-lookup"><span data-stu-id="76cbf-104">Features no longer available in PowerShell Core</span></span>

### <a name="powershell-workflow"></a><span data-ttu-id="76cbf-105">PowerShell 工作流程</span><span class="sxs-lookup"><span data-stu-id="76cbf-105">PowerShell Workflow</span></span>

<span data-ttu-id="76cbf-106">[PowerShell 工作流程][workflow] 是 Windows PowerShell 中建置在 [Windows Workflow Foundation (WF)][workflow-foundation] 上的功能，可讓您建立適用於長時間執行或平行化工作的強固 Runbook。</span><span class="sxs-lookup"><span data-stu-id="76cbf-106">[PowerShell Workflow][workflow] is a feature in Windows PowerShell that builds on top of [Windows Workflow Foundation (WF)][workflow-foundation] that enables the creation of robust runbooks for long-running or parallelized tasks.</span></span>

<span data-ttu-id="76cbf-107">由於 .NET Core 中缺少對 Windows Workflow Foundation 的支援，因此我們將不在 PowerShell Core 中繼續支援 PowerShell 工作流程。</span><span class="sxs-lookup"><span data-stu-id="76cbf-107">Due to the lack of support for Windows Workflow Foundation in .NET Core, we will not continue to support PowerShell Workflow in PowerShell Core.</span></span>

<span data-ttu-id="76cbf-108">未來，我們想要在 PowerShell 語言中啟用原生平行處理原則/並行處理，而不需要 PowerShell 工作流程。</span><span class="sxs-lookup"><span data-stu-id="76cbf-108">In the future, we would like to enable native parallelism/concurrency in the PowerShell language without the need for PowerShell Workflow.</span></span>

[workflow]: https://docs.microsoft.com/powershell/scripting/core-powershell/workflows-guide
[workflow-foundation]: https://docs.microsoft.com/dotnet/framework/windows-workflow-foundation/

### <a name="custom-snap-ins"></a><span data-ttu-id="76cbf-109">自訂嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="76cbf-109">Custom snap-ins</span></span>

<span data-ttu-id="76cbf-110">[PowerShell 嵌入式管理單元][snapin] 是 PowerShell 模組的前身，並未受到 PowerShell 社群廣泛採用。</span><span class="sxs-lookup"><span data-stu-id="76cbf-110">[PowerShell snap-ins][snapin] are a predecessor to PowerShell modules that do not have widespread adoption in the PowerShell community.</span></span>

<span data-ttu-id="76cbf-111">由於支援嵌入式管理單元相當複雜，且其在社群中的使用率不高，因此我們已不再於 PowerShell Core 中支援自訂嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="76cbf-111">Due to the complexity of supporting snap-ins and their lack of usage in the community, we no longer support custom snap-ins in PowerShell Core.</span></span>

<span data-ttu-id="76cbf-112">目前，這會導致 Windows 和 Windows Server 中的 `ActiveDirectory` 與 `DnsClient` 模組中斷。</span><span class="sxs-lookup"><span data-stu-id="76cbf-112">Today, this breaks the `ActiveDirectory` and `DnsClient` modules in Windows and Windows Server.</span></span>

[snapin]: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssnapins

### <a name="wmi-v1-cmdlets"></a><span data-ttu-id="76cbf-113">WMI v1 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="76cbf-113">WMI v1 cmdlets</span></span>

<span data-ttu-id="76cbf-114">由於支援兩組 WMI 型模組相當複雜，因此我們已從 PowerShell Core 中移除 WMI v1 Cmdlet：</span><span class="sxs-lookup"><span data-stu-id="76cbf-114">Due to the complexity of supporting two sets of WMI-based modules, we removed the WMI v1 cmdlets from PowerShell Core:</span></span>

- `Get-WmiObject`
- `Invoke-WmiMethod`
- `Register-WmiEvent`
- `Set-WmiInstance`

<span data-ttu-id="76cbf-115">建議您改用 CIM (也稱為 WMI v2) Cmdlet，這些 Cmdlet 以新的功能和重新設計的語法提供相同的功能：</span><span class="sxs-lookup"><span data-stu-id="76cbf-115">Instead, we recommend that you the use the CIM (aka WMI v2) cmdlets which provide the same functionality with new functionality and a redesigned syntax:</span></span>

- `Get-CimAssociatedInstance`
- `Get-CimClass`
- `Get-CimInstance`
- `Get-CimSession`
- `Invoke-CimMethod`
- `New-CimInstance`
- `New-CimSession`
- `New-CimSessionOption`
- `Register-CimIndicationEvent`
- `Remove-CimInstance`
- `Remove-CimSession`
- `Set-CimInstance`

### <a name="microsoftpowershelllocalaccounts"></a><span data-ttu-id="76cbf-116">Microsoft.PowerShell.LocalAccounts</span><span class="sxs-lookup"><span data-stu-id="76cbf-116">Microsoft.PowerShell.LocalAccounts</span></span>

<span data-ttu-id="76cbf-117">由於使用不支援的 API，因此已從 PowerShell Core 中移除 `Microsoft.PowerShell.LocalAccounts`，直到找到更好的解決方案為止。</span><span class="sxs-lookup"><span data-stu-id="76cbf-117">Due to the use of unsupported APIs, `Microsoft.PowerShell.LocalAccounts` has been removed from PowerShell Core until a better solution is found.</span></span>

### <a name="-counter-cmdlets"></a><span data-ttu-id="76cbf-118">`*-Counter` Cmdlet</span><span class="sxs-lookup"><span data-stu-id="76cbf-118">`*-Counter` cmdlets</span></span>

<span data-ttu-id="76cbf-119">由於使用不支援的 API，因此已從 PowerShell Core 中移除 `*-Counter`，直到找到更好的解決方案為止。</span><span class="sxs-lookup"><span data-stu-id="76cbf-119">Due to the use of unsupported APIs, the `*-Counter` has been removed from PowerShell Core until a better solution is found.</span></span>

## <a name="enginelanguage-changes"></a><span data-ttu-id="76cbf-120">引擎/語言變更</span><span class="sxs-lookup"><span data-stu-id="76cbf-120">Engine/language changes</span></span>

### <a name="rename-powershellexe-to-pwshexe-5101httpsgithubcompowershellpowershellissues5101"></a><span data-ttu-id="76cbf-121">將 `powershell.exe` 重新命名為 `pwsh.exe` [#5101](https://github.com/PowerShell/PowerShell/issues/5101)</span><span class="sxs-lookup"><span data-stu-id="76cbf-121">Rename `powershell.exe` to `pwsh.exe` [#5101](https://github.com/PowerShell/PowerShell/issues/5101)</span></span>

<span data-ttu-id="76cbf-122">為了提供使用者一個呼叫 Windows 上 PowerShell Core (而不是 Windows PowerShell) 的決定性方式，PowerShell Core 二進位檔在 Windows 上已變更為 `pwsh.exe`，而在非 Windows 平台上則變更為 `pwsh`。</span><span class="sxs-lookup"><span data-stu-id="76cbf-122">In order to give users a deterministic way to call PowerShell Core on Windows (as opposed to Windows PowerShell), the PowerShell Core binary was changed to `pwsh.exe` on Windows and `pwsh` on non-Windows platforms.</span></span>

<span data-ttu-id="76cbf-123">該簡短名稱也與非 Windows 平台上殼層的命名一致。</span><span class="sxs-lookup"><span data-stu-id="76cbf-123">The shortened name is also consistent with naming of shells on non-Windows platforms.</span></span>

### <a name="dont-insert-line-breaks-to-output-except-for-tables-5193httpsgithubcompowershellpowershellissues5193"></a><span data-ttu-id="76cbf-124">不在輸出中插入分行符號 (資料表除外) [#5193](https://github.com/PowerShell/PowerShell/issues/5193)</span><span class="sxs-lookup"><span data-stu-id="76cbf-124">Don't insert line breaks to output (except for tables) [#5193](https://github.com/PowerShell/PowerShell/issues/5193)</span></span>

<span data-ttu-id="76cbf-125">先前，輸出會與主控台的寬度對齊，而在主控台的結束寬度會加上分行符號，意謂著當終端機調整大小時，不會如預期般重新製作輸出格式。</span><span class="sxs-lookup"><span data-stu-id="76cbf-125">Previously, output was aligned to the width of the console and line breaks were added at the end width of the console, meaning the output didn't get reformatted as expected if the terminal was resized.</span></span> <span data-ttu-id="76cbf-126">這項變更不會套用至資料表，因為必須要有分行符號，才能讓資料行保持對齊。</span><span class="sxs-lookup"><span data-stu-id="76cbf-126">This change was not applied to tables, as the line breaks are necessary to keep the columns aligned.</span></span>

### <a name="skip-null-element-check-for-collections-with-a-value-type-element-type-5432httpsgithubcompowershellpowershellissues5432"></a><span data-ttu-id="76cbf-127">針對元素類型是值類型的集合略過 Null 元素檢查 [#5432](https://github.com/PowerShell/PowerShell/issues/5432)</span><span class="sxs-lookup"><span data-stu-id="76cbf-127">Skip null-element check for collections with a value-type element type [#5432](https://github.com/PowerShell/PowerShell/issues/5432)</span></span>

<span data-ttu-id="76cbf-128">如果集合的元素類型是值類型，便針對 `Mandatory` 參數及 `ValidateNotNull` 和 `ValidateNotNullOrEmpty` 屬性，略過 Null 元素檢查。</span><span class="sxs-lookup"><span data-stu-id="76cbf-128">For the `Mandatory` parameter and `ValidateNotNull` and `ValidateNotNullOrEmpty` attributes, skip the null-element check if the collection's element type is value type.</span></span>

### <a name="change-outputencoding-to-use-utf-8-nobom-encoding-rather-than-ascii-5369httpsgithubcompowershellpowershellissues5369"></a><span data-ttu-id="76cbf-129">將 `$OutputEncoding` 變更為使用 `UTF-8 NoBOM` 編碼，而不是 ASCII [#5369](https://github.com/PowerShell/PowerShell/issues/5369)</span><span class="sxs-lookup"><span data-stu-id="76cbf-129">Change `$OutputEncoding` to use `UTF-8 NoBOM` encoding rather than ASCII [#5369](https://github.com/PowerShell/PowerShell/issues/5369)</span></span>

<span data-ttu-id="76cbf-130">先前的編碼 ASCII (7 位元) 在某些情況下會造成不正確的輸出變更。</span><span class="sxs-lookup"><span data-stu-id="76cbf-130">The previous encoding, ASCII (7-bit), would result in incorrect alteration of the output in some cases.</span></span> <span data-ttu-id="76cbf-131">這項變更是要將 `UTF-8 NoBOM` 設定為預設值，這會使用大多數工具和作業系統所支援的編碼來保留 Unicode 輸出。</span><span class="sxs-lookup"><span data-stu-id="76cbf-131">This change is to make `UTF-8 NoBOM` default, which preserves Unicode output with an encoding supported by most tools and operating systems.</span></span>

### <a name="remove-allscope-from-most-default-aliases-5268httpsgithubcompowershellpowershellissues5268"></a><span data-ttu-id="76cbf-132">從大多數預設別名中移除 `AllScope` [#5268](https://github.com/PowerShell/PowerShell/issues/5268)</span><span class="sxs-lookup"><span data-stu-id="76cbf-132">Remove `AllScope` from most default aliases [#5268](https://github.com/PowerShell/PowerShell/issues/5268)</span></span>

<span data-ttu-id="76cbf-133">為了加快建立範圍的速度，已從大多數預設別名中移除 `AllScope`。</span><span class="sxs-lookup"><span data-stu-id="76cbf-133">To speed up scope creation, `AllScope` was removed from most default aliases.</span></span> <span data-ttu-id="76cbf-134">針對一些經常使用且查閱速度較快的別名則保留了 `AllScope`。</span><span class="sxs-lookup"><span data-stu-id="76cbf-134">`AllScope` was left for a few frequently used aliases where the lookup was faster.</span></span>

### <a name="-verbose-and--debug-no-longer-overrides-erroractionpreference-5113httpsgithubcompowershellpowershellissues5113"></a><span data-ttu-id="76cbf-135">`-Verbose` 和 `-Debug` 已不再覆寫 `$ErrorActionPreference` [#5113](https://github.com/PowerShell/PowerShell/issues/5113)</span><span class="sxs-lookup"><span data-stu-id="76cbf-135">`-Verbose` and `-Debug` no longer overrides `$ErrorActionPreference` [#5113](https://github.com/PowerShell/PowerShell/issues/5113)</span></span>

<span data-ttu-id="76cbf-136">先前，如果指定了 `-Verbose` 或 `-Debug`，就會覆寫 `$ErrorActionPreference` 的行為。</span><span class="sxs-lookup"><span data-stu-id="76cbf-136">Previously, if `-Verbose` or `-Debug` were specified, it overrode the behavior of `$ErrorActionPreference`.</span></span> <span data-ttu-id="76cbf-137">藉由這項變更，`-Verbose` 和 `-Debug` 便不再影響 `$ErrorActionPreference` 的行為。</span><span class="sxs-lookup"><span data-stu-id="76cbf-137">With this change, `-Verbose` and `-Debug` no longer affect the behavior of `$ErrorActionPreference`.</span></span>

## <a name="cmdlet-changes"></a><span data-ttu-id="76cbf-138">Cmdlet 變更</span><span class="sxs-lookup"><span data-stu-id="76cbf-138">Cmdlet changes</span></span>

### <a name="invoke-restmethod-doesnt-return-useful-info-when-no-data-is-returned-5320httpsgithubcompowershellpowershellissues5320"></a><span data-ttu-id="76cbf-139">未傳回任何資料時，Invoke-RestMethod 不會傳回有用的資訊。</span><span class="sxs-lookup"><span data-stu-id="76cbf-139">Invoke-RestMethod doesn't return useful info when no data is returned.</span></span> [<span data-ttu-id="76cbf-140">#5320</span><span class="sxs-lookup"><span data-stu-id="76cbf-140">#5320</span></span>](https://github.com/PowerShell/PowerShell/issues/5320)

<span data-ttu-id="76cbf-141">當 API 只傳回 `null`時，Invoke-RestMethod 會將其序列化為字串 `"null"`，而不是 `$null`。</span><span class="sxs-lookup"><span data-stu-id="76cbf-141">When an API returns just `null`, Invoke-RestMethod was serializing this as the string `"null"` instead of `$null`.</span></span> <span data-ttu-id="76cbf-142">這項變更會修正 `Invoke-RestMethod` 中的邏輯，將有效的單一值 JSON `null` 常值序列化為 `$null`。</span><span class="sxs-lookup"><span data-stu-id="76cbf-142">This change fixes the logic in `Invoke-RestMethod` to properly serialize a valid single value JSON `null` literal as `$null`.</span></span>

### <a name="remove--computername-from--computer-cmdlets-5277httpsgithubcompowershellpowershellissues5277"></a><span data-ttu-id="76cbf-143">從 `*-Computer` Cmdlet 中移除 `-ComputerName` [#5277](https://github.com/PowerShell/PowerShell/issues/5277)</span><span class="sxs-lookup"><span data-stu-id="76cbf-143">Remove `-ComputerName` from `*-Computer` cmdlets [#5277](https://github.com/PowerShell/PowerShell/issues/5277)</span></span>

<span data-ttu-id="76cbf-144">由於 CoreFX 中的 RPC 遠端處理問題 (特別是在非 Windows 平台上)，以及確保 PowerShell 中有一致的遠端處理體驗，因此已從 `\*-Computer` Cmdlet 中移除 `-ComputerName` 參數。</span><span class="sxs-lookup"><span data-stu-id="76cbf-144">Due to issues with RPC remoting in CoreFX (particularly on non-Windows platforms) and ensuring a consistent remoting experience in PowerShell, the `-ComputerName` parameter was removed from the `\*-Computer` cmdlets.</span></span> <span data-ttu-id="76cbf-145">請改用 `Invoke-Command` 來作為從遠端執行 Cmdlet 的方式。</span><span class="sxs-lookup"><span data-stu-id="76cbf-145">Use `Invoke-Command` instead as the way to execute cmdlets remotely.</span></span>

### <a name="remove--computername-from--service-cmdlets-5090httpsgithubcompowershellpowershellissues5094"></a><span data-ttu-id="76cbf-146">從 `*-Service` Cmdlet 中移除 `-ComputerName` [#5090](https://github.com/PowerShell/PowerShell/issues/5094)</span><span class="sxs-lookup"><span data-stu-id="76cbf-146">Remove `-ComputerName` from `*-Service` cmdlets [#5090](https://github.com/PowerShell/PowerShell/issues/5094)</span></span>

<span data-ttu-id="76cbf-147">為了鼓勵一致地使用 PSRP，已從 `*-Service` Cmdlet 中移除 `-ComputerName` 參數。</span><span class="sxs-lookup"><span data-stu-id="76cbf-147">In order to encourage the consistent use of PSRP, the `-ComputerName` parameter was removed from `*-Service` cmdlets.</span></span>

### <a name="fix-get-item--literalpath-ab-if-ab-doesnt-actually-exist-to-return-error-5197httpsgithubcompowershellpowershellissues5197"></a><span data-ttu-id="76cbf-148">將 `Get-Item -LiteralPath a*b` 修正為如果 `a*b` 未實際存在便傳回錯誤 [#5197](https://github.com/PowerShell/PowerShell/issues/5197)</span><span class="sxs-lookup"><span data-stu-id="76cbf-148">Fix `Get-Item -LiteralPath a*b` if `a*b` doesn't actually exist to return error [#5197](https://github.com/PowerShell/PowerShell/issues/5197)</span></span>

<span data-ttu-id="76cbf-149">先前，將萬用字元指定給 `-LiteralPath` 時，它會將其視為與 `-Path` 相同，而如果該萬用字元找不到任何檔案，它就會以無訊息模式結束。</span><span class="sxs-lookup"><span data-stu-id="76cbf-149">Previously, `-LiteralPath` given a wildcard would treat it the same as `-Path` and if the wildcard found no files, it would silently exit.</span></span> <span data-ttu-id="76cbf-150">正確的行為應該是 `-LiteralPath` 為常值，因此如果檔案不存在，它應該發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="76cbf-150">Correct behavior should be that `-LiteralPath` is literal so if the file doesn't exist, it should error.</span></span> <span data-ttu-id="76cbf-151">這項變更是要將與 `-Literal` 搭配使用的萬用字元視為常值。</span><span class="sxs-lookup"><span data-stu-id="76cbf-151">Change is to treat wildcards used with `-Literal` as literal.</span></span>

### <a name="import-csv-should-apply-pstypenames-upon-import-when-type-information-is-present-in-the-csv-5134httpsgithubcompowershellpowershellissues5134"></a><span data-ttu-id="76cbf-152">當 CSV 中有類型資訊時，`Import-Csv` 應該在匯入時套用 `PSTypeNames` [#5134](https://github.com/PowerShell/PowerShell/issues/5134)</span><span class="sxs-lookup"><span data-stu-id="76cbf-152">`Import-Csv` should apply `PSTypeNames` upon import when type information is present in the CSV [#5134](https://github.com/PowerShell/PowerShell/issues/5134)</span></span>

<span data-ttu-id="76cbf-153">先前，使用 `Export-CSV` 匯出的物件如果具有以 `ConvertFrom-Csv` 匯入的 `TypeInformation`，並不會保留該類型資訊。</span><span class="sxs-lookup"><span data-stu-id="76cbf-153">Previously, objects exported using `Export-CSV` with `TypeInformation` imported with `ConvertFrom-Csv` were not retaining the type information.</span></span> <span data-ttu-id="76cbf-154">這項變更會在 CSV 檔案中有可用的類型資訊時，將該資訊新增至 `PSTypeNames` 成員。</span><span class="sxs-lookup"><span data-stu-id="76cbf-154">This change adds the type information to `PSTypeNames` member if available from the CSV file.</span></span>

### <a name="-notypeinformation-should-be-default-on-export-csv-5131httpsgithubcompowershellpowershellissues5131"></a><span data-ttu-id="76cbf-155">`-NoTypeInformation` 應該是 `Export-Csv` 上的預設值 [#5131](https://github.com/PowerShell/PowerShell/issues/5131)</span><span class="sxs-lookup"><span data-stu-id="76cbf-155">`-NoTypeInformation` should be default on `Export-Csv` [#5131](https://github.com/PowerShell/PowerShell/issues/5131)</span></span>

<span data-ttu-id="76cbf-156">這項變更是為了處理客戶對下列預設行為的意見反應：`Export-CSV` 會包含類型資訊。</span><span class="sxs-lookup"><span data-stu-id="76cbf-156">This change was made to address customer feedback on the default behavior of `Export-CSV` to include type information.</span></span>

<span data-ttu-id="76cbf-157">先前，此 Cmdlet 會輸出包含物件類型名稱的註解作為第一行。</span><span class="sxs-lookup"><span data-stu-id="76cbf-157">Previously, the cmdlet would output a comment as the first line containing the type name of the object.</span></span> <span data-ttu-id="76cbf-158">此變更是要預設抑制此行為，因為大多數工具並無法理解此註解。</span><span class="sxs-lookup"><span data-stu-id="76cbf-158">The change is to suppress this by default as it's not understood by most tools.</span></span> <span data-ttu-id="76cbf-159">若要保留先前的行為，請使用 `-IncludeTypeInformation`。</span><span class="sxs-lookup"><span data-stu-id="76cbf-159">Use `-IncludeTypeInformation` to retain the previous behavior.</span></span>

### <a name="web-cmdlets-should-warn-when--credential-is-sent-over-unencrypted-connections-5112httpsgithubcompowershellpowershellissues5112"></a><span data-ttu-id="76cbf-160">透過未加密的連線傳送 `-Credential` 時，Web Cmdlet 應該發出警告 [#5112](https://github.com/PowerShell/PowerShell/issues/5112)</span><span class="sxs-lookup"><span data-stu-id="76cbf-160">Web Cmdlets should warn when `-Credential` is sent over unencrypted connections [#5112](https://github.com/PowerShell/PowerShell/issues/5112)</span></span>

<span data-ttu-id="76cbf-161">使用 HTTP 時，內容 (包括密碼) 會以純文字方式傳送。</span><span class="sxs-lookup"><span data-stu-id="76cbf-161">When using HTTP, content including passwords are sent as clear-text.</span></span> <span data-ttu-id="76cbf-162">這項變更是要預設禁止此行為，並在以不安全方式傳遞認證時傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="76cbf-162">This change is to not allow this by default and return an error if credentials are being passed in an insecure manner.</span></span> <span data-ttu-id="76cbf-163">使用者可以使用 `-AllowUnencryptedAuthentication` 參數來略過此作業。</span><span class="sxs-lookup"><span data-stu-id="76cbf-163">Users can bypass this by using the `-AllowUnencryptedAuthentication` switch.</span></span>

## <a name="api-changes"></a><span data-ttu-id="76cbf-164">API 變更</span><span class="sxs-lookup"><span data-stu-id="76cbf-164">API changes</span></span>

### <a name="remove-addtypecommandbase-class-5407httpsgithubcompowershellpowershellissues5407"></a><span data-ttu-id="76cbf-165">移除 `AddTypeCommandBase` 類別 [#5407](https://github.com/PowerShell/PowerShell/issues/5407)</span><span class="sxs-lookup"><span data-stu-id="76cbf-165">Remove `AddTypeCommandBase` class [#5407](https://github.com/PowerShell/PowerShell/issues/5407)</span></span>

<span data-ttu-id="76cbf-166">已從 `Add-Type` 中移除 `AddTypeCommandBase` 類別來改善效能。</span><span class="sxs-lookup"><span data-stu-id="76cbf-166">The `AddTypeCommandBase` class was removed from `Add-Type` to improve performance.</span></span> <span data-ttu-id="76cbf-167">此類別僅供 Add-Type Cmdlet 使用，應該不會影響到使用者。</span><span class="sxs-lookup"><span data-stu-id="76cbf-167">This class is only used by the Add-Type cmdlet and should not impact users.</span></span>

### <a name="unify-cmdlets-with-parameter--encoding-to-be-of-type-systemtextencoding-5080httpsgithubcompowershellpowershellissues5080"></a><span data-ttu-id="76cbf-168">將 Cmdlet 與參數 `-Encoding` 整合成屬於類型 `System.Text.Encoding` [#5080](https://github.com/PowerShell/PowerShell/issues/5080)</span><span class="sxs-lookup"><span data-stu-id="76cbf-168">Unify cmdlets with parameter `-Encoding` to be of type `System.Text.Encoding` [#5080](https://github.com/PowerShell/PowerShell/issues/5080)</span></span>

<span data-ttu-id="76cbf-169">已從檔案系統提供者 Cmdlet 中移除 `-Encoding` 值 `Byte`。</span><span class="sxs-lookup"><span data-stu-id="76cbf-169">The `-Encoding` value `Byte` has been removed from the filesystem provider cmdlets.</span></span> <span data-ttu-id="76cbf-170">現在是使用新參數 `-AsByteStream` 來指定必須使用位元組資料流作為輸入，或是指定輸出為位元組資料流。</span><span class="sxs-lookup"><span data-stu-id="76cbf-170">A new parameter, `-AsByteStream`, is now used to specify that a byte stream is required as input or that the output is a stream of bytes.</span></span>

### <a name="add-better-error-message-for-empty-and-null--uformat-parameter-5055httpsgithubcompowershellpowershellissues5055"></a><span data-ttu-id="76cbf-171">為空白或 Null `-UFormat` 參數新增更好的錯誤訊息 [#5055](https://github.com/PowerShell/PowerShell/issues/5055)</span><span class="sxs-lookup"><span data-stu-id="76cbf-171">Add better error message for empty and null `-UFormat` parameter [#5055](https://github.com/PowerShell/PowerShell/issues/5055)</span></span>

<span data-ttu-id="76cbf-172">先前，將空白格式字串傳遞給 `-UFormat` 時，會顯示無用的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="76cbf-172">Previously, when passing an empty format string to `-UFormat`, an unhelpful error message would appear.</span></span> <span data-ttu-id="76cbf-173">現已新增有較詳細描述的錯誤。</span><span class="sxs-lookup"><span data-stu-id="76cbf-173">A more descriptive error has been added.</span></span>

### <a name="clean-up-console-code-4995httpsgithubcompowershellpowershellissues4995"></a><span data-ttu-id="76cbf-174">清除主控台程式碼 [#4995](https://github.com/PowerShell/PowerShell/issues/4995)</span><span class="sxs-lookup"><span data-stu-id="76cbf-174">Clean up console code [#4995](https://github.com/PowerShell/PowerShell/issues/4995)</span></span>

<span data-ttu-id="76cbf-175">已移除下列功能，因為 PowerShell Core 並不支援這些功能，而且也沒有任何新增支援的打算，它們之所以存在是為了滿足舊版 Windows PowerShell 需求：`-psconsolefile` 參數和程式碼、`-importsystemmodules` 參數和程式碼，以及字型變更程式碼。</span><span class="sxs-lookup"><span data-stu-id="76cbf-175">The following features were removed as they are not supported in PowerShell Core, and there are no plans to add support as they exist for legacy reasons for Windows PowerShell: `-psconsolefile` switch and code, `-importsystemmodules` switch and code, and font changing code.</span></span>

### <a name="removed-runspaceconfiguration-support-4942httpsgithubcompowershellpowershellissues4942"></a><span data-ttu-id="76cbf-176">已移除 `RunspaceConfiguration` 支援 [#4942](https://github.com/PowerShell/PowerShell/issues/4942)</span><span class="sxs-lookup"><span data-stu-id="76cbf-176">Removed `RunspaceConfiguration` support [#4942](https://github.com/PowerShell/PowerShell/issues/4942)</span></span>

<span data-ttu-id="76cbf-177">先前，使用 API 以程式設計方式建立 PowerShell Runspace 時，您可以使用舊版 [`RunspaceConfiguration`][runspaceconfig] 或較新的 [`InitialSessionState`][iss]。</span><span class="sxs-lookup"><span data-stu-id="76cbf-177">Previously, when creating a PowerShell runspace programmatically using the API you could use the legacy [`RunspaceConfiguration`][runspaceconfig] or the newer [`InitialSessionState`][iss].</span></span> <span data-ttu-id="76cbf-178">這項變更移除了對 `RunspaceConfiguration` 的支援，而僅支援 `InitialSessionState`。</span><span class="sxs-lookup"><span data-stu-id="76cbf-178">This change removed support for `RunspaceConfiguration` and only supports `InitialSessionState`.</span></span>

[runspaceconfig]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.runspaceconfiguration
[iss]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.initialsessionstate

### <a name="commandinvocationintrinsicsinvokescript-bind-arguments-to-input-instead-of-args-4923httpsgithubcompowershellpowershellissues4923"></a><span data-ttu-id="76cbf-179">`CommandInvocationIntrinsics.InvokeScript` 將引數繫結至 `$input` 而不是 `$args` [#4923](https://github.com/PowerShell/PowerShell/issues/4923)</span><span class="sxs-lookup"><span data-stu-id="76cbf-179">`CommandInvocationIntrinsics.InvokeScript` bind arguments to `$input` instead of `$args` [#4923](https://github.com/PowerShell/PowerShell/issues/4923)</span></span>

<span data-ttu-id="76cbf-180">不正確的參數位置導致引數被當作輸入來傳遞，而不是當成引數。</span><span class="sxs-lookup"><span data-stu-id="76cbf-180">An incorrect position of a parameter resulted in the args passed as input instead of as args.</span></span>

### <a name="remove-unsupported--showwindow-switch-from-get-help-4903httpsgithubcompowershellpowershellissues4903"></a><span data-ttu-id="76cbf-181">從 `Get-Help` 中移除不支援的 `-showwindow` 參數 [#4903](https://github.com/PowerShell/PowerShell/issues/4903)</span><span class="sxs-lookup"><span data-stu-id="76cbf-181">Remove unsupported `-showwindow` switch from `Get-Help` [#4903](https://github.com/PowerShell/PowerShell/issues/4903)</span></span>

<span data-ttu-id="76cbf-182">`-showwindow` 倚賴 WPF，但在 CoreCLR 上並不支援 WPF。</span><span class="sxs-lookup"><span data-stu-id="76cbf-182">`-showwindow` relies on WPF, which is not supported on CoreCLR.</span></span>

### <a name="allow--to-be-used-in-registry-path-for-remove-item-4866httpsgithubcompowershellpowershellissues4866"></a><span data-ttu-id="76cbf-183">允許在 `Remove-Item` 的登錄路徑中使用 \* [#4866](https://github.com/PowerShell/PowerShell/issues/4866)</span><span class="sxs-lookup"><span data-stu-id="76cbf-183">Allow \* to be used in registry path for `Remove-Item` [#4866](https://github.com/PowerShell/PowerShell/issues/4866)</span></span>

<span data-ttu-id="76cbf-184">先前，將萬用字元指定給 `-LiteralPath` 時，它會將其視為與 `-Path` 相同，而如果該萬用字元找不到任何檔案，它就會以無訊息模式結束。</span><span class="sxs-lookup"><span data-stu-id="76cbf-184">Previously, `-LiteralPath` given a wildcard would treat it the same as `-Path` and if the wildcard found no files, it would silently exit.</span></span> <span data-ttu-id="76cbf-185">正確的行為應該是 `-LiteralPath` 為常值，因此如果檔案不存在，它應該發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="76cbf-185">Correct behavior should be that `-LiteralPath` is literal so if the file doesn't exist, it should error.</span></span> <span data-ttu-id="76cbf-186">這項變更是要將與 `-Literal` 搭配使用的萬用字元視為常值。</span><span class="sxs-lookup"><span data-stu-id="76cbf-186">Change is to treat wildcards used with `-Literal` as literal.</span></span>

### <a name="fix-set-service-failing-test-4802httpsgithubcompowershellpowershellissues4802"></a><span data-ttu-id="76cbf-187">修正 `Set-Service` 測試失敗 [#4802](https://github.com/PowerShell/PowerShell/issues/4802)</span><span class="sxs-lookup"><span data-stu-id="76cbf-187">Fix `Set-Service` failing test [#4802](https://github.com/PowerShell/PowerShell/issues/4802)</span></span>

<span data-ttu-id="76cbf-188">先前，如果使用 `New-Service -StartupType foo`，會忽略 `foo`，並以某個預設啟動類型建立服務。</span><span class="sxs-lookup"><span data-stu-id="76cbf-188">Previously, if `New-Service -StartupType foo` was used, `foo` was ignored and the service was created with some default startup type.</span></span> <span data-ttu-id="76cbf-189">這項變更是要針對無效的啟動類型明確擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="76cbf-189">This change is to explicitly throw an error for an invalid startup type.</span></span>

### <a name="rename-isosx-to-ismacos-4700httpsgithubcompowershellpowershellissues4700"></a><span data-ttu-id="76cbf-190">將 `$IsOSX` 重新命名為 `$IsMacOS` [#4700](https://github.com/PowerShell/PowerShell/issues/4700)</span><span class="sxs-lookup"><span data-stu-id="76cbf-190">Rename `$IsOSX` to `$IsMacOS` [#4700](https://github.com/PowerShell/PowerShell/issues/4700)</span></span>

<span data-ttu-id="76cbf-191">該命名在 PowerShell 中應該與我們的命名一致，並且與 Apple 一樣使用 macOS 而非 OSX。</span><span class="sxs-lookup"><span data-stu-id="76cbf-191">The naming in PowerShell should be consistent with our naming and conform to Apple's use of macOS instead of OSX.</span></span> <span data-ttu-id="76cbf-192">不過，為了可讀性及一致性，我們會維持 Pascal 大小寫。</span><span class="sxs-lookup"><span data-stu-id="76cbf-192">However, for readability and consistently we are staying with Pascal casing.</span></span>

### <a name="make-error-message-consistent-when-invalid-script-is-passed-to--file-better-error-when-passed-ambiguous-argument-4573httpsgithubcompowershellpowershellissues4573"></a><span data-ttu-id="76cbf-193">當傳遞給 -File 的指令碼無效時使得錯誤訊息變得一致、當傳遞的引數模稜兩可時提供更詳細的錯誤 [#4573](https://github.com/PowerShell/PowerShell/issues/4573)</span><span class="sxs-lookup"><span data-stu-id="76cbf-193">Make error message consistent when invalid script is passed to -File, better error when passed ambiguous argument [#4573](https://github.com/PowerShell/PowerShell/issues/4573)</span></span>

<span data-ttu-id="76cbf-194">將 `pwsh.exe` 的結束代碼變更為符合 Unix 慣例</span><span class="sxs-lookup"><span data-stu-id="76cbf-194">Change the exit codes of `pwsh.exe` to align with Unix conventions</span></span>

### <a name="removal-of-localaccount-and-cmdlets-from--diagnostics-modules-4302httpsgithubcompowershellpowershellissues4302-4303httpsgithubcompowershellpowershellissues4303"></a><span data-ttu-id="76cbf-195">從 `Diagnostics` 模組中移除 `LocalAccount` 和 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="76cbf-195">Removal of `LocalAccount` and cmdlets from  `Diagnostics` modules.</span></span> <span data-ttu-id="76cbf-196">[#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)</span><span class="sxs-lookup"><span data-stu-id="76cbf-196">[#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)</span></span>

<span data-ttu-id="76cbf-197">由於 API 不是支援的 API，因此已將 `Diagnostics` 中的 `LocalAccounts` 模組和 `Counter` Cmdlet 移除，直到找到更好的解決方案為止。</span><span class="sxs-lookup"><span data-stu-id="76cbf-197">Due to unsupported APIs, the `LocalAccounts` module and the `Counter` cmdlets in the `Diagnostics` module were removed until a better solution is found.</span></span>

### <a name="executing-powershell-script-with-bool-parameter-does-not-work-4036httpsgithubcompowershellpowershellissues4036"></a><span data-ttu-id="76cbf-198">以布林值參數執行 PowerShell 指令碼無法運作 [#4036](https://github.com/PowerShell/PowerShell/issues/4036)</span><span class="sxs-lookup"><span data-stu-id="76cbf-198">Executing powershell script with bool parameter does not work [#4036](https://github.com/PowerShell/PowerShell/issues/4036)</span></span>

<span data-ttu-id="76cbf-199">先前，使用 powershell.exe (現在為 `pwsh.exe`) 以 `-File` 執行 PowerShell 指令碼時，無法傳遞 $true/$false 作為參數值。</span><span class="sxs-lookup"><span data-stu-id="76cbf-199">Previously, using powershell.exe (now `pwsh.exe`) to execute a PowerShell script using `-File` provided no way to pass $true/$false as parameter values.</span></span> <span data-ttu-id="76cbf-200">已新增將 $true/$false 作為參數剖析值的支援。</span><span class="sxs-lookup"><span data-stu-id="76cbf-200">Support for $true/$false as parsed values to parameters was added.</span></span> <span data-ttu-id="76cbf-201">此外，也支援參數值，因為目前記載的語法無法運作。</span><span class="sxs-lookup"><span data-stu-id="76cbf-201">Switch values are also supported as currently documented syntax doesn't work.</span></span>

### <a name="remove-clrversion-property-from-psversiontable-4027httpsgithubcompowershellpowershellissues4027"></a><span data-ttu-id="76cbf-202">從 `$PSVersionTable` 中移除 `ClrVersion` 屬性 [#4027](https://github.com/PowerShell/PowerShell/issues/4027)</span><span class="sxs-lookup"><span data-stu-id="76cbf-202">Remove `ClrVersion` property from `$PSVersionTable` [#4027](https://github.com/PowerShell/PowerShell/issues/4027)</span></span>

<span data-ttu-id="76cbf-203">`$PSVersionTable` 的 `ClrVersion` 屬性對 CoreCLR 來說沒有用，使用者不應該使用該值來判斷相容性。</span><span class="sxs-lookup"><span data-stu-id="76cbf-203">The `ClrVersion` property of `$PSVersionTable` is not useful with CoreCLR, end users should not be using that value to determine compatibility.</span></span>

### <a name="change-positional-parameter-for-powershellexe-from--command-to--file-4019httpsgithubcompowershellpowershellissues4019"></a><span data-ttu-id="76cbf-204">將 `powershell.exe` 的位置參數從 `-Command` 變更為 `-File` [#4019](https://github.com/PowerShell/PowerShell/issues/4019)</span><span class="sxs-lookup"><span data-stu-id="76cbf-204">Change positional parameter for `powershell.exe` from `-Command` to `-File` [#4019](https://github.com/PowerShell/PowerShell/issues/4019)</span></span>

<span data-ttu-id="76cbf-205">允許在非 Windows 平台上透過 Shebang 使用 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="76cbf-205">Enable shebang use of PowerShell on non-Windows platforms.</span></span> <span data-ttu-id="76cbf-206">這意謂著在 Unix 型系統上，您可以建立會自動叫用 PowerShell 的指令碼可執行檔，而無須明確叫用 `pwsh`。</span><span class="sxs-lookup"><span data-stu-id="76cbf-206">This means on Unix based systems, you can make a script executable that would invoke PowerShell automatically rather than explicitly invoking `pwsh`.</span></span> <span data-ttu-id="76cbf-207">這也意謂著您現在可以執行 `powershell foo.ps1` 或 `powershell fooScript` 這類命令，而無須指定 `-File`。</span><span class="sxs-lookup"><span data-stu-id="76cbf-207">This also means that you can now do things like `powershell foo.ps1` or `powershell fooScript` without specifying `-File`.</span></span> <span data-ttu-id="76cbf-208">不過，這項變更現在會要求您在嘗試執行 `powershell.exe Get-Command` 這類命令時，明確指定 `-c` 或 `-Command`。</span><span class="sxs-lookup"><span data-stu-id="76cbf-208">However, this change now requires that you explicitly specify `-c` or `-Command` when trying to do things like `powershell.exe Get-Command`.</span></span>

### <a name="implement-unicode-escape-parsing-3958httpsgithubcompowershellpowershellissues3958"></a><span data-ttu-id="76cbf-209">實作 Unicode 逸出剖析 [#3958](https://github.com/PowerShell/PowerShell/issues/3958)</span><span class="sxs-lookup"><span data-stu-id="76cbf-209">Implement Unicode escape parsing [#3958](https://github.com/PowerShell/PowerShell/issues/3958)</span></span>

<span data-ttu-id="76cbf-210">`` `u#### `` 或 `` `u{####} `` 會轉換成對應的 Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="76cbf-210">`` `u#### `` or `` `u{####} `` is converted to the corresponding Unicode character.</span></span> <span data-ttu-id="76cbf-211">若要輸出常值 `` `u ``，請將反單引號逸出：``` ``u ```。</span><span class="sxs-lookup"><span data-stu-id="76cbf-211">To output a literal `` `u ``, escape the backtick: ``` ``u ```.</span></span>

### <a name="change-new-modulemanifest-encoding-to-utf8nobom-on-non-windows-platforms-3940httpsgithubcompowershellpowershellissues3940"></a><span data-ttu-id="76cbf-212">在非 Windows 平台上將 `New-ModuleManifest` 編碼變更為 `UTF8NoBOM` [#3940](https://github.com/PowerShell/PowerShell/issues/3940)</span><span class="sxs-lookup"><span data-stu-id="76cbf-212">Change `New-ModuleManifest` encoding to `UTF8NoBOM` on non-Windows platforms [#3940](https://github.com/PowerShell/PowerShell/issues/3940)</span></span>

<span data-ttu-id="76cbf-213">先前，`New-ModuleManifest` 會以 UTF-16 建立含有 BOM 的 psd1 資訊清單，而導致對 Linux 工具造成問題。</span><span class="sxs-lookup"><span data-stu-id="76cbf-213">Previously, `New-ModuleManifest` creates psd1 manifests in UTF-16 with BOM, creating a problem for Linux tools.</span></span> <span data-ttu-id="76cbf-214">這項中斷性變更會在非 Windows 平台中，將 `New-ModuleManifest` 的編碼變更為 UTF (無 BOM)。</span><span class="sxs-lookup"><span data-stu-id="76cbf-214">This breaking change changes the encoding of `New-ModuleManifest` to be UTF (no BOM) in non-Windows platforms.</span></span>

### <a name="prevent-get-childitem-from-recursing-into-symlinks-1875-3780httpsgithubcompowershellpowershellissues3780"></a><span data-ttu-id="76cbf-215">防止 `Get-ChildItem` 遞迴到符號連結中 (#1875)。</span><span class="sxs-lookup"><span data-stu-id="76cbf-215">Prevent `Get-ChildItem` from recursing into symlinks (#1875).</span></span> [<span data-ttu-id="76cbf-216">#3780</span><span class="sxs-lookup"><span data-stu-id="76cbf-216">#3780</span></span>](https://github.com/PowerShell/PowerShell/issues/3780)

<span data-ttu-id="76cbf-217">這項變更會讓 `Get-ChildItem`與 Unix `ls -r` 及 Windows `dir /s` 原生命令更趨一致。</span><span class="sxs-lookup"><span data-stu-id="76cbf-217">This change brings `Get-ChildItem` more in line with the Unix `ls -r` and the Windows `dir /s` native commands.</span></span> <span data-ttu-id="76cbf-218">與所提到的命令相同，此 Cmdlet 會顯示在遞迴期間所找到目錄的符號連結，但不會遞迴到這些符號連結中。</span><span class="sxs-lookup"><span data-stu-id="76cbf-218">Like the mentioned commands, the cmdlet displays symbolic links to directories found during recursion, but does not recurse into them.</span></span>

### <a name="fix-get-content--delimiter-to-not-include-the-delimiter-in-the-returned-lines-3706httpsgithubcompowershellpowershellissues3706"></a><span data-ttu-id="76cbf-219">將 `Get-Content -Delimiter` 修正為不在傳回的行中包含分隔符號 [#3706](https://github.com/PowerShell/PowerShell/issues/3706)</span><span class="sxs-lookup"><span data-stu-id="76cbf-219">Fix `Get-Content -Delimiter` to not include the delimiter in the returned lines [#3706](https://github.com/PowerShell/PowerShell/issues/3706)</span></span>

<span data-ttu-id="76cbf-220">先前，使用 `Get-Content -Delimiter` 時的輸出既不一致也不便利，因為需要進行進一步的資料處理，才能移除分隔符號。</span><span class="sxs-lookup"><span data-stu-id="76cbf-220">Previously, the output while using `Get-Content -Delimiter` was inconsistent and inconvenient as it required further processing of the data to remove the delimiter.</span></span> <span data-ttu-id="76cbf-221">這項變更會將所傳回行中的分隔符號移除。</span><span class="sxs-lookup"><span data-stu-id="76cbf-221">This change removes the delimiter in returned lines.</span></span>

### <a name="implement-format-hex-in-c-3320httpsgithubcompowershellpowershellissues3320"></a><span data-ttu-id="76cbf-222">實作 C# 中的 Format-Hex [#3320](https://github.com/PowerShell/PowerShell/issues/3320)</span><span class="sxs-lookup"><span data-stu-id="76cbf-222">Implement Format-Hex in C# [#3320](https://github.com/PowerShell/PowerShell/issues/3320)</span></span>

<span data-ttu-id="76cbf-223">`-Raw` 參數現在是一個「無作業」(亦即不執行任何操作)。</span><span class="sxs-lookup"><span data-stu-id="76cbf-223">The `-Raw` parameter is now a "no-op" (in that it does nothing).</span></span> <span data-ttu-id="76cbf-224">今後，所有的輸出都會以真實的數字表示顯示，其中包括其類型的所有位元組 (這是在這項變更之前，`-Raw` 參數所正式執行的工作)。</span><span class="sxs-lookup"><span data-stu-id="76cbf-224">Going forward all of the output will be displayed with a true representation of numbers that includes all of the bytes for its type (what the `-Raw` parameter was formally doing prior to this change).</span></span>

### <a name="powershell-as-a-default-shell-doesnt-work-with-script-command-3319httpsgithubcompowershellpowershellissues3319"></a><span data-ttu-id="76cbf-225">作為預設殼層的 PowerShell 並不與指令碼命令搭配運作 [#3319](https://github.com/PowerShell/PowerShell/issues/3319)</span><span class="sxs-lookup"><span data-stu-id="76cbf-225">PowerShell as a default shell doesn't work with script command [#3319](https://github.com/PowerShell/PowerShell/issues/3319)</span></span>

<span data-ttu-id="76cbf-226">在 Unix 上，殼層接受互動式殼層的 `-i` 是一項慣例，許多工具都預期此行為 (例如 `script`，以及將 PowerShell 設定為預設殼層時) 而會使用 `-i` 參數來呼叫殼層。</span><span class="sxs-lookup"><span data-stu-id="76cbf-226">On Unix, it is a convention for shells to accept `-i` for an interactive shell and many tools expect this behavior (`script` for example, and when setting PowerShell as the default shell) and calls the shell with the `-i` switch.</span></span> <span data-ttu-id="76cbf-227">這項變更之所以為中斷性變更，在於 `-i` 先前可用來作為用以比對 `-inputformat` 的簡寫，但現在則必須使用 `-in`。</span><span class="sxs-lookup"><span data-stu-id="76cbf-227">This change is breaking in that `-i` previously could be used as short hand to match `-inputformat`, which now needs to be `-in`.</span></span>

### <a name="typo-fix-in-get-computerinfo-property-name-3167httpsgithubcompowershellpowershellissues3167"></a><span data-ttu-id="76cbf-228">Get-ComputerInfo 屬性名稱中的錯字修正 [#3167](https://github.com/PowerShell/PowerShell/issues/3167)</span><span class="sxs-lookup"><span data-stu-id="76cbf-228">Typo fix in Get-ComputerInfo property name [#3167](https://github.com/PowerShell/PowerShell/issues/3167)</span></span>

<span data-ttu-id="76cbf-229">`BiosSerialNumber` 先前拼字錯誤導致變成 `BiosSeralNumber`，現已變更為正確的拼字。</span><span class="sxs-lookup"><span data-stu-id="76cbf-229">`BiosSerialNumber` was misspelled as `BiosSeralNumber` and has been changed to the correct spelling.</span></span>

### <a name="add-get-stringhash-and-get-filehash-cmdlets-3024httpsgithubcompowershellpowershellissues3024"></a><span data-ttu-id="76cbf-230">新增 `Get-StringHash` 和 `Get-FileHash` Cmdlet [#3024](https://github.com/PowerShell/PowerShell/issues/3024)</span><span class="sxs-lookup"><span data-stu-id="76cbf-230">Add `Get-StringHash` and `Get-FileHash` cmdlets [#3024](https://github.com/PowerShell/PowerShell/issues/3024)</span></span>

<span data-ttu-id="76cbf-231">這項變更是因為 CoreFX 不支援某些雜湊演算法，所以已不再提供這些演算法：</span><span class="sxs-lookup"><span data-stu-id="76cbf-231">This change is that some hash algorithms are not supported by CoreFX, therefore they are no longer available:</span></span>

- `MACTripleDES`
- `RIPEMD160`

### <a name="add-validation-on-get--cmdlets-where-passing-null-returns-all-objects-instead-of-error-2672httpsgithubcompowershellpowershellissues2672"></a><span data-ttu-id="76cbf-232">在傳遞 $null 會傳回所有物件而非錯誤的 `Get-*` Cmdlet 上新增驗證 [#2672](https://github.com/PowerShell/PowerShell/issues/2672)</span><span class="sxs-lookup"><span data-stu-id="76cbf-232">Add validation on `Get-*` cmdlets where passing $null returns all objects instead of error [#2672](https://github.com/PowerShell/PowerShell/issues/2672)</span></span>

<span data-ttu-id="76cbf-233">將 `$null` 傳遞給下列任何一項現在都會擲回錯誤：</span><span class="sxs-lookup"><span data-stu-id="76cbf-233">Passing `$null` to any of the following now throws an error:</span></span>

- `Get-Credential -UserName`
- `Get-Event -SourceIdentifier`
- `Get-EventSubscriber -SourceIdentifier`
- `Get-Help -Name`
- `Get-PSBreakpoint -Script`
- `Get-PSProvider -PSProvider`
- `Get-PSSessionConfiguration -Name`
- `Get-PSSnapin -Name`
- `Get-Runspace -Name`
- `Get-RunspaceDebug -RunspaceName`
- `Get-Service -Name`
- `Get-TraceSource -Name`
- `Get-Variable -Name`
- `Get-WmiObject -Class`
- `Get-WmiObject -Property`

### <a name="add-support-w3c-extended-log-file-format-in-import-csv-2482httpsgithubcompowershellpowershellissues2482"></a><span data-ttu-id="76cbf-234">在 `Import-Csv` 中新增對 W3C 延伸記錄檔格式的支援 [#2482](https://github.com/PowerShell/PowerShell/issues/2482)</span><span class="sxs-lookup"><span data-stu-id="76cbf-234">Add support W3C Extended Log File Format in `Import-Csv` [#2482](https://github.com/PowerShell/PowerShell/issues/2482)</span></span>

<span data-ttu-id="76cbf-235">先前，無法使用 `Import-Csv` Cmdlet 來直接匯入 W3C 延伸記錄檔格式的記錄檔，而需要採取額外的動作。</span><span class="sxs-lookup"><span data-stu-id="76cbf-235">Previously, the `Import-Csv` cmdlet cannot be used to directly import the log files in W3C extended log format and additional action would be required.</span></span> <span data-ttu-id="76cbf-236">有了這項變更之後，便可支援 W3C 延伸記錄檔格式。</span><span class="sxs-lookup"><span data-stu-id="76cbf-236">With this change, W3C extended log format is supported.</span></span>

### <a name="parameter-binding-problem-with-valuefromremainingarguments-in-ps-functions-2035httpsgithubcompowershellpowershellissues2035"></a><span data-ttu-id="76cbf-237">PS 函式中的 `ValueFromRemainingArguments` 參數繫結問題 [#2035](https://github.com/PowerShell/PowerShell/issues/2035)</span><span class="sxs-lookup"><span data-stu-id="76cbf-237">Parameter binding problem with `ValueFromRemainingArguments` in PS functions [#2035](https://github.com/PowerShell/PowerShell/issues/2035)</span></span>

<span data-ttu-id="76cbf-238">`ValueFromRemainingArguments` 現在會以陣列的形式傳回值，而不是傳回本身為陣列的單一值。</span><span class="sxs-lookup"><span data-stu-id="76cbf-238">`ValueFromRemainingArguments` now returns the values as an array instead of a single value which itself is an array.</span></span>

### <a name="buildversion-is-removed-from-psversiontable-1415httpsgithubcompowershellpowershellissues1415"></a><span data-ttu-id="76cbf-239">從 `$PSVersionTable` 中移除 `BuildVersion` [#1415](https://github.com/PowerShell/PowerShell/issues/1415)</span><span class="sxs-lookup"><span data-stu-id="76cbf-239">`BuildVersion` is removed from `$PSVersionTable` [#1415](https://github.com/PowerShell/PowerShell/issues/1415)</span></span>

<span data-ttu-id="76cbf-240">從 `$PSVersionTable` 中移除 `BuildVersion` 屬性。</span><span class="sxs-lookup"><span data-stu-id="76cbf-240">Remove the `BuildVersion` property from `$PSVersionTable`.</span></span> <span data-ttu-id="76cbf-241">此屬性已繫結至 Windows 組建版本。</span><span class="sxs-lookup"><span data-stu-id="76cbf-241">This property was tied to the Windows build version.</span></span> <span data-ttu-id="76cbf-242">建議您改用 `GitCommitId` 來擷取 PowerShell Core 的確切組建版本。</span><span class="sxs-lookup"><span data-stu-id="76cbf-242">Instead, we recommend that you use `GitCommitId` to retrieve the exact build version of PowerShell Core.</span></span>

### <a name="changes-to-web-cmdlets"></a><span data-ttu-id="76cbf-243">Web Cmdlet 的變更</span><span class="sxs-lookup"><span data-stu-id="76cbf-243">Changes to Web Cmdlets</span></span>

<span data-ttu-id="76cbf-244">Web Cmdlet 的基礎 .NET API 已變更為 `System.Net.Http.HttpClient`。</span><span class="sxs-lookup"><span data-stu-id="76cbf-244">The underlying .NET API of the Web Cmdlets has been changed to `System.Net.Http.HttpClient`.</span></span> <span data-ttu-id="76cbf-245">這項變更提供許多優點。</span><span class="sxs-lookup"><span data-stu-id="76cbf-245">This change provides many benefits.</span></span> <span data-ttu-id="76cbf-246">不過，這項變更再加上缺乏與 Internet Explorer 的互通性，已在 `Invoke-WebRequest` 和 `Invoke-RestMethod` 內造成數個中斷性變更。</span><span class="sxs-lookup"><span data-stu-id="76cbf-246">However, this change along with a lack of interoperability with Internet Explorer have resulted in several breaking changes within `Invoke-WebRequest` and `Invoke-RestMethod`.</span></span>

- <span data-ttu-id="76cbf-247">`Invoke-WebRequest` 現在僅支援基本 HTML 剖析。</span><span class="sxs-lookup"><span data-stu-id="76cbf-247">`Invoke-WebRequest` now supports basic HTML Parsing only.</span></span> <span data-ttu-id="76cbf-248">`Invoke-WebRequest` 一律會傳回 `BasicHtmlWebResponseObject` 物件。</span><span class="sxs-lookup"><span data-stu-id="76cbf-248">`Invoke-WebRequest` always returns a `BasicHtmlWebResponseObject` object.</span></span> <span data-ttu-id="76cbf-249">`ParsedHtml` 和 `Forms` 屬性已被移除。</span><span class="sxs-lookup"><span data-stu-id="76cbf-249">The `ParsedHtml` and `Forms` properties have been removed.</span></span>
- <span data-ttu-id="76cbf-250">`BasicHtmlWebResponseObject.Headers` 值現在是 `String[]`，而不是 `String`。</span><span class="sxs-lookup"><span data-stu-id="76cbf-250">`BasicHtmlWebResponseObject.Headers` values are now `String[]` instead of `String`.</span></span>
- <span data-ttu-id="76cbf-251">`BasicHtmlWebResponseObject.BaseResponse` 現在是 `System.Net.Http.HttpResponseMessage` 物件。</span><span class="sxs-lookup"><span data-stu-id="76cbf-251">`BasicHtmlWebResponseObject.BaseResponse` is now a `System.Net.Http.HttpResponseMessage` object.</span></span>
- <span data-ttu-id="76cbf-252">Web Cmdlet 例外狀況上的 `Response` 屬性現在是 `System.Net.Http.HttpResponseMessage` 物件。</span><span class="sxs-lookup"><span data-stu-id="76cbf-252">The `Response` property on Web Cmdlet exceptions is now a `System.Net.Http.HttpResponseMessage` object.</span></span>
- <span data-ttu-id="76cbf-253">嚴格 RFC 標頭剖析現在是 `-Headers` 和 `-UserAgent` 參數的預設值。</span><span class="sxs-lookup"><span data-stu-id="76cbf-253">Strict RFC header parsing is now default for the `-Headers` and `-UserAgent` parameter.</span></span> <span data-ttu-id="76cbf-254">您可以使用 `-SkipHeaderValidation` 來略過此作業。</span><span class="sxs-lookup"><span data-stu-id="76cbf-254">This can be bypassed with `-SkipHeaderValidation`.</span></span>
- <span data-ttu-id="76cbf-255">已不再支援 `file://` 和 `ftp://` URI 配置。</span><span class="sxs-lookup"><span data-stu-id="76cbf-255">`file://` and `ftp://` URI schemes are no longer supported.</span></span>
- <span data-ttu-id="76cbf-256">已不再接受 `System.Net.ServicePointManager` 設定。</span><span class="sxs-lookup"><span data-stu-id="76cbf-256">`System.Net.ServicePointManager` settings are no longer honored.</span></span>
- <span data-ttu-id="76cbf-257">macOS 上目前未提供任何憑證型驗證。</span><span class="sxs-lookup"><span data-stu-id="76cbf-257">There is currently no certificate based authentication available on macOS.</span></span>
- <span data-ttu-id="76cbf-258">透過 `http://` URI 使用 `-Credential` 將會造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="76cbf-258">Use of `-Credential` over an `http://` URI will result in an error.</span></span> <span data-ttu-id="76cbf-259">請使用 `https://` URI 或提供 `-AllowUnencryptedAuthentication` 參數來抑制此錯誤。</span><span class="sxs-lookup"><span data-stu-id="76cbf-259">Use an `https://` URI or supply the `-AllowUnencryptedAuthentication` parameter to suppress the error.</span></span>
