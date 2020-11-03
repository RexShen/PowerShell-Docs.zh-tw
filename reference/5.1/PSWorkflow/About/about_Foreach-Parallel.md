---
description: 描述 `ForEach -Parallel` Windows PowerShell 工作流程中的語言結構。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/10/2019
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_foreach-parallel?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Foreach 平行
ms.openlocfilehash: 1012b45396b65d424dacac067c2af8d3b6823f92
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207240"
---
# <a name="about-foreach-parallel"></a><span data-ttu-id="ba6d1-104">關於 Foreach-Parallel</span><span class="sxs-lookup"><span data-stu-id="ba6d1-104">About Foreach-Parallel</span></span>

## <a name="short-description"></a><span data-ttu-id="ba6d1-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="ba6d1-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="ba6d1-106">描述 `ForEach -Parallel` Windows PowerShell 工作流程中的語言結構。</span><span class="sxs-lookup"><span data-stu-id="ba6d1-106">Describes the `ForEach -Parallel` language construct in Windows PowerShell Workflow.</span></span>

## <a name="long-description"></a><span data-ttu-id="ba6d1-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="ba6d1-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="ba6d1-108">關鍵字的 **Parallel** 參數會 `ForEach` 針對所 `ForEach` 指定集合中的每個專案執行一次腳本區塊中的命令。</span><span class="sxs-lookup"><span data-stu-id="ba6d1-108">The **Parallel** parameter of the `ForEach` keyword runs the commands in a `ForEach` script block once for each item in a specified collection.</span></span>

<span data-ttu-id="ba6d1-109">集合中的專案（例如磁片集合中的磁片）會以平行方式處理。</span><span class="sxs-lookup"><span data-stu-id="ba6d1-109">The items in the collection, such as a disk in a collection of disks, are processed in parallel.</span></span> <span data-ttu-id="ba6d1-110">腳本區塊中的命令會在集合中的每個專案上依序執行。</span><span class="sxs-lookup"><span data-stu-id="ba6d1-110">The commands in the script block run sequentially on each item in the collection.</span></span>

<span data-ttu-id="ba6d1-111">`ForEach -Parallel` 只有在 Windows PowerShell 工作流程中才有效。</span><span class="sxs-lookup"><span data-stu-id="ba6d1-111">`ForEach -Parallel` is valid only in a Windows PowerShell Workflow.</span></span>

### <a name="syntax"></a><span data-ttu-id="ba6d1-112">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ba6d1-112">SYNTAX</span></span>

```
ForEach -Parallel ($<item> in $<collection>)
{
    [<Activity1>]
    [<Activity2>]
    ...
}
```

### <a name="detailed-description"></a><span data-ttu-id="ba6d1-113">詳細描述</span><span class="sxs-lookup"><span data-stu-id="ba6d1-113">DETAILED DESCRIPTION</span></span>

<span data-ttu-id="ba6d1-114">就像 Windows PowerShell 中的 ForEach 語句一樣，包含集合的變數 `$<collection>` 必須在語句之前定義 `ForEach -Parallel` ，但代表目前專案的變數 `$<item>` 是在語句中定義 `ForEach -Parallel` 。</span><span class="sxs-lookup"><span data-stu-id="ba6d1-114">Like the ForEach statement in Windows PowerShell, the variable that contains collection `$<collection>` must be defined before the `ForEach -Parallel` statement, but the variable that represents the current item `$<item>` is defined in the `ForEach -Parallel` statement.</span></span>

<span data-ttu-id="ba6d1-115">此 `ForEach -Parallel` 結構與 `ForEach` 關鍵字和 **Parallel** 參數不同。</span><span class="sxs-lookup"><span data-stu-id="ba6d1-115">The `ForEach -Parallel` construct is different from the `ForEach` keyword and the **Parallel** parameter.</span></span> <span data-ttu-id="ba6d1-116">關鍵字會依 `ForEach` 序處理集合中的專案。</span><span class="sxs-lookup"><span data-stu-id="ba6d1-116">The `ForEach` keyword processes the items in the collection in sequence.</span></span> <span data-ttu-id="ba6d1-117">**Parallel** 參數會以平行方式在腳本區塊中執行命令。</span><span class="sxs-lookup"><span data-stu-id="ba6d1-117">The **Parallel** parameter runs commands in a script block in parallel.</span></span> <span data-ttu-id="ba6d1-118">您可以將平行腳本區塊放在 `ForEach -Parallel` 腳本區塊中。</span><span class="sxs-lookup"><span data-stu-id="ba6d1-118">You can enclose a Parallel script block in a `ForEach -Parallel` script block.</span></span>

<span data-ttu-id="ba6d1-119">工作流程中的目的電腦（例如 **PSComputerName** 工作流程一般參數所指定的電腦）一律會以平行方式處理。</span><span class="sxs-lookup"><span data-stu-id="ba6d1-119">The target computers in a workflow, such as those specified by the **PSComputerName** workflow common parameter, are always processed in parallel.</span></span>
<span data-ttu-id="ba6d1-120">您不需要為 `ForEach -Parallel` 此用途指定關鍵字。</span><span class="sxs-lookup"><span data-stu-id="ba6d1-120">You do not need to specify the `ForEach -Parallel` keyword for this purpose.</span></span>

### <a name="examples"></a><span data-ttu-id="ba6d1-121">範例</span><span class="sxs-lookup"><span data-stu-id="ba6d1-121">EXAMPLES</span></span>

<span data-ttu-id="ba6d1-122">下列工作流程包含 `ForEach -Parallel` 處理活動所取得之磁片的語句 `Get-Disk` 。</span><span class="sxs-lookup"><span data-stu-id="ba6d1-122">The following workflow contains a `ForEach -Parallel` statement that processes the disks that the `Get-Disk` activity gets.</span></span> <span data-ttu-id="ba6d1-123">腳本區塊中的命令 `ForEach -Parallel` 會依序執行，但它們會以平行方式在磁片上執行。</span><span class="sxs-lookup"><span data-stu-id="ba6d1-123">The commands in the `ForEach -Parallel` script block run sequentially, but they run on the disks in parallel.</span></span> <span data-ttu-id="ba6d1-124">磁片可能會以任何順序同時進行處理。</span><span class="sxs-lookup"><span data-stu-id="ba6d1-124">The disks might be processed concurrently and in any order.</span></span>

```powershell
workflow Test-Workflow
{
    $Disks = Get-Disk

    # The disks are processed in parallel.
    ForEach -Parallel ($Disk in $Disks)
    {
        # The commands run sequentially on each disk.
        $DiskPath = $Disk.Path
        $Disk | Initialize-Disk
        Set-Disk -Path $DiskPath
    }
}

workflow Test-Workflow
{
    #Run commands in parallel.
    Parallel
    {
        Get-Process
        Get-Service
    }

   $Disks = Get-Disk

   # The disks are processed in parallel.
   ForEach -Parallel ($Disk in $Disks)
   {
       # The commands run in parallel on each disk.
       Parallel
       {
           Initialize-Disk
           InlineScript {.\Get-DiskInventory}
       }
   }
}
```

## <a name="see-also"></a><span data-ttu-id="ba6d1-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba6d1-125">SEE ALSO</span></span>

[<span data-ttu-id="ba6d1-126">Writing a Script Workflow</span><span class="sxs-lookup"><span data-stu-id="ba6d1-126">Writing a Script Workflow</span></span>](/previous-versions/powershell/scripting/developer/workflow/creating-a-workflow-by-using-a-windows-powershell-script)

[<span data-ttu-id="ba6d1-127">about_ForEach</span><span class="sxs-lookup"><span data-stu-id="ba6d1-127">about_ForEach</span></span>](../../Microsoft.PowerShell.Core/About/about_ForEach.md)

[<span data-ttu-id="ba6d1-128">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="ba6d1-128">about_Language_Keywords</span></span>](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[<span data-ttu-id="ba6d1-129">about_Parallel</span><span class="sxs-lookup"><span data-stu-id="ba6d1-129">about_Parallel</span></span>](about_Parallel.md)

[<span data-ttu-id="ba6d1-130">about_Workflows</span><span class="sxs-lookup"><span data-stu-id="ba6d1-130">about_Workflows</span></span>](about_Workflows.md)
