---
ms.date: 07/17/2020
ms.topic: reference
title: DSC for Linux nxArchive 資源
description: DSC for Linux nxArchive 資源
ms.openlocfilehash: 2705829ccae0c1baa27324030433340e7f3949c1
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92648858"
---
# <a name="dsc-for-linux-nxarchive-resource"></a><span data-ttu-id="a2537-103">DSC for Linux nxArchive 資源</span><span class="sxs-lookup"><span data-stu-id="a2537-103">DSC for Linux nxArchive Resource</span></span>

<span data-ttu-id="a2537-104">PowerShell 預期狀態設定 (DSC) 的 **nxArchive** 資源會提供一個機制，將封存 (.tar、.zip) 檔案解壓縮在 Linux 節點上的特定路徑。</span><span class="sxs-lookup"><span data-stu-id="a2537-104">The **nxArchive** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.tar, .zip) files at a specific path on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="a2537-105">語法</span><span class="sxs-lookup"><span data-stu-id="a2537-105">Syntax</span></span>

```Syntax
nxArchive <string> #ResourceName
{
    SourcePath = <string>
    DestinationPath = <string>
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Force = <bool> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="a2537-106">屬性</span><span class="sxs-lookup"><span data-stu-id="a2537-106">Properties</span></span>

|<span data-ttu-id="a2537-107">屬性</span><span class="sxs-lookup"><span data-stu-id="a2537-107">Property</span></span> |<span data-ttu-id="a2537-108">描述</span><span class="sxs-lookup"><span data-stu-id="a2537-108">Description</span></span> |
|---|---|
|<span data-ttu-id="a2537-109">SourcePath</span><span class="sxs-lookup"><span data-stu-id="a2537-109">SourcePath</span></span> |<span data-ttu-id="a2537-110">指定封存檔案的來源路徑。</span><span class="sxs-lookup"><span data-stu-id="a2537-110">Specifies the source path of the archive file.</span></span> <span data-ttu-id="a2537-111">這應該是 .tar、.zip 或 .tar.gz 檔案。</span><span class="sxs-lookup"><span data-stu-id="a2537-111">This should be a .tar, .zip, or .tar.gz file.</span></span> |
|<span data-ttu-id="a2537-112">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="a2537-112">DestinationPath</span></span> |<span data-ttu-id="a2537-113">指定您想要確保的封存內容解壓縮位置。</span><span class="sxs-lookup"><span data-stu-id="a2537-113">Specifies the location where you want to ensure the archive contents are extracted.</span></span> |
|<span data-ttu-id="a2537-114">總和檢查碼</span><span class="sxs-lookup"><span data-stu-id="a2537-114">Checksum</span></span> |<span data-ttu-id="a2537-115">定義判斷是否已更新來源封存檔時所使用的類型。</span><span class="sxs-lookup"><span data-stu-id="a2537-115">Defines the type to use when determining whether the source archive has been updated.</span></span> <span data-ttu-id="a2537-116">值為： **ctime** 、 **mtime** 或 **md5** 。</span><span class="sxs-lookup"><span data-stu-id="a2537-116">Values are: **ctime** , **mtime** , or **md5** .</span></span> <span data-ttu-id="a2537-117">預設值為 **md5** 。</span><span class="sxs-lookup"><span data-stu-id="a2537-117">The default value is **md5** .</span></span> |
|<span data-ttu-id="a2537-118">Force</span><span class="sxs-lookup"><span data-stu-id="a2537-118">Force</span></span> |<span data-ttu-id="a2537-119">某些檔案作業 (例如覆寫檔案，或刪除不是空的目錄) 會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="a2537-119">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="a2537-120">使用 **Force** 屬性會覆寫此類錯誤。</span><span class="sxs-lookup"><span data-stu-id="a2537-120">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="a2537-121">預設值是 `$false`。</span><span class="sxs-lookup"><span data-stu-id="a2537-121">The default value is `$false`.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="a2537-122">通用屬性</span><span class="sxs-lookup"><span data-stu-id="a2537-122">Common properties</span></span>

|<span data-ttu-id="a2537-123">屬性</span><span class="sxs-lookup"><span data-stu-id="a2537-123">Property</span></span> |<span data-ttu-id="a2537-124">描述</span><span class="sxs-lookup"><span data-stu-id="a2537-124">Description</span></span> |
|---|---|
|<span data-ttu-id="a2537-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="a2537-125">DependsOn</span></span> |<span data-ttu-id="a2537-126">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="a2537-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a2537-127">例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="a2537-127">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="a2537-128">Ensure</span><span class="sxs-lookup"><span data-stu-id="a2537-128">Ensure</span></span> |<span data-ttu-id="a2537-129">當 **目的地** 有封存內容時，決定是否要檢查。</span><span class="sxs-lookup"><span data-stu-id="a2537-129">Determines whether to check if the content of the archive exists at the **Destination** .</span></span> <span data-ttu-id="a2537-130">請將這個屬性設為 **Present** 以確保有內容。</span><span class="sxs-lookup"><span data-stu-id="a2537-130">Set this property to **Present** to ensure the contents exist.</span></span> <span data-ttu-id="a2537-131">設為 **Absent** 以確保它們不存在。</span><span class="sxs-lookup"><span data-stu-id="a2537-131">Set it to **Absent** to ensure they do not exist.</span></span> <span data-ttu-id="a2537-132">預設值為 **Present** 。</span><span class="sxs-lookup"><span data-stu-id="a2537-132">The default value is **Present** .</span></span> |

## <a name="example"></a><span data-ttu-id="a2537-133">範例</span><span class="sxs-lookup"><span data-stu-id="a2537-133">Example</span></span>

<span data-ttu-id="a2537-134">下列範例示範如何使用 **nxArchive** 資源以確保 `website.tar` 封存檔案的內容存在，並會解壓縮在指定的目的地。</span><span class="sxs-lookup"><span data-stu-id="a2537-134">The following example shows how to use the **nxArchive** resource to ensure that the contents of an archive file called `website.tar` exist and are extracted at a given destination.</span></span>

```powershell
Import-DSCResource -Module nx

nxFile SyncArchiveFromWeb
{
   Ensure = "Present"
   SourcePath = "http://release.contoso.com/releases/website.tar"
   DestinationPath = "/usr/release/staging/website.tar"
   Type = "File"
   Checksum = "mtime"
}

nxArchive SyncWebDir
{
   SourcePath = "/usr/release/staging/website.tar"
   DestinationPath = "/usr/local/apache2/htdocs/"
   Force = $false
   DependsOn = "[nxFile]SyncArchiveFromWeb"
}
```
