---
title: WideItem WideControl （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083632"
---
# <a name="wideitem-element-for-widecontrol-format"></a><span data-ttu-id="e482f-102">WideControl 的 WideItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e482f-102">WideItem Element for WideControl (Format)</span></span>

<span data-ttu-id="e482f-103">定義屬性或其值會顯示指令碼。</span><span class="sxs-lookup"><span data-stu-id="e482f-103">Defines the property or script whose value is displayed.</span></span>

<span data-ttu-id="e482f-104">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） WideControl 項目 （格式） WideEntries 項目 （格式） WideEntry 項目 （格式） WideItem 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="e482f-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e482f-105">語法</span><span class="sxs-lookup"><span data-stu-id="e482f-105">Syntax</span></span>

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e482f-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e482f-106">Attributes and Elements</span></span>

<span data-ttu-id="e482f-107">下列各節說明屬性、 子項目和父項目`WideItem`項目。</span><span class="sxs-lookup"><span data-stu-id="e482f-107">The following sections describe the attributes, child elements, and the parent element of the `WideItem` element.</span></span> <span data-ttu-id="e482f-108">`FormatString`是選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="e482f-108">The `FormatString` element is optional.</span></span> <span data-ttu-id="e482f-109">不過，您必須指定`PropertyName`或`ScriptBlock`項目，但是您無法同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="e482f-109">However, you must specify a `PropertyName` or `ScriptBlock` element, but you cannot specify both.</span></span>

### <a name="attributes"></a><span data-ttu-id="e482f-110">屬性</span><span class="sxs-lookup"><span data-stu-id="e482f-110">Attributes</span></span>

<span data-ttu-id="e482f-111">無。</span><span class="sxs-lookup"><span data-stu-id="e482f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e482f-112">子元素</span><span class="sxs-lookup"><span data-stu-id="e482f-112">Child Elements</span></span>

|<span data-ttu-id="e482f-113">元素</span><span class="sxs-lookup"><span data-stu-id="e482f-113">Element</span></span>|<span data-ttu-id="e482f-114">描述</span><span class="sxs-lookup"><span data-stu-id="e482f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e482f-115">WideControl （格式） 的 WideItem 的 FormatString 元素</span><span class="sxs-lookup"><span data-stu-id="e482f-115">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="e482f-116">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="e482f-116">Optional element.</span></span><br /><br /> <span data-ttu-id="e482f-117">指定之格式模式所定義的屬性或指令碼的值在檢視中的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="e482f-117">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>|
|[<span data-ttu-id="e482f-118">PropertyName WideItem （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="e482f-118">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="e482f-119">指定其值會顯示在寬型檢視物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="e482f-119">Specifies the property of the object whose value is displayed in the wide view.</span></span>|
|[<span data-ttu-id="e482f-120">ScriptBlock WideItem （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="e482f-120">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="e482f-121">指定其值會顯示在寬型檢視的指令碼。</span><span class="sxs-lookup"><span data-stu-id="e482f-121">Specifies the script whose value is displayed in the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e482f-122">父項目</span><span class="sxs-lookup"><span data-stu-id="e482f-122">Parent Elements</span></span>

|<span data-ttu-id="e482f-123">項目</span><span class="sxs-lookup"><span data-stu-id="e482f-123">Element</span></span>|<span data-ttu-id="e482f-124">描述</span><span class="sxs-lookup"><span data-stu-id="e482f-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e482f-125">WideEntry 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="e482f-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="e482f-126">提供寬型檢視的定義。</span><span class="sxs-lookup"><span data-stu-id="e482f-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e482f-127">備註</span><span class="sxs-lookup"><span data-stu-id="e482f-127">Remarks</span></span>

<span data-ttu-id="e482f-128">如需詳細的寬型檢視元件的相關資訊，請參閱[寬型檢視](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="e482f-128">For more information about the components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e482f-129">範例</span><span class="sxs-lookup"><span data-stu-id="e482f-129">Example</span></span>

<span data-ttu-id="e482f-130">下列範例所示`WideEntry`項目，定義單一`WideItem`項目。</span><span class="sxs-lookup"><span data-stu-id="e482f-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="e482f-131">`WideItem`項目定義之屬性或其值會顯示在檢視中的指令碼。</span><span class="sxs-lookup"><span data-stu-id="e482f-131">The `WideItem` element defines the property or script whose value is displayed in the view.</span></span>

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

<span data-ttu-id="e482f-132">寬型檢視的完整範例，請參閱[（基本） 的寬型檢視](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="e482f-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e482f-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e482f-133">See Also</span></span>

[<span data-ttu-id="e482f-134">WideControl （格式） 的 WideItem 的 FormatString 元素</span><span class="sxs-lookup"><span data-stu-id="e482f-134">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="e482f-135">PropertyName WideItem （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="e482f-135">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="e482f-136">ScriptBlock WideItem （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="e482f-136">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="e482f-137">WideEntry 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="e482f-137">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="e482f-138">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="e482f-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
