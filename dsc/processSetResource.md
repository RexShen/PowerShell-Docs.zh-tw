---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: DSC ProcessSet 資源
ms.openlocfilehash: 33000786a9e17e11168b5e08c3bcfcacf3af2611
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268009"
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="e8f23-103">DSC WindowsProcess 資源</span><span class="sxs-lookup"><span data-stu-id="e8f23-103">DSC WindowsProcess Resource</span></span>

<span data-ttu-id="e8f23-104">_適用於：Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="e8f23-104">_Applies To: Windows PowerShell 5.0_</span></span>

<span data-ttu-id="e8f23-105">Windows PowerShell 預期狀態設定 (DSC) 的 **ProcessSet** 資源提供了在目標節點設定程序的機制。</span><span class="sxs-lookup"><span data-stu-id="e8f23-105">The **ProcessSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span> <span data-ttu-id="e8f23-106">此資源是為 `GroupName` 參數中指定的每個群組呼叫 [WindowsProcess 資源](windowsProcessResource.md)的[複合資源](authoringResourceComposite.md)。</span><span class="sxs-lookup"><span data-stu-id="e8f23-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [WindowsProcess resource](windowsProcessResource.md) for each group specified in the `GroupName` parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="e8f23-107">語法</span><span class="sxs-lookup"><span data-stu-id="e8f23-107">Syntax</span></span>

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="e8f23-108">Properties</span><span class="sxs-lookup"><span data-stu-id="e8f23-108">Properties</span></span>

| <span data-ttu-id="e8f23-109">屬性</span><span class="sxs-lookup"><span data-stu-id="e8f23-109">Property</span></span> | <span data-ttu-id="e8f23-110">描述</span><span class="sxs-lookup"><span data-stu-id="e8f23-110">Description</span></span> |
| --- | --- |
| <span data-ttu-id="e8f23-111">引數</span><span class="sxs-lookup"><span data-stu-id="e8f23-111">Arguments</span></span>| <span data-ttu-id="e8f23-112">內含的引數要保持原狀傳遞至處理程序的字串。</span><span class="sxs-lookup"><span data-stu-id="e8f23-112">A string that contains arguments to pass to the process as-is.</span></span> <span data-ttu-id="e8f23-113">如果需要傳遞數個引數，請將它們都放在這個字串裡。</span><span class="sxs-lookup"><span data-stu-id="e8f23-113">If you need to pass several arguments, put them all in this string.</span></span>|
| <span data-ttu-id="e8f23-114">路徑</span><span class="sxs-lookup"><span data-stu-id="e8f23-114">Path</span></span>| <span data-ttu-id="e8f23-115">處理程序可執行檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="e8f23-115">The paths to the process executables.</span></span> <span data-ttu-id="e8f23-116">如果這些是可執行檔的名稱 (不是完整路徑)，則 DSC 資源會搜尋環境 **Path** 變數 (`$env:Path`) 來尋找檔案。</span><span class="sxs-lookup"><span data-stu-id="e8f23-116">If these are the names of the executable files (not fully qualified paths), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the files.</span></span> <span data-ttu-id="e8f23-117">如果這個屬性的值是完整路徑，DSC 不會使用 **Path** 環境變數尋找檔案，但若任一路徑不存在則會擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="e8f23-117">If the values of this property are fully qualified paths, DSC will not use the **Path** environment variable to find the files, and will throw an error if any of the paths do not exist.</span></span> <span data-ttu-id="e8f23-118">不允許相對路徑。</span><span class="sxs-lookup"><span data-stu-id="e8f23-118">Relative paths are not allowed.</span></span>|
| <span data-ttu-id="e8f23-119">認證</span><span class="sxs-lookup"><span data-stu-id="e8f23-119">Credential</span></span>| <span data-ttu-id="e8f23-120">表示啟動處理程序的認證。</span><span class="sxs-lookup"><span data-stu-id="e8f23-120">Indicates the credentials for starting the process.</span></span>|
| <span data-ttu-id="e8f23-121">Ensure</span><span class="sxs-lookup"><span data-stu-id="e8f23-121">Ensure</span></span>| <span data-ttu-id="e8f23-122">指定處理程序是否存在。</span><span class="sxs-lookup"><span data-stu-id="e8f23-122">Specifies whether the processes exists.</span></span> <span data-ttu-id="e8f23-123">將這個屬性設定為 "Present" 以確保處理程序存在。</span><span class="sxs-lookup"><span data-stu-id="e8f23-123">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="e8f23-124">否則，請設定為 "Absent"。</span><span class="sxs-lookup"><span data-stu-id="e8f23-124">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="e8f23-125">預設值是 "Present"。</span><span class="sxs-lookup"><span data-stu-id="e8f23-125">The default is "Present".</span></span>|
| <span data-ttu-id="e8f23-126">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="e8f23-126">StandardErrorPath</span></span>| <span data-ttu-id="e8f23-127">處理程序要寫入標準錯誤的路徑。</span><span class="sxs-lookup"><span data-stu-id="e8f23-127">The path to which the processes write standard error.</span></span> <span data-ttu-id="e8f23-128">此處的所有檔案都會被覆寫。</span><span class="sxs-lookup"><span data-stu-id="e8f23-128">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="e8f23-129">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="e8f23-129">StandardInputPath</span></span>| <span data-ttu-id="e8f23-130">處理程序從中接收標準輸入的資料流。</span><span class="sxs-lookup"><span data-stu-id="e8f23-130">The stream from which the process receives standard input.</span></span>|
| <span data-ttu-id="e8f23-131">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="e8f23-131">StandardOutputPath</span></span>| <span data-ttu-id="e8f23-132">處理程序要寫入標準輸出的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="e8f23-132">The path of the file to which the processes write standard output.</span></span> <span data-ttu-id="e8f23-133">此處的所有檔案都會被覆寫。</span><span class="sxs-lookup"><span data-stu-id="e8f23-133">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="e8f23-134">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="e8f23-134">WorkingDirectory</span></span>| <span data-ttu-id="e8f23-135">用為處理程序目前工作目錄的位置。</span><span class="sxs-lookup"><span data-stu-id="e8f23-135">The location used as the current working directory for the processes.</span></span>|
| <span data-ttu-id="e8f23-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="e8f23-136">DependsOn</span></span> | <span data-ttu-id="e8f23-137">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="e8f23-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="e8f23-138">例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 **ResourceName**，而它的類型是 **_ResourceType**，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="e8f23-138">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **_ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"` .</span></span>|