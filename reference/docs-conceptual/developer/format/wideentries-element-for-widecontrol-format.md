---
ms.date: 09/13/2016
ms.topic: reference
title: WideControl 的 WideEntries 元素 (格式)
description: WideControl 的 WideEntries 元素 (格式)
ms.openlocfilehash: 567b8acdd0d2e8d5daaef2c31b4fe4ce38c23a47
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651230"
---
# <a name="wideentries-element-for-widecontrol-format"></a><span data-ttu-id="c4153-103">WideControl 的 WideEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c4153-103">WideEntries Element for WideControl (Format)</span></span>

<span data-ttu-id="c4153-104">提供寬視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="c4153-104">Provides the definitions of the wide view.</span></span> <span data-ttu-id="c4153-105">寬型視圖必須指定一或多個定義。</span><span class="sxs-lookup"><span data-stu-id="c4153-105">The wide view must specify one or more definitions.</span></span>

<span data-ttu-id="c4153-106">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) WideEntries 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="c4153-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c4153-107">語法</span><span class="sxs-lookup"><span data-stu-id="c4153-107">Syntax</span></span>

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="c4153-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c4153-108">Attributes and Elements</span></span>

<span data-ttu-id="c4153-109">下列各節描述專案的屬性、子項目和父元素 `WideEntries` 。</span><span class="sxs-lookup"><span data-stu-id="c4153-109">The following sections describe the attributes, child elements, and parent element of the `WideEntries` element.</span></span> <span data-ttu-id="c4153-110">至少必須指定一個子項目。</span><span class="sxs-lookup"><span data-stu-id="c4153-110">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="c4153-111">屬性</span><span class="sxs-lookup"><span data-stu-id="c4153-111">Attributes</span></span>

<span data-ttu-id="c4153-112">無。</span><span class="sxs-lookup"><span data-stu-id="c4153-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c4153-113">子元素</span><span class="sxs-lookup"><span data-stu-id="c4153-113">Child Elements</span></span>

|<span data-ttu-id="c4153-114">元素</span><span class="sxs-lookup"><span data-stu-id="c4153-114">Element</span></span>|<span data-ttu-id="c4153-115">描述</span><span class="sxs-lookup"><span data-stu-id="c4153-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c4153-116">WideEntry 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="c4153-116">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="c4153-117">提供寬視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="c4153-117">Provides a definition of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c4153-118">父項目</span><span class="sxs-lookup"><span data-stu-id="c4153-118">Parent Elements</span></span>

|<span data-ttu-id="c4153-119">元素</span><span class="sxs-lookup"><span data-stu-id="c4153-119">Element</span></span>|<span data-ttu-id="c4153-120">描述</span><span class="sxs-lookup"><span data-stu-id="c4153-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c4153-121">WideControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c4153-121">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="c4153-122">為視圖定義寬 (單一值) 清單格式。</span><span class="sxs-lookup"><span data-stu-id="c4153-122">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c4153-123">備註</span><span class="sxs-lookup"><span data-stu-id="c4153-123">Remarks</span></span>

<span data-ttu-id="c4153-124">寬型視圖是一種清單格式，可顯示每個物件的單一屬性值或腳本值。</span><span class="sxs-lookup"><span data-stu-id="c4153-124">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="c4153-125">如需廣泛視圖元件的詳細資訊，請參閱 [Wide View 元件](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="c4153-125">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c4153-126">範例</span><span class="sxs-lookup"><span data-stu-id="c4153-126">Example</span></span>

<span data-ttu-id="c4153-127">下列範例顯示 `WideEntries` 定義單一專案的元素 `WideEntry` 。</span><span class="sxs-lookup"><span data-stu-id="c4153-127">The following example shows a `WideEntries` element that defines a single `WideEntry` element.</span></span> <span data-ttu-id="c4153-128">`WideEntry`元素包含單一 `WideItem` 元素，可定義顯示在視圖中的屬性或腳本值。</span><span class="sxs-lookup"><span data-stu-id="c4153-128">The `WideEntry` element contains a single `WideItem` element that defines what property or script value is displayed in the view.</span></span>

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="c4153-129">如需完整的完整範例，請參閱 [ (基本) 的寬量視圖 ](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="c4153-129">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c4153-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4153-130">See Also</span></span>

[<span data-ttu-id="c4153-131">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="c4153-131">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="c4153-132">WideControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c4153-132">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="c4153-133">WideEntry 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="c4153-133">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="c4153-134">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="c4153-134">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
