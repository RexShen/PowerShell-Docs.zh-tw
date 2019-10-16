---
title: WideEntry 的之 entryselectedby 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0c98933-b7a5-4205-b811-06c0b0bf8988
caps.latest.revision: 9
ms.openlocfilehash: 54c7c261a23075721cd7bce75e530150dc0e0212
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363327"
---
# <a name="entryselectedby-element-for-wideentry-format"></a><span data-ttu-id="d5393-102">WideEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d5393-102">EntrySelectedBy Element for WideEntry (Format)</span></span>

<span data-ttu-id="d5393-103">定義使用此寬視圖定義的 .NET 類型，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="d5393-103">Defines the .NET types that use this definition of the wide view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="d5393-104">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） WideControl 元素（格式） WideEntries 元素（格式） WideEntry 元素（格式）之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d5393-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d5393-105">語法</span><span class="sxs-lookup"><span data-stu-id="d5393-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d5393-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="d5393-106">Attributes and Elements</span></span>

<span data-ttu-id="d5393-107">下列各節說明屬性、子專案，以及 `EntrySelectedBy` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="d5393-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d5393-108">屬性</span><span class="sxs-lookup"><span data-stu-id="d5393-108">Attributes</span></span>

<span data-ttu-id="d5393-109">無。</span><span class="sxs-lookup"><span data-stu-id="d5393-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d5393-110">子元素</span><span class="sxs-lookup"><span data-stu-id="d5393-110">Child Elements</span></span>

|<span data-ttu-id="d5393-111">元素</span><span class="sxs-lookup"><span data-stu-id="d5393-111">Element</span></span>|<span data-ttu-id="d5393-112">描述</span><span class="sxs-lookup"><span data-stu-id="d5393-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d5393-113">WideEntry 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d5393-113">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="d5393-114">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="d5393-114">Optional element.</span></span><br /><br /> <span data-ttu-id="d5393-115">定義必須存在的條件，才能使用此寬視圖定義。</span><span class="sxs-lookup"><span data-stu-id="d5393-115">Defines the condition that must exist for this wide view definition to be used.</span></span>|
|[<span data-ttu-id="d5393-116">WideEntry 之之 entryselectedby 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d5393-116">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="d5393-117">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="d5393-117">Optional element.</span></span><br /><br /> <span data-ttu-id="d5393-118">指定一組使用此寬視圖定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="d5393-118">Specifies a set of .NET types that use this wide view definition.</span></span>|
|[<span data-ttu-id="d5393-119">WideEntry 之之 entryselectedby 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d5393-119">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="d5393-120">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="d5393-120">Optional element.</span></span><br /><br /> <span data-ttu-id="d5393-121">指定使用此寬視圖定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="d5393-121">Specifies a .NET type that uses this wide view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d5393-122">父元素</span><span class="sxs-lookup"><span data-stu-id="d5393-122">Parent Elements</span></span>

|<span data-ttu-id="d5393-123">元素</span><span class="sxs-lookup"><span data-stu-id="d5393-123">Element</span></span>|<span data-ttu-id="d5393-124">描述</span><span class="sxs-lookup"><span data-stu-id="d5393-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d5393-125">WideEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d5393-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="d5393-126">提供寬視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="d5393-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d5393-127">備註</span><span class="sxs-lookup"><span data-stu-id="d5393-127">Remarks</span></span>

<span data-ttu-id="d5393-128">您必須為寬視圖定義指定至少一個類型、選取範圍或選取條件。</span><span class="sxs-lookup"><span data-stu-id="d5393-128">You must specify at least one type, selection set, or selection condition for a wide view definition.</span></span> <span data-ttu-id="d5393-129">您可以使用的子項目數目沒有上限。</span><span class="sxs-lookup"><span data-stu-id="d5393-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="d5393-130">選取條件是用來定義要使用的定義必須存在的條件，例如，當物件具有特定屬性，或特定屬性值或腳本值評估為 `true` 時。</span><span class="sxs-lookup"><span data-stu-id="d5393-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script value evaluates to `true`.</span></span> <span data-ttu-id="d5393-131">如需選取條件的詳細資訊，請參閱[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="d5393-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="d5393-132">如需有關寬視圖之其他元件的詳細資訊，請參閱[建立寬視圖](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="d5393-132">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d5393-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5393-133">See Also</span></span>

[<span data-ttu-id="d5393-134">WideEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d5393-134">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="d5393-135">WideEntry 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d5393-135">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="d5393-136">WideEntry 之之 entryselectedby 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d5393-136">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="d5393-137">WideEntry 之之 entryselectedby 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d5393-137">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="d5393-138">建立寬型視圖</span><span class="sxs-lookup"><span data-stu-id="d5393-138">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="d5393-139">定義顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="d5393-139">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="d5393-140">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="d5393-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
