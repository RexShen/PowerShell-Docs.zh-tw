---
title: 用於檢視 （格式） 的控制項 CustomEntry EntrySelectedBy 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d80a7d-3797-4c46-ae74-ae5cda79b24f
caps.latest.revision: 8
ms.openlocfilehash: efb20c3f2077547e6eb3cb28240512b444f9c481
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859534"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="004c9-102">檢視之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="004c9-102">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="004c9-103">定義使用此控制項定義或必須存在於要使用此定義條件的.NET 類型。</span><span class="sxs-lookup"><span data-stu-id="004c9-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="004c9-104">定義可供檢視的控制項時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="004c9-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="004c9-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） 項目 （格式） 控制項的 Controls 項目控制項的檢視 （格式） CustomEntries 項目控制項的控制項的檢視 （格式） CustomControl 項目CustomControl CustomEntries CustomEntry 用於檢視 （格式） 的控制項的檢視 （格式） EntrySelectedBy 元素的控制項的檢視 （格式） CustomEntry 元素的控制項</span><span class="sxs-lookup"><span data-stu-id="004c9-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="004c9-106">語法</span><span class="sxs-lookup"><span data-stu-id="004c9-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="004c9-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="004c9-107">Attributes and Elements</span></span>

<span data-ttu-id="004c9-108">下列各節說明屬性、 子項目和父項目`EntrySelectedBy`項目。</span><span class="sxs-lookup"><span data-stu-id="004c9-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="004c9-109">您必須指定至少一個型別、 選取項目集或選擇條件的定義。</span><span class="sxs-lookup"><span data-stu-id="004c9-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="004c9-110">沒有任何子項目的，您可以使用數字的最大限制。</span><span class="sxs-lookup"><span data-stu-id="004c9-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="004c9-111">屬性</span><span class="sxs-lookup"><span data-stu-id="004c9-111">Attributes</span></span>

<span data-ttu-id="004c9-112">無。</span><span class="sxs-lookup"><span data-stu-id="004c9-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="004c9-113">子元素</span><span class="sxs-lookup"><span data-stu-id="004c9-113">Child Elements</span></span>

|<span data-ttu-id="004c9-114">元素</span><span class="sxs-lookup"><span data-stu-id="004c9-114">Element</span></span>|<span data-ttu-id="004c9-115">描述</span><span class="sxs-lookup"><span data-stu-id="004c9-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="004c9-116">用於檢視 （格式） 的控制項 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="004c9-116">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="004c9-117">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="004c9-117">Optional element.</span></span><br /><br /> <span data-ttu-id="004c9-118">定義要使用此定義必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="004c9-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="004c9-119">用於檢視 （格式） 的控制項 EntrySelectedBy SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="004c9-119">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="004c9-120">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="004c9-120">Optional element.</span></span><br /><br /> <span data-ttu-id="004c9-121">指定一組使用這個控制項定義的.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="004c9-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="004c9-122">用於檢視 （格式） 的控制項 EntrySelectedBy TypeName 項目</span><span class="sxs-lookup"><span data-stu-id="004c9-122">TypeName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="004c9-123">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="004c9-123">Optional element.</span></span><br /><br /> <span data-ttu-id="004c9-124">指定使用這個控制項定義的.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="004c9-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="004c9-125">父元素</span><span class="sxs-lookup"><span data-stu-id="004c9-125">Parent Elements</span></span>

|<span data-ttu-id="004c9-126">元素</span><span class="sxs-lookup"><span data-stu-id="004c9-126">Element</span></span>|<span data-ttu-id="004c9-127">描述</span><span class="sxs-lookup"><span data-stu-id="004c9-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="004c9-128">用於檢視 （格式） 的控制項 CustomEntries CustomEntry 項目</span><span class="sxs-lookup"><span data-stu-id="004c9-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="004c9-129">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="004c9-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="004c9-130">備註</span><span class="sxs-lookup"><span data-stu-id="004c9-130">Remarks</span></span>

<span data-ttu-id="004c9-131">選擇條件用來定義的條件必須存在於使用定義，例如當物件只有特定的屬性時，或特定的屬性值，或指令碼會評估`true`。</span><span class="sxs-lookup"><span data-stu-id="004c9-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="004c9-132">如需有關選擇條件的詳細資訊，請參閱[定義條件時檢視項目或項目用](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="004c9-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="004c9-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="004c9-133">See Also</span></span>

[<span data-ttu-id="004c9-134">用於檢視 （格式） 的控制項 CustomEntries CustomEntry 項目</span><span class="sxs-lookup"><span data-stu-id="004c9-134">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="004c9-135">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="004c9-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
