---
title: WideControl (格式的 WideEntries 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 74383b288c945008c1d7b5119363a166c04802ae
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785042"
---
# <a name="wideentries-element-for-widecontrol-format"></a><span data-ttu-id="07f94-102">WideControl 的 WideEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="07f94-102">WideEntries Element for WideControl (Format)</span></span>

<span data-ttu-id="07f94-103">提供寬視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="07f94-103">Provides the definitions of the wide view.</span></span> <span data-ttu-id="07f94-104">寬視圖必須指定一或多個定義。</span><span class="sxs-lookup"><span data-stu-id="07f94-104">The wide view must specify one or more definitions.</span></span>

<span data-ttu-id="07f94-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) WideControl 元素 (格式) WideEntries 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="07f94-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="07f94-106">語法</span><span class="sxs-lookup"><span data-stu-id="07f94-106">Syntax</span></span>

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="07f94-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="07f94-107">Attributes and Elements</span></span>

<span data-ttu-id="07f94-108">下列各節描述元素的屬性、子專案和父項目 `WideEntries` 。</span><span class="sxs-lookup"><span data-stu-id="07f94-108">The following sections describe the attributes, child elements, and parent element of the `WideEntries` element.</span></span> <span data-ttu-id="07f94-109">至少必須指定一個子項目。</span><span class="sxs-lookup"><span data-stu-id="07f94-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="07f94-110">屬性</span><span class="sxs-lookup"><span data-stu-id="07f94-110">Attributes</span></span>

<span data-ttu-id="07f94-111">無。</span><span class="sxs-lookup"><span data-stu-id="07f94-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="07f94-112">子元素</span><span class="sxs-lookup"><span data-stu-id="07f94-112">Child Elements</span></span>

|<span data-ttu-id="07f94-113">元素</span><span class="sxs-lookup"><span data-stu-id="07f94-113">Element</span></span>|<span data-ttu-id="07f94-114">描述</span><span class="sxs-lookup"><span data-stu-id="07f94-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="07f94-115">WideEntry 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="07f94-115">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="07f94-116">提供寬視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="07f94-116">Provides a definition of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="07f94-117">父項目</span><span class="sxs-lookup"><span data-stu-id="07f94-117">Parent Elements</span></span>

|<span data-ttu-id="07f94-118">元素</span><span class="sxs-lookup"><span data-stu-id="07f94-118">Element</span></span>|<span data-ttu-id="07f94-119">描述</span><span class="sxs-lookup"><span data-stu-id="07f94-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="07f94-120">WideControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="07f94-120">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="07f94-121">定義視圖的寬 (單一值) 清單格式。</span><span class="sxs-lookup"><span data-stu-id="07f94-121">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="07f94-122">備註</span><span class="sxs-lookup"><span data-stu-id="07f94-122">Remarks</span></span>

<span data-ttu-id="07f94-123">寬型視圖是一種清單格式，可顯示每個物件的單一屬性值或腳本值。</span><span class="sxs-lookup"><span data-stu-id="07f94-123">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="07f94-124">如需有關寬視圖元件的詳細資訊，請參閱[寬視圖元件](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="07f94-124">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="07f94-125">範例</span><span class="sxs-lookup"><span data-stu-id="07f94-125">Example</span></span>

<span data-ttu-id="07f94-126">下列範例顯示 `WideEntries` 定義單一專案的元素 `WideEntry` 。</span><span class="sxs-lookup"><span data-stu-id="07f94-126">The following example shows a `WideEntries` element that defines a single `WideEntry` element.</span></span> <span data-ttu-id="07f94-127">`WideEntry`元素包含單一 `WideItem` 元素，可定義要在視圖中顯示的屬性或腳本值。</span><span class="sxs-lookup"><span data-stu-id="07f94-127">The `WideEntry` element contains a single `WideItem` element that defines what property or script value is displayed in the view.</span></span>

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="07f94-128">如需寬視圖的完整範例，請參閱[寬視圖 (基本) ](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="07f94-128">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="07f94-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07f94-129">See Also</span></span>

[<span data-ttu-id="07f94-130">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="07f94-130">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="07f94-131">WideControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="07f94-131">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="07f94-132">WideEntry 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="07f94-132">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="07f94-133">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="07f94-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
