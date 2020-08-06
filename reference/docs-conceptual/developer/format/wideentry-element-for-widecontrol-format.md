---
title: WideControl (格式的 WideEntry 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 13dd1f6ad7ac1e9d8d0524f0a0f18fe80ffaf8e2
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780010"
---
# <a name="wideentry-element-for-widecontrol-format"></a><span data-ttu-id="2975f-102">WideControl 的 WideEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2975f-102">WideEntry Element for WideControl (Format)</span></span>

<span data-ttu-id="2975f-103">提供寬視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="2975f-103">Provides a definition of the wide view.</span></span>

<span data-ttu-id="2975f-104">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) WideControl 元素 (格式) WideEntries 專案 (格式) WideEntry 專案 (格式) </span><span class="sxs-lookup"><span data-stu-id="2975f-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2975f-105">語法</span><span class="sxs-lookup"><span data-stu-id="2975f-105">Syntax</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2975f-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2975f-106">Attributes and Elements</span></span>

<span data-ttu-id="2975f-107">下列各節說明屬性、子專案和元素的父元素 `WideEntry` 。</span><span class="sxs-lookup"><span data-stu-id="2975f-107">The following sections describe the attributes, child elements, and the parent element of the `WideEntry` element.</span></span> <span data-ttu-id="2975f-108">您必須指定單一 `WideItem` 子項目。</span><span class="sxs-lookup"><span data-stu-id="2975f-108">You must specify a single `WideItem` child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2975f-109">屬性</span><span class="sxs-lookup"><span data-stu-id="2975f-109">Attributes</span></span>

<span data-ttu-id="2975f-110">無。</span><span class="sxs-lookup"><span data-stu-id="2975f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2975f-111">子元素</span><span class="sxs-lookup"><span data-stu-id="2975f-111">Child Elements</span></span>

|<span data-ttu-id="2975f-112">元素</span><span class="sxs-lookup"><span data-stu-id="2975f-112">Element</span></span>|<span data-ttu-id="2975f-113">描述</span><span class="sxs-lookup"><span data-stu-id="2975f-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2975f-114">WideEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2975f-114">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="2975f-115">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="2975f-115">Optional element.</span></span><br /><br /> <span data-ttu-id="2975f-116">定義使用此寬專案定義的 .NET 類型，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="2975f-116">Defines the .NET types that use this wide entry definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="2975f-117">之 wideitem 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="2975f-117">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="2975f-118">必要元素。</span><span class="sxs-lookup"><span data-stu-id="2975f-118">Required element.</span></span><br /><br /> <span data-ttu-id="2975f-119">定義顯示其值的屬性或腳本。</span><span class="sxs-lookup"><span data-stu-id="2975f-119">Defines the property or script whose value is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2975f-120">父項目</span><span class="sxs-lookup"><span data-stu-id="2975f-120">Parent Elements</span></span>

|<span data-ttu-id="2975f-121">元素</span><span class="sxs-lookup"><span data-stu-id="2975f-121">Element</span></span>|<span data-ttu-id="2975f-122">描述</span><span class="sxs-lookup"><span data-stu-id="2975f-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2975f-123">WideEntries 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="2975f-123">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="2975f-124">提供寬視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="2975f-124">Provides the definitions of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2975f-125">備註</span><span class="sxs-lookup"><span data-stu-id="2975f-125">Remarks</span></span>

<span data-ttu-id="2975f-126">寬型視圖是一種清單格式，可顯示每個物件的單一屬性值或腳本值。</span><span class="sxs-lookup"><span data-stu-id="2975f-126">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="2975f-127">不同于其他類型的視圖，您只能為每個 view 定義指定一個 item 元素。</span><span class="sxs-lookup"><span data-stu-id="2975f-127">Unlike other types of views, you can specify only one item element for each view definition.</span></span> <span data-ttu-id="2975f-128">如需有關寬視圖之其他元件的詳細資訊，請參閱[建立寬視圖](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="2975f-128">For more information about the other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="2975f-129">範例</span><span class="sxs-lookup"><span data-stu-id="2975f-129">Example</span></span>

<span data-ttu-id="2975f-130">下列範例顯示 `WideEntry` 定義單一專案的元素 `WideItem` 。</span><span class="sxs-lookup"><span data-stu-id="2975f-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="2975f-131">`WideItem`元素會定義屬性，其值會顯示在視圖中。</span><span class="sxs-lookup"><span data-stu-id="2975f-131">The `WideItem` element defines the property whose value is displayed in the view.</span></span>

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

<span data-ttu-id="2975f-132">如需寬視圖的完整範例，請參閱[寬視圖 (基本) ](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="2975f-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2975f-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2975f-133">See Also</span></span>

[<span data-ttu-id="2975f-134">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="2975f-134">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="2975f-135">WideEntry (格式的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="2975f-135">SelectionCondition Element for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="2975f-136">WideEntry (格式的 SelectionSetName 元素) </span><span class="sxs-lookup"><span data-stu-id="2975f-136">SelectionSetName Element for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="2975f-137">WideEntry (格式的 TypeName 元素) </span><span class="sxs-lookup"><span data-stu-id="2975f-137">TypeName Element for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="2975f-138">WideEntries 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="2975f-138">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="2975f-139">之 wideitem 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="2975f-139">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="2975f-140">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="2975f-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
