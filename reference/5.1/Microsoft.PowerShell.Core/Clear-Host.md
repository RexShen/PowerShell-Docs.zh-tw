---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
Module Name: Microsoft.PowerShell.Core
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/functions/clear-host?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Host
ms.openlocfilehash: 973d8c4952b99954c3f40bfd11966b754a0607b8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202344"
---
# <span data-ttu-id="08175-103">Clear-Host</span><span class="sxs-lookup"><span data-stu-id="08175-103">Clear-Host</span></span>

## <span data-ttu-id="08175-104">概要</span><span class="sxs-lookup"><span data-stu-id="08175-104">SYNOPSIS</span></span>

<span data-ttu-id="08175-105">清除主機程式中的顯示。</span><span class="sxs-lookup"><span data-stu-id="08175-105">Clears the display in the host program.</span></span>

## <span data-ttu-id="08175-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="08175-106">SYNTAX</span></span>

```
Clear-Host [<CommonParameters>]
```

## <span data-ttu-id="08175-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="08175-107">DESCRIPTION</span></span>

<span data-ttu-id="08175-108">`Clear-Host`函數會從目前的顯示中移除所有文字，包括可能累積的命令和輸出。</span><span class="sxs-lookup"><span data-stu-id="08175-108">The `Clear-Host` function removes all text from the current display, including commands and output that might have accumulated.</span></span> <span data-ttu-id="08175-109">完成時，它會顯示命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="08175-109">When complete, it displays the command prompt.</span></span> <span data-ttu-id="08175-110">您可以使用函式名稱或其別名 `cls` 。</span><span class="sxs-lookup"><span data-stu-id="08175-110">You can use the function name or its alias, `cls`.</span></span>

<span data-ttu-id="08175-111">`Clear-Host` 只會影響目前的顯示。</span><span class="sxs-lookup"><span data-stu-id="08175-111">`Clear-Host` affects only the current display.</span></span> <span data-ttu-id="08175-112">它不會刪除已儲存的結果，也不會從工作階段中移除任何項目。</span><span class="sxs-lookup"><span data-stu-id="08175-112">It does not delete saved results or remove any items from the session.</span></span> <span data-ttu-id="08175-113">工作階段特定項目 (例如變數和函式) 不會受到此函式的影響。</span><span class="sxs-lookup"><span data-stu-id="08175-113">Session-specific items, such as variables and functions, are not affected by this function.</span></span>

<span data-ttu-id="08175-114">由於函式的行為 `Clear-Host` 取決於主機程式，因此 `Clear-Host` 在不同的主機程式中的運作方式可能不同。</span><span class="sxs-lookup"><span data-stu-id="08175-114">Because the behavior of the `Clear-Host` function is determined by the host program, `Clear-Host` might work differently in different host programs.</span></span>

## <span data-ttu-id="08175-115">範例</span><span class="sxs-lookup"><span data-stu-id="08175-115">EXAMPLES</span></span>

### <span data-ttu-id="08175-116">範例 1</span><span class="sxs-lookup"><span data-stu-id="08175-116">Example 1</span></span>

```
# Before

PS C:\> Get-Process

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    843      33    14428      22556    99    17.41   1688 CcmExec
     44       6     2196       4964    52     0.23    692 conhost
    646      12     2332       4896    49     1.12    388 csrss
    189      11     2860       7084   114     0.66   2896 csrss
     78      11     1876       4008    42     0.22   4000 csrss
     76       7     1848       5064    54     0.08   1028 dwm
    610      41    23952      44048   208     4.40   2080 explorer
      0       0        0         24     0               0 Idle
    182      32     7692      15980    91     0.23   3056 LogonUI
    186      25     7832      16068    91     0.27   3996 LogonUI
   1272      32    11512      20432    58    25.07    548 lsass
    267      10     3536       6736    34     0.80    556 lsm
    137      17     3520       7472    61     0.05   1220 msdtc
    447      31    70316      84476   201 1,429.67    836 MsMpEng
    265      18     7136      15628   134     2.20   3544 msseces
    248      16     6476       4076    76     0.22   1592 NisSrv
    368      25    61312      65508   614     1.78    848 powershell
    101       8     2304       6624    70     0.64   3648 rdpclip
    258      15     6804      12156    50     2.65    536 services
...

PS C:\> cls
#After

PS C:>
```

<span data-ttu-id="08175-117">此命令會使用的 `cls` 別名 `Clear-Host` 來清除目前的顯示。</span><span class="sxs-lookup"><span data-stu-id="08175-117">This command uses the `cls` alias of `Clear-Host` to clear the current display.</span></span>

## <span data-ttu-id="08175-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="08175-118">PARAMETERS</span></span>

### <span data-ttu-id="08175-119">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="08175-119">CommonParameters</span></span>
<span data-ttu-id="08175-120">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="08175-120">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="08175-121">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="08175-121">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="08175-122">輸入</span><span class="sxs-lookup"><span data-stu-id="08175-122">INPUTS</span></span>

### <span data-ttu-id="08175-123">無</span><span class="sxs-lookup"><span data-stu-id="08175-123">None</span></span>

<span data-ttu-id="08175-124">您無法透過管道傳送輸入 `Clear-Host` 。</span><span class="sxs-lookup"><span data-stu-id="08175-124">You cannot pipe input to `Clear-Host`.</span></span>

## <span data-ttu-id="08175-125">輸出</span><span class="sxs-lookup"><span data-stu-id="08175-125">OUTPUTS</span></span>

### <span data-ttu-id="08175-126">無</span><span class="sxs-lookup"><span data-stu-id="08175-126">None</span></span>

<span data-ttu-id="08175-127">`Clear-Host` 不會產生任何輸出</span><span class="sxs-lookup"><span data-stu-id="08175-127">`Clear-Host` does not generate any output</span></span>

## <span data-ttu-id="08175-128">注意</span><span class="sxs-lookup"><span data-stu-id="08175-128">NOTES</span></span>

<span data-ttu-id="08175-129">`Clear-Host` 是簡單的函式，而非 advanced 函數。</span><span class="sxs-lookup"><span data-stu-id="08175-129">`Clear-Host` is a simple function, not an advanced function.</span></span> <span data-ttu-id="08175-130">因此，您無法在命令中使用一般參數，例如 **Debug** `Clear-Host` 。</span><span class="sxs-lookup"><span data-stu-id="08175-130">As such, you cannot use common parameters, such as **Debug** , in a `Clear-Host` command.</span></span>

## <span data-ttu-id="08175-131">相關連結</span><span class="sxs-lookup"><span data-stu-id="08175-131">RELATED LINKS</span></span>

[<span data-ttu-id="08175-132">Get-Host</span><span class="sxs-lookup"><span data-stu-id="08175-132">Get-Host</span></span>](../Microsoft.PowerShell.Utility/Get-Host.md)

[<span data-ttu-id="08175-133">Out-Host</span><span class="sxs-lookup"><span data-stu-id="08175-133">Out-Host</span></span>](Out-Host.md)

[<span data-ttu-id="08175-134">Read-Host</span><span class="sxs-lookup"><span data-stu-id="08175-134">Read-Host</span></span>](../Microsoft.PowerShell.Utility/Read-Host.md)

[<span data-ttu-id="08175-135">Write-Host</span><span class="sxs-lookup"><span data-stu-id="08175-135">Write-Host</span></span>](../Microsoft.PowerShell.Utility/Write-Host.md)
