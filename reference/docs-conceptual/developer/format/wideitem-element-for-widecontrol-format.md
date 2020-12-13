---
ms.date: 09/13/2016
ms.topic: reference
title: WideControl 的 WideItem 元素 (格式)
description: WideControl 的 WideItem 元素 (格式)
ms.openlocfilehash: b9c416bbe3befcd689b8a2c0b72a8ff1301b9659
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647806"
---
# <a name="wideitem-element-for-widecontrol-format"></a><span data-ttu-id="e8643-103">WideControl 的 WideItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e8643-103">WideItem Element for WideControl (Format)</span></span>

<span data-ttu-id="e8643-104">定義顯示其值的屬性或腳本。</span><span class="sxs-lookup"><span data-stu-id="e8643-104">Defines the property or script whose value is displayed.</span></span>

<span data-ttu-id="e8643-105">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) WideControl 元素 (格式) WideEntries 元素 (格式) WideEntry 專案 (格式) 之 wideitem 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="e8643-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e8643-106">語法</span><span class="sxs-lookup"><span data-stu-id="e8643-106">Syntax</span></span>

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e8643-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e8643-107">Attributes and Elements</span></span>

<span data-ttu-id="e8643-108">下列章節說明屬性、子專案和元素的父元素 `WideItem` 。</span><span class="sxs-lookup"><span data-stu-id="e8643-108">The following sections describe the attributes, child elements, and the parent element of the `WideItem` element.</span></span> <span data-ttu-id="e8643-109">`FormatString` 則是選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="e8643-109">The `FormatString` element is optional.</span></span> <span data-ttu-id="e8643-110">不過，您必須指定 `PropertyName` 或 `ScriptBlock` 元素，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="e8643-110">However, you must specify a `PropertyName` or `ScriptBlock` element, but you cannot specify both.</span></span>

### <a name="attributes"></a><span data-ttu-id="e8643-111">屬性</span><span class="sxs-lookup"><span data-stu-id="e8643-111">Attributes</span></span>

<span data-ttu-id="e8643-112">無。</span><span class="sxs-lookup"><span data-stu-id="e8643-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e8643-113">子元素</span><span class="sxs-lookup"><span data-stu-id="e8643-113">Child Elements</span></span>

|<span data-ttu-id="e8643-114">元素</span><span class="sxs-lookup"><span data-stu-id="e8643-114">Element</span></span>|<span data-ttu-id="e8643-115">描述</span><span class="sxs-lookup"><span data-stu-id="e8643-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e8643-116">WideControl 之 WideItem 的 FormatString 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e8643-116">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="e8643-117">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="e8643-117">Optional element.</span></span><br /><br /> <span data-ttu-id="e8643-118">指定格式模式，定義屬性或腳本值在視圖中的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="e8643-118">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>|
|[<span data-ttu-id="e8643-119">之 wideitem (格式的 PropertyName 元素) </span><span class="sxs-lookup"><span data-stu-id="e8643-119">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="e8643-120">指定物件的屬性，其值會顯示在寬視圖中。</span><span class="sxs-lookup"><span data-stu-id="e8643-120">Specifies the property of the object whose value is displayed in the wide view.</span></span>|
|[<span data-ttu-id="e8643-121">之 wideitem (格式的 ScriptBlock 元素) </span><span class="sxs-lookup"><span data-stu-id="e8643-121">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="e8643-122">指定以寬視圖顯示其值的腳本。</span><span class="sxs-lookup"><span data-stu-id="e8643-122">Specifies the script whose value is displayed in the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e8643-123">父項目</span><span class="sxs-lookup"><span data-stu-id="e8643-123">Parent Elements</span></span>

|<span data-ttu-id="e8643-124">元素</span><span class="sxs-lookup"><span data-stu-id="e8643-124">Element</span></span>|<span data-ttu-id="e8643-125">描述</span><span class="sxs-lookup"><span data-stu-id="e8643-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e8643-126">WideEntry 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="e8643-126">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="e8643-127">提供寬視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="e8643-127">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e8643-128">備註</span><span class="sxs-lookup"><span data-stu-id="e8643-128">Remarks</span></span>

<span data-ttu-id="e8643-129">如需廣泛視圖元件的詳細資訊，請參閱 [Wide view](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="e8643-129">For more information about the components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e8643-130">範例</span><span class="sxs-lookup"><span data-stu-id="e8643-130">Example</span></span>

<span data-ttu-id="e8643-131">下列範例顯示 `WideEntry` 定義單一專案的元素 `WideItem` 。</span><span class="sxs-lookup"><span data-stu-id="e8643-131">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="e8643-132">`WideItem`元素會定義屬性或腳本，其值會顯示在視圖中。</span><span class="sxs-lookup"><span data-stu-id="e8643-132">The `WideItem` element defines the property or script whose value is displayed in the view.</span></span>

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

<span data-ttu-id="e8643-133">如需完整的完整範例，請參閱 [ (基本) 的寬量視圖 ](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="e8643-133">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e8643-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8643-134">See Also</span></span>

[<span data-ttu-id="e8643-135">WideControl 之 WideItem 的 FormatString 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e8643-135">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="e8643-136">之 wideitem (格式的 PropertyName 元素) </span><span class="sxs-lookup"><span data-stu-id="e8643-136">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="e8643-137">之 wideitem (格式的 ScriptBlock 元素) </span><span class="sxs-lookup"><span data-stu-id="e8643-137">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="e8643-138">WideEntry 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="e8643-138">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="e8643-139">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="e8643-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
