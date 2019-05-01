---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: DSC 檔案資源
ms.openlocfilehash: b5bc2c305b8cfccbd044274811df631264a24279
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077325"
---
# <a name="dsc-file-resource"></a><span data-ttu-id="f3544-103">DSC 檔案資源</span><span class="sxs-lookup"><span data-stu-id="f3544-103">DSC File Resource</span></span>

> <span data-ttu-id="f3544-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f3544-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="f3544-105">Windows PowerShell 預期狀態設定 (DSC) 的檔案資源會提供一個機制，在目標節點管理檔案和資料夾。</span><span class="sxs-lookup"><span data-stu-id="f3544-105">The File resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and folders on the target node.</span></span> <span data-ttu-id="f3544-106">**DestinationPath** 和 **SourcePath** 都必須可供目標節點存取。</span><span class="sxs-lookup"><span data-stu-id="f3544-106">The **DestinationPath** and **SourcePath** must both be accessible by the target Node.</span></span>

## <a name="syntax"></a><span data-ttu-id="f3544-107">語法</span><span class="sxs-lookup"><span data-stu-id="f3544-107">Syntax</span></span>

```
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ DependsOn = [string[]] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
}
```

## <a name="properties"></a><span data-ttu-id="f3544-108">Properties</span><span class="sxs-lookup"><span data-stu-id="f3544-108">Properties</span></span>

|<span data-ttu-id="f3544-109">屬性</span><span class="sxs-lookup"><span data-stu-id="f3544-109">Property</span></span>       |<span data-ttu-id="f3544-110">描述</span><span class="sxs-lookup"><span data-stu-id="f3544-110">Description</span></span>                                                                   |<span data-ttu-id="f3544-111">必要</span><span class="sxs-lookup"><span data-stu-id="f3544-111">Required</span></span>|<span data-ttu-id="f3544-112">Default</span><span class="sxs-lookup"><span data-stu-id="f3544-112">Default</span></span>|
|---------------|------------------------------------------------------------------------------|--------|-------|
|<span data-ttu-id="f3544-113">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="f3544-113">DestinationPath</span></span>|<span data-ttu-id="f3544-114">您想要確保目標節點上的位置是 `Present` 或 `Absent`。</span><span class="sxs-lookup"><span data-stu-id="f3544-114">The location, on the target node, you want to ensure is `Present` or `Absent`.</span></span>|<span data-ttu-id="f3544-115">是</span><span class="sxs-lookup"><span data-stu-id="f3544-115">Yes</span></span>|<span data-ttu-id="f3544-116">否</span><span class="sxs-lookup"><span data-stu-id="f3544-116">No</span></span>|
|<span data-ttu-id="f3544-117">屬性</span><span class="sxs-lookup"><span data-stu-id="f3544-117">Attributes</span></span>     |<span data-ttu-id="f3544-118">目標檔案或目錄屬性的預期狀態。</span><span class="sxs-lookup"><span data-stu-id="f3544-118">The desired state of the attributes for the targeted file or directory.</span></span> <span data-ttu-id="f3544-119">有效值為 **Archive**、**Hidden**、**ReadOnly** 及 **System**。</span><span class="sxs-lookup"><span data-stu-id="f3544-119">Valid values are **Archive**, **Hidden**, **ReadOnly**, and **System**.</span></span>|<span data-ttu-id="f3544-120">否</span><span class="sxs-lookup"><span data-stu-id="f3544-120">No</span></span>|<span data-ttu-id="f3544-121">無</span><span class="sxs-lookup"><span data-stu-id="f3544-121">None</span></span>|
|<span data-ttu-id="f3544-122">總和檢查碼</span><span class="sxs-lookup"><span data-stu-id="f3544-122">Checksum</span></span>      |<span data-ttu-id="f3544-123">判斷兩個檔案是否相同時所使用的總和檢查碼類型。</span><span class="sxs-lookup"><span data-stu-id="f3544-123">The checksum type to use when determining whether two files are the same.</span></span> <span data-ttu-id="f3544-124">有效值包括：SHA-1、SHA-256、SHA-512、createdDate、modifiedDate。</span><span class="sxs-lookup"><span data-stu-id="f3544-124">Valid values include: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.</span></span>|<span data-ttu-id="f3544-125">否</span><span class="sxs-lookup"><span data-stu-id="f3544-125">No</span></span>|<span data-ttu-id="f3544-126">只會比較檔案或目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="f3544-126">Only the file or directory name is compared.</span></span>|
|<span data-ttu-id="f3544-127">內容</span><span class="sxs-lookup"><span data-stu-id="f3544-127">Contents</span></span>       |<span data-ttu-id="f3544-128">只有在搭配 `File` 類型使用時才有效。</span><span class="sxs-lookup"><span data-stu-id="f3544-128">Only valid when used with `File` type.</span></span> <span data-ttu-id="f3544-129">表示在目標檔案中要確認的內容為 `Present` 或 `Absent`。</span><span class="sxs-lookup"><span data-stu-id="f3544-129">Indicates the contents to Ensure are `Present` or `Absent` from the targeted file.</span></span> |<span data-ttu-id="f3544-130">否</span><span class="sxs-lookup"><span data-stu-id="f3544-130">No</span></span>|<span data-ttu-id="f3544-131">無</span><span class="sxs-lookup"><span data-stu-id="f3544-131">None</span></span>|
|<span data-ttu-id="f3544-132">認證</span><span class="sxs-lookup"><span data-stu-id="f3544-132">Credential</span></span>     |<span data-ttu-id="f3544-133">存取資源所需的認證，例如來源檔案。</span><span class="sxs-lookup"><span data-stu-id="f3544-133">The credentials that are required to access resources, such as source files.</span></span>|<span data-ttu-id="f3544-134">否</span><span class="sxs-lookup"><span data-stu-id="f3544-134">No</span></span>|<span data-ttu-id="f3544-135">目標節點的電腦帳戶。</span><span class="sxs-lookup"><span data-stu-id="f3544-135">The target node's Computer Account.</span></span> <span data-ttu-id="f3544-136">(*請參閱備註*)</span><span class="sxs-lookup"><span data-stu-id="f3544-136">(*see note*)</span></span>|
|<span data-ttu-id="f3544-137">Ensure</span><span class="sxs-lookup"><span data-stu-id="f3544-137">Ensure</span></span>         |<span data-ttu-id="f3544-138">目標檔案或目錄的預期狀態。</span><span class="sxs-lookup"><span data-stu-id="f3544-138">The desired state of the target file or directory.</span></span> |<span data-ttu-id="f3544-139">否</span><span class="sxs-lookup"><span data-stu-id="f3544-139">No</span></span>|<span data-ttu-id="f3544-140">**目前**</span><span class="sxs-lookup"><span data-stu-id="f3544-140">**Present**</span></span>|
|<span data-ttu-id="f3544-141">Force</span><span class="sxs-lookup"><span data-stu-id="f3544-141">Force</span></span>          |<span data-ttu-id="f3544-142">覆寫會導致錯誤的存取作業 (例如覆寫檔案，或刪除不是空的目錄)。</span><span class="sxs-lookup"><span data-stu-id="f3544-142">Overrides access operations that would result in an error (such as overwriting a file or deleting a directory that is not empty).</span></span>|<span data-ttu-id="f3544-143">否</span><span class="sxs-lookup"><span data-stu-id="f3544-143">No</span></span>|`$false`|
|<span data-ttu-id="f3544-144">Recurse</span><span class="sxs-lookup"><span data-stu-id="f3544-144">Recurse</span></span>        |<span data-ttu-id="f3544-145">只有在搭配 `Directory` 類型使用時才有效。</span><span class="sxs-lookup"><span data-stu-id="f3544-145">Only valid when used with `Directory` type.</span></span> <span data-ttu-id="f3544-146">以遞迴方式在所有子目錄中執行狀態作業。</span><span class="sxs-lookup"><span data-stu-id="f3544-146">Performs the state operation recursively to all subdirectories.</span></span>|<span data-ttu-id="f3544-147">否</span><span class="sxs-lookup"><span data-stu-id="f3544-147">No</span></span>|`$false`|
|<span data-ttu-id="f3544-148">DependsOn</span><span class="sxs-lookup"><span data-stu-id="f3544-148">DependsOn</span></span>      |<span data-ttu-id="f3544-149">在指定的資源上設定相依性。</span><span class="sxs-lookup"><span data-stu-id="f3544-149">Sets a dependency on specified resource(s).</span></span> <span data-ttu-id="f3544-150">唯有成功執行任何相依資源之後，此資源才能執行。</span><span class="sxs-lookup"><span data-stu-id="f3544-150">This resource will only execute after successful execution of any dependent resources.</span></span> <span data-ttu-id="f3544-151">您可以使用 `"[ResourceType]ResourceName"` 語法來指定相依資源。</span><span class="sxs-lookup"><span data-stu-id="f3544-151">You can specify dependent resources using the syntax `"[ResourceType]ResourceName"`.</span></span> <span data-ttu-id="f3544-152">請參閱 [about_DependsOn](../../../configurations/resource-depends-on.md)</span><span class="sxs-lookup"><span data-stu-id="f3544-152">See [about_DependsOn](../../../configurations/resource-depends-on.md)</span></span>|<span data-ttu-id="f3544-153">否</span><span class="sxs-lookup"><span data-stu-id="f3544-153">No</span></span>|<span data-ttu-id="f3544-154">無</span><span class="sxs-lookup"><span data-stu-id="f3544-154">None</span></span>|
|<span data-ttu-id="f3544-155">SourcePath</span><span class="sxs-lookup"><span data-stu-id="f3544-155">SourcePath</span></span>     |<span data-ttu-id="f3544-156">要從中複製檔案或資料夾資源的路徑。</span><span class="sxs-lookup"><span data-stu-id="f3544-156">The path from which to copy the file or folder resource.</span></span>|<span data-ttu-id="f3544-157">否</span><span class="sxs-lookup"><span data-stu-id="f3544-157">No</span></span>|<span data-ttu-id="f3544-158">無</span><span class="sxs-lookup"><span data-stu-id="f3544-158">None</span></span>|
|<span data-ttu-id="f3544-159">類型</span><span class="sxs-lookup"><span data-stu-id="f3544-159">Type</span></span>           |<span data-ttu-id="f3544-160">要設定的資源類型。</span><span class="sxs-lookup"><span data-stu-id="f3544-160">The type of resource being configured.</span></span> <span data-ttu-id="f3544-161">有效值為 `Directory` 和 `File`。</span><span class="sxs-lookup"><span data-stu-id="f3544-161">Valid values are `Directory` and `File`.</span></span>|<span data-ttu-id="f3544-162">否</span><span class="sxs-lookup"><span data-stu-id="f3544-162">No</span></span>|`File`|
|<span data-ttu-id="f3544-163">MatchSource</span><span class="sxs-lookup"><span data-stu-id="f3544-163">MatchSource</span></span>    |<span data-ttu-id="f3544-164">判斷資源是否應該監視在初始複本之後新增至來源目錄的新檔案。</span><span class="sxs-lookup"><span data-stu-id="f3544-164">Determines if the resource should monitor for new files added to the source directory after the initial copy.</span></span> <span data-ttu-id="f3544-165">若值為 `$true`，即表示在初始複本之後，任何新的原始程式檔都應該複製到目的地。</span><span class="sxs-lookup"><span data-stu-id="f3544-165">A value of `$true` indicates that, after the initial copy, any new source files should be copied to the destination.</span></span> <span data-ttu-id="f3544-166">若設為 `$False`，資源就會快取來源目錄的內容，並忽略任何初始複本之後新增的檔案。</span><span class="sxs-lookup"><span data-stu-id="f3544-166">If set to `$False`, the resource caches the contents of the source directory and ignores any files added after the initial copy.</span></span>|<span data-ttu-id="f3544-167">否</span><span class="sxs-lookup"><span data-stu-id="f3544-167">No</span></span>|`$false`|

> [!WARNING]
> <span data-ttu-id="f3544-168">如果您未指定 `Credential` 或 `PSRunAsCredential` (PS V.5) 的值，資源將使用目標節點的電腦帳戶來存取 `SourcePath`。</span><span class="sxs-lookup"><span data-stu-id="f3544-168">If you do not specify a value for `Credential` or `PSRunAsCredential` (PS V.5), the resource will use the computer account of the target node to access the `SourcePath`.</span></span>  <span data-ttu-id="f3544-169">當 `SourcePath` 為 UNC 共用時，這可能導致「拒絕存取」錯誤。</span><span class="sxs-lookup"><span data-stu-id="f3544-169">When the `SourcePath` is a UNC share, this could result in an "Access Denied" error.</span></span> <span data-ttu-id="f3544-170">請確定會據以設定您的權限，或是使用 `Credential` 或 `PSRunAsCredential` 屬性來指定應使用的帳戶。</span><span class="sxs-lookup"><span data-stu-id="f3544-170">Please ensure your permissions are set accordingly, or use the `Credential` or `PSRunAsCredential` properties to specify the account that should be used.</span></span>

## <a name="present-vs-absent"></a><span data-ttu-id="f3544-171">Present 與Absent</span><span class="sxs-lookup"><span data-stu-id="f3544-171">Present vs. Absent</span></span>

<span data-ttu-id="f3544-172">每個 DSC 資源都會根據您針對 `Ensure` 屬性指定的值來執行不同的作業。</span><span class="sxs-lookup"><span data-stu-id="f3544-172">Each DSC resource performs different operations based on the value you specify for the `Ensure` property.</span></span> <span data-ttu-id="f3544-173">您針對上述屬性指定的值會決定要執行的狀態作業。</span><span class="sxs-lookup"><span data-stu-id="f3544-173">The values you specify for the above properties determines the state operation performed.</span></span>

### <a name="existence"></a><span data-ttu-id="f3544-174">存在</span><span class="sxs-lookup"><span data-stu-id="f3544-174">Existence</span></span>

<span data-ttu-id="f3544-175">當您只指定 `DestinationPath` 時，資源可確保路徑存在 (`Present`) 或不存在 (`Absent`)。</span><span class="sxs-lookup"><span data-stu-id="f3544-175">When you only specify a `DestinationPath`, the resource ensures that the path exists (`Present`) or does not exist (`Absent`).</span></span>

### <a name="copy-operations"></a><span data-ttu-id="f3544-176">複製作業</span><span class="sxs-lookup"><span data-stu-id="f3544-176">Copy Operations</span></span>

<span data-ttu-id="f3544-177">當您指定 `SourcePath` 和 `DestinationPath` 且 `Type` 的值為 **Directory** 時，資源會將來源目錄複製到目的地路徑。</span><span class="sxs-lookup"><span data-stu-id="f3544-177">When you specify a `SourcePath` and a `DestinationPath` with a `Type` value of **Directory**, the resource copies source directory to the destination path.</span></span> <span data-ttu-id="f3544-178">屬性 `Recurse`、`Force` 及 `MatchSource` 會變更所執行的複製作業類型，而 `Credential` 會判斷要使用哪一個帳戶來存取來源目錄。</span><span class="sxs-lookup"><span data-stu-id="f3544-178">The properties `Recurse`, `Force`, and `MatchSource` change the type of copy operation performed, while `Credential` determines which account to use to access the source directory.</span></span>

### <a name="limitations"></a><span data-ttu-id="f3544-179">限制</span><span class="sxs-lookup"><span data-stu-id="f3544-179">Limitations</span></span>

<span data-ttu-id="f3544-180">如果您與 `DestinationPath` 一起為 `Attributes` 屬性指定了 `ReadOnly` 的值，則 `Ensure = "Present"` 會建立指定的路徑，而 `Contents` 會設定檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="f3544-180">If you specified a value of `ReadOnly` for the `Attributes` property alongside a `DestinationPath`, `Ensure = "Present"` would create the path specified, while `Contents` would set the contents of the file.</span></span>  <span data-ttu-id="f3544-181">`Absent` 狀態作業會完全忽略 `Attributes` 屬性，並移除指定路徑上的任何檔案。</span><span class="sxs-lookup"><span data-stu-id="f3544-181">An `Absent` state operation would ignore the `Attributes` property entirely, and remove any file at the specified path.</span></span>

## <a name="example"></a><span data-ttu-id="f3544-182">範例</span><span class="sxs-lookup"><span data-stu-id="f3544-182">Example</span></span>

<span data-ttu-id="f3544-183">下列範例會使用檔案資源，將某個目錄及其子目錄從提取伺服器複製到目標節點。</span><span class="sxs-lookup"><span data-stu-id="f3544-183">The following example copies a directory and its subdirectories from a pull server to a target node using the File Resource.</span></span> <span data-ttu-id="f3544-184">如果此作業成功，記錄資源就會將確認訊息寫入至事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="f3544-184">If the operation succeeds, the Log resource writes a confirmation message to the event log.</span></span>

<span data-ttu-id="f3544-185">來源目錄是從提取伺服器共用的 UNC 路徑 (`\\PullServer\DemoSource`)。</span><span class="sxs-lookup"><span data-stu-id="f3544-185">The source directory is a UNC path (`\\PullServer\DemoSource`) shared from the Pull Server.</span></span> <span data-ttu-id="f3544-186">`Recurse` 屬性確保會一併複製所有子目錄。</span><span class="sxs-lookup"><span data-stu-id="f3544-186">The `Recurse` property ensures that all subdirectories are copied as well.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f3544-187">根據預設，目標節點上的 LCM 會在本機系統帳戶的內容中執行。</span><span class="sxs-lookup"><span data-stu-id="f3544-187">The LCM on the target Node executes in the context of the local system account by default.</span></span> <span data-ttu-id="f3544-188">若要授與存取 **SourcePath**，請為目標節點的電腦帳戶提供適當的權限。</span><span class="sxs-lookup"><span data-stu-id="f3544-188">To grant access to the **SourcePath**, give the target Node's computer account appropriate permissions.</span></span> <span data-ttu-id="f3544-189">**Credential** 和 **PSDSCRunAsCredential** (v5) 都會變更 LCM 用來存取 **SourcePath** 的內容。</span><span class="sxs-lookup"><span data-stu-id="f3544-189">The **Credential** and **PSDSCRunAsCredential** (v5) both change the context the LCM uses to access the **SourcePath**.</span></span> <span data-ttu-id="f3544-190">您仍然需要授與存取將用來存取 **SourcePath** 的帳戶。</span><span class="sxs-lookup"><span data-stu-id="f3544-190">You still need to grant access to the account that will be used to access the **SourcePath**.</span></span>

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present" # Ensure the directory is Present on the target node.
            Type = "Directory" # The default is File.
            Recurse = $true # Recursively copy all subdirectories.
            SourcePath = "\\PullServer\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # Depends on successful execution of the File resource.
        }
    }
}
```

<span data-ttu-id="f3544-191">如需在 DSC 中使用**認證**的詳細資訊，請參閱[以使用者身分執行](../../../configurations/runAsUser.md)或[設定資料認證](../../../configurations/configDataCredentials.md)。</span><span class="sxs-lookup"><span data-stu-id="f3544-191">For more on using **Credentials** in DSC see [Run As User](../../../configurations/runAsUser.md) or [Config Data Credentials](../../../configurations/configDataCredentials.md).</span></span>
