---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 6/24/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-recyclebin?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-RecycleBin
ms.openlocfilehash: 9314aaf7c444f9a1159b301135d4130737daa439
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204063"
---
# <span data-ttu-id="7d226-103">Clear-RecycleBin</span><span class="sxs-lookup"><span data-stu-id="7d226-103">Clear-RecycleBin</span></span>

## <span data-ttu-id="7d226-104">概要</span><span class="sxs-lookup"><span data-stu-id="7d226-104">SYNOPSIS</span></span>
<span data-ttu-id="7d226-105">清除回收站的內容。</span><span class="sxs-lookup"><span data-stu-id="7d226-105">Clears the contents of a recycle bin.</span></span>

## <span data-ttu-id="7d226-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7d226-106">SYNTAX</span></span>

### <span data-ttu-id="7d226-107">全部</span><span class="sxs-lookup"><span data-stu-id="7d226-107">All</span></span>

```
Clear-RecycleBin [[-DriveLetter] <String[]>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="7d226-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="7d226-108">DESCRIPTION</span></span>

<span data-ttu-id="7d226-109">`Clear-RecycleBin`Cmdlet 會刪除電腦回收站的內容。</span><span class="sxs-lookup"><span data-stu-id="7d226-109">The `Clear-RecycleBin` cmdlet deletes the content of a computer's recycle bin.</span></span> <span data-ttu-id="7d226-110">這個動作就像使用 Windows **Empty 資源回收筒** 一樣。</span><span class="sxs-lookup"><span data-stu-id="7d226-110">This action is like using Windows **Empty Recycle Bin** .</span></span>

## <span data-ttu-id="7d226-111">範例</span><span class="sxs-lookup"><span data-stu-id="7d226-111">EXAMPLES</span></span>

### <span data-ttu-id="7d226-112">1：清除所有回收站</span><span class="sxs-lookup"><span data-stu-id="7d226-112">1: Clear all recycle bins</span></span>

<span data-ttu-id="7d226-113">在此範例中，會清除所有本機電腦的回收站。</span><span class="sxs-lookup"><span data-stu-id="7d226-113">In this example, all the local computer's recycle bins are cleared.</span></span>

```powershell
Clear-RecycleBin
```

```Output
Confirm
Are you sure you want to perform this action?
Performing the operation "Clear-RecycleBin" on target "All of the contents of the Recycle Bin".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="7d226-114">`Clear-RecycleBin` 提示使用者進行確認，以清除本機電腦上的所有回收站。</span><span class="sxs-lookup"><span data-stu-id="7d226-114">`Clear-RecycleBin` prompts the user for confirmation to clear all recycle bins on the local computer.</span></span>

### <span data-ttu-id="7d226-115">2：清除指定的回收站</span><span class="sxs-lookup"><span data-stu-id="7d226-115">2: Clear a specified recycle bin</span></span>

<span data-ttu-id="7d226-116">此範例會清除指定磁碟機號的回收站。</span><span class="sxs-lookup"><span data-stu-id="7d226-116">This example clears the recycle bin for a specified drive letter.</span></span>

```powershell
Clear-RecycleBin -DriveLetter C
```

<span data-ttu-id="7d226-117">`Clear-RecycleBin` 使用 **r** 參數來指定 **C** 磁片區上的回收站。</span><span class="sxs-lookup"><span data-stu-id="7d226-117">`Clear-RecycleBin` uses the **DriveLetter** parameter to specify the recycle bin on the **C** volume.</span></span> <span data-ttu-id="7d226-118">系統會提示使用者進行確認，以執行命令。</span><span class="sxs-lookup"><span data-stu-id="7d226-118">The user is prompted for confirmation to run the command.</span></span>

### <span data-ttu-id="7d226-119">3：清除所有回收站但不確認</span><span class="sxs-lookup"><span data-stu-id="7d226-119">3: Clear all recycle bins without confirmation</span></span>

<span data-ttu-id="7d226-120">此範例不會提示您確認是否要清除本機電腦的回收站。</span><span class="sxs-lookup"><span data-stu-id="7d226-120">This example doesn't prompt for confirmation to clear the local computer's recycle bins.</span></span>

```powershell
Clear-RecycleBin -Force
```

<span data-ttu-id="7d226-121">`Clear-RecycleBin` 使用 **Force** 參數，且不會提示使用者進行確認，以清除本機電腦上的所有回收站。</span><span class="sxs-lookup"><span data-stu-id="7d226-121">`Clear-RecycleBin` uses the **Force** parameter and doesn't prompt the user for confirmation to clear all recycle bins on the local computer.</span></span>

<span data-ttu-id="7d226-122">替代方法是將取代 `-Force` 為 `-Confirm:$false` 。</span><span class="sxs-lookup"><span data-stu-id="7d226-122">An alternative is to replace `-Force` with `-Confirm:$false`.</span></span>

## <span data-ttu-id="7d226-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7d226-123">PARAMETERS</span></span>

### <span data-ttu-id="7d226-124">-R</span><span class="sxs-lookup"><span data-stu-id="7d226-124">-DriveLetter</span></span>

<span data-ttu-id="7d226-125">指定要清除單一磁碟機號或磁碟機號陣列的回收站。</span><span class="sxs-lookup"><span data-stu-id="7d226-125">Specifies the recycle bin to clear for a single drive letter or an array of drive letters.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="7d226-126">-Force</span><span class="sxs-lookup"><span data-stu-id="7d226-126">-Force</span></span>

<span data-ttu-id="7d226-127">指定不提示使用者確認清除回收站。</span><span class="sxs-lookup"><span data-stu-id="7d226-127">Specifies that the user isn't prompted for confirmation to clear a recycle bin.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7d226-128">-Confirm</span><span class="sxs-lookup"><span data-stu-id="7d226-128">-Confirm</span></span>

<span data-ttu-id="7d226-129">執行 Cmdlet 之前，提示使用者確認。</span><span class="sxs-lookup"><span data-stu-id="7d226-129">Prompts for user confirmation before running the cmdlet.</span></span> <span data-ttu-id="7d226-130">即使未指定 **Confirm** 參數，仍會提示使用者進行確認。</span><span class="sxs-lookup"><span data-stu-id="7d226-130">The user is prompted for confirmation even if the **Confirm** parameter isn't specified.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7d226-131">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="7d226-131">-WhatIf</span></span>

<span data-ttu-id="7d226-132">顯示執行時所發生 `Clear-RecycleBin` 的情況。</span><span class="sxs-lookup"><span data-stu-id="7d226-132">Shows what would happen if `Clear-RecycleBin` runs.</span></span> <span data-ttu-id="7d226-133">不會執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7d226-133">The cmdlet isn't run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7d226-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7d226-134">CommonParameters</span></span>

<span data-ttu-id="7d226-135">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="7d226-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7d226-136">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="7d226-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7d226-137">輸入</span><span class="sxs-lookup"><span data-stu-id="7d226-137">INPUTS</span></span>

## <span data-ttu-id="7d226-138">輸出</span><span class="sxs-lookup"><span data-stu-id="7d226-138">OUTPUTS</span></span>

### <span data-ttu-id="7d226-139">無</span><span class="sxs-lookup"><span data-stu-id="7d226-139">None</span></span>

## <span data-ttu-id="7d226-140">注意</span><span class="sxs-lookup"><span data-stu-id="7d226-140">NOTES</span></span>

## <span data-ttu-id="7d226-141">相關連結</span><span class="sxs-lookup"><span data-stu-id="7d226-141">RELATED LINKS</span></span>
