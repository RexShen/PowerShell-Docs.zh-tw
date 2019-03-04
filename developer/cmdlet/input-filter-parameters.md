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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854464"
---
# <a name="input-filter-parameters"></a><span data-ttu-id="3237d-102">輸入篩選參數</span><span class="sxs-lookup"><span data-stu-id="3237d-102">Input Filter Parameters</span></span>

<span data-ttu-id="3237d-103">Cmdlet 可以定義`Filter`， `Include`，和`Exclude`篩選一組指令程式會影響的輸入物件的參數。</span><span class="sxs-lookup"><span data-stu-id="3237d-103">A cmdlet can define `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

<span data-ttu-id="3237d-104">一組輸入物件由通常`InputObject`， `Path`，或`Name`參數。</span><span class="sxs-lookup"><span data-stu-id="3237d-104">Typically, the set of input objects is specified by an `InputObject`, `Path`, or `Name` parameter.</span></span> <span data-ttu-id="3237d-105">例如下, 一個 cmdlet 可以有`Path`接受多個路徑使用萬用字元，以及每個路徑會指向輸入物件的參數。</span><span class="sxs-lookup"><span data-stu-id="3237d-105">For example, a cmdlet can have a `Path` parameter that accepts multiple paths by using wildcard characters, and each path points to an input object.</span></span> <span data-ttu-id="3237d-106">一起使用， `Filter`， `Include`，和`Exclude`參數進一步限定 cmdlet 適用於每次叫用時的路徑。</span><span class="sxs-lookup"><span data-stu-id="3237d-106">Used together, the `Filter`, `Include`, and `Exclude` parameters further qualify the paths the cmdlet works on each time it is invoked.</span></span>

## <a name="include-and-exclude-parameters"></a><span data-ttu-id="3237d-107">Include 和 Exclude 參數</span><span class="sxs-lookup"><span data-stu-id="3237d-107">Include and Exclude Parameters</span></span>

<span data-ttu-id="3237d-108">`Include`和`Exclude`參數識別的物件，包含或排除的一組輸入物件傳遞至 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3237d-108">The `Include` and `Exclude` parameters identify the objects that are included or excluded from the set of input objects passed to the cmdlet.</span></span> <span data-ttu-id="3237d-109">篩選條件可以表示的標準萬用字元語言時，請使用這些參數。</span><span class="sxs-lookup"><span data-stu-id="3237d-109">Use these parameters when the filter can be expressed in the standard wildcard language.</span></span> <span data-ttu-id="3237d-110">(如需萬用字元的詳細資訊，請參閱[在 Cmdlet 參數中的 支援使用萬用字元](./supporting-wildcard-characters-in-cmdlet-parameters.md)。)`Include`參數包含其名稱符合包含篩選條件的所有物件。</span><span class="sxs-lookup"><span data-stu-id="3237d-110">(For more information about wildcard characters, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).) The `Include` parameter includes all the objects whose names match the inclusion filter.</span></span> <span data-ttu-id="3237d-111">`Exclude`參數不包括其名稱符合篩選條件的所有物件。</span><span class="sxs-lookup"><span data-stu-id="3237d-111">The `Exclude` parameter excludes all the objects whose names match the filter.</span></span>

## <a name="filter-parameter"></a><span data-ttu-id="3237d-112">Filter 參數</span><span class="sxs-lookup"><span data-stu-id="3237d-112">Filter Parameter</span></span>

<span data-ttu-id="3237d-113">`Filter`參數可指定篩選，不表示在標準萬用字元語言中。</span><span class="sxs-lookup"><span data-stu-id="3237d-113">The `Filter` parameter specifies a filter that is not expressed in the standard wildcard language.</span></span> <span data-ttu-id="3237d-114">例如，Active Directory 服務介面 (ADSI) 或 SQL 篩選器可能會傳遞至 cmdlet，透過其`Filter`參數。</span><span class="sxs-lookup"><span data-stu-id="3237d-114">For example, Active Directory Service Interfaces (ADSI) or SQL filters might be passed to the cmdlet through its `Filter` parameter.</span></span> <span data-ttu-id="3237d-115">在 Windows PowerShell 所提供的 cmdlet，這些篩選器使用 cmdlet 來存取資料存放區的 Windows PowerShell 提供者所指定。</span><span class="sxs-lookup"><span data-stu-id="3237d-115">In the cmdlets provided by Windows PowerShell, these filters are specified by the Windows PowerShell providers that use the cmdlet to access a data store.</span></span> <span data-ttu-id="3237d-116">每個提供者通常會定義自己的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="3237d-116">Each provider typically defines its own filter.</span></span>

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a><span data-ttu-id="3237d-117">如果不指定了任何一組輸入物件的篩選</span><span class="sxs-lookup"><span data-stu-id="3237d-117">Filtering If No Set of Input Objects Is Specified</span></span>

<span data-ttu-id="3237d-118">如果不指定了任何一組輸入物件，這通常表示篩選器的所有物件。</span><span class="sxs-lookup"><span data-stu-id="3237d-118">If no set of input objects is specified, this typically means to filter against all objects.</span></span> <span data-ttu-id="3237d-119">如需詳細資訊，請參閱 <<c0> [ Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)。</span><span class="sxs-lookup"><span data-stu-id="3237d-119">For more information, see[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).</span></span>

## <a name="see-also"></a><span data-ttu-id="3237d-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3237d-120">See Also</span></span>

[<span data-ttu-id="3237d-121">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3237d-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)