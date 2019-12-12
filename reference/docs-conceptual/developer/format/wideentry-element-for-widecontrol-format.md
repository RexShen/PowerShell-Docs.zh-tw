---
title: WideControl 的 WideEntry 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 014763cb-7716-4931-899c-8375b5d7a3dd
caps.latest.revision: 15
ms.openlocfilehash: d1d13b5c3436871053353814293d9163ea13c7fb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367897"
---
# <a name="wideentry-element-for-widecontrol-format"></a><span data-ttu-id="c231a-102">WideControl 的 WideEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c231a-102">WideEntry Element for WideControl (Format)</span></span>

<span data-ttu-id="c231a-103">提供寬視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="c231a-103">Provides a definition of the wide view.</span></span>

<span data-ttu-id="c231a-104">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（格式） WideControl 元素（格式） WideEntries 元素（格式） WideEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c231a-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c231a-105">語法</span><span class="sxs-lookup"><span data-stu-id="c231a-105">Syntax</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c231a-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="c231a-106">Attributes and Elements</span></span>

<span data-ttu-id="c231a-107">下列各節說明屬性、子專案，以及 `WideEntry` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="c231a-107">The following sections describe the attributes, child elements, and the parent element of the `WideEntry` element.</span></span> <span data-ttu-id="c231a-108">您必須指定單一 `WideItem` 子項目。</span><span class="sxs-lookup"><span data-stu-id="c231a-108">You must specify a single `WideItem` child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c231a-109">屬性</span><span class="sxs-lookup"><span data-stu-id="c231a-109">Attributes</span></span>

<span data-ttu-id="c231a-110">無。</span><span class="sxs-lookup"><span data-stu-id="c231a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c231a-111">子元素</span><span class="sxs-lookup"><span data-stu-id="c231a-111">Child Elements</span></span>

|<span data-ttu-id="c231a-112">元素</span><span class="sxs-lookup"><span data-stu-id="c231a-112">Element</span></span>|<span data-ttu-id="c231a-113">描述</span><span class="sxs-lookup"><span data-stu-id="c231a-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c231a-114">WideEntry 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c231a-114">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="c231a-115">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="c231a-115">Optional element.</span></span><br /><br /> <span data-ttu-id="c231a-116">定義使用此寬專案定義的 .NET 類型，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="c231a-116">Defines the .NET types that use this wide entry definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="c231a-117">之 wideitem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c231a-117">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="c231a-118">必要項目。</span><span class="sxs-lookup"><span data-stu-id="c231a-118">Required element.</span></span><br /><br /> <span data-ttu-id="c231a-119">定義顯示其值的屬性或腳本。</span><span class="sxs-lookup"><span data-stu-id="c231a-119">Defines the property or script whose value is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c231a-120">父元素</span><span class="sxs-lookup"><span data-stu-id="c231a-120">Parent Elements</span></span>

|<span data-ttu-id="c231a-121">元素</span><span class="sxs-lookup"><span data-stu-id="c231a-121">Element</span></span>|<span data-ttu-id="c231a-122">描述</span><span class="sxs-lookup"><span data-stu-id="c231a-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c231a-123">WideEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c231a-123">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="c231a-124">提供寬視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="c231a-124">Provides the definitions of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c231a-125">備註</span><span class="sxs-lookup"><span data-stu-id="c231a-125">Remarks</span></span>

<span data-ttu-id="c231a-126">寬型視圖是一種清單格式，可顯示每個物件的單一屬性值或腳本值。</span><span class="sxs-lookup"><span data-stu-id="c231a-126">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="c231a-127">不同于其他類型的視圖，您只能為每個 view 定義指定一個 item 元素。</span><span class="sxs-lookup"><span data-stu-id="c231a-127">Unlike other types of views, you can specify only one item element for each view definition.</span></span> <span data-ttu-id="c231a-128">如需有關寬視圖之其他元件的詳細資訊，請參閱[建立寬視圖](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="c231a-128">For more information about the other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c231a-129">範例</span><span class="sxs-lookup"><span data-stu-id="c231a-129">Example</span></span>

<span data-ttu-id="c231a-130">下列範例顯示定義單一 `WideItem` 元素的 `WideEntry` 專案。</span><span class="sxs-lookup"><span data-stu-id="c231a-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="c231a-131">`WideItem` 元素會定義屬性，其值會顯示在視圖中。</span><span class="sxs-lookup"><span data-stu-id="c231a-131">The `WideItem` element defines the property whose value is displayed in the view.</span></span>

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

<span data-ttu-id="c231a-132">如需寬視圖的完整範例，請參閱[寬視圖（基本）](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="c231a-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c231a-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c231a-133">See Also</span></span>

[<span data-ttu-id="c231a-134">建立寬型視圖</span><span class="sxs-lookup"><span data-stu-id="c231a-134">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="c231a-135">WideEntry 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c231a-135">SelectionCondition Element for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="c231a-136">WideEntry 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c231a-136">SelectionSetName Element for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="c231a-137">WideEntry 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c231a-137">TypeName Element for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="c231a-138">WideEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c231a-138">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="c231a-139">之 wideitem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c231a-139">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="c231a-140">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="c231a-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
