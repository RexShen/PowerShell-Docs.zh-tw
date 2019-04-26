---
title: WideEntries WideControl （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4bff45-0960-4b3a-95e7-47f2cee03ac5
caps.latest.revision: 12
ms.openlocfilehash: 083f3c8df8136858e32778ed231943ef983e47aa
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083683"
---
# <a name="wideentries-element-for-widecontrol-format"></a><span data-ttu-id="d5ff2-102">WideControl 的 WideEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d5ff2-102">WideEntries Element for WideControl (Format)</span></span>

<span data-ttu-id="d5ff2-103">提供的寬型檢視的定義。</span><span class="sxs-lookup"><span data-stu-id="d5ff2-103">Provides the definitions of the wide view.</span></span> <span data-ttu-id="d5ff2-104">寬型檢視必須指定一個或多個定義。</span><span class="sxs-lookup"><span data-stu-id="d5ff2-104">The wide view must specify one or more definitions.</span></span>

<span data-ttu-id="d5ff2-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） WideControl 項目 （格式） WideEntries 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="d5ff2-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d5ff2-106">語法</span><span class="sxs-lookup"><span data-stu-id="d5ff2-106">Syntax</span></span>

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="d5ff2-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d5ff2-107">Attributes and Elements</span></span>

<span data-ttu-id="d5ff2-108">下列各節說明屬性、 子項目和父項目`WideEntries`項目。</span><span class="sxs-lookup"><span data-stu-id="d5ff2-108">The following sections describe the attributes, child elements, and parent element of the `WideEntries` element.</span></span> <span data-ttu-id="d5ff2-109">必須指定至少一個子系項目。</span><span class="sxs-lookup"><span data-stu-id="d5ff2-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="d5ff2-110">屬性</span><span class="sxs-lookup"><span data-stu-id="d5ff2-110">Attributes</span></span>

<span data-ttu-id="d5ff2-111">無。</span><span class="sxs-lookup"><span data-stu-id="d5ff2-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d5ff2-112">子元素</span><span class="sxs-lookup"><span data-stu-id="d5ff2-112">Child Elements</span></span>

|<span data-ttu-id="d5ff2-113">元素</span><span class="sxs-lookup"><span data-stu-id="d5ff2-113">Element</span></span>|<span data-ttu-id="d5ff2-114">描述</span><span class="sxs-lookup"><span data-stu-id="d5ff2-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d5ff2-115">WideEntry 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="d5ff2-115">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="d5ff2-116">提供寬型檢視的定義。</span><span class="sxs-lookup"><span data-stu-id="d5ff2-116">Provides a definition of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d5ff2-117">父項目</span><span class="sxs-lookup"><span data-stu-id="d5ff2-117">Parent Elements</span></span>

|<span data-ttu-id="d5ff2-118">項目</span><span class="sxs-lookup"><span data-stu-id="d5ff2-118">Element</span></span>|<span data-ttu-id="d5ff2-119">描述</span><span class="sxs-lookup"><span data-stu-id="d5ff2-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d5ff2-120">WideControl 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="d5ff2-120">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="d5ff2-121">寬 （單一值） 會定義檢視的清單格式。</span><span class="sxs-lookup"><span data-stu-id="d5ff2-121">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d5ff2-122">備註</span><span class="sxs-lookup"><span data-stu-id="d5ff2-122">Remarks</span></span>

<span data-ttu-id="d5ff2-123">寬型檢視是顯示單一屬性值或每個物件的指令碼值以清單格式。</span><span class="sxs-lookup"><span data-stu-id="d5ff2-123">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="d5ff2-124">如需詳細的寬型檢視元件的相關資訊，請參閱[寬型檢視元件](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="d5ff2-124">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="d5ff2-125">範例</span><span class="sxs-lookup"><span data-stu-id="d5ff2-125">Example</span></span>

<span data-ttu-id="d5ff2-126">下列範例所示`WideEntries`項目，定義單一`WideEntry`項目。</span><span class="sxs-lookup"><span data-stu-id="d5ff2-126">The following example shows a `WideEntries` element that defines a single `WideEntry` element.</span></span> <span data-ttu-id="d5ff2-127">`WideEntry`元素包含單一`WideItem`項目，定義在檢視中顯示哪些屬性或指令碼的值。</span><span class="sxs-lookup"><span data-stu-id="d5ff2-127">The `WideEntry` element contains a single `WideItem` element that defines what property or script value is displayed in the view.</span></span>

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="d5ff2-128">寬型檢視的完整範例，請參閱[（基本） 的寬型檢視](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="d5ff2-128">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d5ff2-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5ff2-129">See Also</span></span>

[<span data-ttu-id="d5ff2-130">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="d5ff2-130">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="d5ff2-131">WideControl 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="d5ff2-131">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="d5ff2-132">WideEntry 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="d5ff2-132">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="d5ff2-133">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="d5ff2-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
