---
title: WideControl (格式的之 wideitem 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6b2f7c97978c20350caeec894589c5995ae7ccc4
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779891"
---
# <a name="wideitem-element-for-widecontrol-format"></a><span data-ttu-id="dd42d-102">WideControl 的 WideItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="dd42d-102">WideItem Element for WideControl (Format)</span></span>

<span data-ttu-id="dd42d-103">定義顯示其值的屬性或腳本。</span><span class="sxs-lookup"><span data-stu-id="dd42d-103">Defines the property or script whose value is displayed.</span></span>

<span data-ttu-id="dd42d-104">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) WideControl 元素 (格式) WideEntries 專案 (格式) WideEntry 專案 (格式) 之 wideitem 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="dd42d-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dd42d-105">語法</span><span class="sxs-lookup"><span data-stu-id="dd42d-105">Syntax</span></span>

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dd42d-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="dd42d-106">Attributes and Elements</span></span>

<span data-ttu-id="dd42d-107">下列各節說明屬性、子專案和元素的父元素 `WideItem` 。</span><span class="sxs-lookup"><span data-stu-id="dd42d-107">The following sections describe the attributes, child elements, and the parent element of the `WideItem` element.</span></span> <span data-ttu-id="dd42d-108">`FormatString` 則是選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="dd42d-108">The `FormatString` element is optional.</span></span> <span data-ttu-id="dd42d-109">不過，您必須指定 `PropertyName` 或專案 `ScriptBlock` ，但不能同時指定這兩個專案。</span><span class="sxs-lookup"><span data-stu-id="dd42d-109">However, you must specify a `PropertyName` or `ScriptBlock` element, but you cannot specify both.</span></span>

### <a name="attributes"></a><span data-ttu-id="dd42d-110">屬性</span><span class="sxs-lookup"><span data-stu-id="dd42d-110">Attributes</span></span>

<span data-ttu-id="dd42d-111">無。</span><span class="sxs-lookup"><span data-stu-id="dd42d-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dd42d-112">子元素</span><span class="sxs-lookup"><span data-stu-id="dd42d-112">Child Elements</span></span>

|<span data-ttu-id="dd42d-113">元素</span><span class="sxs-lookup"><span data-stu-id="dd42d-113">Element</span></span>|<span data-ttu-id="dd42d-114">描述</span><span class="sxs-lookup"><span data-stu-id="dd42d-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dd42d-115">WideControl 之 WideItem 的 FormatString 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="dd42d-115">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="dd42d-116">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="dd42d-116">Optional element.</span></span><br /><br /> <span data-ttu-id="dd42d-117">指定定義屬性或腳本值在視圖中顯示方式的格式模式。</span><span class="sxs-lookup"><span data-stu-id="dd42d-117">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>|
|[<span data-ttu-id="dd42d-118">之 wideitem (格式的 PropertyName 元素) </span><span class="sxs-lookup"><span data-stu-id="dd42d-118">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="dd42d-119">指定物件的屬性，其值會顯示在寬視圖中。</span><span class="sxs-lookup"><span data-stu-id="dd42d-119">Specifies the property of the object whose value is displayed in the wide view.</span></span>|
|[<span data-ttu-id="dd42d-120">之 wideitem (格式的 ScriptBlock 元素) </span><span class="sxs-lookup"><span data-stu-id="dd42d-120">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="dd42d-121">指定在寬視圖中顯示其值的腳本。</span><span class="sxs-lookup"><span data-stu-id="dd42d-121">Specifies the script whose value is displayed in the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="dd42d-122">父項目</span><span class="sxs-lookup"><span data-stu-id="dd42d-122">Parent Elements</span></span>

|<span data-ttu-id="dd42d-123">元素</span><span class="sxs-lookup"><span data-stu-id="dd42d-123">Element</span></span>|<span data-ttu-id="dd42d-124">描述</span><span class="sxs-lookup"><span data-stu-id="dd42d-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dd42d-125">WideEntry 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="dd42d-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="dd42d-126">提供寬視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="dd42d-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="dd42d-127">備註</span><span class="sxs-lookup"><span data-stu-id="dd42d-127">Remarks</span></span>

<span data-ttu-id="dd42d-128">如需有關寬視圖元件的詳細資訊，請參閱[Wide view](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="dd42d-128">For more information about the components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="dd42d-129">範例</span><span class="sxs-lookup"><span data-stu-id="dd42d-129">Example</span></span>

<span data-ttu-id="dd42d-130">下列範例顯示 `WideEntry` 定義單一專案的元素 `WideItem` 。</span><span class="sxs-lookup"><span data-stu-id="dd42d-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="dd42d-131">`WideItem`元素會定義屬性或腳本，其值會顯示在視圖中。</span><span class="sxs-lookup"><span data-stu-id="dd42d-131">The `WideItem` element defines the property or script whose value is displayed in the view.</span></span>

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

<span data-ttu-id="dd42d-132">如需寬視圖的完整範例，請參閱[寬視圖 (基本) ](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="dd42d-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dd42d-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd42d-133">See Also</span></span>

[<span data-ttu-id="dd42d-134">WideControl 之 WideItem 的 FormatString 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="dd42d-134">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="dd42d-135">之 wideitem (格式的 PropertyName 元素) </span><span class="sxs-lookup"><span data-stu-id="dd42d-135">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="dd42d-136">之 wideitem (格式的 ScriptBlock 元素) </span><span class="sxs-lookup"><span data-stu-id="dd42d-136">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="dd42d-137">WideEntry 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="dd42d-137">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="dd42d-138">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="dd42d-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
