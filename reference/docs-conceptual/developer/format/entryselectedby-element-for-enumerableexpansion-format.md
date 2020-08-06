---
title: EnumerableExpansion (格式的之 entryselectedby 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 031bf10cfb1aed2c737fdd53fa4f20f025351d40
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783665"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a><span data-ttu-id="a7543-102">EnumerableExpansion 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a7543-102">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="a7543-103">定義使用此定義的 .NET 類型，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="a7543-103">Defines the .NET types that use this definition or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="a7543-104">Configuration 元素 (格式) DefaultSettings 元素 (格式) EnumerableExpansions 元素 (格式) EnumerableExpansion 專案 (格式) EnumerableExpansion (格式的之 entryselectedby 元素) </span><span class="sxs-lookup"><span data-stu-id="a7543-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a7543-105">語法</span><span class="sxs-lookup"><span data-stu-id="a7543-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a7543-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a7543-106">Attributes and Elements</span></span>

<span data-ttu-id="a7543-107">下列各節說明屬性、子專案和元素的父元素 `EntrySelectedBy` 。</span><span class="sxs-lookup"><span data-stu-id="a7543-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a7543-108">屬性</span><span class="sxs-lookup"><span data-stu-id="a7543-108">Attributes</span></span>

<span data-ttu-id="a7543-109">無。</span><span class="sxs-lookup"><span data-stu-id="a7543-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a7543-110">子元素</span><span class="sxs-lookup"><span data-stu-id="a7543-110">Child Elements</span></span>

|<span data-ttu-id="a7543-111">元素</span><span class="sxs-lookup"><span data-stu-id="a7543-111">Element</span></span>|<span data-ttu-id="a7543-112">描述</span><span class="sxs-lookup"><span data-stu-id="a7543-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a7543-113">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a7543-113">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="a7543-114">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="a7543-114">Optional element.</span></span><br /><br /> <span data-ttu-id="a7543-115">定義必須存在的條件，才能展開這個定義的集合物件。</span><span class="sxs-lookup"><span data-stu-id="a7543-115">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|
|[<span data-ttu-id="a7543-116">EnumerableExpansion 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a7543-116">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="a7543-117">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="a7543-117">Optional element.</span></span><br /><br /> <span data-ttu-id="a7543-118">指定一組 .NET 類型，使用此定義來擴充集合物件的方式。</span><span class="sxs-lookup"><span data-stu-id="a7543-118">Specifies a set of .NET types that use this definition of how collection objects are expanded.</span></span>|
|[<span data-ttu-id="a7543-119">EnumerableExpansion 之 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a7543-119">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="a7543-120">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="a7543-120">Optional element.</span></span><br /><br /> <span data-ttu-id="a7543-121">指定 .NET 類型，其使用此定義來擴充集合物件的方式。</span><span class="sxs-lookup"><span data-stu-id="a7543-121">Specifies a .NET type that uses this definition of how collection objects are expanded.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a7543-122">父項目</span><span class="sxs-lookup"><span data-stu-id="a7543-122">Parent Elements</span></span>

|<span data-ttu-id="a7543-123">元素</span><span class="sxs-lookup"><span data-stu-id="a7543-123">Element</span></span>|<span data-ttu-id="a7543-124">描述</span><span class="sxs-lookup"><span data-stu-id="a7543-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a7543-125">EnumerableExpansion 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a7543-125">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="a7543-126">定義特定 .NET 集合物件在視圖中顯示時的擴充方式。</span><span class="sxs-lookup"><span data-stu-id="a7543-126">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a7543-127">備註</span><span class="sxs-lookup"><span data-stu-id="a7543-127">Remarks</span></span>

<span data-ttu-id="a7543-128">您必須為定義專案指定至少一個類型、選擇集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="a7543-128">You must specify at least one type, selection set, or selection condition for a definition entry.</span></span> <span data-ttu-id="a7543-129">您可以使用的子項目數目沒有上限。</span><span class="sxs-lookup"><span data-stu-id="a7543-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="a7543-130">選取條件是用來定義要使用的定義必須存在的條件，例如，當物件具有特定屬性或特定屬性值或腳本評估為時 `true` 。</span><span class="sxs-lookup"><span data-stu-id="a7543-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="a7543-131">如需選取條件的詳細資訊，請參閱[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="a7543-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a7543-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7543-132">See Also</span></span>

[<span data-ttu-id="a7543-133">定義用於顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="a7543-133">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="a7543-134">EnumerableExpansion 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a7543-134">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)

[<span data-ttu-id="a7543-135">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a7543-135">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="a7543-136">EnumerableExpansion 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a7543-136">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="a7543-137">EnumerableExpansion 之 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a7543-137">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="a7543-138">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="a7543-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
