---
ms.date: 07/16/2020
keywords: dsc,powershell,設定,安裝
title: DSC 檔案資源
ms.openlocfilehash: 28e9ea3a590a0972e505912efae4a934bc39ba1d
ms.sourcegitcommit: 9a8bb1b459b5939c95e1f6d9499fcb13d01a58c4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88799599"
---
# <a name="dsc-file-resource"></a><span data-ttu-id="f5add-103">DSC 檔案資源</span><span class="sxs-lookup"><span data-stu-id="f5add-103">DSC File Resource</span></span>

> <span data-ttu-id="f5add-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="f5add-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="f5add-105">Windows PowerShell Desired State Configuration (DSC) 的**檔案**資源會提供機制，以在目標節點管理檔案和資料夾。</span><span class="sxs-lookup"><span data-stu-id="f5add-105">The **File** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and folders on the target node.</span></span> <span data-ttu-id="f5add-106">**DestinationPath** 和 **SourcePath** 都必須可供目標節點存取。</span><span class="sxs-lookup"><span data-stu-id="f5add-106">**DestinationPath** and **SourcePath** must both be accessible by the target Node.</span></span>

## <a name="syntax"></a><span data-ttu-id="f5add-107">語法</span><span class="sxs-lookup"><span data-stu-id="f5add-107">Syntax</span></span>

```Syntax
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="f5add-108">屬性</span><span class="sxs-lookup"><span data-stu-id="f5add-108">Properties</span></span>

|<span data-ttu-id="f5add-109">屬性</span><span class="sxs-lookup"><span data-stu-id="f5add-109">Property</span></span> |<span data-ttu-id="f5add-110">描述</span><span class="sxs-lookup"><span data-stu-id="f5add-110">Description</span></span> |
|---|---|
|<span data-ttu-id="f5add-111">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="f5add-111">DestinationPath</span></span> |<span data-ttu-id="f5add-112">您想要確保目標節點上的位置是 **Present** 或 **Absent** 與 **Ensure**。</span><span class="sxs-lookup"><span data-stu-id="f5add-112">The location, on the target node, you want to ensure is **Present** or **Absent** with **Ensure**.</span></span> |
|<span data-ttu-id="f5add-113">屬性</span><span class="sxs-lookup"><span data-stu-id="f5add-113">Attributes</span></span> |<span data-ttu-id="f5add-114">目標檔案或目錄屬性的預期狀態。</span><span class="sxs-lookup"><span data-stu-id="f5add-114">The desired state of the attributes for the targeted file or directory.</span></span> <span data-ttu-id="f5add-115">有效值為 _Archive_、_Hidden_、_ReadOnly_ 及 _System_。</span><span class="sxs-lookup"><span data-stu-id="f5add-115">Valid values are _Archive_, _Hidden_, _ReadOnly_, and _System_.</span></span> |
|<span data-ttu-id="f5add-116">總和檢查碼</span><span class="sxs-lookup"><span data-stu-id="f5add-116">Checksum</span></span> |<span data-ttu-id="f5add-117">判斷兩個檔案是否相同時所使用的總和檢查碼類型。</span><span class="sxs-lookup"><span data-stu-id="f5add-117">The checksum type to use when determining whether two files are the same.</span></span> <span data-ttu-id="f5add-118">有效值包括：**SHA-1**、**SHA-256**、**SHA-512**、**createdDate**、**modifiedDate**。</span><span class="sxs-lookup"><span data-stu-id="f5add-118">Valid values include: **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**.</span></span> |
|<span data-ttu-id="f5add-119">內容</span><span class="sxs-lookup"><span data-stu-id="f5add-119">Contents</span></span> |<span data-ttu-id="f5add-120">只有在搭配**類型** **檔案**類型使用時才有效。</span><span class="sxs-lookup"><span data-stu-id="f5add-120">Only valid when used with **Type** **File**.</span></span> <span data-ttu-id="f5add-121">表示在目標檔案中要確認的內容為 **Present** 或 **Absent** 與 **Ensure**。</span><span class="sxs-lookup"><span data-stu-id="f5add-121">Indicates the contents to **Ensure** are **Present** or **Absent** from the targeted file.</span></span> |
|<span data-ttu-id="f5add-122">認證</span><span class="sxs-lookup"><span data-stu-id="f5add-122">Credential</span></span> |<span data-ttu-id="f5add-123">存取資源所需的認證，例如來源檔案。</span><span class="sxs-lookup"><span data-stu-id="f5add-123">The credentials that are required to access resources, such as source files.</span></span> |
|<span data-ttu-id="f5add-124">Force</span><span class="sxs-lookup"><span data-stu-id="f5add-124">Force</span></span> |<span data-ttu-id="f5add-125">覆寫會導致錯誤的存取作業 (例如覆寫檔案，或刪除不是空的目錄)。</span><span class="sxs-lookup"><span data-stu-id="f5add-125">Overrides access operations that would result in an error (such as overwriting a file or deleting a directory that is not empty).</span></span> <span data-ttu-id="f5add-126">預設值為 `$false`。</span><span class="sxs-lookup"><span data-stu-id="f5add-126">Default value is `$false`.</span></span> |
|<span data-ttu-id="f5add-127">Recurse</span><span class="sxs-lookup"><span data-stu-id="f5add-127">Recurse</span></span> |<span data-ttu-id="f5add-128">只有在搭配**類型** **目錄**使用時才有效。</span><span class="sxs-lookup"><span data-stu-id="f5add-128">Only valid when used with **Type** **Directory**.</span></span> <span data-ttu-id="f5add-129">以遞迴方式對所有目錄內容、子目錄和子目錄內容執行狀態作業。</span><span class="sxs-lookup"><span data-stu-id="f5add-129">Performs the state operation recursively to all directory content, subdirectories, and subdirectory content.</span></span> <span data-ttu-id="f5add-130">預設值為 `$false`。</span><span class="sxs-lookup"><span data-stu-id="f5add-130">Default value is `$false`.</span></span> |
|<span data-ttu-id="f5add-131">SourcePath</span><span class="sxs-lookup"><span data-stu-id="f5add-131">SourcePath</span></span> |<span data-ttu-id="f5add-132">要從中複製檔案或資料夾資源的路徑。</span><span class="sxs-lookup"><span data-stu-id="f5add-132">The path from which to copy the file or folder resource.</span></span> |
|<span data-ttu-id="f5add-133">類型</span><span class="sxs-lookup"><span data-stu-id="f5add-133">Type</span></span> |<span data-ttu-id="f5add-134">要設定的資源類型。</span><span class="sxs-lookup"><span data-stu-id="f5add-134">The type of resource being configured.</span></span> <span data-ttu-id="f5add-135">有效值為 **Directory** 和 **File**。</span><span class="sxs-lookup"><span data-stu-id="f5add-135">Valid values are **Directory** and **File**.</span></span> <span data-ttu-id="f5add-136">預設值為 **File**。</span><span class="sxs-lookup"><span data-stu-id="f5add-136">Default value is **File**.</span></span> |
|<span data-ttu-id="f5add-137">MatchSource</span><span class="sxs-lookup"><span data-stu-id="f5add-137">MatchSource</span></span> |<span data-ttu-id="f5add-138">判斷資源是否應該監視在初始複本之後新增至來源目錄的新檔案。</span><span class="sxs-lookup"><span data-stu-id="f5add-138">Determines if the resource should monitor for new files added to the source directory after the initial copy.</span></span> <span data-ttu-id="f5add-139">若值為 `$true`，即表示在初始複本之後，任何新的原始程式檔都應該複製到目的地。</span><span class="sxs-lookup"><span data-stu-id="f5add-139">A value of `$true` indicates that, after the initial copy, any new source files should be copied to the destination.</span></span> <span data-ttu-id="f5add-140">若設為 `$false`，資源就會快取來源目錄的內容，並忽略任何初始複本之後新增的檔案。</span><span class="sxs-lookup"><span data-stu-id="f5add-140">If set to `$false`, the resource caches the contents of the source directory and ignores any files added after the initial copy.</span></span> <span data-ttu-id="f5add-141">預設值為 `$false`。</span><span class="sxs-lookup"><span data-stu-id="f5add-141">Default value is `$false`.</span></span> |

> [!WARNING]
> <span data-ttu-id="f5add-142">如果您未指定 **Credential** 或 **PSRunAsCredential** 的值，資源將使用目標節點的電腦帳戶來存取 **SourcePath**。</span><span class="sxs-lookup"><span data-stu-id="f5add-142">If you do not specify a value for **Credential** or **PSRunAsCredential**, the resource will use the computer account of the target node to access the **SourcePath**.</span></span> <span data-ttu-id="f5add-143">當 **SourcePath** 為 UNC 共用時，這可能導致「拒絕存取」錯誤。</span><span class="sxs-lookup"><span data-stu-id="f5add-143">When the **SourcePath** is a UNC share, this could result in an "Access Denied" error.</span></span> <span data-ttu-id="f5add-144">請確定已相應地設定您的權限，或使用 **Credential** 或 **PSRunAsCredential** 屬性來指定應使用的帳戶。</span><span class="sxs-lookup"><span data-stu-id="f5add-144">Please ensure your permissions are set accordingly, or use the **Credential** or **PSRunAsCredential** properties to specify the account that should be used.</span></span>

## <a name="common-properties"></a><span data-ttu-id="f5add-145">通用屬性</span><span class="sxs-lookup"><span data-stu-id="f5add-145">Common properties</span></span>

|<span data-ttu-id="f5add-146">屬性</span><span class="sxs-lookup"><span data-stu-id="f5add-146">Property</span></span> |<span data-ttu-id="f5add-147">描述</span><span class="sxs-lookup"><span data-stu-id="f5add-147">Description</span></span> |
|---|---|
|<span data-ttu-id="f5add-148">DependsOn</span><span class="sxs-lookup"><span data-stu-id="f5add-148">DependsOn</span></span> |<span data-ttu-id="f5add-149">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="f5add-149">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f5add-150">例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="f5add-150">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="f5add-151">Ensure</span><span class="sxs-lookup"><span data-stu-id="f5add-151">Ensure</span></span> |<span data-ttu-id="f5add-152">判斷位於 **Destination** 的檔案和 **Contents** 是否應存在。</span><span class="sxs-lookup"><span data-stu-id="f5add-152">Determines whether the file and **Contents** at the **Destination** should exist or not.</span></span> <span data-ttu-id="f5add-153">將此屬性設定為 **Present** 以確保檔案存在。</span><span class="sxs-lookup"><span data-stu-id="f5add-153">Set this property to **Present** to ensure the file exists.</span></span> <span data-ttu-id="f5add-154">設為 **Absent** 以確保它們不存在。</span><span class="sxs-lookup"><span data-stu-id="f5add-154">Set it to **Absent** to ensure they do not exist.</span></span> <span data-ttu-id="f5add-155">預設值為 **Present**。</span><span class="sxs-lookup"><span data-stu-id="f5add-155">The default value is **Present**.</span></span> |
|<span data-ttu-id="f5add-156">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="f5add-156">PsDscRunAsCredential</span></span> |<span data-ttu-id="f5add-157">設定用於執行整個資源的認證。</span><span class="sxs-lookup"><span data-stu-id="f5add-157">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="f5add-158">已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="f5add-158">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="f5add-159">如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="f5add-159">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

### <a name="additional-information"></a><span data-ttu-id="f5add-160">其他資訊</span><span class="sxs-lookup"><span data-stu-id="f5add-160">Additional information</span></span>

- <span data-ttu-id="f5add-161">當您只指定 **DestinationPath** 時，資源可確保路徑存在 (若為 **Present**) 或不存在 (若為 **Absent**)。</span><span class="sxs-lookup"><span data-stu-id="f5add-161">When you only specify a **DestinationPath**, the resource ensures that the path exists if **Present** or does not exist if **Absent**.</span></span>
- <span data-ttu-id="f5add-162">當您以 **Directory** 的 **Type** 值指定 **SourcePath** 和 **DestinationPath** 時，資源會將來源目錄複寫到目的地路徑。</span><span class="sxs-lookup"><span data-stu-id="f5add-162">When you specify a **SourcePath** and a **DestinationPath** with a **Type** value of **Directory**, the resource copies source directory to the destination path.</span></span> <span data-ttu-id="f5add-163">屬性 **Recurse**、**Force** 和 **MatchSource** 會變更所執行的複製作業類型，而 **Credential** 會判斷要使用哪一個帳戶來存取來源目錄。</span><span class="sxs-lookup"><span data-stu-id="f5add-163">The properties **Recurse**, **Force**, and **MatchSource** change the type of copy operation performed, while **Credential** determines which account to use to access the source directory.</span></span>
- <span data-ttu-id="f5add-164">如果未在複製目錄時將 **Recurse** 屬性設定為 `$true`，即不會複製現有目錄的任何內容。</span><span class="sxs-lookup"><span data-stu-id="f5add-164">If you do not set the **Recurse** property to `$true` when copying a directory, none of the contents of the existing directory will be copied.</span></span> <span data-ttu-id="f5add-165">只會複製指定的目錄。</span><span class="sxs-lookup"><span data-stu-id="f5add-165">Only the directory specified will be copied.</span></span>
- <span data-ttu-id="f5add-166">如果您為 **Attributes** 屬性和 **DestinationPath** 指定了 **ReadOnly** 值，則 **Ensure** **Present** 會建立指定的路徑，而 **Contents** 會設定檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="f5add-166">If you specified a value of **ReadOnly** for the **Attributes** property alongside a **DestinationPath**, **Ensure** **Present** would create the path specified, while **Contents** would set the contents of the file.</span></span> <span data-ttu-id="f5add-167">**Ensure** **Absent** 設定會完全忽略 **Attributes** 屬性，並移除指定路徑上的任何檔案。</span><span class="sxs-lookup"><span data-stu-id="f5add-167">An **Ensure** **Absent** setting would ignore the **Attributes** property entirely, and remove any file at the specified path.</span></span>

## <a name="example"></a><span data-ttu-id="f5add-168">範例</span><span class="sxs-lookup"><span data-stu-id="f5add-168">Example</span></span>

<span data-ttu-id="f5add-169">下列範例會使用檔案資源，將某個目錄及其子目錄從提取伺服器複製到目標節點。</span><span class="sxs-lookup"><span data-stu-id="f5add-169">The following example copies a directory and its subdirectories from a pull server to a target node using the File Resource.</span></span> <span data-ttu-id="f5add-170">如果此作業成功，記錄資源就會將確認訊息寫入至事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="f5add-170">If the operation succeeds, the Log resource writes a confirmation message to the event log.</span></span>

<span data-ttu-id="f5add-171">來源目錄是從提取伺服器共用的 UNC 路徑 (`\\PullServer\DemoSource`)。</span><span class="sxs-lookup"><span data-stu-id="f5add-171">The source directory is a UNC path (`\\PullServer\DemoSource`) shared from the Pull Server.</span></span> <span data-ttu-id="f5add-172">**Recurse** 屬性確保會一併複製所有子目錄。</span><span class="sxs-lookup"><span data-stu-id="f5add-172">The **Recurse** property ensures that all subdirectories are copied as well.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f5add-173">根據預設，目標節點上的 LCM 會在本機系統帳戶的內容中執行。</span><span class="sxs-lookup"><span data-stu-id="f5add-173">The LCM on the target Node executes in the context of the local system account by default.</span></span> <span data-ttu-id="f5add-174">若要授與存取 **SourcePath**，請為目標節點的電腦帳戶提供適當的權限。</span><span class="sxs-lookup"><span data-stu-id="f5add-174">To grant access to the **SourcePath**, give the target Node's computer account appropriate permissions.</span></span> <span data-ttu-id="f5add-175">**Credential** 和 **PSDSCRunAsCredential** 都會變更 LCM 用來存取 **SourcePath** 的內容。</span><span class="sxs-lookup"><span data-stu-id="f5add-175">The **Credential** and **PSDSCRunAsCredential** both change the context the LCM uses to access the **SourcePath**.</span></span> <span data-ttu-id="f5add-176">您仍然需要授與存取將用來存取 **SourcePath** 的帳戶。</span><span class="sxs-lookup"><span data-stu-id="f5add-176">You still need to grant access to the account that will be used to access the **SourcePath**.</span></span>

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

<span data-ttu-id="f5add-177">如需在 DSC 中使用**認證**的詳細資訊，請參閱[以使用者身分執行](../../../configurations/runAsUser.md)或[設定資料認證](../../../configurations/configDataCredentials.md)。</span><span class="sxs-lookup"><span data-stu-id="f5add-177">For more on using **Credentials** in DSC see [Run As User](../../../configurations/runAsUser.md) or [Config Data Credentials](../../../configurations/configDataCredentials.md).</span></span>
