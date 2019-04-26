---
title: EntrySelectedBy WideEntry （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0c98933-b7a5-4205-b811-06c0b0bf8988
caps.latest.revision: 9
ms.openlocfilehash: 54c7c261a23075721cd7bce75e530150dc0e0212
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066170"
---
# <a name="entryselectedby-element-for-wideentry-format"></a><span data-ttu-id="7b901-102">WideEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7b901-102">EntrySelectedBy Element for WideEntry (Format)</span></span>

<span data-ttu-id="7b901-103">定義使用此定義的寬型檢視或條件必須存在於要使用此定義的.NET 類型。</span><span class="sxs-lookup"><span data-stu-id="7b901-103">Defines the .NET types that use this definition of the wide view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="7b901-104">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） WideControl 項目 （格式） WideEntries 項目 （格式） WideEntry 項目 （格式） EntrySelectedBy 項目 WideEntry （格式）</span><span class="sxs-lookup"><span data-stu-id="7b901-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7b901-105">語法</span><span class="sxs-lookup"><span data-stu-id="7b901-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7b901-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7b901-106">Attributes and Elements</span></span>

<span data-ttu-id="7b901-107">下列各節說明屬性、 子項目和父項目`EntrySelectedBy`項目。</span><span class="sxs-lookup"><span data-stu-id="7b901-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7b901-108">屬性</span><span class="sxs-lookup"><span data-stu-id="7b901-108">Attributes</span></span>

<span data-ttu-id="7b901-109">無。</span><span class="sxs-lookup"><span data-stu-id="7b901-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7b901-110">子元素</span><span class="sxs-lookup"><span data-stu-id="7b901-110">Child Elements</span></span>

|<span data-ttu-id="7b901-111">元素</span><span class="sxs-lookup"><span data-stu-id="7b901-111">Element</span></span>|<span data-ttu-id="7b901-112">描述</span><span class="sxs-lookup"><span data-stu-id="7b901-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7b901-113">WideEntry （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="7b901-113">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="7b901-114">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="7b901-114">Optional element.</span></span><br /><br /> <span data-ttu-id="7b901-115">定義要使用此寬型檢視定義必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="7b901-115">Defines the condition that must exist for this wide view definition to be used.</span></span>|
|[<span data-ttu-id="7b901-116">WideEntry （格式） 的 EntrySelectedBy SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="7b901-116">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="7b901-117">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="7b901-117">Optional element.</span></span><br /><br /> <span data-ttu-id="7b901-118">指定一組使用此寬型檢視定義的.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="7b901-118">Specifies a set of .NET types that use this wide view definition.</span></span>|
|[<span data-ttu-id="7b901-119">WideEntry （格式） 的 EntrySelectedBy TypeName 項目</span><span class="sxs-lookup"><span data-stu-id="7b901-119">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="7b901-120">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="7b901-120">Optional element.</span></span><br /><br /> <span data-ttu-id="7b901-121">指定使用此寬型檢視定義的.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="7b901-121">Specifies a .NET type that uses this wide view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7b901-122">父項目</span><span class="sxs-lookup"><span data-stu-id="7b901-122">Parent Elements</span></span>

|<span data-ttu-id="7b901-123">項目</span><span class="sxs-lookup"><span data-stu-id="7b901-123">Element</span></span>|<span data-ttu-id="7b901-124">描述</span><span class="sxs-lookup"><span data-stu-id="7b901-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7b901-125">WideEntry 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="7b901-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="7b901-126">提供寬型檢視的定義。</span><span class="sxs-lookup"><span data-stu-id="7b901-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7b901-127">備註</span><span class="sxs-lookup"><span data-stu-id="7b901-127">Remarks</span></span>

<span data-ttu-id="7b901-128">您必須指定至少一個型別、 選取項目集或選擇條件的寬型檢視定義。</span><span class="sxs-lookup"><span data-stu-id="7b901-128">You must specify at least one type, selection set, or selection condition for a wide view definition.</span></span> <span data-ttu-id="7b901-129">沒有任何子項目的，您可以使用數字的最大限制。</span><span class="sxs-lookup"><span data-stu-id="7b901-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="7b901-130">選擇條件用來定義要使用，例如當物件具有特定屬性的定義必須存在的條件，或特定的屬性值或指令碼的值評估為`true`。</span><span class="sxs-lookup"><span data-stu-id="7b901-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script value evaluates to `true`.</span></span> <span data-ttu-id="7b901-131">如需有關選擇條件的詳細資訊，請參閱[定義的條件，顯示資料](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="7b901-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="7b901-132">寬型檢視的其他元件的相關資訊，請參閱[建立寬型檢視](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="7b901-132">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7b901-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b901-133">See Also</span></span>

[<span data-ttu-id="7b901-134">WideEntry 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="7b901-134">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="7b901-135">WideEntry （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="7b901-135">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="7b901-136">WideEntry （格式） 的 EntrySelectedBy SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="7b901-136">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="7b901-137">WideEntry （格式） 的 EntrySelectedBy TypeName 項目</span><span class="sxs-lookup"><span data-stu-id="7b901-137">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="7b901-138">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="7b901-138">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="7b901-139">定義用於顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="7b901-139">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="7b901-140">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="7b901-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
