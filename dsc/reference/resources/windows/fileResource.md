---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: DSC 檔案資源
ms.openlocfilehash: e5f7a91e5f19c8c7bbada090804d8f29a7cfedd5
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047403"
---
# <a name="dsc-file-resource"></a><span data-ttu-id="ef5df-103">DSC 檔案資源</span><span class="sxs-lookup"><span data-stu-id="ef5df-103">DSC File Resource</span></span>

> <span data-ttu-id="ef5df-104">適用於：Windows PowerShell 4.0 中，Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="ef5df-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="ef5df-105">Windows PowerShell 預期狀態設定 (DSC) 的檔案資源會提供一個機制，在目標節點管理檔案和資料夾。</span><span class="sxs-lookup"><span data-stu-id="ef5df-105">The File resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and folders on the target node.</span></span>

><span data-ttu-id="ef5df-106">**注意：** 如果 **MatchSource** 屬性設定為 **$false** (此為預設值)，則會在第一次套用設定時快取要複製的內容。</span><span class="sxs-lookup"><span data-stu-id="ef5df-106">**Note:** If the **MatchSource** property is set to **$false** (which is the default value), the contents to be copied are cached the first time the configuration is applied.</span></span>
><span data-ttu-id="ef5df-107">後續套用的設定不會檢查由 **SourcePath** 指定的路徑中是否有更新的檔案及/或資料夾。</span><span class="sxs-lookup"><span data-stu-id="ef5df-107">Subsequent applications of the configuration will not check for updated files and/or folders in the path specified by **SourcePath**.</span></span> <span data-ttu-id="ef5df-108">如果想要在每次套用設定時都檢查 **SourcePath** 中是否有檔案及/或資料夾更新，請將 **MatchSource** 設為 **$true**。</span><span class="sxs-lookup"><span data-stu-id="ef5df-108">If you want to check for updates to the files and/or folders in **SourcePath** every time the configuration is applied, set **MatchSource** to **$true**.</span></span>

## <a name="syntax"></a><span data-ttu-id="ef5df-109">語法</span><span class="sxs-lookup"><span data-stu-id="ef5df-109">Syntax</span></span>
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

## <a name="properties"></a><span data-ttu-id="ef5df-110">Properties</span><span class="sxs-lookup"><span data-stu-id="ef5df-110">Properties</span></span>

|  <span data-ttu-id="ef5df-111">屬性</span><span class="sxs-lookup"><span data-stu-id="ef5df-111">Property</span></span>  |  <span data-ttu-id="ef5df-112">描述</span><span class="sxs-lookup"><span data-stu-id="ef5df-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="ef5df-113">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="ef5df-113">DestinationPath</span></span>| <span data-ttu-id="ef5df-114">表示您要確認檔案或目錄狀態的位置。</span><span class="sxs-lookup"><span data-stu-id="ef5df-114">Indicates the location where you want to ensure the state for a file or directory.</span></span>|
| <span data-ttu-id="ef5df-115">屬性</span><span class="sxs-lookup"><span data-stu-id="ef5df-115">Attributes</span></span>| <span data-ttu-id="ef5df-116">指定目標檔案或目錄的屬性所需狀態。</span><span class="sxs-lookup"><span data-stu-id="ef5df-116">Specifies the desired state of the attributes for the targeted file or directory.</span></span>|
| <span data-ttu-id="ef5df-117">總和檢查碼</span><span class="sxs-lookup"><span data-stu-id="ef5df-117">Checksum</span></span>| <span data-ttu-id="ef5df-118">指出判斷兩個檔案是否相同時所使用的密碼總和類型。</span><span class="sxs-lookup"><span data-stu-id="ef5df-118">Indicates the checksum type to use when determining whether two files are the same.</span></span> <span data-ttu-id="ef5df-119">如不指定 __Checksum__，只會使用檔案或目錄名稱進行比較。</span><span class="sxs-lookup"><span data-stu-id="ef5df-119">If __Checksum__ is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="ef5df-120">有效值包括：Sha-1、 SHA-256、 SHA-512、-512、createddate、modifieddate、 modifiedDate。</span><span class="sxs-lookup"><span data-stu-id="ef5df-120">Valid values include: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.</span></span>|
| <span data-ttu-id="ef5df-121">內容</span><span class="sxs-lookup"><span data-stu-id="ef5df-121">Contents</span></span>| <span data-ttu-id="ef5df-122">指定檔案的內容，例如特定字串。</span><span class="sxs-lookup"><span data-stu-id="ef5df-122">Specifies the contents of a file, such as a particular string.</span></span>|
| <span data-ttu-id="ef5df-123">認證</span><span class="sxs-lookup"><span data-stu-id="ef5df-123">Credential</span></span>| <span data-ttu-id="ef5df-124">指出存取資源的必要認證，例如來源檔案 (如果需要這類存取)。</span><span class="sxs-lookup"><span data-stu-id="ef5df-124">Indicates the credentials that are required to access resources, such as source files, if such access is required.</span></span>|
| <span data-ttu-id="ef5df-125">Ensure</span><span class="sxs-lookup"><span data-stu-id="ef5df-125">Ensure</span></span>| <span data-ttu-id="ef5df-126">表示檔案或目錄是否存在。</span><span class="sxs-lookup"><span data-stu-id="ef5df-126">Indicates if the file or directory exists.</span></span> <span data-ttu-id="ef5df-127">設定此屬性為 "Absent" 以確保檔案或目錄不存在。</span><span class="sxs-lookup"><span data-stu-id="ef5df-127">Set this property to "Absent" to ensure that the file or directory does not exist.</span></span> <span data-ttu-id="ef5df-128">將此屬性設定為 "Present"，以確保檔案或目錄存在。</span><span class="sxs-lookup"><span data-stu-id="ef5df-128">Set it to "Present" to ensure that the file or directory does exist.</span></span> <span data-ttu-id="ef5df-129">預設值是 "Present"。</span><span class="sxs-lookup"><span data-stu-id="ef5df-129">The default is "Present".</span></span>|
| <span data-ttu-id="ef5df-130">Force</span><span class="sxs-lookup"><span data-stu-id="ef5df-130">Force</span></span>| <span data-ttu-id="ef5df-131">某些檔案作業 (例如覆寫檔案，或刪除不是空的目錄) 會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="ef5df-131">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="ef5df-132">使用 Force 屬性會覆寫此類錯誤。</span><span class="sxs-lookup"><span data-stu-id="ef5df-132">Using the Force property overrides such errors.</span></span> <span data-ttu-id="ef5df-133">預設值為 __$false__。</span><span class="sxs-lookup"><span data-stu-id="ef5df-133">The default value is __$false__.</span></span>|
| <span data-ttu-id="ef5df-134">Recurse</span><span class="sxs-lookup"><span data-stu-id="ef5df-134">Recurse</span></span>| <span data-ttu-id="ef5df-135">表示是否包含子目錄。</span><span class="sxs-lookup"><span data-stu-id="ef5df-135">Indicates if subdirectories are included.</span></span> <span data-ttu-id="ef5df-136">將此屬性設定為 __$true__，表示您想要包含子目錄。</span><span class="sxs-lookup"><span data-stu-id="ef5df-136">Set this property to __$true__ to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="ef5df-137">預設值為 __$false__。</span><span class="sxs-lookup"><span data-stu-id="ef5df-137">The default is __$false__.</span></span> <span data-ttu-id="ef5df-138">**注意**：當 Type 屬性設定為目錄，此屬性才有效。</span><span class="sxs-lookup"><span data-stu-id="ef5df-138">**Note**: This property is only valid when the Type property is set to Directory.</span></span>|
| <span data-ttu-id="ef5df-139">DependsOn</span><span class="sxs-lookup"><span data-stu-id="ef5df-139">DependsOn</span></span> | <span data-ttu-id="ef5df-140">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="ef5df-140">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="ef5df-141">例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 __ResourceName__，而它的類型是 __ResourceType__，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="ef5df-141">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="ef5df-142">SourcePath</span><span class="sxs-lookup"><span data-stu-id="ef5df-142">SourcePath</span></span>| <span data-ttu-id="ef5df-143">表示要從中複製檔案或資料夾資源的路徑。</span><span class="sxs-lookup"><span data-stu-id="ef5df-143">Indicates the path from which to copy the file or folder resource.</span></span>|
| <span data-ttu-id="ef5df-144">類型</span><span class="sxs-lookup"><span data-stu-id="ef5df-144">Type</span></span>| <span data-ttu-id="ef5df-145">表示正在設定的資源是否為目錄或檔案。</span><span class="sxs-lookup"><span data-stu-id="ef5df-145">Indicates if the resource being configured is a directory or a file.</span></span> <span data-ttu-id="ef5df-146">將此屬性設定為 "Directory"，表示該資源為目錄。</span><span class="sxs-lookup"><span data-stu-id="ef5df-146">Set this property to "Directory" to indicate that the resource is a directory.</span></span> <span data-ttu-id="ef5df-147">將此屬性設定為 "File"，表示該資源為檔案。</span><span class="sxs-lookup"><span data-stu-id="ef5df-147">Set it to "File" to indicate that the resource is a file.</span></span> <span data-ttu-id="ef5df-148">預設值為 "File"。</span><span class="sxs-lookup"><span data-stu-id="ef5df-148">The default value is “File”.</span></span>|
| <span data-ttu-id="ef5df-149">MatchSource</span><span class="sxs-lookup"><span data-stu-id="ef5df-149">MatchSource</span></span>| <span data-ttu-id="ef5df-150">如果設定為 __$false__ 的預設值，則當第一次套用此設定時，會將來源 (例如檔案 A、B 和 C) 上的任何檔案加入目的地。</span><span class="sxs-lookup"><span data-stu-id="ef5df-150">If set to the default value of __$false__, then any files on the source (say, files A, B, and C) will be added to the destination the first time the configuration is applied.</span></span> <span data-ttu-id="ef5df-151">如果將新的檔案 (D) 加入來源，就不會將這個檔案加入目的地，即使稍後重新套用此設定亦同。</span><span class="sxs-lookup"><span data-stu-id="ef5df-151">If a new file (D) is added to the source, it will not be added to the destination, even when the configuration is re-applied later.</span></span> <span data-ttu-id="ef5df-152">如果值為 __$true__，則每次套用此設定時，會將此來源 (例如，在此範例中的檔案 D) 上後續找到的新檔案加入目的地。</span><span class="sxs-lookup"><span data-stu-id="ef5df-152">If the value is __$true__, then each time the configuration is applied, new files subsequently found on the source (such as file D in this example) are added to the destination.</span></span> <span data-ttu-id="ef5df-153">預設值為 **$false**。</span><span class="sxs-lookup"><span data-stu-id="ef5df-153">The default value is **$false**.</span></span>|

## <a name="example"></a><span data-ttu-id="ef5df-154">範例</span><span class="sxs-lookup"><span data-stu-id="ef5df-154">Example</span></span>

<span data-ttu-id="ef5df-155">下列範例示範如何使用檔案資源，以確保來源電腦上路徑為 `C:\Users\Public\Documents\DSCDemo\DemoSource` (例如「提取」伺服器) 的目錄 (以及所有子目錄) 也會出現在目標節點上。</span><span class="sxs-lookup"><span data-stu-id="ef5df-155">The following example shows how to use the File resource to ensure that a directory with the path `C:\Users\Public\Documents\DSCDemo\DemoSource` on a source computer (such as the “pull” server) is also present (along with all subdirectories) on the target node.</span></span> <span data-ttu-id="ef5df-156">此外，也會在完成時將確認訊息寫入記錄檔，並包含陳述式，以確保記錄作業之前先執行檔案檢查作業。</span><span class="sxs-lookup"><span data-stu-id="ef5df-156">It also writes a confirmatory message to the log when complete and includes a statement to ensure that the file-checking operation runs prior to the logging operation.</span></span>

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present"  # You can also set Ensure to "Absent"
            Type = "Directory" # Default is "File".
            Recurse = $true # Ensure presence of subdirectories, too
            SourcePath = "C:\Users\Public\Documents\DSCDemo\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # This means run "DirectoryCopy" first.
        }
    }
}
```