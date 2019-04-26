---
title: WideEntry WideControl （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 014763cb-7716-4931-899c-8375b5d7a3dd
caps.latest.revision: 15
ms.openlocfilehash: d1d13b5c3436871053353814293d9163ea13c7fb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083666"
---
# <a name="wideentry-element-for-widecontrol-format"></a><span data-ttu-id="cef81-102">WideControl 的 WideEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="cef81-102">WideEntry Element for WideControl (Format)</span></span>

<span data-ttu-id="cef81-103">提供寬型檢視的定義。</span><span class="sxs-lookup"><span data-stu-id="cef81-103">Provides a definition of the wide view.</span></span>

<span data-ttu-id="cef81-104">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） WideControl 項目 （格式） WideEntries 項目 （格式） WideEntry 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="cef81-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cef81-105">語法</span><span class="sxs-lookup"><span data-stu-id="cef81-105">Syntax</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cef81-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cef81-106">Attributes and Elements</span></span>

<span data-ttu-id="cef81-107">下列各節說明屬性、 子項目和父項目`WideEntry`項目。</span><span class="sxs-lookup"><span data-stu-id="cef81-107">The following sections describe the attributes, child elements, and the parent element of the `WideEntry` element.</span></span> <span data-ttu-id="cef81-108">您必須指定單一`WideItem`子項目。</span><span class="sxs-lookup"><span data-stu-id="cef81-108">You must specify a single `WideItem` child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cef81-109">屬性</span><span class="sxs-lookup"><span data-stu-id="cef81-109">Attributes</span></span>

<span data-ttu-id="cef81-110">無。</span><span class="sxs-lookup"><span data-stu-id="cef81-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cef81-111">子元素</span><span class="sxs-lookup"><span data-stu-id="cef81-111">Child Elements</span></span>

|<span data-ttu-id="cef81-112">元素</span><span class="sxs-lookup"><span data-stu-id="cef81-112">Element</span></span>|<span data-ttu-id="cef81-113">描述</span><span class="sxs-lookup"><span data-stu-id="cef81-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cef81-114">EntrySelectedBy WideEntry （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="cef81-114">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="cef81-115">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="cef81-115">Optional element.</span></span><br /><br /> <span data-ttu-id="cef81-116">定義使用此寬的項目定義或必須存在於要使用此定義條件的.NET 類型。</span><span class="sxs-lookup"><span data-stu-id="cef81-116">Defines the .NET types that use this wide entry definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="cef81-117">WideItem 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="cef81-117">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="cef81-118">必要項目。</span><span class="sxs-lookup"><span data-stu-id="cef81-118">Required element.</span></span><br /><br /> <span data-ttu-id="cef81-119">定義屬性或其值會顯示指令碼。</span><span class="sxs-lookup"><span data-stu-id="cef81-119">Defines the property or script whose value is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cef81-120">父項目</span><span class="sxs-lookup"><span data-stu-id="cef81-120">Parent Elements</span></span>

|<span data-ttu-id="cef81-121">項目</span><span class="sxs-lookup"><span data-stu-id="cef81-121">Element</span></span>|<span data-ttu-id="cef81-122">描述</span><span class="sxs-lookup"><span data-stu-id="cef81-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cef81-123">WideEntries 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="cef81-123">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="cef81-124">提供的寬型檢視的定義。</span><span class="sxs-lookup"><span data-stu-id="cef81-124">Provides the definitions of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cef81-125">備註</span><span class="sxs-lookup"><span data-stu-id="cef81-125">Remarks</span></span>

<span data-ttu-id="cef81-126">寬型檢視是顯示單一屬性值或每個物件的指令碼值以清單格式。</span><span class="sxs-lookup"><span data-stu-id="cef81-126">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="cef81-127">不同於其他類型的檢視中，您可以指定只有一個項目元素的每個檢視定義。</span><span class="sxs-lookup"><span data-stu-id="cef81-127">Unlike other types of views, you can specify only one item element for each view definition.</span></span> <span data-ttu-id="cef81-128">寬型檢視的其他元件的相關資訊，請參閱[建立寬型檢視](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="cef81-128">For more information about the other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="cef81-129">範例</span><span class="sxs-lookup"><span data-stu-id="cef81-129">Example</span></span>

<span data-ttu-id="cef81-130">下列範例所示`WideEntry`項目，定義單一`WideItem`項目。</span><span class="sxs-lookup"><span data-stu-id="cef81-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="cef81-131">`WideItem`項目會定義在檢視中顯示其值的屬性。</span><span class="sxs-lookup"><span data-stu-id="cef81-131">The `WideItem` element defines the property whose value is displayed in the view.</span></span>

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

<span data-ttu-id="cef81-132">寬型檢視的完整範例，請參閱[（基本） 的寬型檢視](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="cef81-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cef81-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cef81-133">See Also</span></span>

[<span data-ttu-id="cef81-134">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="cef81-134">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="cef81-135">SelectionCondition WideEntry （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="cef81-135">SelectionCondition Element for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="cef81-136">SelectionSetName WideEntry （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="cef81-136">SelectionSetName Element for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="cef81-137">TypeName WideEntry （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="cef81-137">TypeName Element for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="cef81-138">WideEntries 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="cef81-138">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="cef81-139">WideItem 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="cef81-139">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="cef81-140">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="cef81-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
