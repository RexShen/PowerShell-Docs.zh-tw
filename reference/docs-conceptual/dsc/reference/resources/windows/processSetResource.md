---
ms.date: 07/16/2020
ms.topic: reference
title: DSC ProcessSet 資源
description: DSC ProcessSet 資源
ms.openlocfilehash: 3e09c8c7b4ca7d8e95b36f9d4c20c2a85abad9dd
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142560"
---
# <a name="dsc-processset-resource"></a><span data-ttu-id="d20bf-103">DSC ProcessSet 資源</span><span class="sxs-lookup"><span data-stu-id="d20bf-103">DSC ProcessSet Resource</span></span>

> <span data-ttu-id="d20bf-104">適用於：Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="d20bf-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="d20bf-105">Windows PowerShell 預期狀態設定 (DSC) 的 **ProcessSet** 資源提供了在目標節點設定程序的機制。</span><span class="sxs-lookup"><span data-stu-id="d20bf-105">The **ProcessSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a><span data-ttu-id="d20bf-106">語法</span><span class="sxs-lookup"><span data-stu-id="d20bf-106">Syntax</span></span>

```Syntax
ProcessSet [string] #ResourceName
{
    Path = [string]
    [ Credential = [PSCredential] ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="d20bf-107">屬性</span><span class="sxs-lookup"><span data-stu-id="d20bf-107">Properties</span></span>

|<span data-ttu-id="d20bf-108">屬性</span><span class="sxs-lookup"><span data-stu-id="d20bf-108">Property</span></span> |<span data-ttu-id="d20bf-109">描述</span><span class="sxs-lookup"><span data-stu-id="d20bf-109">Description</span></span> |
|---|---|
|<span data-ttu-id="d20bf-110">Path</span><span class="sxs-lookup"><span data-stu-id="d20bf-110">Path</span></span> |<span data-ttu-id="d20bf-111">處理程序可執行檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="d20bf-111">The path to the process executable.</span></span> <span data-ttu-id="d20bf-112">如果這些是可執行檔的檔案名稱 (不是完整路徑)，則 DSC 資源會搜尋環境 `$env:Path` 變數來尋找檔案。</span><span class="sxs-lookup"><span data-stu-id="d20bf-112">If these are the names of the executable files (not fully qualified paths), the DSC resource will search the environment `$env:Path` variable to find the files.</span></span> <span data-ttu-id="d20bf-113">如果這個屬性的值是完整路徑，則 DSC 不會使用 `$env:Path` 環境變數來尋找檔案，但若任一路徑不存在則會擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="d20bf-113">If the values of this property are fully qualified paths, DSC will not use the `$env:Path` environment variable to find the files, and will throw an error if any of the paths do not exist.</span></span> <span data-ttu-id="d20bf-114">不允許相對路徑。</span><span class="sxs-lookup"><span data-stu-id="d20bf-114">Relative paths are not allowed.</span></span> |
|<span data-ttu-id="d20bf-115">認證</span><span class="sxs-lookup"><span data-stu-id="d20bf-115">Credential</span></span> |<span data-ttu-id="d20bf-116">表示啟動處理程序的認證。</span><span class="sxs-lookup"><span data-stu-id="d20bf-116">Indicates the credentials for starting the process.</span></span> |
|<span data-ttu-id="d20bf-117">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="d20bf-117">StandardErrorPath</span></span> |<span data-ttu-id="d20bf-118">處理程序要寫入標準錯誤的路徑。</span><span class="sxs-lookup"><span data-stu-id="d20bf-118">The path to which the processes write standard error.</span></span> <span data-ttu-id="d20bf-119">此處的所有檔案都會被覆寫。</span><span class="sxs-lookup"><span data-stu-id="d20bf-119">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="d20bf-120">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="d20bf-120">StandardInputPath</span></span> |<span data-ttu-id="d20bf-121">處理程序從中接收標準輸入的資料流。</span><span class="sxs-lookup"><span data-stu-id="d20bf-121">The stream from which the process receives standard input.</span></span> |
|<span data-ttu-id="d20bf-122">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="d20bf-122">StandardOutputPath</span></span> |<span data-ttu-id="d20bf-123">處理程序要寫入標準輸出的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="d20bf-123">The path of the file to which the processes write standard output.</span></span> <span data-ttu-id="d20bf-124">此處的所有檔案都會被覆寫。</span><span class="sxs-lookup"><span data-stu-id="d20bf-124">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="d20bf-125">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="d20bf-125">WorkingDirectory</span></span> |<span data-ttu-id="d20bf-126">用為處理程序目前工作目錄的位置。</span><span class="sxs-lookup"><span data-stu-id="d20bf-126">The location used as the current working directory for the processes.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="d20bf-127">通用屬性</span><span class="sxs-lookup"><span data-stu-id="d20bf-127">Common properties</span></span>

|<span data-ttu-id="d20bf-128">屬性</span><span class="sxs-lookup"><span data-stu-id="d20bf-128">Property</span></span> |<span data-ttu-id="d20bf-129">描述</span><span class="sxs-lookup"><span data-stu-id="d20bf-129">Description</span></span> |
|---|---|
|<span data-ttu-id="d20bf-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="d20bf-130">DependsOn</span></span> |<span data-ttu-id="d20bf-131">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="d20bf-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="d20bf-132">例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="d20bf-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="d20bf-133">Ensure</span><span class="sxs-lookup"><span data-stu-id="d20bf-133">Ensure</span></span> |<span data-ttu-id="d20bf-134">指定處理程序是否存在。</span><span class="sxs-lookup"><span data-stu-id="d20bf-134">Specifies whether the processes exists.</span></span> <span data-ttu-id="d20bf-135">將此屬性設定為 **Present** 以確保處理程序存在。</span><span class="sxs-lookup"><span data-stu-id="d20bf-135">Set this property to **Present** to ensure that the process exists.</span></span> <span data-ttu-id="d20bf-136">否則，請設定為 **Absent** 。</span><span class="sxs-lookup"><span data-stu-id="d20bf-136">Otherwise, set it to **Absent** .</span></span> <span data-ttu-id="d20bf-137">預設值為 **Present** 。</span><span class="sxs-lookup"><span data-stu-id="d20bf-137">The default value is **Present** .</span></span> |
|<span data-ttu-id="d20bf-138">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="d20bf-138">PsDscRunAsCredential</span></span> |<span data-ttu-id="d20bf-139">設定用於執行整個資源的認證。</span><span class="sxs-lookup"><span data-stu-id="d20bf-139">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="d20bf-140">已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="d20bf-140">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="d20bf-141">如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="d20bf-141">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>
