---
ms.date: 07/08/2020
keywords: dsc,powershell,設定,安裝
title: 資源撰寫檢查清單
description: 此文章包含最佳做法檢查清單，其應該在撰寫新的 DSC 資源時加以使用。
ms.openlocfilehash: 5b618511f730c80104620c84e693c13ae4f536ac
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656334"
---
# <a name="resource-authoring-checklist"></a><span data-ttu-id="68c9d-104">資源撰寫檢查清單</span><span class="sxs-lookup"><span data-stu-id="68c9d-104">Resource authoring checklist</span></span>

<span data-ttu-id="68c9d-105">此檢查清單是撰寫新 DSC 資源時的最佳做法清單。</span><span class="sxs-lookup"><span data-stu-id="68c9d-105">This checklist is a list of best practices when authoring a new DSC Resource.</span></span>

## <a name="resource-module-contains-psd1-file-and-schemamof-for-every-resource"></a><span data-ttu-id="68c9d-106">資源模組包含各項資源的 .psd1 檔案和 schema.mof</span><span class="sxs-lookup"><span data-stu-id="68c9d-106">Resource module contains .psd1 file and schema.mof for every resource</span></span>

<span data-ttu-id="68c9d-107">檢查資源有沒有正確的結構，以及是否包含所有必要的檔案。</span><span class="sxs-lookup"><span data-stu-id="68c9d-107">Check that your resource has correct structure and contains all required files.</span></span> <span data-ttu-id="68c9d-108">每個資源模組都應該包含 .psd1 檔案，且每個非複合資源都應該有 schema.mof 檔案。</span><span class="sxs-lookup"><span data-stu-id="68c9d-108">Every resource module should contain a .psd1 file and every non-composite resource should have schema.mof file.</span></span>
<span data-ttu-id="68c9d-109">`Get-DscResource` 將不會列出未包含結構描述的資源，而且使用者也不能在於 ISE 中針對那些模組撰寫程式碼時使用 IntelliSense。</span><span class="sxs-lookup"><span data-stu-id="68c9d-109">Resources that do not contain schema will not be listed by `Get-DscResource` and users will not be able to use the IntelliSense when writing code against those modules in ISE.</span></span> <span data-ttu-id="68c9d-110">xRemoteFile 資源的目錄結構，是 [xPSDesiredStateConfiguration 資源模組](https://github.com/PowerShell/xPSDesiredStateConfiguration)的一部分，看起來像這樣︰</span><span class="sxs-lookup"><span data-stu-id="68c9d-110">The directory structure for xRemoteFile resource, which is part of the [xPSDesiredStateConfiguration resource module](https://github.com/PowerShell/xPSDesiredStateConfiguration), looks as follows:</span></span>

```
xPSDesiredStateConfiguration
    DSCResources
        MSFT_xRemoteFile
            MSFT_xRemoteFile.psm1
            MSFT_xRemoteFile.schema.mof
    Examples
        xRemoteFile_DownloadFile.ps1
    ResourceDesignerScripts
        GenerateXRemoteFileSchema.ps1
    Tests
        ResourceDesignerTests.ps1
    xPSDesiredStateConfiguration.psd1
```

## <a name="resource-and-schema-are-correct"></a><span data-ttu-id="68c9d-111">資源和結構描述正確</span><span class="sxs-lookup"><span data-stu-id="68c9d-111">Resource and schema are correct</span></span>

<span data-ttu-id="68c9d-112">驗證資源結構描述 (`*.schema.mof`) 檔案。</span><span class="sxs-lookup"><span data-stu-id="68c9d-112">Verify the resource schema (`*.schema.mof`) file.</span></span> <span data-ttu-id="68c9d-113">您可以使用 [DSC 資源設計工具](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0)協助開發及測試您的結構描述。</span><span class="sxs-lookup"><span data-stu-id="68c9d-113">You can use the [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) to help develop and test your schema.</span></span> <span data-ttu-id="68c9d-114">請確認：</span><span class="sxs-lookup"><span data-stu-id="68c9d-114">Make sure that:</span></span>

- <span data-ttu-id="68c9d-115">屬性類型正確 (例如，接受數值的屬性不使用字串，應改用 UInt32 或其他數值類型)</span><span class="sxs-lookup"><span data-stu-id="68c9d-115">Property types are correct (e.g. don't use String for properties which accept numeric values, you should use UInt32 or other numeric types instead)</span></span>
- <span data-ttu-id="68c9d-116">已正確指定屬性 (property) 屬性 (attribute)：([key]、[required]、[write]、[read])</span><span class="sxs-lookup"><span data-stu-id="68c9d-116">Property attributes are specified correctly as: ([key], [required], [write], [read])</span></span>
- <span data-ttu-id="68c9d-117">結構描述中至少要有一個參數標示為 [key]</span><span class="sxs-lookup"><span data-stu-id="68c9d-117">At least one parameter in the schema has to be marked as [key]</span></span>
- <span data-ttu-id="68c9d-118">[read] 屬性和後列任一項不並存：[required]、[key]、[write]</span><span class="sxs-lookup"><span data-stu-id="68c9d-118">[read] property does not coexist together with any of: [required], [key], [write]</span></span>
- <span data-ttu-id="68c9d-119">如果除 [read] 以外指定了多個限定詞，則 [key] 優先</span><span class="sxs-lookup"><span data-stu-id="68c9d-119">If multiple qualifiers are specified except [read], then [key] takes precedence</span></span>
- <span data-ttu-id="68c9d-120">如果指定 [write] 和 [required]，則 [required] 優先</span><span class="sxs-lookup"><span data-stu-id="68c9d-120">If [write] and [required] are specified, then [required] takes precedence</span></span>
- <span data-ttu-id="68c9d-121">視需要指定 ValueMap。範例：</span><span class="sxs-lookup"><span data-stu-id="68c9d-121">ValueMap is specified where appropriate Example:</span></span>

  ```
  [Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
  ```

- <span data-ttu-id="68c9d-122">指定易記的名稱並確認 DSC 命名慣例</span><span class="sxs-lookup"><span data-stu-id="68c9d-122">Friendly name is specified and confirms to DSC naming conventions</span></span>

  <span data-ttu-id="68c9d-123">範例： `[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]`</span><span class="sxs-lookup"><span data-stu-id="68c9d-123">Example: `[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]`</span></span>

- <span data-ttu-id="68c9d-124">每個欄位都有具意義的描述。</span><span class="sxs-lookup"><span data-stu-id="68c9d-124">Every field has meaningful description.</span></span> <span data-ttu-id="68c9d-125">PowerShell GitHub 存放庫有很好的範例，例如[用於 xRemoteFile 的 .schema.mof](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/DSCResources/DSC_xRemoteFile/DSC_xRemoteFile.schema.mof)</span><span class="sxs-lookup"><span data-stu-id="68c9d-125">The PowerShell GitHub repository has good examples, such as the [.schema.mof for xRemoteFile](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/DSCResources/DSC_xRemoteFile/DSC_xRemoteFile.schema.mof)</span></span>

<span data-ttu-id="68c9d-126">此外，建議使用 [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) (DSC 資源設計工具) 的 `Test-xDscResource` 和 `Test-xDscSchema` Cmdlet 來自動驗證資源和結構描述：</span><span class="sxs-lookup"><span data-stu-id="68c9d-126">Additionally, you should use `Test-xDscResource` and `Test-xDscSchema` cmdlets from [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) to automatically verify the resource and schema:</span></span>

```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```

<span data-ttu-id="68c9d-127">例如：</span><span class="sxs-lookup"><span data-stu-id="68c9d-127">For example:</span></span>

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="resource-loads-without-errors"></a><span data-ttu-id="68c9d-128">資源載入無錯誤</span><span class="sxs-lookup"><span data-stu-id="68c9d-128">Resource loads without errors</span></span>

<span data-ttu-id="68c9d-129">檢查是否可以成功載入資源模組。</span><span class="sxs-lookup"><span data-stu-id="68c9d-129">Check whether the resource module can be successfully loaded.</span></span> <span data-ttu-id="68c9d-130">這可以手動方式操作，執行 `Import-Module <resource_module> -force` 並確認無任何錯誤發生，或撰寫測試自動化。</span><span class="sxs-lookup"><span data-stu-id="68c9d-130">This can be achieved manually, by running `Import-Module <resource_module> -force` and confirming that no errors occurred, or by writing test automation.</span></span> <span data-ttu-id="68c9d-131">如果是後者，您可以在測試案例遵循這個結構：</span><span class="sxs-lookup"><span data-stu-id="68c9d-131">In case of the latter, you can follow this structure in your test case:</span></span>

```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw "Module was not imported correctly. Errors returned: $error"
}
```

## <a name="resource-is-idempotent-in-the-positive-case"></a><span data-ttu-id="68c9d-132">資源在正案例中為等冪</span><span class="sxs-lookup"><span data-stu-id="68c9d-132">Resource is idempotent in the positive case</span></span>

<span data-ttu-id="68c9d-133">DSC 資源的基本特性之一為等冪。</span><span class="sxs-lookup"><span data-stu-id="68c9d-133">One of the fundamental characteristics of DSC resources is idempotence.</span></span> <span data-ttu-id="68c9d-134">這表示多次套用包含該資源的 DSC 設定，都會得到相同的結果。</span><span class="sxs-lookup"><span data-stu-id="68c9d-134">It means that applying a DSC configuration containing that resource multiple times will always achieve the same result.</span></span> <span data-ttu-id="68c9d-135">例如，如果我們建立包含下列檔案資源的設定：</span><span class="sxs-lookup"><span data-stu-id="68c9d-135">For example, if we create a configuration which contains the following File resource:</span></span>

```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
}
```

<span data-ttu-id="68c9d-136">第一次套用它之後，檔案 test.txt 應該會出現在 `C:\test` 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="68c9d-136">After applying it for the first time, file test.txt should appear in `C:\test` folder.</span></span> <span data-ttu-id="68c9d-137">不過，後續進行相同設定時應該不會變更電腦的狀態 (例如，應該不會建立任何 `test.txt` 檔案複本)。</span><span class="sxs-lookup"><span data-stu-id="68c9d-137">However, subsequent runs of the same configuration should not change the state of the machine (e.g. no copies of the `test.txt` file should be created).</span></span> <span data-ttu-id="68c9d-138">為確保資源為等冪的，您可以在直接測試資源時重複呼叫 `Set-TargetResource`，或在執行端對端測試時多次呼叫 `Start-DscConfiguration`。</span><span class="sxs-lookup"><span data-stu-id="68c9d-138">To ensure a resource is idempotent you can repeatedly call `Set-TargetResource` when testing the resource directly, or call `Start-DscConfiguration` multiple times when doing end to end testing.</span></span> <span data-ttu-id="68c9d-139">每次執行後的結果都應該相同。</span><span class="sxs-lookup"><span data-stu-id="68c9d-139">The result should be the same after every run.</span></span>

## <a name="test-user-modification-scenario"></a><span data-ttu-id="68c9d-140">測試使用者修改案例</span><span class="sxs-lookup"><span data-stu-id="68c9d-140">Test user modification scenario</span></span>

<span data-ttu-id="68c9d-141">透過變更電腦狀態，然後重新執行 DSC，您就可以驗證 `Set-TargetResource` 和 `Test-TargetResource` 是否正確執行。</span><span class="sxs-lookup"><span data-stu-id="68c9d-141">By changing the state of the machine and then rerunning DSC, you can verify that `Set-TargetResource` and `Test-TargetResource` function properly.</span></span> <span data-ttu-id="68c9d-142">以下為應該採取的步驟：</span><span class="sxs-lookup"><span data-stu-id="68c9d-142">Here are steps you should take:</span></span>

1. <span data-ttu-id="68c9d-143">請從不在預期狀態的資源開始。</span><span class="sxs-lookup"><span data-stu-id="68c9d-143">Start with the resource not in the desired state.</span></span>
1. <span data-ttu-id="68c9d-144">以資源執行設定</span><span class="sxs-lookup"><span data-stu-id="68c9d-144">Run configuration with your resource</span></span>
1. <span data-ttu-id="68c9d-145">驗證 `Test-DscConfiguration` 會傳回 True</span><span class="sxs-lookup"><span data-stu-id="68c9d-145">Verify `Test-DscConfiguration` returns True</span></span>
1. <span data-ttu-id="68c9d-146">將已設定的項目修改為不在所需狀態</span><span class="sxs-lookup"><span data-stu-id="68c9d-146">Modify the configured item to be out of the desired state</span></span>
1. <span data-ttu-id="68c9d-147">驗證 `Test-DscConfiguration` 會傳回 False</span><span class="sxs-lookup"><span data-stu-id="68c9d-147">Verify `Test-DscConfiguration` returns false</span></span>

<span data-ttu-id="68c9d-148">以下是更具體的登錄資源使用範例：</span><span class="sxs-lookup"><span data-stu-id="68c9d-148">Here's a more concrete example using Registry resource:</span></span>

1. <span data-ttu-id="68c9d-149">請從不在預期狀態的登錄機碼開始</span><span class="sxs-lookup"><span data-stu-id="68c9d-149">Start with registry key not in the desired state</span></span>
1. <span data-ttu-id="68c9d-150">搭配設定執行 `Start-DscConfiguration`，以使其進入預期狀態，並驗證它會通過。</span><span class="sxs-lookup"><span data-stu-id="68c9d-150">Run `Start-DscConfiguration` with a configuration to put it in the desired state and verify it passes.</span></span>
1. <span data-ttu-id="68c9d-151">執行 `Test-DscConfiguration`，並驗證它會傳回 True</span><span class="sxs-lookup"><span data-stu-id="68c9d-151">Run `Test-DscConfiguration` and verify it returns true</span></span>
1. <span data-ttu-id="68c9d-152">修改機碼值，使它不在預期狀態</span><span class="sxs-lookup"><span data-stu-id="68c9d-152">Modify the value of the key so that it is not in the desired state</span></span>
1. <span data-ttu-id="68c9d-153">執行 `Test-DscConfiguration`，並驗證它會傳回 False</span><span class="sxs-lookup"><span data-stu-id="68c9d-153">Run `Test-DscConfiguration` and verify it returns false</span></span>
1. <span data-ttu-id="68c9d-154">已使用 `Get-DscConfiguration` 驗證 `Get-TargetResource` 功能</span><span class="sxs-lookup"><span data-stu-id="68c9d-154">`Get-TargetResource` functionality was verified using `Get-DscConfiguration`</span></span>

<span data-ttu-id="68c9d-155">`Get-TargetResource` 應該會傳回資源目前狀態的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="68c9d-155">`Get-TargetResource` should return details of the current state of the resource.</span></span> <span data-ttu-id="68c9d-156">確定會以下列方法進行測試：在套用設定後呼叫 `Get-DscConfiguration`，並驗證輸出會正確反映電腦目前的狀態。</span><span class="sxs-lookup"><span data-stu-id="68c9d-156">Make sure to test it by calling `Get-DscConfiguration` after you apply the configuration and verifying that output correctly reflects the current state of the machine.</span></span> <span data-ttu-id="68c9d-157">請務必分開測試，因為呼叫 `Start-DscConfiguration` 時，不會顯示這個區域的任何問題。</span><span class="sxs-lookup"><span data-stu-id="68c9d-157">It's important to test it separately, since any issues in this area won't appear when calling `Start-DscConfiguration`.</span></span>

## <a name="call-getsettest-targetresource-functions-directly"></a><span data-ttu-id="68c9d-158">直接呼叫 **Get/Set/Test-TargetResource** 函式</span><span class="sxs-lookup"><span data-stu-id="68c9d-158">Call **Get/Set/Test-TargetResource** functions directly</span></span>

<span data-ttu-id="68c9d-159">請務必測試在資源中實作的 `Get/Set/Test-TargetResource` 函式，方法是直接呼叫這些函式並確認其如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="68c9d-159">Make sure you test the `Get/Set/Test-TargetResource` functions implemented in your resource by calling them directly and verifying that they work as expected.</span></span>

## <a name="verify-end-to-end-using-start-dscconfiguration"></a><span data-ttu-id="68c9d-160">使用 Start-DscConfiguration 驗證端對端</span><span class="sxs-lookup"><span data-stu-id="68c9d-160">Verify End to End using Start-DscConfiguration</span></span>

<span data-ttu-id="68c9d-161">以直接呼叫的方式測試這些 `Get/Set/Test-TargetResource` 函式很重要，但並非所有的問題都能以這種方式發現。</span><span class="sxs-lookup"><span data-stu-id="68c9d-161">Testing `Get/Set/Test-TargetResource` functions by calling them directly is important, but not all issues will be discovered this way.</span></span> <span data-ttu-id="68c9d-162">測試重點應該放在使用 `Start-DscConfiguration` 或提取伺服器上。</span><span class="sxs-lookup"><span data-stu-id="68c9d-162">You should focus significant part of your testing on using `Start-DscConfiguration` or the pull server.</span></span> <span data-ttu-id="68c9d-163">事實上，這就是使用者使用資源的方法，所以請勿低估這種測試的重要性。</span><span class="sxs-lookup"><span data-stu-id="68c9d-163">In fact, this is how users will use the resource, so don't underestimate the significance of this type of tests.</span></span> <span data-ttu-id="68c9d-164">可能有的問題類型：</span><span class="sxs-lookup"><span data-stu-id="68c9d-164">Possible types of issues:</span></span>

- <span data-ttu-id="68c9d-165">因為 DSC 代理程式以服務方式執行，所以認證/工作階段的行為可能不同。</span><span class="sxs-lookup"><span data-stu-id="68c9d-165">Credential/Session may behave differently because the DSC agent runs as a service.</span></span> <span data-ttu-id="68c9d-166">請務必在此端對端測試所有功能。</span><span class="sxs-lookup"><span data-stu-id="68c9d-166">Be sure to test any features here end to end.</span></span>
- <span data-ttu-id="68c9d-167">`Start-DscConfiguration` 所輸出的錯誤和直接呼叫 `Set-TargetResource` 函式所顯示的錯誤可能不同。</span><span class="sxs-lookup"><span data-stu-id="68c9d-167">Errors output by `Start-DscConfiguration` may be different than those displayed when calling the `Set-TargetResource` function directly.</span></span>

## <a name="test-compatibility-on-all-dsc-supported-platforms"></a><span data-ttu-id="68c9d-168">測試所有 DSC 支援平台的相容性</span><span class="sxs-lookup"><span data-stu-id="68c9d-168">Test compatibility on all DSC supported platforms</span></span>

<span data-ttu-id="68c9d-169">資源應該能在所有 DSC 支援的平台上運作 (Windows Server 2008 R2 及更新版本)。</span><span class="sxs-lookup"><span data-stu-id="68c9d-169">Resource should work on all DSC supported platforms (Windows Server 2008 R2 and newer).</span></span> <span data-ttu-id="68c9d-170">在您的作業系統上安裝最新的 WMF (Windows Management Framework)，以取得最新版的 DSC。</span><span class="sxs-lookup"><span data-stu-id="68c9d-170">Install the latest WMF (Windows Management Framework) on your OS to get the latest version of DSC.</span></span> <span data-ttu-id="68c9d-171">如果最初設計的資源在部分這些平台上無法運作，應該會傳回特定的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="68c9d-171">If your resource does not work on some of these platforms by design, a specific error message should be returned.</span></span> <span data-ttu-id="68c9d-172">亦請確定資源檢查特定電腦上是否有呼叫中的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="68c9d-172">Also, make sure your resource checks whether cmdlets you are calling are present on particular machine.</span></span> <span data-ttu-id="68c9d-173">Windows Server 2012 加入的大量新 Cmdlet，是即使安裝 WMF，Windows Server 2008R2 也不提供的。</span><span class="sxs-lookup"><span data-stu-id="68c9d-173">Windows Server 2012 added a large number of new cmdlets that are not available on Windows Server 2008R2, even with WMF installed.</span></span>

## <a name="verify-on-windows-client-if-applicable"></a><span data-ttu-id="68c9d-174">在 Windows 用戶端上驗證 (如果適用)</span><span class="sxs-lookup"><span data-stu-id="68c9d-174">Verify on Windows Client (if applicable)</span></span>

<span data-ttu-id="68c9d-175">一個極常見的測試間距正在驗證資源是否只能存在於 Windows 的伺服器版本。</span><span class="sxs-lookup"><span data-stu-id="68c9d-175">One very common test gap is verifying the resource only on server versions of Windows.</span></span> <span data-ttu-id="68c9d-176">許多資源也設計在用戶端 SKU 上運作，如果這符合您的情況，請記得也要在這些平台上進行測試。</span><span class="sxs-lookup"><span data-stu-id="68c9d-176">Many resources are also designed to work on Client SKUs, so if that's true in your case, don't forget to test it on those platforms as well.</span></span>

## <a name="get-dscresource-lists-the-resource"></a><span data-ttu-id="68c9d-177">Get-DSCResource 列出這些資源</span><span class="sxs-lookup"><span data-stu-id="68c9d-177">Get-DSCResource lists the resource</span></span>

<span data-ttu-id="68c9d-178">部署模組之後，呼叫 `Get-DscResource` 最後應該會在其他資源中列出您的資源。</span><span class="sxs-lookup"><span data-stu-id="68c9d-178">After deploying the module, calling `Get-DscResource` should list your resource among others as a result.</span></span> <span data-ttu-id="68c9d-179">如果清單中找不到您的資源，請確定您有該資源的 schema.mof 檔案。</span><span class="sxs-lookup"><span data-stu-id="68c9d-179">If you can't find your resource in the list, make sure that schema.mof file for that resource exists.</span></span>

## <a name="resource-module-contains-examples"></a><span data-ttu-id="68c9d-180">資源模組包含範例</span><span class="sxs-lookup"><span data-stu-id="68c9d-180">Resource module contains examples</span></span>

<span data-ttu-id="68c9d-181">建立可幫助其他人了解用法的優質範例。</span><span class="sxs-lookup"><span data-stu-id="68c9d-181">Creating quality examples which will help others understand how to use it.</span></span> <span data-ttu-id="68c9d-182">特別是許多使用者視範例程式碼為文件，這十分重要。</span><span class="sxs-lookup"><span data-stu-id="68c9d-182">This is crucial, especially since many users treat sample code as documentation.</span></span>

- <span data-ttu-id="68c9d-183">首先，您應該決定模組要包含的範例，起碼應涵蓋最重要的資源使用案例：</span><span class="sxs-lookup"><span data-stu-id="68c9d-183">First, you should determine the examples that will be included with the module – at minimum, you should cover most important use cases for your resource:</span></span>
- <span data-ttu-id="68c9d-184">如果模組包含的數項資源，在端對端案例中必須一起工作，基本的端對端範例最好排第一。</span><span class="sxs-lookup"><span data-stu-id="68c9d-184">If your module contains several resources that need to work together for an end-to-end scenario, the basic end-to-end example would ideally be first.</span></span>
- <span data-ttu-id="68c9d-185">初始範例應該簡單易懂：如何在小而易於管理的區塊中 (例如建立新的 VHD) 開始使用資源</span><span class="sxs-lookup"><span data-stu-id="68c9d-185">The initial examples should be very simple -- how to get started with your resources in small manageable chunks (e.g. creating a new VHD)</span></span>
- <span data-ttu-id="68c9d-186">後續的範例應建置於這些範例上 (例如，從 VHD 建立 VM、移除 VM、修改 VM)，顯示進階的功能 (例如，建立具有動態記憶體的 VM)</span><span class="sxs-lookup"><span data-stu-id="68c9d-186">Subsequent examples should build on those examples (e.g. creating a VM from a VHD, removing VM, modifying VM), and show advanced functionality (e.g. creating a VM with dynamic memory)</span></span>
- <span data-ttu-id="68c9d-187">範例設定應該參數化 (所有值都應該當做參數傳遞至設定，不該有任何硬式編碼值)：</span><span class="sxs-lookup"><span data-stu-id="68c9d-187">Example configurations should be parameterized (all values should be passed to the configuration as parameters and there should be no hardcoded values):</span></span>

```powershell
configuration Sample_xRemoteFile_DownloadFile
{
    param
    (
        [string[]] $nodeName = 'localhost',

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $destinationPath,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $uri,

        [String] $userAgent,

        [Hashtable] $headers
    )

    Import-DscResource -Name MSFT_xRemoteFile -ModuleName xPSDesiredStateConfiguration

    Node $nodeName
    {
        xRemoteFile DownloadFile
        {
            DestinationPath = $destinationPath
            Uri = $uri
            UserAgent = $userAgent
            Headers = $headers
        }
    }
}
```

- <span data-ttu-id="68c9d-188">包含一個如何呼叫在範例指令碼結尾有實際值設定的 (註解化) 範例，是個不錯的做法。</span><span class="sxs-lookup"><span data-stu-id="68c9d-188">It's a good practice to include (commented out) example of how to call the configuration with the actual values at the end of the example script.</span></span> <span data-ttu-id="68c9d-189">例如，在上述設定中，將 UserAgent 指定為下列項目，很明顯地不是最佳做法：</span><span class="sxs-lookup"><span data-stu-id="68c9d-189">For example, in the configuration above it isn't necessarily obvious that the best way to specify UserAgent is:</span></span>

  <span data-ttu-id="68c9d-190">`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` 在註解可以釐清設定預期執行的案例中︰</span><span class="sxs-lookup"><span data-stu-id="68c9d-190">`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` In which case a comment can clarify the intended execution of the configuration:</span></span>

```powershell
<#
Sample use (parameter values need to be changed according to your scenario):

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
-userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
#>
```

- <span data-ttu-id="68c9d-191">每個範例請撰寫簡短的描述，說明其用途及參數意義。</span><span class="sxs-lookup"><span data-stu-id="68c9d-191">For each example, write a short description which explains what it does, and the meaning of the parameters.</span></span>
- <span data-ttu-id="68c9d-192">請確定範例涵蓋資源多數的重要案例，且如果沒有任何缺漏，請確認它們是否都可執行，並能讓電腦處於預期狀態。</span><span class="sxs-lookup"><span data-stu-id="68c9d-192">Make sure examples cover most the important scenarios for your resource and if there's nothing missing, verify that they all execute and put machine in the desired state.</span></span>

## <a name="error-messages-are-easy-to-understand-and-help-users-solve-problems"></a><span data-ttu-id="68c9d-193">錯誤訊息容易了解，且能幫助使用者解決問題</span><span class="sxs-lookup"><span data-stu-id="68c9d-193">Error messages are easy to understand and help users solve problems</span></span>

<span data-ttu-id="68c9d-194">好的錯誤訊息應該是：</span><span class="sxs-lookup"><span data-stu-id="68c9d-194">Good error messages should be:</span></span>

- <span data-ttu-id="68c9d-195">有訊息：錯誤訊息的最大問題是它們通常不存在，所以請確定錯誤訊息存在。</span><span class="sxs-lookup"><span data-stu-id="68c9d-195">There: The biggest problem with error messages is that they often don't exist, so make sure they are there.</span></span>
- <span data-ttu-id="68c9d-196">容易了解：一般人看得懂，沒有晦澀難懂的錯誤代碼</span><span class="sxs-lookup"><span data-stu-id="68c9d-196">Easy to understand: Human readable, no obscure error codes</span></span>
- <span data-ttu-id="68c9d-197">精確：確切地描述問題</span><span class="sxs-lookup"><span data-stu-id="68c9d-197">Precise: Describe what's exactly the problem</span></span>
- <span data-ttu-id="68c9d-198">建設性：建議如何修正問題</span><span class="sxs-lookup"><span data-stu-id="68c9d-198">Constructive: Advice how to fix the issue</span></span>
- <span data-ttu-id="68c9d-199">有禮貌：不責怪使用者或讓他們覺得不舒服</span><span class="sxs-lookup"><span data-stu-id="68c9d-199">Polite: Don't blame user or make them feel bad</span></span>

<span data-ttu-id="68c9d-200">請務必驗證端對端案例中的錯誤 (使用 `Start-DscConfiguration`)，因為它們可能與直接執行資源函式時所傳回的錯誤不同。</span><span class="sxs-lookup"><span data-stu-id="68c9d-200">Make sure you verify errors in End to End scenarios (using `Start-DscConfiguration`), because they may differ from those returned when running resource functions directly.</span></span>

## <a name="log-messages-are-easy-to-understand-and-informative-including-verbose-debug-and-etw-logs"></a><span data-ttu-id="68c9d-201">記錄檔訊息容易了解且提供資訊 (包括 –verbose、–debug 和 ETW 記錄檔)</span><span class="sxs-lookup"><span data-stu-id="68c9d-201">Log messages are easy to understand and informative (including –verbose, –debug and ETW logs)</span></span>

<span data-ttu-id="68c9d-202">請確保資源輸出的記錄檔容易了解並向使用者提供值。</span><span class="sxs-lookup"><span data-stu-id="68c9d-202">Ensure that logs outputted by the resource are easy to understand and provide value to the user.</span></span>
<span data-ttu-id="68c9d-203">資源應該要輸出所有對使用者可能有幫助的資訊，但記錄愈多不一定愈好。</span><span class="sxs-lookup"><span data-stu-id="68c9d-203">Resources should output all information which might be helpful to the user, but more logs is not always better.</span></span> <span data-ttu-id="68c9d-204">您應該避免備援以及輸出不提供附加價值的資料 – 不要讓使用者翻找數百筆記錄後才找到自己要找的。</span><span class="sxs-lookup"><span data-stu-id="68c9d-204">You should avoid redundancy and outputting data which does not provide additional value – don't make someone go through hundreds of log entries in order to find what they're looking for.</span></span> <span data-ttu-id="68c9d-205">當然，全無記錄檔也不是這個問題可以接受的解決方案。</span><span class="sxs-lookup"><span data-stu-id="68c9d-205">Of course, no logs is not an acceptable solution for this problem either.</span></span>

<span data-ttu-id="68c9d-206">測試時，您也應該分析詳細資訊和偵錯記錄 (方法是適當地執行 `Start-DscConfiguration` 並搭配 `–Verbose` 和 `–Debug` 參數) 以及 ETW 記錄。</span><span class="sxs-lookup"><span data-stu-id="68c9d-206">When testing, you should also analyze verbose and debug logs (by running `Start-DscConfiguration` with `–Verbose` and `–Debug` switches appropriately), as well as ETW logs.</span></span> <span data-ttu-id="68c9d-207">若要查看 DSC ETW 記錄，請移至事件檢視器，並開啟下列資料夾：Applications and Services- Microsoft - Windows - Desired State Configuration。</span><span class="sxs-lookup"><span data-stu-id="68c9d-207">To see DSC ETW logs, go to Event Viewer and open the following folder: Applications and Services- Microsoft - Windows - Desired State Configuration.</span></span> <span data-ttu-id="68c9d-208">預設會有操作通道，但請確定先啟用分析與偵錯通道，再執行設定。</span><span class="sxs-lookup"><span data-stu-id="68c9d-208">By default there will be Operational channel, but make sure you enable Analytic and Debug channels before running the configuration.</span></span> <span data-ttu-id="68c9d-209">若要啟用分析/偵錯通道，您可以執行下列指令碼︰</span><span class="sxs-lookup"><span data-stu-id="68c9d-209">To enable Analytic/Debug channels, you can execute script below:</span></span>

```powershell
$statusEnabled = $true
# Use "Analytic" to enable Analytic channel
$eventLogFullName = "Microsoft-Windows-Dsc/Debug"
$commandToExecute = "wevtutil set-log $eventLogFullName /e:$statusEnabled /q:$statusEnabled   "
$log = New-Object System.Diagnostics.Eventing.Reader.EventLogConfiguration $eventLogFullName
if($statusEnabled -eq $log.IsEnabled)
{
    Write-Host -Verbose "The channel event log is already enabled"
    return
}
Invoke-Expression $commandToExecute
```

## <a name="resource-implementation-does-not-contain-hardcoded-paths"></a><span data-ttu-id="68c9d-210">資源實作不包含硬式編碼路徑</span><span class="sxs-lookup"><span data-stu-id="68c9d-210">Resource implementation does not contain hardcoded paths</span></span>

<span data-ttu-id="68c9d-211">請確定資源實作中沒有硬式編碼路徑，特別是當它們假設語言 (en-us) 或有可用的系統變數時。</span><span class="sxs-lookup"><span data-stu-id="68c9d-211">Ensure there are no hardcoded paths in the resource implementation, particularly if they assume language (en-us), or when there are system variables that can be used.</span></span> <span data-ttu-id="68c9d-212">如果您的資源需要存取特定的路徑，請使用環境變數，不要使用硬式編碼路徑，因為它在其他電腦上可能不同。</span><span class="sxs-lookup"><span data-stu-id="68c9d-212">If your resource need to access specific paths, use environment variables instead of hardcoding the path, as it may differ on other machines.</span></span>

<span data-ttu-id="68c9d-213">範例：</span><span class="sxs-lookup"><span data-stu-id="68c9d-213">Example:</span></span>

<span data-ttu-id="68c9d-214">不要這樣撰寫：</span><span class="sxs-lookup"><span data-stu-id="68c9d-214">Instead of:</span></span>

```powershell
$tempPath = "C:\Users\kkaczma\AppData\Local\Temp\MyResource"
$programFilesPath = "C:\Program Files (x86)"
```

<span data-ttu-id="68c9d-215">您可以撰寫︰</span><span class="sxs-lookup"><span data-stu-id="68c9d-215">You can write:</span></span>

```powershell
$tempPath = Join-Path $env:temp "MyResource"
$programFilesPath = ${env:ProgramFiles(x86)}
```

## <a name="resource-implementation-does-not-contain-user-information"></a><span data-ttu-id="68c9d-216">資源實作不包含使用者資訊</span><span class="sxs-lookup"><span data-stu-id="68c9d-216">Resource implementation does not contain user information</span></span>

<span data-ttu-id="68c9d-217">請確認程式碼中沒有任何電子郵件名稱、帳戶資訊或人名。</span><span class="sxs-lookup"><span data-stu-id="68c9d-217">Make sure there are no email names, account information, or names of people in the code.</span></span>

## <a name="resource-was-tested-with-validinvalid-credentials"></a><span data-ttu-id="68c9d-218">資源已使用有效/無效的認證測試</span><span class="sxs-lookup"><span data-stu-id="68c9d-218">Resource was tested with valid/invalid credentials</span></span>

<span data-ttu-id="68c9d-219">如果資源使用認證為參數：</span><span class="sxs-lookup"><span data-stu-id="68c9d-219">If your resource takes a credential as parameter:</span></span>

- <span data-ttu-id="68c9d-220">確認當本機系統 (或遠端資源的電腦帳戶) 無存取權時，資源可運作。</span><span class="sxs-lookup"><span data-stu-id="68c9d-220">Verify the resource works when Local System (or the computer account for remote resources) does not have access.</span></span>
- <span data-ttu-id="68c9d-221">確認資源能搭配為 Get、Set 和 Test 指定的認證運作</span><span class="sxs-lookup"><span data-stu-id="68c9d-221">Verify the resource works with a credential specified for Get, Set and Test</span></span>
- <span data-ttu-id="68c9d-222">如果資源存取權是共用的，請測試所有需要支援的變數，如：</span><span class="sxs-lookup"><span data-stu-id="68c9d-222">If your resource accesses shares, test all the variants you need to support, such as:</span></span>
  - <span data-ttu-id="68c9d-223">標準的 Windows 共用。</span><span class="sxs-lookup"><span data-stu-id="68c9d-223">Standard windows shares.</span></span>
  - <span data-ttu-id="68c9d-224">DFS 共用。</span><span class="sxs-lookup"><span data-stu-id="68c9d-224">DFS shares.</span></span>
  - <span data-ttu-id="68c9d-225">SAMBA 共用 (如想要支援 Linux)。</span><span class="sxs-lookup"><span data-stu-id="68c9d-225">SAMBA shares (if you want to support Linux.)</span></span>

## <a name="resource-does-not-require-interactive-input"></a><span data-ttu-id="68c9d-226">資源不需要互動式輸入</span><span class="sxs-lookup"><span data-stu-id="68c9d-226">Resource does not require interactive input</span></span>

<span data-ttu-id="68c9d-227">`Get/Set/Test-TargetResource` 函式應該要自動執行，絕不能等到使用者在執行的任何階段輸入時才動作 (例如，不應在這些函式內使用 `Get-Credential`)。</span><span class="sxs-lookup"><span data-stu-id="68c9d-227">`Get/Set/Test-TargetResource` functions should be executed automatically and must not wait for user's input at any stage of execution (e.g. you should not use `Get-Credential` inside these functions).</span></span> <span data-ttu-id="68c9d-228">如果您需要提供使用者輸入，就應該在編譯階段將它當作參數傳遞至設定。</span><span class="sxs-lookup"><span data-stu-id="68c9d-228">If you need to provide user's input, you should pass it to the configuration as parameter during the compilation phase.</span></span>

## <a name="resource-functionality-was-thoroughly-tested"></a><span data-ttu-id="68c9d-229">已徹底測試資源功能</span><span class="sxs-lookup"><span data-stu-id="68c9d-229">Resource functionality was thoroughly tested</span></span>

<span data-ttu-id="68c9d-230">這份檢查清單包含要測試和/或經常遺漏的重要項目。</span><span class="sxs-lookup"><span data-stu-id="68c9d-230">This checklist contains items which are important to be tested and/or are often missed.</span></span> <span data-ttu-id="68c9d-231">還有一些測試，主要是資源特定的功能測試，而這裡未提及。</span><span class="sxs-lookup"><span data-stu-id="68c9d-231">There will be bunch of tests, mainly functional ones which will be specific to the resource you are testing and are not mentioned here.</span></span> <span data-ttu-id="68c9d-232">別忘了反向測試案例。</span><span class="sxs-lookup"><span data-stu-id="68c9d-232">Don't forget about negative test cases.</span></span>

## <a name="best-practice-resource-module-contains-tests-folder-with-resourcedesignertestsps1-script"></a><span data-ttu-id="68c9d-233">最佳做法：資源模組包含具有 ResourceDesignerTests.ps1 指令碼的測試資料夾</span><span class="sxs-lookup"><span data-stu-id="68c9d-233">Best practice: Resource module contains Tests folder with ResourceDesignerTests.ps1 script</span></span>

<span data-ttu-id="68c9d-234">良好的做法是在資源模組中建立 "Tests" 資料夾，建立 `ResourceDesignerTests.ps1` 檔案，然後使用 `Test-xDscResource` 和 `Test-xDscSchema` 為所有指定模組中的資源新增測試。</span><span class="sxs-lookup"><span data-stu-id="68c9d-234">It's a good practice to create folder "Tests" inside resource module, create `ResourceDesignerTests.ps1` file and add tests using `Test-xDscResource` and `Test-xDscSchema` for all resources in given module.</span></span> <span data-ttu-id="68c9d-235">如此，就可以快速驗證指定模組中所有資源的結構描述，並在發行前執行例行性檢查。</span><span class="sxs-lookup"><span data-stu-id="68c9d-235">This way you can quickly validate schemas of all resources from the given modules and do a sanity check before publishing.</span></span> <span data-ttu-id="68c9d-236">針對 xRemoteFile，`ResourceTests.ps1` 可能看起來很簡單：</span><span class="sxs-lookup"><span data-stu-id="68c9d-236">For xRemoteFile, `ResourceTests.ps1` could look as simple as:</span></span>

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="best-practice-resource-supports--whatif"></a><span data-ttu-id="68c9d-237">最佳做法︰資源支援 -WhatIf</span><span class="sxs-lookup"><span data-stu-id="68c9d-237">Best practice: Resource supports -WhatIf</span></span>

<span data-ttu-id="68c9d-238">如果資源執行的是「危險」作業，實作 `-WhatIf` 功能是個不錯的做法。</span><span class="sxs-lookup"><span data-stu-id="68c9d-238">If your resource is performing "dangerous" operations, it's a good practice to implement `-WhatIf` functionality.</span></span> <span data-ttu-id="68c9d-239">完成後，請確定 `-WhatIf` 輸出會正確描述不使用 `-WhatIf` 參數執行命令時，作業會發生的狀況。</span><span class="sxs-lookup"><span data-stu-id="68c9d-239">After it's done, make sure that `-WhatIf` output correctly describes operations which would happen if command was executed without `-WhatIf` switch.</span></span> <span data-ttu-id="68c9d-240">另請確認，當使用 `–WhatIf` 參數時，作業不會執行 (不會變更節點狀態)。</span><span class="sxs-lookup"><span data-stu-id="68c9d-240">Also, verify that operations does not execute (no changes to the node's state are made) when `–WhatIf` switch is present.</span></span> <span data-ttu-id="68c9d-241">例如，假設現在要測試檔案資源。</span><span class="sxs-lookup"><span data-stu-id="68c9d-241">For example, let's assume we are testing File resource.</span></span> <span data-ttu-id="68c9d-242">以下簡單設定會建立含有內容 "Tests" 的檔案 `test.txt`：</span><span class="sxs-lookup"><span data-stu-id="68c9d-242">Below is simple configuration which creates file `test.txt` with contents "test":</span></span>

```powershell
configuration config
{
    node localhost
    {
        File file
        {
            Contents="test"
            DestinationPath="C:\test\test.txt"
        }
    }
}
config
```

<span data-ttu-id="68c9d-243">如果在編譯後以 `-WhatIf` 參數執行設定，輸出就會告訴我們執行設定時所發生的確切狀況。</span><span class="sxs-lookup"><span data-stu-id="68c9d-243">If we compile and then execute the configuration with the `-WhatIf` switch, the output is telling us exactly what would happen when we run the configuration.</span></span> <span data-ttu-id="68c9d-244">但是，設定本身並未執行 (未建立 `test.txt` 檔案)。</span><span class="sxs-lookup"><span data-stu-id="68c9d-244">The configuration itself however was not executed (`test.txt` file was not created).</span></span>

```powershell
Start-DscConfiguration -Path .\config -ComputerName localhost -Wait -Verbose -WhatIf
```

```Output
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer CHARLESX1 with user sid
S-1-5-21-397955417-626881126-188441444-5179871.
What if: [X]: LCM:  [ Start  Set      ]
What if: [X]: LCM:  [ Start  Resource ]  [[File]file]
What if: [X]: LCM:  [ Start  Test     ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]: LCM:  [ End    Test     ]  [[File]file]  in 0.0270 seconds.
What if: [X]: LCM:  [ Start  Set      ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]:                            [C:\test\test.txt] Creating and writing contents and setting attributes.
What if: [X]: LCM:  [ End    Set      ]  [[File]file]  in 0.0180 seconds.
What if: [X]: LCM:  [ End    Resource ]  [[File]file]
What if: [X]: LCM:  [ End    Set      ]
VERBOSE: [X]: LCM:  [ End    Set      ]    in  0.1050 seconds.
VERBOSE: Operation 'Invoke CimMethod' complete.
```

<span data-ttu-id="68c9d-245">這不是完整詳盡的清單，但涵蓋了許多在設計、開發和測試 DSC 資源時所遇到的重要問題。</span><span class="sxs-lookup"><span data-stu-id="68c9d-245">This list is not exhaustive, but it covers many important issues which can be encountered while designing, developing and testing DSC resources.</span></span>
