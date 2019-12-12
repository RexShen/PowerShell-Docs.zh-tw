---
title: WideControl 的 WideEntries 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4bff45-0960-4b3a-95e7-47f2cee03ac5
caps.latest.revision: 12
ms.openlocfilehash: 083f3c8df8136858e32778ed231943ef983e47aa
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361427"
---
# <a name="wideentries-element-for-widecontrol-format"></a><span data-ttu-id="176f9-102">WideControl 的 WideEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="176f9-102">WideEntries Element for WideControl (Format)</span></span>

<span data-ttu-id="176f9-103">提供寬視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="176f9-103">Provides the definitions of the wide view.</span></span> <span data-ttu-id="176f9-104">寬視圖必須指定一或多個定義。</span><span class="sxs-lookup"><span data-stu-id="176f9-104">The wide view must specify one or more definitions.</span></span>

<span data-ttu-id="176f9-105">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） WideControl 元素（格式） WideEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="176f9-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="176f9-106">語法</span><span class="sxs-lookup"><span data-stu-id="176f9-106">Syntax</span></span>

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="176f9-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="176f9-107">Attributes and Elements</span></span>

<span data-ttu-id="176f9-108">下列各節描述 `WideEntries` 專案的屬性、子專案和父項目。</span><span class="sxs-lookup"><span data-stu-id="176f9-108">The following sections describe the attributes, child elements, and parent element of the `WideEntries` element.</span></span> <span data-ttu-id="176f9-109">至少必須指定一個子項目。</span><span class="sxs-lookup"><span data-stu-id="176f9-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="176f9-110">屬性</span><span class="sxs-lookup"><span data-stu-id="176f9-110">Attributes</span></span>

<span data-ttu-id="176f9-111">無。</span><span class="sxs-lookup"><span data-stu-id="176f9-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="176f9-112">子元素</span><span class="sxs-lookup"><span data-stu-id="176f9-112">Child Elements</span></span>

|<span data-ttu-id="176f9-113">元素</span><span class="sxs-lookup"><span data-stu-id="176f9-113">Element</span></span>|<span data-ttu-id="176f9-114">描述</span><span class="sxs-lookup"><span data-stu-id="176f9-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="176f9-115">WideEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="176f9-115">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="176f9-116">提供寬視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="176f9-116">Provides a definition of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="176f9-117">父元素</span><span class="sxs-lookup"><span data-stu-id="176f9-117">Parent Elements</span></span>

|<span data-ttu-id="176f9-118">元素</span><span class="sxs-lookup"><span data-stu-id="176f9-118">Element</span></span>|<span data-ttu-id="176f9-119">描述</span><span class="sxs-lookup"><span data-stu-id="176f9-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="176f9-120">WideControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="176f9-120">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="176f9-121">定義視圖的寬（單一值）清單格式。</span><span class="sxs-lookup"><span data-stu-id="176f9-121">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="176f9-122">備註</span><span class="sxs-lookup"><span data-stu-id="176f9-122">Remarks</span></span>

<span data-ttu-id="176f9-123">寬型視圖是一種清單格式，可顯示每個物件的單一屬性值或腳本值。</span><span class="sxs-lookup"><span data-stu-id="176f9-123">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="176f9-124">如需有關寬視圖元件的詳細資訊，請參閱[寬視圖元件](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="176f9-124">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="176f9-125">範例</span><span class="sxs-lookup"><span data-stu-id="176f9-125">Example</span></span>

<span data-ttu-id="176f9-126">下列範例顯示定義單一 `WideEntry` 元素的 `WideEntries` 專案。</span><span class="sxs-lookup"><span data-stu-id="176f9-126">The following example shows a `WideEntries` element that defines a single `WideEntry` element.</span></span> <span data-ttu-id="176f9-127">`WideEntry` 元素包含單一 `WideItem` 元素，可定義要在視圖中顯示的屬性或腳本值。</span><span class="sxs-lookup"><span data-stu-id="176f9-127">The `WideEntry` element contains a single `WideItem` element that defines what property or script value is displayed in the view.</span></span>

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="176f9-128">如需寬視圖的完整範例，請參閱[寬視圖（基本）](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="176f9-128">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="176f9-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="176f9-129">See Also</span></span>

[<span data-ttu-id="176f9-130">建立寬型視圖</span><span class="sxs-lookup"><span data-stu-id="176f9-130">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="176f9-131">WideControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="176f9-131">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="176f9-132">WideEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="176f9-132">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="176f9-133">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="176f9-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
