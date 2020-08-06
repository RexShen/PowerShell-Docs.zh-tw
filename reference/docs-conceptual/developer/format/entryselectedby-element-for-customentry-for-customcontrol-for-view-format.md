---
title: CustomControl for View (格式) 的 CustomEntry 的之 entryselectedby 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4d4900cefb0d499397fc9dff7e037ce0a541f72f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783682"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="77e3c-102">檢視之 CustomControl 的 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="77e3c-102">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="77e3c-103">定義使用此自訂專案的 .NET 類型，或必須存在才能使用此專案的條件。</span><span class="sxs-lookup"><span data-stu-id="77e3c-103">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>

<span data-ttu-id="77e3c-104">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) CustomControl 專案 (格式) CustomControl for view (CustomEntry 元素（CustomEntries for view) 之 entryselectedby 元素的 CustomEntry for view (格式) </span><span class="sxs-lookup"><span data-stu-id="77e3c-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="77e3c-105">語法</span><span class="sxs-lookup"><span data-stu-id="77e3c-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="77e3c-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="77e3c-106">Attributes and Elements</span></span>

<span data-ttu-id="77e3c-107">下列各節說明屬性、子專案和元素的父元素 `EntrySelectedBy` 。</span><span class="sxs-lookup"><span data-stu-id="77e3c-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="77e3c-108">屬性</span><span class="sxs-lookup"><span data-stu-id="77e3c-108">Attributes</span></span>

<span data-ttu-id="77e3c-109">無。</span><span class="sxs-lookup"><span data-stu-id="77e3c-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="77e3c-110">子元素</span><span class="sxs-lookup"><span data-stu-id="77e3c-110">Child Elements</span></span>

|<span data-ttu-id="77e3c-111">元素</span><span class="sxs-lookup"><span data-stu-id="77e3c-111">Element</span></span>|<span data-ttu-id="77e3c-112">描述</span><span class="sxs-lookup"><span data-stu-id="77e3c-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="77e3c-113">CustomEntry (格式的之 entryselectedby 的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="77e3c-113">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="77e3c-114">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="77e3c-114">Optional element.</span></span><br /><br /> <span data-ttu-id="77e3c-115">定義必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="77e3c-115">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="77e3c-116">CustomEntry (格式的之 entryselectedby 的 SelectionSetName 元素) </span><span class="sxs-lookup"><span data-stu-id="77e3c-116">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|<span data-ttu-id="77e3c-117">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="77e3c-117">Optional element.</span></span><br /><br /> <span data-ttu-id="77e3c-118">指定一組使用此控制項視圖定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="77e3c-118">Specifies a set of .NET types that use this definition of the control view.</span></span>|
|[<span data-ttu-id="77e3c-119">之 entryselectedby for CustomEntry (格式的 TypeName 元素) </span><span class="sxs-lookup"><span data-stu-id="77e3c-119">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="77e3c-120">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="77e3c-120">Optional element.</span></span><br /><br /> <span data-ttu-id="77e3c-121">指定使用此控制項視圖定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="77e3c-121">Specifies a .NET type that uses this definition of the control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="77e3c-122">父項目</span><span class="sxs-lookup"><span data-stu-id="77e3c-122">Parent Elements</span></span>

|<span data-ttu-id="77e3c-123">元素</span><span class="sxs-lookup"><span data-stu-id="77e3c-123">Element</span></span>|<span data-ttu-id="77e3c-124">描述</span><span class="sxs-lookup"><span data-stu-id="77e3c-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="77e3c-125">CustomEntries for View (格式的 CustomEntry 元素) </span><span class="sxs-lookup"><span data-stu-id="77e3c-125">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="77e3c-126">定義特定 .NET 物件所使用的控制項。</span><span class="sxs-lookup"><span data-stu-id="77e3c-126">Defines the controls used by specific .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="77e3c-127">備註</span><span class="sxs-lookup"><span data-stu-id="77e3c-127">Remarks</span></span>

<span data-ttu-id="77e3c-128">您必須為專案指定至少一種類型、選擇集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="77e3c-128">You must specify at least one type, selection set, or selection condition for an entry.</span></span> <span data-ttu-id="77e3c-129">您可以使用的子項目數目沒有上限。</span><span class="sxs-lookup"><span data-stu-id="77e3c-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="77e3c-130">選取條件是用來定義必須存在才能使用之專案的條件，例如當物件具有特定屬性時，或特定屬性值或腳本評估為時 `true` 。</span><span class="sxs-lookup"><span data-stu-id="77e3c-130">Selection conditions are used to define a condition that must exist for the entry to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="77e3c-131">如需選取條件的詳細資訊，請參閱[定義使用視圖專案或專案時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="77e3c-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="77e3c-132">如需自訂控制項視圖之元件的詳細資訊，請參閱[自訂控制項視圖](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="77e3c-132">For more information about the components of a custom control view, see [Custom Control View](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="77e3c-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77e3c-133">See Also</span></span>

[<span data-ttu-id="77e3c-134">CustomEntry (格式的之 entryselectedby 的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="77e3c-134">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="77e3c-135">CustomEntry (格式的之 entryselectedby 的 SelectionSetName 元素) </span><span class="sxs-lookup"><span data-stu-id="77e3c-135">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[<span data-ttu-id="77e3c-136">之 entryselectedby for CustomEntry (格式的 TypeName 元素) </span><span class="sxs-lookup"><span data-stu-id="77e3c-136">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="77e3c-137">CustomEntries for View (格式的 CustomEntry 元素) </span><span class="sxs-lookup"><span data-stu-id="77e3c-137">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="77e3c-138">自訂控制項視圖</span><span class="sxs-lookup"><span data-stu-id="77e3c-138">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="77e3c-139">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="77e3c-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
