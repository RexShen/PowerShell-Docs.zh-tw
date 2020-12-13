---
ms.date: 09/13/2016
ms.topic: reference
title: WideControl 的 WideEntry 元素 (格式)
description: WideControl 的 WideEntry 元素 (格式)
ms.openlocfilehash: 3faaf767d11914792effd6765beed956a502c642
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664548"
---
# <a name="wideentry-element-for-widecontrol-format"></a><span data-ttu-id="62b57-103">WideControl 的 WideEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="62b57-103">WideEntry Element for WideControl (Format)</span></span>

<span data-ttu-id="62b57-104">提供寬視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="62b57-104">Provides a definition of the wide view.</span></span>

<span data-ttu-id="62b57-105">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) WideControl 元素 (格式) WideEntries 元素 (格式) WideEntry 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="62b57-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="62b57-106">語法</span><span class="sxs-lookup"><span data-stu-id="62b57-106">Syntax</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="62b57-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="62b57-107">Attributes and Elements</span></span>

<span data-ttu-id="62b57-108">下列章節說明屬性、子專案和元素的父元素 `WideEntry` 。</span><span class="sxs-lookup"><span data-stu-id="62b57-108">The following sections describe the attributes, child elements, and the parent element of the `WideEntry` element.</span></span> <span data-ttu-id="62b57-109">您必須指定單一 `WideItem` 子項目。</span><span class="sxs-lookup"><span data-stu-id="62b57-109">You must specify a single `WideItem` child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="62b57-110">屬性</span><span class="sxs-lookup"><span data-stu-id="62b57-110">Attributes</span></span>

<span data-ttu-id="62b57-111">無。</span><span class="sxs-lookup"><span data-stu-id="62b57-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="62b57-112">子元素</span><span class="sxs-lookup"><span data-stu-id="62b57-112">Child Elements</span></span>

|<span data-ttu-id="62b57-113">元素</span><span class="sxs-lookup"><span data-stu-id="62b57-113">Element</span></span>|<span data-ttu-id="62b57-114">描述</span><span class="sxs-lookup"><span data-stu-id="62b57-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="62b57-115">WideEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="62b57-115">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="62b57-116">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="62b57-116">Optional element.</span></span><br /><br /> <span data-ttu-id="62b57-117">定義使用此大專案定義的 .NET 型別，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="62b57-117">Defines the .NET types that use this wide entry definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="62b57-118">之 wideitem 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="62b57-118">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="62b57-119">必要元素。</span><span class="sxs-lookup"><span data-stu-id="62b57-119">Required element.</span></span><br /><br /> <span data-ttu-id="62b57-120">定義顯示其值的屬性或腳本。</span><span class="sxs-lookup"><span data-stu-id="62b57-120">Defines the property or script whose value is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="62b57-121">父項目</span><span class="sxs-lookup"><span data-stu-id="62b57-121">Parent Elements</span></span>

|<span data-ttu-id="62b57-122">元素</span><span class="sxs-lookup"><span data-stu-id="62b57-122">Element</span></span>|<span data-ttu-id="62b57-123">描述</span><span class="sxs-lookup"><span data-stu-id="62b57-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="62b57-124">WideEntries 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="62b57-124">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="62b57-125">提供寬視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="62b57-125">Provides the definitions of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="62b57-126">備註</span><span class="sxs-lookup"><span data-stu-id="62b57-126">Remarks</span></span>

<span data-ttu-id="62b57-127">寬型視圖是一種清單格式，可顯示每個物件的單一屬性值或腳本值。</span><span class="sxs-lookup"><span data-stu-id="62b57-127">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="62b57-128">不同于其他類型的視圖，您只能針對每個 view 定義指定一個 item 專案。</span><span class="sxs-lookup"><span data-stu-id="62b57-128">Unlike other types of views, you can specify only one item element for each view definition.</span></span> <span data-ttu-id="62b57-129">如需更多有關廣泛視圖元件的詳細資訊，請參閱 [建立寬視圖](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="62b57-129">For more information about the other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="62b57-130">範例</span><span class="sxs-lookup"><span data-stu-id="62b57-130">Example</span></span>

<span data-ttu-id="62b57-131">下列範例顯示 `WideEntry` 定義單一專案的元素 `WideItem` 。</span><span class="sxs-lookup"><span data-stu-id="62b57-131">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="62b57-132">`WideItem`元素會定義其值會顯示在視圖中的屬性。</span><span class="sxs-lookup"><span data-stu-id="62b57-132">The `WideItem` element defines the property whose value is displayed in the view.</span></span>

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

<span data-ttu-id="62b57-133">如需完整的完整範例，請參閱 [ (基本) 的寬量視圖 ](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="62b57-133">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="62b57-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62b57-134">See Also</span></span>

[<span data-ttu-id="62b57-135">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="62b57-135">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="62b57-136">WideEntry (格式的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="62b57-136">SelectionCondition Element for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="62b57-137">WideEntry (格式的 SelectionSetName 元素) </span><span class="sxs-lookup"><span data-stu-id="62b57-137">SelectionSetName Element for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="62b57-138">WideEntry (格式的 TypeName 元素) </span><span class="sxs-lookup"><span data-stu-id="62b57-138">TypeName Element for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="62b57-139">WideEntries 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="62b57-139">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="62b57-140">之 wideitem 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="62b57-140">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="62b57-141">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="62b57-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
