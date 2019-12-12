---
title: WideControl 的之 wideitem 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361397"
---
# <a name="wideitem-element-for-widecontrol-format"></a><span data-ttu-id="fbf7c-102">WideControl 的 WideItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="fbf7c-102">WideItem Element for WideControl (Format)</span></span>

<span data-ttu-id="fbf7c-103">定義顯示其值的屬性或腳本。</span><span class="sxs-lookup"><span data-stu-id="fbf7c-103">Defines the property or script whose value is displayed.</span></span>

<span data-ttu-id="fbf7c-104">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（格式） WideControl 元素（格式） WideEntries 元素（格式） WideEntry 元素（格式）之 wideitem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="fbf7c-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fbf7c-105">語法</span><span class="sxs-lookup"><span data-stu-id="fbf7c-105">Syntax</span></span>

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fbf7c-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="fbf7c-106">Attributes and Elements</span></span>

<span data-ttu-id="fbf7c-107">下列各節說明屬性、子專案，以及 `WideItem` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="fbf7c-107">The following sections describe the attributes, child elements, and the parent element of the `WideItem` element.</span></span> <span data-ttu-id="fbf7c-108">`FormatString` 元素為選擇性。</span><span class="sxs-lookup"><span data-stu-id="fbf7c-108">The `FormatString` element is optional.</span></span> <span data-ttu-id="fbf7c-109">不過，您必須指定 `PropertyName` 或 `ScriptBlock` 元素，但不能同時指定這兩個專案。</span><span class="sxs-lookup"><span data-stu-id="fbf7c-109">However, you must specify a `PropertyName` or `ScriptBlock` element, but you cannot specify both.</span></span>

### <a name="attributes"></a><span data-ttu-id="fbf7c-110">屬性</span><span class="sxs-lookup"><span data-stu-id="fbf7c-110">Attributes</span></span>

<span data-ttu-id="fbf7c-111">無。</span><span class="sxs-lookup"><span data-stu-id="fbf7c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fbf7c-112">子元素</span><span class="sxs-lookup"><span data-stu-id="fbf7c-112">Child Elements</span></span>

|<span data-ttu-id="fbf7c-113">元素</span><span class="sxs-lookup"><span data-stu-id="fbf7c-113">Element</span></span>|<span data-ttu-id="fbf7c-114">描述</span><span class="sxs-lookup"><span data-stu-id="fbf7c-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fbf7c-115">WideControl 之之 wideitem 的格式字串元素（格式）</span><span class="sxs-lookup"><span data-stu-id="fbf7c-115">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="fbf7c-116">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="fbf7c-116">Optional element.</span></span><br /><br /> <span data-ttu-id="fbf7c-117">指定定義屬性或腳本值在視圖中顯示方式的格式模式。</span><span class="sxs-lookup"><span data-stu-id="fbf7c-117">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>|
|[<span data-ttu-id="fbf7c-118">之 wideitem 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="fbf7c-118">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="fbf7c-119">指定物件的屬性，其值會顯示在寬視圖中。</span><span class="sxs-lookup"><span data-stu-id="fbf7c-119">Specifies the property of the object whose value is displayed in the wide view.</span></span>|
|[<span data-ttu-id="fbf7c-120">之 wideitem 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="fbf7c-120">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="fbf7c-121">指定在寬視圖中顯示其值的腳本。</span><span class="sxs-lookup"><span data-stu-id="fbf7c-121">Specifies the script whose value is displayed in the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="fbf7c-122">父元素</span><span class="sxs-lookup"><span data-stu-id="fbf7c-122">Parent Elements</span></span>

|<span data-ttu-id="fbf7c-123">元素</span><span class="sxs-lookup"><span data-stu-id="fbf7c-123">Element</span></span>|<span data-ttu-id="fbf7c-124">描述</span><span class="sxs-lookup"><span data-stu-id="fbf7c-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fbf7c-125">WideEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="fbf7c-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="fbf7c-126">提供寬視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="fbf7c-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fbf7c-127">備註</span><span class="sxs-lookup"><span data-stu-id="fbf7c-127">Remarks</span></span>

<span data-ttu-id="fbf7c-128">如需有關寬視圖元件的詳細資訊，請參閱[Wide view](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="fbf7c-128">For more information about the components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="fbf7c-129">範例</span><span class="sxs-lookup"><span data-stu-id="fbf7c-129">Example</span></span>

<span data-ttu-id="fbf7c-130">下列範例顯示定義單一 `WideItem` 元素的 `WideEntry` 專案。</span><span class="sxs-lookup"><span data-stu-id="fbf7c-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="fbf7c-131">`WideItem` 元素會定義屬性或腳本，其值會顯示在視圖中。</span><span class="sxs-lookup"><span data-stu-id="fbf7c-131">The `WideItem` element defines the property or script whose value is displayed in the view.</span></span>

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

<span data-ttu-id="fbf7c-132">如需寬視圖的完整範例，請參閱[寬視圖（基本）](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="fbf7c-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fbf7c-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fbf7c-133">See Also</span></span>

[<span data-ttu-id="fbf7c-134">WideControl 之之 wideitem 的格式字串元素（格式）</span><span class="sxs-lookup"><span data-stu-id="fbf7c-134">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="fbf7c-135">之 wideitem 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="fbf7c-135">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="fbf7c-136">之 wideitem 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="fbf7c-136">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="fbf7c-137">WideEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="fbf7c-137">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="fbf7c-138">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="fbf7c-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
