---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "DSC WindowsProcess 資源"
ms.openlocfilehash: ec77209637d574a0e530f4cce283e1ad98701cdb
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="5b287-103">DSC WindowsProcess 資源</span><span class="sxs-lookup"><span data-stu-id="5b287-103">DSC WindowsProcess Resource</span></span>

> <span data-ttu-id="5b287-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="5b287-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="5b287-105">Windows PowerShell 預期狀態設定 (DSC) 的 **WindowsProcess** 資源提供了在目標節點設定程序的機制。</span><span class="sxs-lookup"><span data-stu-id="5b287-105">The **WindowsProcess** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="5b287-106">語法</span><span class="sxs-lookup"><span data-stu-id="5b287-106">Syntax</span></span>

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ DependsOn = [string[]] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="5b287-107">Properties</span><span class="sxs-lookup"><span data-stu-id="5b287-107">Properties</span></span>
|  <span data-ttu-id="5b287-108">屬性</span><span class="sxs-lookup"><span data-stu-id="5b287-108">Property</span></span>  |  <span data-ttu-id="5b287-109">描述</span><span class="sxs-lookup"><span data-stu-id="5b287-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="5b287-110">引數</span><span class="sxs-lookup"><span data-stu-id="5b287-110">Arguments</span></span>| <span data-ttu-id="5b287-111">表示要保持原狀傳遞至處理程序的引數字串。</span><span class="sxs-lookup"><span data-stu-id="5b287-111">Indicates a string of arguments to pass to the process as-is.</span></span> <span data-ttu-id="5b287-112">如果需要傳遞數個引數，請將它們都放在這個字串裡。</span><span class="sxs-lookup"><span data-stu-id="5b287-112">If you need to pass several arguments, put them all in this string.</span></span>| 
| <span data-ttu-id="5b287-113">路徑</span><span class="sxs-lookup"><span data-stu-id="5b287-113">Path</span></span>| <span data-ttu-id="5b287-114">處理程序可執行檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="5b287-114">The path to the process executable.</span></span> <span data-ttu-id="5b287-115">如果這是可執行檔的名稱 (不是完整路徑)，則 DSC 資源會搜尋環境 **Path** 變數 (`$env:Path`) 來尋找可執行檔。</span><span class="sxs-lookup"><span data-stu-id="5b287-115">If this the file name of the executable (not the fully qualified path), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the executable file.</span></span> <span data-ttu-id="5b287-116">如果這個屬性的值是完整路徑，DSC 不會使用 **Path** 環境變數尋找檔案，但若路徑不存在則會擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="5b287-116">If the value of this property is a fully qualified path, DSC will not use the **Path** environment variable to find the file, and will throw an error if the path does not exist.</span></span> <span data-ttu-id="5b287-117">不允許相對路徑。</span><span class="sxs-lookup"><span data-stu-id="5b287-117">Relative paths are not allowed.</span></span>| 
| <span data-ttu-id="5b287-118">認證</span><span class="sxs-lookup"><span data-stu-id="5b287-118">Credential</span></span>| <span data-ttu-id="5b287-119">表示啟動處理程序的認證。</span><span class="sxs-lookup"><span data-stu-id="5b287-119">Indicates the credentials for starting the process.</span></span>| 
| <span data-ttu-id="5b287-120">Ensure</span><span class="sxs-lookup"><span data-stu-id="5b287-120">Ensure</span></span>| <span data-ttu-id="5b287-121">表示處理程序是否存在。</span><span class="sxs-lookup"><span data-stu-id="5b287-121">Indicates if the process exists.</span></span> <span data-ttu-id="5b287-122">將這個屬性設定為 "Present" 以確保處理程序存在。</span><span class="sxs-lookup"><span data-stu-id="5b287-122">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="5b287-123">否則，請設定為 "Absent"。</span><span class="sxs-lookup"><span data-stu-id="5b287-123">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="5b287-124">預設值是 "Present"。</span><span class="sxs-lookup"><span data-stu-id="5b287-124">The default is "Present".</span></span>| 
| <span data-ttu-id="5b287-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="5b287-125">DependsOn</span></span> | <span data-ttu-id="5b287-126">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="5b287-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="5b287-127">例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 __ResourceName__，而它的類型是 __ResourceType__，則使用這個屬性的語法就是 \`DependsOn = "[ResourceType]ResourceName"\`\`。</span><span class="sxs-lookup"><span data-stu-id="5b287-127">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\` .</span></span>| 
| <span data-ttu-id="5b287-128">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="5b287-128">StandardErrorPath</span></span>| <span data-ttu-id="5b287-129">表示寫入標準錯誤的目錄路徑。</span><span class="sxs-lookup"><span data-stu-id="5b287-129">Indicates the directory path to write the standard error.</span></span> <span data-ttu-id="5b287-130">此處的所有檔案都會被覆寫。</span><span class="sxs-lookup"><span data-stu-id="5b287-130">Any existing file there will be overwritten.</span></span>| 
| <span data-ttu-id="5b287-131">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="5b287-131">StandardInputPath</span></span>| <span data-ttu-id="5b287-132">表示標準輸入的位置。</span><span class="sxs-lookup"><span data-stu-id="5b287-132">Indicates the standard input location.</span></span>| 
| <span data-ttu-id="5b287-133">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="5b287-133">StandardOutputPath</span></span>| <span data-ttu-id="5b287-134">表示寫入標準輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="5b287-134">Indicates the location to write the standard output.</span></span> <span data-ttu-id="5b287-135">此處的所有檔案都會被覆寫。</span><span class="sxs-lookup"><span data-stu-id="5b287-135">Any existing file there will be overwritten.</span></span>| 
| <span data-ttu-id="5b287-136">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="5b287-136">WorkingDirectory</span></span>| <span data-ttu-id="5b287-137">表示會用為處理程序目前工作目錄的位置。</span><span class="sxs-lookup"><span data-stu-id="5b287-137">Indicates the location that will be used as the current working directory for the process.</span></span>| 

