---
title: SelectionSets 元素 (格式) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 718b08e02220f285ef215fdca727492fd4407466
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785195"
---
# <a name="selectionsets-element-format"></a><span data-ttu-id="13263-102">SelectionSets 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="13263-102">SelectionSets Element (Format)</span></span>

<span data-ttu-id="13263-103">定義一組通用的 .NET 物件，可供格式化檔案的所有視圖使用。</span><span class="sxs-lookup"><span data-stu-id="13263-103">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span> <span data-ttu-id="13263-104">格式設定檔案的視圖和控制項只能使用選取範圍的名稱來參考一組完整的物件。</span><span class="sxs-lookup"><span data-stu-id="13263-104">The views and controls of the formatting file can reference the complete set of objects by using only the name of the selection set.</span></span>

<span data-ttu-id="13263-105">Configuration 元素 SelectionSets 元素格式</span><span class="sxs-lookup"><span data-stu-id="13263-105">Configuration Element SelectionSets Element Format</span></span>

## <a name="syntax"></a><span data-ttu-id="13263-106">語法</span><span class="sxs-lookup"><span data-stu-id="13263-106">Syntax</span></span>

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="13263-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="13263-107">Attributes and Elements</span></span>

<span data-ttu-id="13263-108">下列各節描述元素的屬性、子專案和父項目 `SelectionSets` 。</span><span class="sxs-lookup"><span data-stu-id="13263-108">The following sections describe the attributes, child elements, and parent element of the `SelectionSets` element.</span></span> <span data-ttu-id="13263-109">每個子專案都會定義一組可由集合名稱參考的物件。</span><span class="sxs-lookup"><span data-stu-id="13263-109">Each child element defines a set of objects that can be referenced by the name of the set.</span></span> <span data-ttu-id="13263-110">子項目的順序並不重要。</span><span class="sxs-lookup"><span data-stu-id="13263-110">The order of the child elements is not significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="13263-111">屬性</span><span class="sxs-lookup"><span data-stu-id="13263-111">Attributes</span></span>

<span data-ttu-id="13263-112">無。</span><span class="sxs-lookup"><span data-stu-id="13263-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="13263-113">子元素</span><span class="sxs-lookup"><span data-stu-id="13263-113">Child Elements</span></span>

|<span data-ttu-id="13263-114">元素</span><span class="sxs-lookup"><span data-stu-id="13263-114">Element</span></span>|<span data-ttu-id="13263-115">描述</span><span class="sxs-lookup"><span data-stu-id="13263-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="13263-116">SelectionSet 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="13263-116">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="13263-117">必要元素。</span><span class="sxs-lookup"><span data-stu-id="13263-117">Required element.</span></span><br /><br /> <span data-ttu-id="13263-118">定義一組可由集合名稱參考的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="13263-118">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="13263-119">父項目</span><span class="sxs-lookup"><span data-stu-id="13263-119">Parent Elements</span></span>

|<span data-ttu-id="13263-120">元素</span><span class="sxs-lookup"><span data-stu-id="13263-120">Element</span></span>|<span data-ttu-id="13263-121">描述</span><span class="sxs-lookup"><span data-stu-id="13263-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="13263-122">組態元素</span><span class="sxs-lookup"><span data-stu-id="13263-122">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="13263-123">代表格式化檔案的最上層元素。</span><span class="sxs-lookup"><span data-stu-id="13263-123">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="13263-124">備註</span><span class="sxs-lookup"><span data-stu-id="13263-124">Remarks</span></span>

<span data-ttu-id="13263-125">當您有一組想要使用單一名稱來參考的相關物件（例如透過繼承相關的一組物件）時，您可以使用 [選擇集]。</span><span class="sxs-lookup"><span data-stu-id="13263-125">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="13263-126">定義您的視圖時，您可以使用選取範圍的名稱來指定物件集合，而不會列出每個視圖內的所有物件。</span><span class="sxs-lookup"><span data-stu-id="13263-126">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="13263-127">定義格式檔案的觀點或 views 定義時，會以名稱指定一般選取範圍。</span><span class="sxs-lookup"><span data-stu-id="13263-127">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="13263-128">在這些情況下， `SelectionSetName` 和元素的子 `ViewSelectedBy` 專案 `EntrySelectedBy` 會指定要使用的集合。</span><span class="sxs-lookup"><span data-stu-id="13263-128">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="13263-129">如需選取集的詳細資訊，請參閱[定義物件的集合](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="13263-129">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="13263-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13263-130">See Also</span></span>

[<span data-ttu-id="13263-131">組態元素</span><span class="sxs-lookup"><span data-stu-id="13263-131">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="13263-132">定義選取範圍集合</span><span class="sxs-lookup"><span data-stu-id="13263-132">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="13263-133">SelectionSet 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="13263-133">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="13263-134">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="13263-134">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
