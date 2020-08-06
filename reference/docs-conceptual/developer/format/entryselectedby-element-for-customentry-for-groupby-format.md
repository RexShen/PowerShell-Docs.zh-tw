---
title: 適用于 CustomEntry 之 GroupBy (格式的之 entryselectedby 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 75a0f42e7722b54791a873200a35c8fcbbd665b1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774128"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a><span data-ttu-id="45471-102">GroupBy 之 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="45471-102">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="45471-103">定義使用此控制項定義的 .NET 類型，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="45471-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="45471-104">此元素是在定義新物件群組的顯示方式時使用。</span><span class="sxs-lookup"><span data-stu-id="45471-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="45471-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy 元素（GroupBy (格式）) CustomEntries 元素（適用于 CustomEntry 的 groupby (格式) CustomControl 元素） (之 entryselectedby 專案（適用于 GroupBy) 格式的 CustomEntry） (</span><span class="sxs-lookup"><span data-stu-id="45471-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="45471-106">語法</span><span class="sxs-lookup"><span data-stu-id="45471-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="45471-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="45471-107">Attributes and Elements</span></span>

<span data-ttu-id="45471-108">下列各節描述元素的屬性、子專案和父項目 `EntrySelectedBy` 。</span><span class="sxs-lookup"><span data-stu-id="45471-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="45471-109">您必須為定義指定至少一個類型、選取集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="45471-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="45471-110">您可以使用的子項目數目沒有上限。</span><span class="sxs-lookup"><span data-stu-id="45471-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="45471-111">屬性</span><span class="sxs-lookup"><span data-stu-id="45471-111">Attributes</span></span>

<span data-ttu-id="45471-112">無。</span><span class="sxs-lookup"><span data-stu-id="45471-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="45471-113">子元素</span><span class="sxs-lookup"><span data-stu-id="45471-113">Child Elements</span></span>

|<span data-ttu-id="45471-114">元素</span><span class="sxs-lookup"><span data-stu-id="45471-114">Element</span></span>|<span data-ttu-id="45471-115">描述</span><span class="sxs-lookup"><span data-stu-id="45471-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="45471-116">GroupBy 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="45471-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="45471-117">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="45471-117">Optional element.</span></span><br /><br /> <span data-ttu-id="45471-118">定義必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="45471-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="45471-119">GroupBy 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="45471-119">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="45471-120">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="45471-120">Optional element.</span></span><br /><br /> <span data-ttu-id="45471-121">指定一組使用此控制項定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="45471-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="45471-122">GroupBy 之 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="45471-122">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="45471-123">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="45471-123">Optional element.</span></span><br /><br /> <span data-ttu-id="45471-124">指定使用此控制項定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="45471-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="45471-125">父項目</span><span class="sxs-lookup"><span data-stu-id="45471-125">Parent Elements</span></span>

|<span data-ttu-id="45471-126">元素</span><span class="sxs-lookup"><span data-stu-id="45471-126">Element</span></span>|<span data-ttu-id="45471-127">描述</span><span class="sxs-lookup"><span data-stu-id="45471-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="45471-128">GroupBy 之 CustomControl 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="45471-128">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="45471-129">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="45471-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="45471-130">備註</span><span class="sxs-lookup"><span data-stu-id="45471-130">Remarks</span></span>

<span data-ttu-id="45471-131">選取條件是用來定義要使用的定義必須存在的條件，例如當物件具有特定屬性或特定屬性值或腳本評估為時 `true` 。</span><span class="sxs-lookup"><span data-stu-id="45471-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="45471-132">如需選取條件的詳細資訊，請參閱[定義使用視圖專案或專案時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="45471-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="45471-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45471-133">See Also</span></span>

[<span data-ttu-id="45471-134">GroupBy 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="45471-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="45471-135">GroupBy 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="45471-135">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="45471-136">GroupBy 之 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="45471-136">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="45471-137">檢視之控制項的 CustomEntries 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="45471-137">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="45471-138">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="45471-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
