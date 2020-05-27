---
ms.date: 09/20/2019
keywords: dsc,powershell,設定,安裝
title: DSC WindowsProcess 資源
ms.openlocfilehash: 5c30af98bf7b99551396082630605c566a866697
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560486"
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="49882-103">DSC WindowsProcess 資源</span><span class="sxs-lookup"><span data-stu-id="49882-103">DSC WindowsProcess Resource</span></span>

> <span data-ttu-id="49882-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="49882-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="49882-105">Windows PowerShell 預期狀態設定 (DSC) 的 **WindowsProcess** 資源提供了在目標節點設定程序的機制。</span><span class="sxs-lookup"><span data-stu-id="49882-105">The **WindowsProcess** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="49882-106">語法</span><span class="sxs-lookup"><span data-stu-id="49882-106">Syntax</span></span>

```Syntax
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="49882-107">屬性</span><span class="sxs-lookup"><span data-stu-id="49882-107">Properties</span></span>

|<span data-ttu-id="49882-108">屬性</span><span class="sxs-lookup"><span data-stu-id="49882-108">Property</span></span> |<span data-ttu-id="49882-109">描述</span><span class="sxs-lookup"><span data-stu-id="49882-109">Description</span></span> |
|---|---|
|<span data-ttu-id="49882-110">引數</span><span class="sxs-lookup"><span data-stu-id="49882-110">Arguments</span></span> |<span data-ttu-id="49882-111">表示要保持原狀傳遞至處理程序的引數字串。</span><span class="sxs-lookup"><span data-stu-id="49882-111">Indicates a string of arguments to pass to the process as-is.</span></span> <span data-ttu-id="49882-112">如果需要傳遞數個引數，請將它們都放在這個字串裡。</span><span class="sxs-lookup"><span data-stu-id="49882-112">If you need to pass several arguments, put them all in this string.</span></span> |
|<span data-ttu-id="49882-113">Path</span><span class="sxs-lookup"><span data-stu-id="49882-113">Path</span></span> |<span data-ttu-id="49882-114">處理程序可執行檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="49882-114">The path to the process executable.</span></span> <span data-ttu-id="49882-115">如果這是可執行檔的檔案名稱 (不是完整路徑)，則 DSC 資源會搜尋環境 `$env:Path` 變數來尋找可執行檔。</span><span class="sxs-lookup"><span data-stu-id="49882-115">If this the file name of the executable (not the fully qualified path), the DSC resource will search the environment `$env:Path` variable to find the executable file.</span></span> <span data-ttu-id="49882-116">如果這個屬性的值是完整路徑，DSC 將不會使用 `$env:Path` 變數來尋找檔案，但若路徑不存在則會擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="49882-116">If the value of this property is a fully qualified path, DSC will not use the `$env:Path` variable to find the file, and will throw an error if the path does not exist.</span></span> <span data-ttu-id="49882-117">不允許相對路徑。</span><span class="sxs-lookup"><span data-stu-id="49882-117">Relative paths are not allowed.</span></span> |
|<span data-ttu-id="49882-118">認證</span><span class="sxs-lookup"><span data-stu-id="49882-118">Credential</span></span> |<span data-ttu-id="49882-119">表示啟動處理程序的認證。</span><span class="sxs-lookup"><span data-stu-id="49882-119">Indicates the credentials for starting the process.</span></span> |
|<span data-ttu-id="49882-120">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="49882-120">StandardErrorPath</span></span> |<span data-ttu-id="49882-121">表示寫入標準錯誤的目錄路徑。</span><span class="sxs-lookup"><span data-stu-id="49882-121">Indicates the directory path to write the standard error.</span></span> <span data-ttu-id="49882-122">此處的所有檔案都會被覆寫。</span><span class="sxs-lookup"><span data-stu-id="49882-122">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="49882-123">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="49882-123">StandardInputPath</span></span> |<span data-ttu-id="49882-124">表示標準輸入的位置。</span><span class="sxs-lookup"><span data-stu-id="49882-124">Indicates the standard input location.</span></span> |
|<span data-ttu-id="49882-125">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="49882-125">StandardOutputPath</span></span> |<span data-ttu-id="49882-126">表示寫入標準輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="49882-126">Indicates the location to write the standard output.</span></span> <span data-ttu-id="49882-127">此處的所有檔案都會被覆寫。</span><span class="sxs-lookup"><span data-stu-id="49882-127">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="49882-128">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="49882-128">WorkingDirectory</span></span> |<span data-ttu-id="49882-129">表示會用為處理程序目前工作目錄的位置。</span><span class="sxs-lookup"><span data-stu-id="49882-129">Indicates the location that will be used as the current working directory for the process.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="49882-130">通用屬性</span><span class="sxs-lookup"><span data-stu-id="49882-130">Common properties</span></span>

|<span data-ttu-id="49882-131">屬性</span><span class="sxs-lookup"><span data-stu-id="49882-131">Property</span></span> |<span data-ttu-id="49882-132">描述</span><span class="sxs-lookup"><span data-stu-id="49882-132">Description</span></span> |
|---|---|
|<span data-ttu-id="49882-133">DependsOn</span><span class="sxs-lookup"><span data-stu-id="49882-133">DependsOn</span></span> |<span data-ttu-id="49882-134">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="49882-134">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="49882-135">例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="49882-135">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="49882-136">Ensure</span><span class="sxs-lookup"><span data-stu-id="49882-136">Ensure</span></span> |<span data-ttu-id="49882-137">表示處理程序是否存在。</span><span class="sxs-lookup"><span data-stu-id="49882-137">Indicates if the process exists.</span></span> <span data-ttu-id="49882-138">將此屬性設定為 **Present** 以確保處理程序存在。</span><span class="sxs-lookup"><span data-stu-id="49882-138">Set this property to **Present** to ensure that the process exists.</span></span> <span data-ttu-id="49882-139">否則，請設定為 **Absent**。</span><span class="sxs-lookup"><span data-stu-id="49882-139">Otherwise, set it to **Absent**.</span></span> <span data-ttu-id="49882-140">預設值為 **Present**。</span><span class="sxs-lookup"><span data-stu-id="49882-140">The default value is **Present**.</span></span> |
|<span data-ttu-id="49882-141">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="49882-141">PsDscRunAsCredential</span></span> |<span data-ttu-id="49882-142">設定用於執行整個資源的認證。</span><span class="sxs-lookup"><span data-stu-id="49882-142">Sets the credential for running the entire resource as.</span></span> |
