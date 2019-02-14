---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: DSC 檔案資源
ms.openlocfilehash: b5bc2c305b8cfccbd044274811df631264a24279
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55679296"
---
# <a name="dsc-file-resource"></a><span data-ttu-id="99849-103">DSC 檔案資源</span><span class="sxs-lookup"><span data-stu-id="99849-103">DSC File Resource</span></span>

> <span data-ttu-id="99849-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="99849-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="99849-105">Windows PowerShell 預期狀態設定 (DSC) 的檔案資源會提供一個機制，在目標節點管理檔案和資料夾。</span><span class="sxs-lookup"><span data-stu-id="99849-105">The File resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and folders on the target node.</span></span> <span data-ttu-id="99849-106">**DestinationPath**並**SourcePath**兩者都必須是供目標節點。</span><span class="sxs-lookup"><span data-stu-id="99849-106">The **DestinationPath** and **SourcePath** must both be accessible by the target Node.</span></span>

## <a name="syntax"></a><span data-ttu-id="99849-107">語法</span><span class="sxs-lookup"><span data-stu-id="99849-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="99849-108">Properties</span><span class="sxs-lookup"><span data-stu-id="99849-108">Properties</span></span>

|<span data-ttu-id="99849-109">屬性</span><span class="sxs-lookup"><span data-stu-id="99849-109">Property</span></span>       |<span data-ttu-id="99849-110">描述</span><span class="sxs-lookup"><span data-stu-id="99849-110">Description</span></span>                                                                   |<span data-ttu-id="99849-111">必要</span><span class="sxs-lookup"><span data-stu-id="99849-111">Required</span></span>|<span data-ttu-id="99849-112">Default</span><span class="sxs-lookup"><span data-stu-id="99849-112">Default</span></span>|
|---------------|------------------------------------------------------------------------------|--------|-------|
|<span data-ttu-id="99849-113">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="99849-113">DestinationPath</span></span>|<span data-ttu-id="99849-114">您想要確保目標節點上的位置是`Present`或`Absent`。</span><span class="sxs-lookup"><span data-stu-id="99849-114">The location, on the target node, you want to ensure is `Present` or `Absent`.</span></span>|<span data-ttu-id="99849-115">是</span><span class="sxs-lookup"><span data-stu-id="99849-115">Yes</span></span>|<span data-ttu-id="99849-116">否</span><span class="sxs-lookup"><span data-stu-id="99849-116">No</span></span>|
|<span data-ttu-id="99849-117">屬性</span><span class="sxs-lookup"><span data-stu-id="99849-117">Attributes</span></span>     |<span data-ttu-id="99849-118">目標的檔案或目錄的屬性所需的狀態。</span><span class="sxs-lookup"><span data-stu-id="99849-118">The desired state of the attributes for the targeted file or directory.</span></span> <span data-ttu-id="99849-119">有效值**封存**， **Hidden**， **ReadOnly**，以及**系統**。</span><span class="sxs-lookup"><span data-stu-id="99849-119">Valid values are **Archive**, **Hidden**, **ReadOnly**, and **System**.</span></span>|<span data-ttu-id="99849-120">否</span><span class="sxs-lookup"><span data-stu-id="99849-120">No</span></span>|<span data-ttu-id="99849-121">無</span><span class="sxs-lookup"><span data-stu-id="99849-121">None</span></span>|
|<span data-ttu-id="99849-122">總和檢查碼</span><span class="sxs-lookup"><span data-stu-id="99849-122">Checksum</span></span>      |<span data-ttu-id="99849-123">要判斷是否有兩個檔案都是相同時所使用的總和檢查碼類型。</span><span class="sxs-lookup"><span data-stu-id="99849-123">The checksum type to use when determining whether two files are the same.</span></span> <span data-ttu-id="99849-124">有效值包括：Sha-1、 SHA-256、 SHA-512、-512、createddate、modifieddate、 modifiedDate。</span><span class="sxs-lookup"><span data-stu-id="99849-124">Valid values include: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.</span></span>|<span data-ttu-id="99849-125">否</span><span class="sxs-lookup"><span data-stu-id="99849-125">No</span></span>|<span data-ttu-id="99849-126">只有檔案或目錄名稱進行比較。</span><span class="sxs-lookup"><span data-stu-id="99849-126">Only the file or directory name is compared.</span></span>|
|<span data-ttu-id="99849-127">內容</span><span class="sxs-lookup"><span data-stu-id="99849-127">Contents</span></span>       |<span data-ttu-id="99849-128">搭配使用時，唯一有效`File`型別。</span><span class="sxs-lookup"><span data-stu-id="99849-128">Only valid when used with `File` type.</span></span> <span data-ttu-id="99849-129">表示內容，請確定`Present`或`Absent`從目標檔案。</span><span class="sxs-lookup"><span data-stu-id="99849-129">Indicates the contents to Ensure are `Present` or `Absent` from the targeted file.</span></span> |<span data-ttu-id="99849-130">否</span><span class="sxs-lookup"><span data-stu-id="99849-130">No</span></span>|<span data-ttu-id="99849-131">無</span><span class="sxs-lookup"><span data-stu-id="99849-131">None</span></span>|
|<span data-ttu-id="99849-132">認證</span><span class="sxs-lookup"><span data-stu-id="99849-132">Credential</span></span>     |<span data-ttu-id="99849-133">輸入的認證才能存取資源，例如來源檔案。</span><span class="sxs-lookup"><span data-stu-id="99849-133">The credentials that are required to access resources, such as source files.</span></span>|<span data-ttu-id="99849-134">否</span><span class="sxs-lookup"><span data-stu-id="99849-134">No</span></span>|<span data-ttu-id="99849-135">目標節點的電腦帳戶。</span><span class="sxs-lookup"><span data-stu-id="99849-135">The target node's Computer Account.</span></span> <span data-ttu-id="99849-136">(*請參閱備註*)</span><span class="sxs-lookup"><span data-stu-id="99849-136">(*see note*)</span></span>|
|<span data-ttu-id="99849-137">Ensure</span><span class="sxs-lookup"><span data-stu-id="99849-137">Ensure</span></span>         |<span data-ttu-id="99849-138">目標檔案或目錄所需的狀態。</span><span class="sxs-lookup"><span data-stu-id="99849-138">The desired state of the target file or directory.</span></span> |<span data-ttu-id="99849-139">否</span><span class="sxs-lookup"><span data-stu-id="99849-139">No</span></span>|<span data-ttu-id="99849-140">**目前**</span><span class="sxs-lookup"><span data-stu-id="99849-140">**Present**</span></span>|
|<span data-ttu-id="99849-141">Force</span><span class="sxs-lookup"><span data-stu-id="99849-141">Force</span></span>          |<span data-ttu-id="99849-142">覆寫會導致錯誤 （例如覆寫檔案，或刪除不是空的目錄） 的存取作業。</span><span class="sxs-lookup"><span data-stu-id="99849-142">Overrides access operations that would result in an error (such as overwriting a file or deleting a directory that is not empty).</span></span>|<span data-ttu-id="99849-143">否</span><span class="sxs-lookup"><span data-stu-id="99849-143">No</span></span>|`$false`|
|<span data-ttu-id="99849-144">Recurse</span><span class="sxs-lookup"><span data-stu-id="99849-144">Recurse</span></span>        |<span data-ttu-id="99849-145">搭配使用時，唯一有效`Directory`型別。</span><span class="sxs-lookup"><span data-stu-id="99849-145">Only valid when used with `Directory` type.</span></span> <span data-ttu-id="99849-146">執行狀態的作業以遞迴方式，所有子目錄中。</span><span class="sxs-lookup"><span data-stu-id="99849-146">Performs the state operation recursively to all subdirectories.</span></span>|<span data-ttu-id="99849-147">否</span><span class="sxs-lookup"><span data-stu-id="99849-147">No</span></span>|`$false`|
|<span data-ttu-id="99849-148">DependsOn</span><span class="sxs-lookup"><span data-stu-id="99849-148">DependsOn</span></span>      |<span data-ttu-id="99849-149">設定指定的資源相依性。</span><span class="sxs-lookup"><span data-stu-id="99849-149">Sets a dependency on specified resource(s).</span></span> <span data-ttu-id="99849-150">在成功執行的任何相依的資源後，才能執行這項資源。</span><span class="sxs-lookup"><span data-stu-id="99849-150">This resource will only execute after successful execution of any dependent resources.</span></span> <span data-ttu-id="99849-151">您可以指定使用語法的相依資源`"[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="99849-151">You can specify dependent resources using the syntax `"[ResourceType]ResourceName"`.</span></span> <span data-ttu-id="99849-152">請參閱 [about_DependsOn](../../../configurations/resource-depends-on.md)</span><span class="sxs-lookup"><span data-stu-id="99849-152">See [about_DependsOn](../../../configurations/resource-depends-on.md)</span></span>|<span data-ttu-id="99849-153">否</span><span class="sxs-lookup"><span data-stu-id="99849-153">No</span></span>|<span data-ttu-id="99849-154">無</span><span class="sxs-lookup"><span data-stu-id="99849-154">None</span></span>|
|<span data-ttu-id="99849-155">SourcePath</span><span class="sxs-lookup"><span data-stu-id="99849-155">SourcePath</span></span>     |<span data-ttu-id="99849-156">要從中複製檔案或資料夾資源的路徑。</span><span class="sxs-lookup"><span data-stu-id="99849-156">The path from which to copy the file or folder resource.</span></span>|<span data-ttu-id="99849-157">否</span><span class="sxs-lookup"><span data-stu-id="99849-157">No</span></span>|<span data-ttu-id="99849-158">無</span><span class="sxs-lookup"><span data-stu-id="99849-158">None</span></span>|
|<span data-ttu-id="99849-159">類型</span><span class="sxs-lookup"><span data-stu-id="99849-159">Type</span></span>           |<span data-ttu-id="99849-160">正在設定的資源類型。</span><span class="sxs-lookup"><span data-stu-id="99849-160">The type of resource being configured.</span></span> <span data-ttu-id="99849-161">有效值`Directory`和`File`。</span><span class="sxs-lookup"><span data-stu-id="99849-161">Valid values are `Directory` and `File`.</span></span>|<span data-ttu-id="99849-162">否</span><span class="sxs-lookup"><span data-stu-id="99849-162">No</span></span>|`File`|
|<span data-ttu-id="99849-163">MatchSource</span><span class="sxs-lookup"><span data-stu-id="99849-163">MatchSource</span></span>    |<span data-ttu-id="99849-164">決定是否資源應該監視有新檔案新增至來源目錄的初始複本之後。</span><span class="sxs-lookup"><span data-stu-id="99849-164">Determines if the resource should monitor for new files added to the source directory after the initial copy.</span></span> <span data-ttu-id="99849-165">值為`$true`表示，初始複製之後，任何新的原始程式檔應該要複製到目的地。</span><span class="sxs-lookup"><span data-stu-id="99849-165">A value of `$true` indicates that, after the initial copy, any new source files should be copied to the destination.</span></span> <span data-ttu-id="99849-166">如果設定為`$False`，資源會快取來源目錄的內容，並忽略任何初始複本之後新增的檔案。</span><span class="sxs-lookup"><span data-stu-id="99849-166">If set to `$False`, the resource caches the contents of the source directory and ignores any files added after the initial copy.</span></span>|<span data-ttu-id="99849-167">否</span><span class="sxs-lookup"><span data-stu-id="99849-167">No</span></span>|`$false`|

> [!WARNING]
> <span data-ttu-id="99849-168">如果您未指定的值`Credential`或是`PSRunAsCredential`(PS V.5)，資源會使用目標節點的電腦帳戶來存取`SourcePath`。</span><span class="sxs-lookup"><span data-stu-id="99849-168">If you do not specify a value for `Credential` or `PSRunAsCredential` (PS V.5), the resource will use the computer account of the target node to access the `SourcePath`.</span></span>  <span data-ttu-id="99849-169">當`SourcePath`是 UNC 共用，這可能會導致 「 拒絕存取 」 錯誤。</span><span class="sxs-lookup"><span data-stu-id="99849-169">When the `SourcePath` is a UNC share, this could result in an "Access Denied" error.</span></span> <span data-ttu-id="99849-170">請確定您的權限會相應地設定，或使用`Credential`或`PSRunAsCredential`屬性，以指定應該使用的帳戶。</span><span class="sxs-lookup"><span data-stu-id="99849-170">Please ensure your permissions are set accordingly, or use the `Credential` or `PSRunAsCredential` properties to specify the account that should be used.</span></span>

## <a name="present-vs-absent"></a><span data-ttu-id="99849-171">提供 vs。不存在</span><span class="sxs-lookup"><span data-stu-id="99849-171">Present vs. Absent</span></span>

<span data-ttu-id="99849-172">每個 DSC 資源執行指定的值為基礎的不同作業`Ensure`屬性。</span><span class="sxs-lookup"><span data-stu-id="99849-172">Each DSC resource performs different operations based on the value you specify for the `Ensure` property.</span></span> <span data-ttu-id="99849-173">執行您指定的上述屬性決定狀態作業的值。</span><span class="sxs-lookup"><span data-stu-id="99849-173">The values you specify for the above properties determines the state operation performed.</span></span>

### <a name="existence"></a><span data-ttu-id="99849-174">存在</span><span class="sxs-lookup"><span data-stu-id="99849-174">Existence</span></span>

<span data-ttu-id="99849-175">當您只指定`DestinationPath`，資源可確保此路徑是否存在 (`Present`) 或不存在 (`Absent`)。</span><span class="sxs-lookup"><span data-stu-id="99849-175">When you only specify a `DestinationPath`, the resource ensures that the path exists (`Present`) or does not exist (`Absent`).</span></span>

### <a name="copy-operations"></a><span data-ttu-id="99849-176">複製作業</span><span class="sxs-lookup"><span data-stu-id="99849-176">Copy Operations</span></span>

<span data-ttu-id="99849-177">當您指定`SourcePath`和`DestinationPath`具有`Type`的值**Directory**，為目的路徑的資源複製來源目錄。</span><span class="sxs-lookup"><span data-stu-id="99849-177">When you specify a `SourcePath` and a `DestinationPath` with a `Type` value of **Directory**, the resource copies source directory to the destination path.</span></span> <span data-ttu-id="99849-178">屬性`Recurse`， `Force`，並`MatchSource`變更複製作業的型別執行，而`Credential`判斷哪一個帳戶用來存取來源目錄。</span><span class="sxs-lookup"><span data-stu-id="99849-178">The properties `Recurse`, `Force`, and `MatchSource` change the type of copy operation performed, while `Credential` determines which account to use to access the source directory.</span></span>

### <a name="limitations"></a><span data-ttu-id="99849-179">限制</span><span class="sxs-lookup"><span data-stu-id="99849-179">Limitations</span></span>

<span data-ttu-id="99849-180">如果您指定的值`ReadOnly`for`Attributes`屬性一起`DestinationPath`，`Ensure = "Present"`會建立指定的路徑時`Contents`會設定檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="99849-180">If you specified a value of `ReadOnly` for the `Attributes` property alongside a `DestinationPath`, `Ensure = "Present"` would create the path specified, while `Contents` would set the contents of the file.</span></span>  <span data-ttu-id="99849-181">`Absent`狀態的作業會忽略`Attributes`屬性，請完全移除位於指定路徑的任何檔案。</span><span class="sxs-lookup"><span data-stu-id="99849-181">An `Absent` state operation would ignore the `Attributes` property entirely, and remove any file at the specified path.</span></span>

## <a name="example"></a><span data-ttu-id="99849-182">範例</span><span class="sxs-lookup"><span data-stu-id="99849-182">Example</span></span>

<span data-ttu-id="99849-183">下列範例會複製目錄和子目錄從提取伺服器到目標節點使用檔案資源。</span><span class="sxs-lookup"><span data-stu-id="99849-183">The following example copies a directory and its subdirectories from a pull server to a target node using the File Resource.</span></span> <span data-ttu-id="99849-184">如果作業成功，則記錄檔資源會將確認訊息寫入事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="99849-184">If the operation succeeds, the Log resource writes a confirmation message to the event log.</span></span>

<span data-ttu-id="99849-185">來源目錄是 UNC 路徑 (`\\PullServer\DemoSource`) 從提取伺服器共用。</span><span class="sxs-lookup"><span data-stu-id="99849-185">The source directory is a UNC path (`\\PullServer\DemoSource`) shared from the Pull Server.</span></span> <span data-ttu-id="99849-186">`Recurse`屬性，可確保一併複製所有的子目錄。</span><span class="sxs-lookup"><span data-stu-id="99849-186">The `Recurse` property ensures that all subdirectories are copied as well.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="99849-187">根據預設，本機系統帳戶內容中執行目標節點上的 LCM。</span><span class="sxs-lookup"><span data-stu-id="99849-187">The LCM on the target Node executes in the context of the local system account by default.</span></span> <span data-ttu-id="99849-188">若要授與存取權**SourcePath**，授與目標節點的電腦帳戶適當的權限。</span><span class="sxs-lookup"><span data-stu-id="99849-188">To grant access to the **SourcePath**, give the target Node's computer account appropriate permissions.</span></span> <span data-ttu-id="99849-189">**認證**並**PSDSCRunAsCredential** (v5) 兩者都變更用來存取的內容 LCM **SourcePath**。</span><span class="sxs-lookup"><span data-stu-id="99849-189">The **Credential** and **PSDSCRunAsCredential** (v5) both change the context the LCM uses to access the **SourcePath**.</span></span> <span data-ttu-id="99849-190">您仍然需要授與存取權的帳戶將用來存取**SourcePath**。</span><span class="sxs-lookup"><span data-stu-id="99849-190">You still need to grant access to the account that will be used to access the **SourcePath**.</span></span>

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

<span data-ttu-id="99849-191">如需在使用**認證**在 DSC，請參閱[使用者的身分執行](../../../configurations/runAsUser.md)或[組態資料認證](../../../configurations/configDataCredentials.md)。</span><span class="sxs-lookup"><span data-stu-id="99849-191">For more on using **Credentials** in DSC see [Run As User](../../../configurations/runAsUser.md) or [Config Data Credentials](../../../configurations/configDataCredentials.md).</span></span>
