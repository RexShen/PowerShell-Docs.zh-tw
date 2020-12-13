---
ms.date: 09/13/2016
ms.topic: reference
title: 輸入篩選參數
description: 輸入篩選參數
ms.openlocfilehash: 419ffea2afb4aa534a3e19ecdfce6d6af1da46a6
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648541"
---
# <a name="input-filter-parameters"></a><span data-ttu-id="f47f2-103">輸入篩選參數</span><span class="sxs-lookup"><span data-stu-id="f47f2-103">Input Filter Parameters</span></span>

<span data-ttu-id="f47f2-104">Cmdlet 可以定義 `Filter` 、 `Include` 和參數， `Exclude` 以篩選 Cmdlet 所影響的輸入物件集合。</span><span class="sxs-lookup"><span data-stu-id="f47f2-104">A cmdlet can define `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

<span data-ttu-id="f47f2-105">通常，輸入物件的集合是由 `InputObject` 、 `Path` 或參數所指定 `Name` 。</span><span class="sxs-lookup"><span data-stu-id="f47f2-105">Typically, the set of input objects is specified by an `InputObject`, `Path`, or `Name` parameter.</span></span> <span data-ttu-id="f47f2-106">例如，Cmdlet 可以有 `Path` 使用萬用字元接受多個路徑的參數，而且每個路徑都指向輸入物件。</span><span class="sxs-lookup"><span data-stu-id="f47f2-106">For example, a cmdlet can have a `Path` parameter that accepts multiple paths by using wildcard characters, and each path points to an input object.</span></span> <span data-ttu-id="f47f2-107">搭配使用時， `Filter` 、 `Include` 和 `Exclude` 參數可進一步限定 Cmdlet 在每次叫用時所能運作的路徑。</span><span class="sxs-lookup"><span data-stu-id="f47f2-107">Used together, the `Filter`, `Include`, and `Exclude` parameters further qualify the paths the cmdlet works on each time it is invoked.</span></span>

## <a name="include-and-exclude-parameters"></a><span data-ttu-id="f47f2-108">包含和排除參數</span><span class="sxs-lookup"><span data-stu-id="f47f2-108">Include and Exclude Parameters</span></span>

<span data-ttu-id="f47f2-109">`Include`和 `Exclude` 參數會識別傳遞給 Cmdlet 的輸入物件集合中包含或排除的物件。</span><span class="sxs-lookup"><span data-stu-id="f47f2-109">The `Include` and `Exclude` parameters identify the objects that are included or excluded from the set of input objects passed to the cmdlet.</span></span> <span data-ttu-id="f47f2-110">當篩選可以用標準萬用字元語言表示時，請使用這些參數。</span><span class="sxs-lookup"><span data-stu-id="f47f2-110">Use these parameters when the filter can be expressed in the standard wildcard language.</span></span> <span data-ttu-id="f47f2-111"> (如需萬用字元的詳細資訊，請參閱 [在 Cmdlet 參數中支援萬用字元](./supporting-wildcard-characters-in-cmdlet-parameters.md)。 ) `Include` 參數包含名稱符合包含篩選準則的所有物件。</span><span class="sxs-lookup"><span data-stu-id="f47f2-111">(For more information about wildcard characters, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).) The `Include` parameter includes all the objects whose names match the inclusion filter.</span></span> <span data-ttu-id="f47f2-112">`Exclude`參數會排除名稱符合篩選準則的所有物件。</span><span class="sxs-lookup"><span data-stu-id="f47f2-112">The `Exclude` parameter excludes all the objects whose names match the filter.</span></span>

## <a name="filter-parameter"></a><span data-ttu-id="f47f2-113">篩選參數</span><span class="sxs-lookup"><span data-stu-id="f47f2-113">Filter Parameter</span></span>

<span data-ttu-id="f47f2-114">`Filter`參數指定的篩選準則未以標準萬用字元語言表示。</span><span class="sxs-lookup"><span data-stu-id="f47f2-114">The `Filter` parameter specifies a filter that is not expressed in the standard wildcard language.</span></span> <span data-ttu-id="f47f2-115">例如， (ADSI) 或 SQL 篩選器 Active Directory 服務介面，可能會透過其參數傳遞至 Cmdlet `Filter` 。</span><span class="sxs-lookup"><span data-stu-id="f47f2-115">For example, Active Directory Service Interfaces (ADSI) or SQL filters might be passed to the cmdlet through its `Filter` parameter.</span></span> <span data-ttu-id="f47f2-116">在 Windows PowerShell 所提供的 Cmdlet 中，這些篩選是由使用指令程式來存取資料存放區的 Windows PowerShell 提供者所指定。</span><span class="sxs-lookup"><span data-stu-id="f47f2-116">In the cmdlets provided by Windows PowerShell, these filters are specified by the Windows PowerShell providers that use the cmdlet to access a data store.</span></span> <span data-ttu-id="f47f2-117">每個提供者通常會定義自己的篩選準則。</span><span class="sxs-lookup"><span data-stu-id="f47f2-117">Each provider typically defines its own filter.</span></span>

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a><span data-ttu-id="f47f2-118">篩選是否未指定輸入物件集合</span><span class="sxs-lookup"><span data-stu-id="f47f2-118">Filtering If No Set of Input Objects Is Specified</span></span>

<span data-ttu-id="f47f2-119">如果未指定任何輸入物件集，這通常表示要針對所有物件進行篩選。</span><span class="sxs-lookup"><span data-stu-id="f47f2-119">If no set of input objects is specified, this typically means to filter against all objects.</span></span> <span data-ttu-id="f47f2-120">如需詳細資訊，請參閱[Get 流程](/powershell/module/Microsoft.PowerShell.Management/Get-Process)。</span><span class="sxs-lookup"><span data-stu-id="f47f2-120">For more information, see[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).</span></span>

## <a name="see-also"></a><span data-ttu-id="f47f2-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f47f2-121">See Also</span></span>

[<span data-ttu-id="f47f2-122">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f47f2-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
