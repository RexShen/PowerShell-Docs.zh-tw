---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-recyclebin?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-RecycleBin
ms.openlocfilehash: 85e4ac857135a6df8215dcfe415057dd8aacde86
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201480"
---
# <span data-ttu-id="d5cc3-103">Clear-RecycleBin</span><span class="sxs-lookup"><span data-stu-id="d5cc3-103">Clear-RecycleBin</span></span>

## <span data-ttu-id="d5cc3-104">概要</span><span class="sxs-lookup"><span data-stu-id="d5cc3-104">SYNOPSIS</span></span>
<span data-ttu-id="d5cc3-105">清除回收站的內容。</span><span class="sxs-lookup"><span data-stu-id="d5cc3-105">Clears the contents of a recycle bin.</span></span>

## <span data-ttu-id="d5cc3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d5cc3-106">SYNTAX</span></span>

### <span data-ttu-id="d5cc3-107">全部</span><span class="sxs-lookup"><span data-stu-id="d5cc3-107">All</span></span>

```
Clear-RecycleBin [[-DriveLetter] <String[]>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="d5cc3-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="d5cc3-108">DESCRIPTION</span></span>

<span data-ttu-id="d5cc3-109">`Clear-RecycleBin`Cmdlet 會刪除電腦回收站的內容。</span><span class="sxs-lookup"><span data-stu-id="d5cc3-109">The `Clear-RecycleBin` cmdlet deletes the content of a computer's recycle bin.</span></span> <span data-ttu-id="d5cc3-110">這個動作就像使用 Windows **Empty 資源回收筒** 一樣。</span><span class="sxs-lookup"><span data-stu-id="d5cc3-110">This action is like using Windows **Empty Recycle Bin** .</span></span>

<span data-ttu-id="d5cc3-111">此 Cmdlet 是在 PowerShell 7 中 readded。</span><span class="sxs-lookup"><span data-stu-id="d5cc3-111">This cmdlet was readded in PowerShell 7.</span></span>

## <span data-ttu-id="d5cc3-112">範例</span><span class="sxs-lookup"><span data-stu-id="d5cc3-112">EXAMPLES</span></span>

### <span data-ttu-id="d5cc3-113">1：清除所有回收站</span><span class="sxs-lookup"><span data-stu-id="d5cc3-113">1: Clear all recycle bins</span></span>

<span data-ttu-id="d5cc3-114">在此範例中，會清除所有本機電腦的回收站。</span><span class="sxs-lookup"><span data-stu-id="d5cc3-114">In this example, all the local computer's recycle bins are cleared.</span></span>

```powershell
Clear-RecycleBin
```

```Output
Confirm
Are you sure you want to perform this action?
Performing the operation "Clear-RecycleBin" on target "All of the contents of the Recycle Bin".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="d5cc3-115">`Clear-RecycleBin` 提示使用者進行確認，以清除本機電腦上的所有回收站。</span><span class="sxs-lookup"><span data-stu-id="d5cc3-115">`Clear-RecycleBin` prompts the user for confirmation to clear all recycle bins on the local computer.</span></span>

### <span data-ttu-id="d5cc3-116">2：清除指定的回收站</span><span class="sxs-lookup"><span data-stu-id="d5cc3-116">2: Clear a specified recycle bin</span></span>

<span data-ttu-id="d5cc3-117">此範例會清除指定磁碟機號的回收站。</span><span class="sxs-lookup"><span data-stu-id="d5cc3-117">This example clears the recycle bin for a specified drive letter.</span></span>

```powershell
Clear-RecycleBin -DriveLetter C
```

<span data-ttu-id="d5cc3-118">`Clear-RecycleBin` 使用 **r** 參數來指定 **C** 磁片區上的回收站。</span><span class="sxs-lookup"><span data-stu-id="d5cc3-118">`Clear-RecycleBin` uses the **DriveLetter** parameter to specify the recycle bin on the **C** volume.</span></span> <span data-ttu-id="d5cc3-119">系統會提示使用者進行確認，以執行命令。</span><span class="sxs-lookup"><span data-stu-id="d5cc3-119">The user is prompted for confirmation to run the command.</span></span>

### <span data-ttu-id="d5cc3-120">3：清除所有回收站但不確認</span><span class="sxs-lookup"><span data-stu-id="d5cc3-120">3: Clear all recycle bins without confirmation</span></span>

<span data-ttu-id="d5cc3-121">此範例不會提示您確認是否要清除本機電腦的回收站。</span><span class="sxs-lookup"><span data-stu-id="d5cc3-121">This example doesn't prompt for confirmation to clear the local computer's recycle bins.</span></span>

```powershell
Clear-RecycleBin -Force
```

<span data-ttu-id="d5cc3-122">`Clear-RecycleBin` 使用 **Force** 參數，且不會提示使用者進行確認，以清除本機電腦上的所有回收站。</span><span class="sxs-lookup"><span data-stu-id="d5cc3-122">`Clear-RecycleBin` uses the **Force** parameter and doesn't prompt the user for confirmation to clear all recycle bins on the local computer.</span></span>

<span data-ttu-id="d5cc3-123">替代方法是將取代 `-Force` 為 `-Confirm:$false` 。</span><span class="sxs-lookup"><span data-stu-id="d5cc3-123">An alternative is to replace `-Force` with `-Confirm:$false`.</span></span>

## <span data-ttu-id="d5cc3-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d5cc3-124">PARAMETERS</span></span>

### <span data-ttu-id="d5cc3-125">-R</span><span class="sxs-lookup"><span data-stu-id="d5cc3-125">-DriveLetter</span></span>

<span data-ttu-id="d5cc3-126">指定要清除單一磁碟機號或磁碟機號陣列的回收站。</span><span class="sxs-lookup"><span data-stu-id="d5cc3-126">Specifies the recycle bin to clear for a single drive letter or an array of drive letters.</span></span>

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

### <span data-ttu-id="d5cc3-127">-Force</span><span class="sxs-lookup"><span data-stu-id="d5cc3-127">-Force</span></span>

<span data-ttu-id="d5cc3-128">指定不提示使用者確認清除回收站。</span><span class="sxs-lookup"><span data-stu-id="d5cc3-128">Specifies that the user isn't prompted for confirmation to clear a recycle bin.</span></span>

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

### <span data-ttu-id="d5cc3-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d5cc3-129">-Confirm</span></span>

<span data-ttu-id="d5cc3-130">執行 Cmdlet 之前，提示使用者確認。</span><span class="sxs-lookup"><span data-stu-id="d5cc3-130">Prompts for user confirmation before running the cmdlet.</span></span> <span data-ttu-id="d5cc3-131">即使未指定 **Confirm** 參數，仍會提示使用者進行確認。</span><span class="sxs-lookup"><span data-stu-id="d5cc3-131">The user is prompted for confirmation even if the **Confirm** parameter isn't specified.</span></span>

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

### <span data-ttu-id="d5cc3-132">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d5cc3-132">-WhatIf</span></span>

<span data-ttu-id="d5cc3-133">顯示執行時所發生 `Clear-RecycleBin` 的情況。</span><span class="sxs-lookup"><span data-stu-id="d5cc3-133">Shows what would happen if `Clear-RecycleBin` runs.</span></span> <span data-ttu-id="d5cc3-134">不會執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d5cc3-134">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="d5cc3-135">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d5cc3-135">CommonParameters</span></span>

<span data-ttu-id="d5cc3-136">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="d5cc3-136">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d5cc3-137">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="d5cc3-137">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d5cc3-138">輸入</span><span class="sxs-lookup"><span data-stu-id="d5cc3-138">INPUTS</span></span>

## <span data-ttu-id="d5cc3-139">輸出</span><span class="sxs-lookup"><span data-stu-id="d5cc3-139">OUTPUTS</span></span>

### <span data-ttu-id="d5cc3-140">無</span><span class="sxs-lookup"><span data-stu-id="d5cc3-140">None</span></span>

## <span data-ttu-id="d5cc3-141">注意</span><span class="sxs-lookup"><span data-stu-id="d5cc3-141">NOTES</span></span>

## <span data-ttu-id="d5cc3-142">相關連結</span><span class="sxs-lookup"><span data-stu-id="d5cc3-142">RELATED LINKS</span></span>