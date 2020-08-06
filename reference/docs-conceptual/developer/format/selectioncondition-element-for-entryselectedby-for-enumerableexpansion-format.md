---
title: EnumerableExpansion (格式) 的之 entryselectedby 的 SelectionCondition 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d5858145e092dc962174a776889a4f62db366d71
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785331"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="15bb0-102">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="15bb0-102">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="15bb0-103">定義必須存在的條件，才能展開這個定義的集合物件。</span><span class="sxs-lookup"><span data-stu-id="15bb0-103">Defines the condition that must exist to expand the collection objects of this definition.</span></span>

<span data-ttu-id="15bb0-104">Configuration 元素 (格式) DefaultSettings 元素 (格式) EnumerableExpansions 元素 (格式) EnumerableExpansion 專案 (格式) EnumerableExpansion (格式) SelectionCondition 元素之 entryselectedby (格式) </span><span class="sxs-lookup"><span data-stu-id="15bb0-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="15bb0-105">語法</span><span class="sxs-lookup"><span data-stu-id="15bb0-105">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="15bb0-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="15bb0-106">Attributes and Elements</span></span>

<span data-ttu-id="15bb0-107">下列各節說明屬性、子專案和元素的父元素 `SelectionCondition` 。</span><span class="sxs-lookup"><span data-stu-id="15bb0-107">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="15bb0-108">您必須指定單一 `PropertyName` 或 `ScriptBlock` 元素。</span><span class="sxs-lookup"><span data-stu-id="15bb0-108">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="15bb0-109">`SelectionSetName`和 `TypeName` 元素是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="15bb0-109">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="15bb0-110">您可以指定其中一個元素。</span><span class="sxs-lookup"><span data-stu-id="15bb0-110">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="15bb0-111">屬性</span><span class="sxs-lookup"><span data-stu-id="15bb0-111">Attributes</span></span>

<span data-ttu-id="15bb0-112">無。</span><span class="sxs-lookup"><span data-stu-id="15bb0-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="15bb0-113">子元素</span><span class="sxs-lookup"><span data-stu-id="15bb0-113">Child Elements</span></span>

|<span data-ttu-id="15bb0-114">元素</span><span class="sxs-lookup"><span data-stu-id="15bb0-114">Element</span></span>|<span data-ttu-id="15bb0-115">描述</span><span class="sxs-lookup"><span data-stu-id="15bb0-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="15bb0-116">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="15bb0-116">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="15bb0-117">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="15bb0-117">Optional element.</span></span><br /><br /> <span data-ttu-id="15bb0-118">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="15bb0-118">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="15bb0-119">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="15bb0-119">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="15bb0-120">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="15bb0-120">Optional element.</span></span><br /><br /> <span data-ttu-id="15bb0-121">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="15bb0-121">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="15bb0-122">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="15bb0-122">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="15bb0-123">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="15bb0-123">Optional element.</span></span><br /><br /> <span data-ttu-id="15bb0-124">指定觸發條件的 .NET 類型集合。</span><span class="sxs-lookup"><span data-stu-id="15bb0-124">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="15bb0-125">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="15bb0-125">TypeName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="15bb0-126">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="15bb0-126">Optional element.</span></span><br /><br /> <span data-ttu-id="15bb0-127">指定觸發條件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="15bb0-127">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="15bb0-128">父項目</span><span class="sxs-lookup"><span data-stu-id="15bb0-128">Parent Elements</span></span>

|<span data-ttu-id="15bb0-129">元素</span><span class="sxs-lookup"><span data-stu-id="15bb0-129">Element</span></span>|<span data-ttu-id="15bb0-130">描述</span><span class="sxs-lookup"><span data-stu-id="15bb0-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="15bb0-131">EnumerableExpansion 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="15bb0-131">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="15bb0-132">定義由這個定義擴充的 .NET 集合物件。</span><span class="sxs-lookup"><span data-stu-id="15bb0-132">Defines which .NET collection objects are expanded by this definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="15bb0-133">備註</span><span class="sxs-lookup"><span data-stu-id="15bb0-133">Remarks</span></span>

<span data-ttu-id="15bb0-134">每個定義都必須定義至少一個型別名稱、選擇集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="15bb0-134">Each definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="15bb0-135">當您定義選取條件時，適用下列需求：</span><span class="sxs-lookup"><span data-stu-id="15bb0-135">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="15bb0-136">選取條件必須指定至少一個屬性名稱或腳本區塊，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="15bb0-136">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="15bb0-137">選取條件可以指定任意數目的 .NET 類型或選擇集，但無法同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="15bb0-137">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="15bb0-138">如需如何使用選取條件的詳細資訊，請參閱[定義 Diplaying 資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="15bb0-138">For more information about how to use selection conditions, see [Defining Conditions for Diplaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="15bb0-139">如需有關寬視圖之其他元件的詳細資訊，請參閱[Wide view](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="15bb0-139">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="15bb0-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15bb0-140">See Also</span></span>

[<span data-ttu-id="15bb0-141">定義資料顯示時的條件</span><span class="sxs-lookup"><span data-stu-id="15bb0-141">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="15bb0-142">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="15bb0-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
