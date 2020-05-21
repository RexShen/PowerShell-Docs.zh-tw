---
title: 輸入篩選參數 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e45929d1-bbb4-4dc6-892f-f9eacdb1c84c
caps.latest.revision: 8
ms.openlocfilehash: 7a1582031d27f78bad069f5539408312ccabb3f2
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83563881"
---
# <a name="input-filter-parameters"></a><span data-ttu-id="7a6b1-102">輸入篩選參數</span><span class="sxs-lookup"><span data-stu-id="7a6b1-102">Input Filter Parameters</span></span>

<span data-ttu-id="7a6b1-103">Cmdlet 可以定義 `Filter` 、 `Include` 和參數， `Exclude` 以篩選 Cmdlet 所影響的一組輸入物件。</span><span class="sxs-lookup"><span data-stu-id="7a6b1-103">A cmdlet can define `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

<span data-ttu-id="7a6b1-104">一般來說，輸入物件的集合是由 `InputObject` 、 `Path` 或 `Name` 參數指定。</span><span class="sxs-lookup"><span data-stu-id="7a6b1-104">Typically, the set of input objects is specified by an `InputObject`, `Path`, or `Name` parameter.</span></span> <span data-ttu-id="7a6b1-105">例如，Cmdlet 可以具有 `Path` 接受多個路徑的參數，方法是使用萬用字元，而每個路徑都會指向輸入物件。</span><span class="sxs-lookup"><span data-stu-id="7a6b1-105">For example, a cmdlet can have a `Path` parameter that accepts multiple paths by using wildcard characters, and each path points to an input object.</span></span> <span data-ttu-id="7a6b1-106">一起使用時， `Filter` 、 `Include` 和 `Exclude` 參數會進一步限定 Cmdlet 在每次叫用時所能運作的路徑。</span><span class="sxs-lookup"><span data-stu-id="7a6b1-106">Used together, the `Filter`, `Include`, and `Exclude` parameters further qualify the paths the cmdlet works on each time it is invoked.</span></span>

## <a name="include-and-exclude-parameters"></a><span data-ttu-id="7a6b1-107">包含和排除參數</span><span class="sxs-lookup"><span data-stu-id="7a6b1-107">Include and Exclude Parameters</span></span>

<span data-ttu-id="7a6b1-108">`Include`和 `Exclude` 參數會識別傳遞給 Cmdlet 的一組輸入物件所包含或排除的物件。</span><span class="sxs-lookup"><span data-stu-id="7a6b1-108">The `Include` and `Exclude` parameters identify the objects that are included or excluded from the set of input objects passed to the cmdlet.</span></span> <span data-ttu-id="7a6b1-109">當篩選準則可以用標準萬用字元語言表示時，請使用這些參數。</span><span class="sxs-lookup"><span data-stu-id="7a6b1-109">Use these parameters when the filter can be expressed in the standard wildcard language.</span></span> <span data-ttu-id="7a6b1-110">（如需萬用字元的詳細資訊，請參閱[在 Cmdlet 參數中支援萬用字元](./supporting-wildcard-characters-in-cmdlet-parameters.md)）。`Include`參數包含其名稱符合包含篩選準則的所有物件。</span><span class="sxs-lookup"><span data-stu-id="7a6b1-110">(For more information about wildcard characters, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).) The `Include` parameter includes all the objects whose names match the inclusion filter.</span></span> <span data-ttu-id="7a6b1-111">`Exclude`參數會排除其名稱符合篩選準則的所有物件。</span><span class="sxs-lookup"><span data-stu-id="7a6b1-111">The `Exclude` parameter excludes all the objects whose names match the filter.</span></span>

## <a name="filter-parameter"></a><span data-ttu-id="7a6b1-112">篩選參數</span><span class="sxs-lookup"><span data-stu-id="7a6b1-112">Filter Parameter</span></span>

<span data-ttu-id="7a6b1-113">`Filter`參數指定的篩選準則不是以標準萬用字元語言表示。</span><span class="sxs-lookup"><span data-stu-id="7a6b1-113">The `Filter` parameter specifies a filter that is not expressed in the standard wildcard language.</span></span> <span data-ttu-id="7a6b1-114">例如，Active Directory 服務介面（ADSI）或 SQL 篩選器可能會透過其參數傳遞至 Cmdlet `Filter` 。</span><span class="sxs-lookup"><span data-stu-id="7a6b1-114">For example, Active Directory Service Interfaces (ADSI) or SQL filters might be passed to the cmdlet through its `Filter` parameter.</span></span> <span data-ttu-id="7a6b1-115">在 Windows PowerShell 所提供的 Cmdlet 中，這些篩選器是由使用 Cmdlet 來存取資料存放區的 Windows PowerShell 提供者所指定。</span><span class="sxs-lookup"><span data-stu-id="7a6b1-115">In the cmdlets provided by Windows PowerShell, these filters are specified by the Windows PowerShell providers that use the cmdlet to access a data store.</span></span> <span data-ttu-id="7a6b1-116">每個提供者通常會定義它自己的篩選準則。</span><span class="sxs-lookup"><span data-stu-id="7a6b1-116">Each provider typically defines its own filter.</span></span>

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a><span data-ttu-id="7a6b1-117">篩選是否未指定輸入物件集合</span><span class="sxs-lookup"><span data-stu-id="7a6b1-117">Filtering If No Set of Input Objects Is Specified</span></span>

<span data-ttu-id="7a6b1-118">如果未指定任何一組輸入物件，這通常表示要針對所有物件進行篩選。</span><span class="sxs-lookup"><span data-stu-id="7a6b1-118">If no set of input objects is specified, this typically means to filter against all objects.</span></span> <span data-ttu-id="7a6b1-119">如需詳細資訊，請參閱[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)。</span><span class="sxs-lookup"><span data-stu-id="7a6b1-119">For more information, see[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).</span></span>

## <a name="see-also"></a><span data-ttu-id="7a6b1-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a6b1-120">See Also</span></span>

[<span data-ttu-id="7a6b1-121">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7a6b1-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
