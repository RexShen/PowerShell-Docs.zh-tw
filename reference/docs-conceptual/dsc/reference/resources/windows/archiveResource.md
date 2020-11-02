---
ms.date: 07/16/2020
ms.topic: reference
title: DSC 封存資源
description: DSC 封存資源
ms.openlocfilehash: 28e2436683d7cb3b69f894ac75bb1a58b8eb1e8a
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142393"
---
# <a name="dsc-archive-resource"></a><span data-ttu-id="a1bdb-103">DSC 封存資源</span><span class="sxs-lookup"><span data-stu-id="a1bdb-103">DSC Archive Resource</span></span>

> <span data-ttu-id="a1bdb-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="a1bdb-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="a1bdb-105">Windows PowerShell 預期狀態設定 (DSC) 的封存資源會提供一個機制，將封存 (.zip) 檔案解壓縮在特定路徑。</span><span class="sxs-lookup"><span data-stu-id="a1bdb-105">The Archive resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.zip) files at a specific path.</span></span>

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a><span data-ttu-id="a1bdb-106">語法</span><span class="sxs-lookup"><span data-stu-id="a1bdb-106">Syntax</span></span>

```Syntax
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Credential = [PSCredential] ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
    [ Ensure = [string] { Absent | Present } ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="a1bdb-107">屬性</span><span class="sxs-lookup"><span data-stu-id="a1bdb-107">Properties</span></span>

|<span data-ttu-id="a1bdb-108">屬性</span><span class="sxs-lookup"><span data-stu-id="a1bdb-108">Property</span></span> |<span data-ttu-id="a1bdb-109">描述</span><span class="sxs-lookup"><span data-stu-id="a1bdb-109">Description</span></span> |
|---|---|
| <span data-ttu-id="a1bdb-110">Destination</span><span class="sxs-lookup"><span data-stu-id="a1bdb-110">Destination</span></span> | <span data-ttu-id="a1bdb-111">指定您想要確保的封存內容解壓縮位置。</span><span class="sxs-lookup"><span data-stu-id="a1bdb-111">Specifies the location where you want to ensure the archive contents are extracted.</span></span> |
| <span data-ttu-id="a1bdb-112">Path</span><span class="sxs-lookup"><span data-stu-id="a1bdb-112">Path</span></span> | <span data-ttu-id="a1bdb-113">指定封存檔案的來源路徑。</span><span class="sxs-lookup"><span data-stu-id="a1bdb-113">Specifies the source path of the archive file.</span></span> |
| <span data-ttu-id="a1bdb-114">總和檢查碼</span><span class="sxs-lookup"><span data-stu-id="a1bdb-114">Checksum</span></span> | <span data-ttu-id="a1bdb-115">定義判斷兩個檔案是否相同時所使用的類型。</span><span class="sxs-lookup"><span data-stu-id="a1bdb-115">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="a1bdb-116">如不指定 **Checksum** ，只會使用檔案或目錄名稱進行比較。</span><span class="sxs-lookup"><span data-stu-id="a1bdb-116">If **Checksum** is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="a1bdb-117">有效值包括： **SHA-1** 、 **SHA-256** 、 **SHA-512** 、 **createdDate** 、 **modifiedDate** 。</span><span class="sxs-lookup"><span data-stu-id="a1bdb-117">Valid values include: **SHA-1** , **SHA-256** , **SHA-512** , **createdDate** , **modifiedDate** .</span></span> <span data-ttu-id="a1bdb-118">如果指定 **Checksum** 但無 **Validate** ，設定會失敗。</span><span class="sxs-lookup"><span data-stu-id="a1bdb-118">If you specify **Checksum** without **Validate** , the configuration will fail.</span></span> |
| <span data-ttu-id="a1bdb-119">認證</span><span class="sxs-lookup"><span data-stu-id="a1bdb-119">Credential</span></span> | <span data-ttu-id="a1bdb-120">有權存取指定封存路徑和目的地的使用者帳戶認證 (如有需要)。</span><span class="sxs-lookup"><span data-stu-id="a1bdb-120">The credential of a user account with permissions to access the specified archive path and destination if needed.</span></span> |
| <span data-ttu-id="a1bdb-121">Force</span><span class="sxs-lookup"><span data-stu-id="a1bdb-121">Force</span></span> | <span data-ttu-id="a1bdb-122">某些檔案作業 (例如覆寫檔案，或刪除不是空的目錄) 會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="a1bdb-122">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="a1bdb-123">使用 **Force** 屬性會覆寫此類錯誤。</span><span class="sxs-lookup"><span data-stu-id="a1bdb-123">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="a1bdb-124">預設值為 **[False]** 。</span><span class="sxs-lookup"><span data-stu-id="a1bdb-124">The default value is **False** .</span></span> |
| <span data-ttu-id="a1bdb-125">Validate</span><span class="sxs-lookup"><span data-stu-id="a1bdb-125">Validate</span></span>| <span data-ttu-id="a1bdb-126">使用 **Checksum** 屬性判斷封存是否符合簽章。</span><span class="sxs-lookup"><span data-stu-id="a1bdb-126">Uses the **Checksum** property to determine if the archive matches the signature.</span></span> <span data-ttu-id="a1bdb-127">如果指定 **Checksum** 但無 **Validate** ，設定會失敗。</span><span class="sxs-lookup"><span data-stu-id="a1bdb-127">If you specify **Checksum** without **Validate** , the configuration will fail.</span></span> <span data-ttu-id="a1bdb-128">如果指定 **Validate** 但無 **Checksum** ，則預設會使用 _SHA-256_ **Checksum** 。</span><span class="sxs-lookup"><span data-stu-id="a1bdb-128">If you specify **Validate** without **Checksum** , a _SHA-256_ **Checksum** is used by default.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="a1bdb-129">通用屬性</span><span class="sxs-lookup"><span data-stu-id="a1bdb-129">Common properties</span></span>

|<span data-ttu-id="a1bdb-130">屬性</span><span class="sxs-lookup"><span data-stu-id="a1bdb-130">Property</span></span> |<span data-ttu-id="a1bdb-131">描述</span><span class="sxs-lookup"><span data-stu-id="a1bdb-131">Description</span></span> |
|---|---|
|<span data-ttu-id="a1bdb-132">DependsOn</span><span class="sxs-lookup"><span data-stu-id="a1bdb-132">DependsOn</span></span> |<span data-ttu-id="a1bdb-133">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="a1bdb-133">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a1bdb-134">例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="a1bdb-134">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="a1bdb-135">Ensure</span><span class="sxs-lookup"><span data-stu-id="a1bdb-135">Ensure</span></span> |<span data-ttu-id="a1bdb-136">當 **目的地** 有封存內容時，決定是否要檢查。</span><span class="sxs-lookup"><span data-stu-id="a1bdb-136">Determines whether to check if the content of the archive exists at the **Destination** .</span></span> <span data-ttu-id="a1bdb-137">請將這個屬性設為 **Present** 以確保有內容。</span><span class="sxs-lookup"><span data-stu-id="a1bdb-137">Set this property to **Present** to ensure the contents exist.</span></span> <span data-ttu-id="a1bdb-138">設為 **Absent** 以確保它們不存在。</span><span class="sxs-lookup"><span data-stu-id="a1bdb-138">Set it to **Absent** to ensure they do not exist.</span></span> <span data-ttu-id="a1bdb-139">預設值為 **Present** 。</span><span class="sxs-lookup"><span data-stu-id="a1bdb-139">The default value is **Present** .</span></span> |
|<span data-ttu-id="a1bdb-140">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="a1bdb-140">PsDscRunAsCredential</span></span> |<span data-ttu-id="a1bdb-141">設定用於執行整個資源的認證。</span><span class="sxs-lookup"><span data-stu-id="a1bdb-141">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="a1bdb-142">已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="a1bdb-142">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="a1bdb-143">如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="a1bdb-143">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="a1bdb-144">範例</span><span class="sxs-lookup"><span data-stu-id="a1bdb-144">Example</span></span>

<span data-ttu-id="a1bdb-145">下例示範如何使用封存資源以確保 `Test.zip` 封存檔案的內容確實存在，並使用授權將內容解壓縮在指定的目的地。</span><span class="sxs-lookup"><span data-stu-id="a1bdb-145">The following example shows how to use the Archive resource to ensure that the contents of an archive file called `Test.zip` exist and are extracted at a given destination using and authorized.</span></span>

```powershell
Archive ArchiveExample {
    Ensure = "Present"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```
