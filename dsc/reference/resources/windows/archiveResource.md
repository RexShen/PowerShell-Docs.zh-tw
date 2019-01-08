---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: DSC 封存資源
ms.openlocfilehash: d5ccd242d000a0907c6768f30923764be6bf20a3
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047312"
---
# <a name="dsc-archive-resource"></a><span data-ttu-id="5cdc0-103">DSC 封存資源</span><span class="sxs-lookup"><span data-stu-id="5cdc0-103">DSC Archive Resource</span></span>

> <span data-ttu-id="5cdc0-104">適用於：Windows PowerShell 4.0 中，Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="5cdc0-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="5cdc0-105">Windows PowerShell 預期狀態設定 (DSC) 的封存資源會提供一個機制，將封存 (.zip) 檔案解壓縮在特定路徑。</span><span class="sxs-lookup"><span data-stu-id="5cdc0-105">The Archive resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.zip) files at a specific path.</span></span>

## <a name="syntax"></a><span data-ttu-id="5cdc0-106">語法</span><span class="sxs-lookup"><span data-stu-id="5cdc0-106">Syntax</span></span>
```MOF
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
}
```

## <a name="properties"></a><span data-ttu-id="5cdc0-107">Properties</span><span class="sxs-lookup"><span data-stu-id="5cdc0-107">Properties</span></span>

|  <span data-ttu-id="5cdc0-108">屬性</span><span class="sxs-lookup"><span data-stu-id="5cdc0-108">Property</span></span>  |  <span data-ttu-id="5cdc0-109">描述</span><span class="sxs-lookup"><span data-stu-id="5cdc0-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="5cdc0-110">Destination</span><span class="sxs-lookup"><span data-stu-id="5cdc0-110">Destination</span></span>| <span data-ttu-id="5cdc0-111">指定您想要確保的封存內容解壓縮位置。</span><span class="sxs-lookup"><span data-stu-id="5cdc0-111">Specifies the location where you want to ensure the archive contents are extracted.</span></span>|
| <span data-ttu-id="5cdc0-112">路徑</span><span class="sxs-lookup"><span data-stu-id="5cdc0-112">Path</span></span>| <span data-ttu-id="5cdc0-113">指定封存檔案的來源路徑。</span><span class="sxs-lookup"><span data-stu-id="5cdc0-113">Specifies the source path of the archive file.</span></span>|
| <span data-ttu-id="5cdc0-114">__Checksum__</span><span class="sxs-lookup"><span data-stu-id="5cdc0-114">__Checksum__</span></span>| <span data-ttu-id="5cdc0-115">定義判斷兩個檔案是否相同時所使用的類型。</span><span class="sxs-lookup"><span data-stu-id="5cdc0-115">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="5cdc0-116">如不指定 __Checksum__，只會使用檔案或目錄名稱進行比較。</span><span class="sxs-lookup"><span data-stu-id="5cdc0-116">If __Checksum__ is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="5cdc0-117">有效值包括：Sha-1、 SHA-256、 SHA-512、-512、createddate、modifieddate、 modifiedDate none （預設值）。</span><span class="sxs-lookup"><span data-stu-id="5cdc0-117">Valid values include: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate, none (default).</span></span> <span data-ttu-id="5cdc0-118">如果指定 __Checksum__ 但無 __Validate__，設定會失敗。</span><span class="sxs-lookup"><span data-stu-id="5cdc0-118">If you specify __Checksum__ without __Validate__, the configuration will fail.</span></span>|
| <span data-ttu-id="5cdc0-119">Ensure</span><span class="sxs-lookup"><span data-stu-id="5cdc0-119">Ensure</span></span>| <span data-ttu-id="5cdc0-120">當__目的地__有封存內容時，決定是否要檢查。</span><span class="sxs-lookup"><span data-stu-id="5cdc0-120">Determines whether to check if the content of the archive exists at the __Destination__.</span></span> <span data-ttu-id="5cdc0-121">請將這個屬性設為 __Present__ 以確保有內容。</span><span class="sxs-lookup"><span data-stu-id="5cdc0-121">Set this property to __Present__ to ensure the contents exist.</span></span> <span data-ttu-id="5cdc0-122">設為 __Absent__ 以確保它們不存在。</span><span class="sxs-lookup"><span data-stu-id="5cdc0-122">Set it to __Absent__ to ensure they do not exist.</span></span> <span data-ttu-id="5cdc0-123">預設值為 __Present__。</span><span class="sxs-lookup"><span data-stu-id="5cdc0-123">The default value is __Present__.</span></span>|
| <span data-ttu-id="5cdc0-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="5cdc0-124">DependsOn</span></span> | <span data-ttu-id="5cdc0-125">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="5cdc0-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="5cdc0-126">例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 ResourceName，而它的類型是 __ResourceType__，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="5cdc0-126">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="5cdc0-127">驗證</span><span class="sxs-lookup"><span data-stu-id="5cdc0-127">Validate</span></span>| <span data-ttu-id="5cdc0-128">使用 Checksum 屬性判斷封存是否符合簽章。</span><span class="sxs-lookup"><span data-stu-id="5cdc0-128">Uses the Checksum property to determine if the archive matches the signature.</span></span> <span data-ttu-id="5cdc0-129">如果指定 Checksum 但無 Validate，設定會失敗。</span><span class="sxs-lookup"><span data-stu-id="5cdc0-129">If you specify Checksum without Validate, the configuration will fail.</span></span> <span data-ttu-id="5cdc0-130">如果指定 Validate 但無 Checksum，預設使用 SHA-256 總和檢查碼。</span><span class="sxs-lookup"><span data-stu-id="5cdc0-130">If you specify Validate without Checksum, a SHA-256 checksum is used by default.</span></span>|
| <span data-ttu-id="5cdc0-131">Force</span><span class="sxs-lookup"><span data-stu-id="5cdc0-131">Force</span></span>| <span data-ttu-id="5cdc0-132">某些檔案作業 (例如覆寫檔案，或刪除不是空的目錄) 會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="5cdc0-132">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="5cdc0-133">使用 Force 屬性會覆寫此類錯誤。</span><span class="sxs-lookup"><span data-stu-id="5cdc0-133">Using the Force property overrides such errors.</span></span> <span data-ttu-id="5cdc0-134">預設值為 False。</span><span class="sxs-lookup"><span data-stu-id="5cdc0-134">The default value is False.</span></span>|

## <a name="example"></a><span data-ttu-id="5cdc0-135">範例</span><span class="sxs-lookup"><span data-stu-id="5cdc0-135">Example</span></span>

<span data-ttu-id="5cdc0-136">下列範例示範如何使用封存資源以確保 Test.zip 封存檔案的內容存在，並會解壓縮在指定的目的地。</span><span class="sxs-lookup"><span data-stu-id="5cdc0-136">The following example shows how to use the Archive resource to ensure that the contents of an archive file called Test.zip exist and are extracted at a given destination.</span></span>

```
Archive ArchiveExample {
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```