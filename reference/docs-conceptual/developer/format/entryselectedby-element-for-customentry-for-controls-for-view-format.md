---
title: View 之控制項的 CustomEntry 的之 entryselectedby 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d80a7d-3797-4c46-ae74-ae5cda79b24f
caps.latest.revision: 8
ms.openlocfilehash: efb20c3f2077547e6eb3cb28240512b444f9c481
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363887"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="a9cc1-102">檢視之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a9cc1-102">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="a9cc1-103">定義使用此控制項定義的 .NET 類型，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="a9cc1-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="a9cc1-104">定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="a9cc1-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="a9cc1-105">設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 專案（格式）控制項的控制項專案（格式） CustomControl 元素，用於控制項的 View （Format） CustomEntries 元素CustomControl for view （format） CustomEntry 元素的 CustomEntries for view （format）之 entryselectedby 元素 for view （format）控制項的 CustomEntry 的控制項</span><span class="sxs-lookup"><span data-stu-id="a9cc1-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a9cc1-106">語法</span><span class="sxs-lookup"><span data-stu-id="a9cc1-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a9cc1-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="a9cc1-107">Attributes and Elements</span></span>

<span data-ttu-id="a9cc1-108">下列各節描述 `EntrySelectedBy` 元素的屬性、子專案和父元素。</span><span class="sxs-lookup"><span data-stu-id="a9cc1-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="a9cc1-109">您必須為定義指定至少一個類型、選取集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="a9cc1-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="a9cc1-110">您可以使用的子項目數目沒有上限。</span><span class="sxs-lookup"><span data-stu-id="a9cc1-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="a9cc1-111">屬性</span><span class="sxs-lookup"><span data-stu-id="a9cc1-111">Attributes</span></span>

<span data-ttu-id="a9cc1-112">無。</span><span class="sxs-lookup"><span data-stu-id="a9cc1-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a9cc1-113">子元素</span><span class="sxs-lookup"><span data-stu-id="a9cc1-113">Child Elements</span></span>

|<span data-ttu-id="a9cc1-114">元素</span><span class="sxs-lookup"><span data-stu-id="a9cc1-114">Element</span></span>|<span data-ttu-id="a9cc1-115">描述</span><span class="sxs-lookup"><span data-stu-id="a9cc1-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a9cc1-116">View 之控制項的之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a9cc1-116">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="a9cc1-117">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="a9cc1-117">Optional element.</span></span><br /><br /> <span data-ttu-id="a9cc1-118">定義必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="a9cc1-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="a9cc1-119">View 之控制項的之 entryselectedby 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a9cc1-119">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="a9cc1-120">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="a9cc1-120">Optional element.</span></span><br /><br /> <span data-ttu-id="a9cc1-121">指定一組使用此控制項定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="a9cc1-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="a9cc1-122">View 之控制項的之 entryselectedby 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a9cc1-122">TypeName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="a9cc1-123">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="a9cc1-123">Optional element.</span></span><br /><br /> <span data-ttu-id="a9cc1-124">指定使用此控制項定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="a9cc1-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a9cc1-125">父元素</span><span class="sxs-lookup"><span data-stu-id="a9cc1-125">Parent Elements</span></span>

|<span data-ttu-id="a9cc1-126">元素</span><span class="sxs-lookup"><span data-stu-id="a9cc1-126">Element</span></span>|<span data-ttu-id="a9cc1-127">描述</span><span class="sxs-lookup"><span data-stu-id="a9cc1-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a9cc1-128">View 之控制項的 CustomEntries 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a9cc1-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="a9cc1-129">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="a9cc1-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a9cc1-130">備註</span><span class="sxs-lookup"><span data-stu-id="a9cc1-130">Remarks</span></span>

<span data-ttu-id="a9cc1-131">選取條件是用來定義要使用的定義必須存在的條件，例如當物件具有特定屬性時，或特定屬性值或腳本評估為 `true` 時。</span><span class="sxs-lookup"><span data-stu-id="a9cc1-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="a9cc1-132">如需選取條件的詳細資訊，請參閱[定義使用視圖專案或專案時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="a9cc1-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a9cc1-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9cc1-133">See Also</span></span>

[<span data-ttu-id="a9cc1-134">View 之控制項的 CustomEntries 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a9cc1-134">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="a9cc1-135">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="a9cc1-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
