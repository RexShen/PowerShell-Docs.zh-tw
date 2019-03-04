---
title: SelectionSets 項目 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebbac73a-1c99-4388-9f47-703cd024dc6d
caps.latest.revision: 18
ms.openlocfilehash: a9356635d60d5f8c5d4dec4ec8b7d0aea2b037dd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853564"
---
# <a name="selectionsets-element-format"></a><span data-ttu-id="e044e-102">SelectionSets 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e044e-102">SelectionSets Element (Format)</span></span>

<span data-ttu-id="e044e-103">定義通用的集合，可供所有檢視的格式化檔案的.NET 物件。</span><span class="sxs-lookup"><span data-stu-id="e044e-103">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span> <span data-ttu-id="e044e-104">使用選取項目集的名稱，以檢視和控制項的格式化檔案可以參考一組完整的物件。</span><span class="sxs-lookup"><span data-stu-id="e044e-104">The views and controls of the formatting file can reference the complete set of objects by using only the name of the selection set.</span></span>

<span data-ttu-id="e044e-105">組態項目 SelectionSets 元素格式</span><span class="sxs-lookup"><span data-stu-id="e044e-105">Configuration Element SelectionSets Element Format</span></span>

## <a name="syntax"></a><span data-ttu-id="e044e-106">語法</span><span class="sxs-lookup"><span data-stu-id="e044e-106">Syntax</span></span>

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e044e-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="e044e-107">Attributes and Elements</span></span>

<span data-ttu-id="e044e-108">下列各節說明屬性、 子項目和父項目`SelectionSets`項目。</span><span class="sxs-lookup"><span data-stu-id="e044e-108">The following sections describe the attributes, child elements, and parent element of the `SelectionSets` element.</span></span> <span data-ttu-id="e044e-109">每個子項目會定義一組可以集的名稱所參考的物件。</span><span class="sxs-lookup"><span data-stu-id="e044e-109">Each child element defines a set of objects that can be referenced by the name of the set.</span></span> <span data-ttu-id="e044e-110">子元素的順序並不重要。</span><span class="sxs-lookup"><span data-stu-id="e044e-110">The order of the child elements is not significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="e044e-111">屬性</span><span class="sxs-lookup"><span data-stu-id="e044e-111">Attributes</span></span>

<span data-ttu-id="e044e-112">無。</span><span class="sxs-lookup"><span data-stu-id="e044e-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e044e-113">子元素</span><span class="sxs-lookup"><span data-stu-id="e044e-113">Child Elements</span></span>

|<span data-ttu-id="e044e-114">元素</span><span class="sxs-lookup"><span data-stu-id="e044e-114">Element</span></span>|<span data-ttu-id="e044e-115">描述</span><span class="sxs-lookup"><span data-stu-id="e044e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e044e-116">SelectionSet 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="e044e-116">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="e044e-117">必要項目。</span><span class="sxs-lookup"><span data-stu-id="e044e-117">Required element.</span></span><br /><br /> <span data-ttu-id="e044e-118">定義一組.NET 物件，可以參考集的名稱。</span><span class="sxs-lookup"><span data-stu-id="e044e-118">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e044e-119">父元素</span><span class="sxs-lookup"><span data-stu-id="e044e-119">Parent Elements</span></span>

|<span data-ttu-id="e044e-120">元素</span><span class="sxs-lookup"><span data-stu-id="e044e-120">Element</span></span>|<span data-ttu-id="e044e-121">描述</span><span class="sxs-lookup"><span data-stu-id="e044e-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e044e-122">組態項目</span><span class="sxs-lookup"><span data-stu-id="e044e-122">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="e044e-123">表示格式化檔案的最上層項目。</span><span class="sxs-lookup"><span data-stu-id="e044e-123">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e044e-124">備註</span><span class="sxs-lookup"><span data-stu-id="e044e-124">Remarks</span></span>

<span data-ttu-id="e044e-125">當您有一組您想要使用單一的名稱，例如一組透過繼承相關聯的物件參考的相關物件時，您可以使用選取項目集。</span><span class="sxs-lookup"><span data-stu-id="e044e-125">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="e044e-126">在定義您的檢視時，您可以指定一組物件使用的設定而非列出每個檢視中的所有物件的選取範圍的名稱。</span><span class="sxs-lookup"><span data-stu-id="e044e-126">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="e044e-127">定義格式化檔案的檢視或檢視的定義時常見的選取項目集指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="e044e-127">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="e044e-128">在這些情況下，`SelectionSetName`子元素`ViewSelectedBy`和`EntrySelectedBy`元素指定要使用的集合。</span><span class="sxs-lookup"><span data-stu-id="e044e-128">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="e044e-129">如需選取項目集的詳細資訊，請參閱[定義設定的物件](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="e044e-129">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e044e-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e044e-130">See Also</span></span>

[<span data-ttu-id="e044e-131">組態項目</span><span class="sxs-lookup"><span data-stu-id="e044e-131">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="e044e-132">定義選取範圍</span><span class="sxs-lookup"><span data-stu-id="e044e-132">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="e044e-133">SelectionSet 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="e044e-133">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="e044e-134">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="e044e-134">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
