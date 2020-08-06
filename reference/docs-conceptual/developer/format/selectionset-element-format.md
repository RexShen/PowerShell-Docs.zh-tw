---
title: SelectionSet 元素 (格式) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: cf47229993458492c712d28e04913e75d1bde386
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783393"
---
# <a name="selectionset-element-format"></a><span data-ttu-id="6aa50-102">SelectionSet 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="6aa50-102">SelectionSet Element (Format)</span></span>

<span data-ttu-id="6aa50-103">定義一組可由集合名稱參考的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="6aa50-103">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>

<span data-ttu-id="6aa50-104">Configuration 元素 (格式) SelectionSets 元素 (格式) SelectionSet 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="6aa50-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6aa50-105">語法</span><span class="sxs-lookup"><span data-stu-id="6aa50-105">Syntax</span></span>

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6aa50-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6aa50-106">Attributes and Elements</span></span>

<span data-ttu-id="6aa50-107">下列各節說明屬性、子專案和元素的父元素 `SelectionSet` 。</span><span class="sxs-lookup"><span data-stu-id="6aa50-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSet` element.</span></span> <span data-ttu-id="6aa50-108">每個選取範圍都必須要有名稱，而且必須指定集合的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="6aa50-108">Each selection set must have a name, and it must specify the .NET objects of the set.</span></span>

### <a name="attributes"></a><span data-ttu-id="6aa50-109">屬性</span><span class="sxs-lookup"><span data-stu-id="6aa50-109">Attributes</span></span>

<span data-ttu-id="6aa50-110">無。</span><span class="sxs-lookup"><span data-stu-id="6aa50-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6aa50-111">子元素</span><span class="sxs-lookup"><span data-stu-id="6aa50-111">Child Elements</span></span>

|<span data-ttu-id="6aa50-112">元素</span><span class="sxs-lookup"><span data-stu-id="6aa50-112">Element</span></span>|<span data-ttu-id="6aa50-113">描述</span><span class="sxs-lookup"><span data-stu-id="6aa50-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6aa50-114">SelectionSet 的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="6aa50-114">Name Element for SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)|<span data-ttu-id="6aa50-115">必要元素。</span><span class="sxs-lookup"><span data-stu-id="6aa50-115">Required element.</span></span><br /><br /> <span data-ttu-id="6aa50-116">指定用來參考選取集的名稱。</span><span class="sxs-lookup"><span data-stu-id="6aa50-116">Specifies the name used to reference the selection set.</span></span>|
|[<span data-ttu-id="6aa50-117">Types 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="6aa50-117">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="6aa50-118">必要元素。</span><span class="sxs-lookup"><span data-stu-id="6aa50-118">Required element.</span></span><br /><br /> <span data-ttu-id="6aa50-119">定義選取集中的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="6aa50-119">Defines the .NET objects that are in the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6aa50-120">父項目</span><span class="sxs-lookup"><span data-stu-id="6aa50-120">Parent Elements</span></span>

|<span data-ttu-id="6aa50-121">元素</span><span class="sxs-lookup"><span data-stu-id="6aa50-121">Element</span></span>|<span data-ttu-id="6aa50-122">描述</span><span class="sxs-lookup"><span data-stu-id="6aa50-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6aa50-123">SelectionSets 元素格式</span><span class="sxs-lookup"><span data-stu-id="6aa50-123">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="6aa50-124">定義一組通用的 .NET 物件，可供格式化檔案的所有視圖使用。</span><span class="sxs-lookup"><span data-stu-id="6aa50-124">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6aa50-125">備註</span><span class="sxs-lookup"><span data-stu-id="6aa50-125">Remarks</span></span>

<span data-ttu-id="6aa50-126">當您有一組想要使用單一名稱來參考的相關物件（例如透過繼承相關的一組物件）時，您可以使用 [選擇集]。</span><span class="sxs-lookup"><span data-stu-id="6aa50-126">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="6aa50-127">定義您的視圖時，您可以使用選取範圍的名稱來指定物件集合，而不會列出每個視圖內的所有物件。</span><span class="sxs-lookup"><span data-stu-id="6aa50-127">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="6aa50-128">定義格式檔案的觀點或 views 定義時，會以名稱指定一般選取範圍。</span><span class="sxs-lookup"><span data-stu-id="6aa50-128">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="6aa50-129">在這些情況下， `SelectionSetName` 和元素的子 `ViewSelectedBy` 專案 `EntrySelectedBy` 會指定要使用的集合。</span><span class="sxs-lookup"><span data-stu-id="6aa50-129">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="6aa50-130">如需選取集的詳細資訊，請參閱[定義物件的集合](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="6aa50-130">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="6aa50-131">範例</span><span class="sxs-lookup"><span data-stu-id="6aa50-131">Example</span></span>

<span data-ttu-id="6aa50-132">下列範例顯示 `SelectionSet` 定義四個 .net 類型的元素。</span><span class="sxs-lookup"><span data-stu-id="6aa50-132">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

```xml
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

## <a name="see-also"></a><span data-ttu-id="6aa50-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6aa50-133">See Also</span></span>

[<span data-ttu-id="6aa50-134">定義選取範圍集合</span><span class="sxs-lookup"><span data-stu-id="6aa50-134">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="6aa50-135">SelectionSet (格式的 Name 元素) </span><span class="sxs-lookup"><span data-stu-id="6aa50-135">Name Element of SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="6aa50-136">SelectionSets 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="6aa50-136">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="6aa50-137">Types 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="6aa50-137">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="6aa50-138">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="6aa50-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
