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
ms.openlocfilehash: 553878c34e74129f9876cca25a5393cb0d53445a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364387"
---
# <a name="input-filter-parameters"></a><span data-ttu-id="4d4af-102">輸入篩選參數</span><span class="sxs-lookup"><span data-stu-id="4d4af-102">Input Filter Parameters</span></span>

<span data-ttu-id="4d4af-103">Cmdlet 可以定義 `Filter`、`Include` 和 `Exclude` 參數，以篩選 Cmdlet 所影響的輸入物件集合。</span><span class="sxs-lookup"><span data-stu-id="4d4af-103">A cmdlet can define `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

<span data-ttu-id="4d4af-104">一般來說，輸入物件的集合是由 `InputObject`、`Path` 或 @no__t 2 參數所指定。</span><span class="sxs-lookup"><span data-stu-id="4d4af-104">Typically, the set of input objects is specified by an `InputObject`, `Path`, or `Name` parameter.</span></span> <span data-ttu-id="4d4af-105">例如，Cmdlet 可以有 `Path` 參數，它會接受使用萬用字元的多個路徑，而每個路徑會指向輸入物件。</span><span class="sxs-lookup"><span data-stu-id="4d4af-105">For example, a cmdlet can have a `Path` parameter that accepts multiple paths by using wildcard characters, and each path points to an input object.</span></span> <span data-ttu-id="4d4af-106">一起使用時，`Filter`、`Include` 和 @no__t 2 參數會進一步限定 Cmdlet 在每次叫用時所能運作的路徑。</span><span class="sxs-lookup"><span data-stu-id="4d4af-106">Used together, the `Filter`, `Include`, and `Exclude` parameters further qualify the paths the cmdlet works on each time it is invoked.</span></span>

## <a name="include-and-exclude-parameters"></a><span data-ttu-id="4d4af-107">包含和排除參數</span><span class="sxs-lookup"><span data-stu-id="4d4af-107">Include and Exclude Parameters</span></span>

<span data-ttu-id="4d4af-108">@No__t-0 和 @no__t 1 參數會識別傳遞給 Cmdlet 的一組輸入物件所包含或排除的物件。</span><span class="sxs-lookup"><span data-stu-id="4d4af-108">The `Include` and `Exclude` parameters identify the objects that are included or excluded from the set of input objects passed to the cmdlet.</span></span> <span data-ttu-id="4d4af-109">當篩選準則可以用標準萬用字元語言表示時，請使用這些參數。</span><span class="sxs-lookup"><span data-stu-id="4d4af-109">Use these parameters when the filter can be expressed in the standard wildcard language.</span></span> <span data-ttu-id="4d4af-110">（如需萬用字元的詳細資訊，請參閱[在 Cmdlet 參數中支援萬用字元](./supporting-wildcard-characters-in-cmdlet-parameters.md)）。@No__t 1 參數包含其名稱符合包含篩選準則的所有物件。</span><span class="sxs-lookup"><span data-stu-id="4d4af-110">(For more information about wildcard characters, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).) The `Include` parameter includes all the objects whose names match the inclusion filter.</span></span> <span data-ttu-id="4d4af-111">@No__t-0 參數會排除其名稱符合篩選準則的所有物件。</span><span class="sxs-lookup"><span data-stu-id="4d4af-111">The `Exclude` parameter excludes all the objects whose names match the filter.</span></span>

## <a name="filter-parameter"></a><span data-ttu-id="4d4af-112">篩選參數</span><span class="sxs-lookup"><span data-stu-id="4d4af-112">Filter Parameter</span></span>

<span data-ttu-id="4d4af-113">@No__t-0 參數指定的篩選準則不是以標準萬用字元語言表示。</span><span class="sxs-lookup"><span data-stu-id="4d4af-113">The `Filter` parameter specifies a filter that is not expressed in the standard wildcard language.</span></span> <span data-ttu-id="4d4af-114">例如，Active Directory 服務介面（ADSI）或 SQL 篩選器可能會透過其 `Filter` 參數傳遞至 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4d4af-114">For example, Active Directory Service Interfaces (ADSI) or SQL filters might be passed to the cmdlet through its `Filter` parameter.</span></span> <span data-ttu-id="4d4af-115">在 Windows PowerShell 所提供的 Cmdlet 中，這些篩選器是由使用 Cmdlet 來存取資料存放區的 Windows PowerShell 提供者所指定。</span><span class="sxs-lookup"><span data-stu-id="4d4af-115">In the cmdlets provided by Windows PowerShell, these filters are specified by the Windows PowerShell providers that use the cmdlet to access a data store.</span></span> <span data-ttu-id="4d4af-116">每個提供者通常會定義它自己的篩選準則。</span><span class="sxs-lookup"><span data-stu-id="4d4af-116">Each provider typically defines its own filter.</span></span>

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a><span data-ttu-id="4d4af-117">篩選是否未指定輸入物件集合</span><span class="sxs-lookup"><span data-stu-id="4d4af-117">Filtering If No Set of Input Objects Is Specified</span></span>

<span data-ttu-id="4d4af-118">如果未指定任何一組輸入物件，這通常表示要針對所有物件進行篩選。</span><span class="sxs-lookup"><span data-stu-id="4d4af-118">If no set of input objects is specified, this typically means to filter against all objects.</span></span> <span data-ttu-id="4d4af-119">如需詳細資訊，請參閱[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)。</span><span class="sxs-lookup"><span data-stu-id="4d4af-119">For more information, see[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).</span></span>

## <a name="see-also"></a><span data-ttu-id="4d4af-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d4af-120">See Also</span></span>

[<span data-ttu-id="4d4af-121">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4d4af-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)