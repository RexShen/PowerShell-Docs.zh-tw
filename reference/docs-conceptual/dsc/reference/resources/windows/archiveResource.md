---
ms.date: 09/20/2019
keywords: dsc,powershell,設定,安裝
title: DSC 封存資源
ms.openlocfilehash: ddabe1a623783fe213b8059f47851184d5253fc5
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954765"
---
# <a name="dsc-archive-resource"></a><span data-ttu-id="d8732-103">DSC 封存資源</span><span class="sxs-lookup"><span data-stu-id="d8732-103">DSC Archive Resource</span></span>

> <span data-ttu-id="d8732-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="d8732-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="d8732-105">Windows PowerShell 預期狀態設定 (DSC) 的封存資源會提供一個機制，將封存 (.zip) 檔案解壓縮在特定路徑。</span><span class="sxs-lookup"><span data-stu-id="d8732-105">The Archive resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.zip) files at a specific path.</span></span>

## <a name="syntax"></a><span data-ttu-id="d8732-106">語法</span><span class="sxs-lookup"><span data-stu-id="d8732-106">Syntax</span></span>

```Syntax
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
    [ Ensure = [string] { Absent | Present } ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="d8732-107">Properties</span><span class="sxs-lookup"><span data-stu-id="d8732-107">Properties</span></span>

|<span data-ttu-id="d8732-108">屬性</span><span class="sxs-lookup"><span data-stu-id="d8732-108">Property</span></span> |<span data-ttu-id="d8732-109">描述</span><span class="sxs-lookup"><span data-stu-id="d8732-109">Description</span></span> |
|---|---|
|<span data-ttu-id="d8732-110">Destination</span><span class="sxs-lookup"><span data-stu-id="d8732-110">Destination</span></span> |<span data-ttu-id="d8732-111">指定您想要確保的封存內容解壓縮位置。</span><span class="sxs-lookup"><span data-stu-id="d8732-111">Specifies the location where you want to ensure the archive contents are extracted.</span></span> |
|<span data-ttu-id="d8732-112">路徑</span><span class="sxs-lookup"><span data-stu-id="d8732-112">Path</span></span> |<span data-ttu-id="d8732-113">指定封存檔案的來源路徑。</span><span class="sxs-lookup"><span data-stu-id="d8732-113">Specifies the source path of the archive file.</span></span> |
|<span data-ttu-id="d8732-114">總和檢查碼</span><span class="sxs-lookup"><span data-stu-id="d8732-114">Checksum</span></span> |<span data-ttu-id="d8732-115">定義判斷兩個檔案是否相同時所使用的類型。</span><span class="sxs-lookup"><span data-stu-id="d8732-115">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="d8732-116">如不指定 **Checksum**，只會使用檔案或目錄名稱進行比較。</span><span class="sxs-lookup"><span data-stu-id="d8732-116">If **Checksum** is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="d8732-117">有效值包括：**SHA-1**、**SHA-256**、**SHA-512**、**createdDate**、**modifiedDate**。</span><span class="sxs-lookup"><span data-stu-id="d8732-117">Valid values include: **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**.</span></span> <span data-ttu-id="d8732-118">如果指定 **Checksum** 但無 **Validate**，設定會失敗。</span><span class="sxs-lookup"><span data-stu-id="d8732-118">If you specify **Checksum** without **Validate**, the configuration will fail.</span></span> |
|<span data-ttu-id="d8732-119">Force</span><span class="sxs-lookup"><span data-stu-id="d8732-119">Force</span></span> |<span data-ttu-id="d8732-120">某些檔案作業 (例如覆寫檔案，或刪除不是空的目錄) 會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="d8732-120">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="d8732-121">使用 **Force** 屬性會覆寫此類錯誤。</span><span class="sxs-lookup"><span data-stu-id="d8732-121">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="d8732-122">預設值為 **False**。</span><span class="sxs-lookup"><span data-stu-id="d8732-122">The default value is **False**.</span></span> |
|<span data-ttu-id="d8732-123">驗證</span><span class="sxs-lookup"><span data-stu-id="d8732-123">Validate</span></span>| <span data-ttu-id="d8732-124">使用 **Checksum** 屬性判斷封存是否符合簽章。</span><span class="sxs-lookup"><span data-stu-id="d8732-124">Uses the **Checksum** property to determine if the archive matches the signature.</span></span> <span data-ttu-id="d8732-125">如果指定 **Checksum** 但無 **Validate**，設定會失敗。</span><span class="sxs-lookup"><span data-stu-id="d8732-125">If you specify **Checksum** without **Validate**, the configuration will fail.</span></span> <span data-ttu-id="d8732-126">如果指定 **Validate** 但無 **Checksum**，則預設會使用 _SHA-256_ **Checksum**。</span><span class="sxs-lookup"><span data-stu-id="d8732-126">If you specify **Validate** without **Checksum**, a _SHA-256_ **Checksum** is used by default.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="d8732-127">通用屬性</span><span class="sxs-lookup"><span data-stu-id="d8732-127">Common properties</span></span>

|<span data-ttu-id="d8732-128">屬性</span><span class="sxs-lookup"><span data-stu-id="d8732-128">Property</span></span> |<span data-ttu-id="d8732-129">描述</span><span class="sxs-lookup"><span data-stu-id="d8732-129">Description</span></span> |
|---|---|
|<span data-ttu-id="d8732-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="d8732-130">DependsOn</span></span> |<span data-ttu-id="d8732-131">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="d8732-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="d8732-132">例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="d8732-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="d8732-133">Ensure</span><span class="sxs-lookup"><span data-stu-id="d8732-133">Ensure</span></span> |<span data-ttu-id="d8732-134">當**目的地**有封存內容時，決定是否要檢查。</span><span class="sxs-lookup"><span data-stu-id="d8732-134">Determines whether to check if the content of the archive exists at the **Destination**.</span></span> <span data-ttu-id="d8732-135">請將這個屬性設為 **Present** 以確保有內容。</span><span class="sxs-lookup"><span data-stu-id="d8732-135">Set this property to **Present** to ensure the contents exist.</span></span> <span data-ttu-id="d8732-136">設為 **Absent** 以確保它們不存在。</span><span class="sxs-lookup"><span data-stu-id="d8732-136">Set it to **Absent** to ensure they do not exist.</span></span> <span data-ttu-id="d8732-137">預設值為 **Present**。</span><span class="sxs-lookup"><span data-stu-id="d8732-137">The default value is **Present**.</span></span> |
|<span data-ttu-id="d8732-138">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="d8732-138">PsDscRunAsCredential</span></span> |<span data-ttu-id="d8732-139">設定用於執行整個資源的認證。</span><span class="sxs-lookup"><span data-stu-id="d8732-139">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="d8732-140">已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="d8732-140">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="d8732-141">如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="d8732-141">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="d8732-142">範例</span><span class="sxs-lookup"><span data-stu-id="d8732-142">Example</span></span>

<span data-ttu-id="d8732-143">下列範例示範如何使用封存資源以確保 `Test.zip` 封存檔案的內容存在，並會解壓縮在指定的目的地。</span><span class="sxs-lookup"><span data-stu-id="d8732-143">The following example shows how to use the Archive resource to ensure that the contents of an archive file called `Test.zip` exist and are extracted at a given destination.</span></span>

```powershell
Archive ArchiveExample {
    Ensure = "Present"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```