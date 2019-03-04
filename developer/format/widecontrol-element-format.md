---
title: WideControl 項目 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715ea055-037b-46ad-b70f-87b3f5134403
caps.latest.revision: 14
ms.openlocfilehash: 2742be0389a1bf04af100a490a59c0d938165811
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859824"
---
# <a name="widecontrol-element-format"></a><span data-ttu-id="13595-102">WideControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="13595-102">WideControl Element (Format)</span></span>

<span data-ttu-id="13595-103">寬 （單一值） 會定義檢視的清單格式。</span><span class="sxs-lookup"><span data-stu-id="13595-103">Defines a wide (single value) list format for the view.</span></span> <span data-ttu-id="13595-104">此檢視會顯示單一屬性值或每個物件的指令碼值。</span><span class="sxs-lookup"><span data-stu-id="13595-104">This view displays a single property value or script value for each object.</span></span>

<span data-ttu-id="13595-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） WideControl 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="13595-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="13595-106">語法</span><span class="sxs-lookup"><span data-stu-id="13595-106">Syntax</span></span>

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="13595-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="13595-107">Attributes and Elements</span></span>

<span data-ttu-id="13595-108">下列各節說明屬性、 子項目和父項目`WideControl`項目。</span><span class="sxs-lookup"><span data-stu-id="13595-108">The following sections describe the attributes, child elements, and parent element of the `WideControl` element.</span></span> <span data-ttu-id="13595-109">您無法指定`AutoSize`和`ColumnNumber`在同一時間的項目。</span><span class="sxs-lookup"><span data-stu-id="13595-109">You cannot specify the `AutoSize` and `ColumnNumber` elements at the same time.</span></span>

### <a name="attributes"></a><span data-ttu-id="13595-110">屬性</span><span class="sxs-lookup"><span data-stu-id="13595-110">Attributes</span></span>

<span data-ttu-id="13595-111">無。</span><span class="sxs-lookup"><span data-stu-id="13595-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="13595-112">子元素</span><span class="sxs-lookup"><span data-stu-id="13595-112">Child Elements</span></span>

|<span data-ttu-id="13595-113">元素</span><span class="sxs-lookup"><span data-stu-id="13595-113">Element</span></span>|<span data-ttu-id="13595-114">描述</span><span class="sxs-lookup"><span data-stu-id="13595-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="13595-115">AutoSize WideControl （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="13595-115">AutoSize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)|<span data-ttu-id="13595-116">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="13595-116">Optional element.</span></span><br /><br /> <span data-ttu-id="13595-117">指定是否資料行大小和資料行數目根據調整大小的資料大小。</span><span class="sxs-lookup"><span data-stu-id="13595-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="13595-118">ColumnNumber WideControl （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="13595-118">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)|<span data-ttu-id="13595-119">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="13595-119">Optional element.</span></span><br /><br /> <span data-ttu-id="13595-120">指定在寬型檢視中顯示的資料行數目。</span><span class="sxs-lookup"><span data-stu-id="13595-120">Specifies the number of columns displayed in the wide view.</span></span>|
|[<span data-ttu-id="13595-121">WideEntries 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="13595-121">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="13595-122">必要項目。</span><span class="sxs-lookup"><span data-stu-id="13595-122">Required element.</span></span><br /><br /> <span data-ttu-id="13595-123">提供的寬型檢視的定義。</span><span class="sxs-lookup"><span data-stu-id="13595-123">Provides the definitions of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="13595-124">父元素</span><span class="sxs-lookup"><span data-stu-id="13595-124">Parent Elements</span></span>

|<span data-ttu-id="13595-125">元素</span><span class="sxs-lookup"><span data-stu-id="13595-125">Element</span></span>|<span data-ttu-id="13595-126">描述</span><span class="sxs-lookup"><span data-stu-id="13595-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="13595-127">檢視項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="13595-127">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="13595-128">定義用來顯示一或多個.NET 物件的檢視。</span><span class="sxs-lookup"><span data-stu-id="13595-128">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="13595-129">備註</span><span class="sxs-lookup"><span data-stu-id="13595-129">Remarks</span></span>

<span data-ttu-id="13595-130">當定義的寬型檢視，您可以加入`AutoSize`項目或`ColumnNumber`但您無法新增。</span><span class="sxs-lookup"><span data-stu-id="13595-130">When defining a wide view, you can add the `AutoSize` element or the `ColumnNumber` but you cannot add both.</span></span>

<span data-ttu-id="13595-131">在大部分情況下，只有一個定義需要針對每個寬型檢視，但可以有多個定義，如果您想要使用相同的檢視來顯示不同的.NET 物件。</span><span class="sxs-lookup"><span data-stu-id="13595-131">In most cases, only one definition is required for each wide view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="13595-132">在這些情況下，您可以針對每個物件或一組物件提供不同的定義。</span><span class="sxs-lookup"><span data-stu-id="13595-132">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

<span data-ttu-id="13595-133">如需詳細的寬型檢視元件的相關資訊，請參閱[寬型檢視元件](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="13595-133">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="13595-134">範例</span><span class="sxs-lookup"><span data-stu-id="13595-134">Example</span></span>

<span data-ttu-id="13595-135">下列範例所示`WideControl`用來顯示屬性的項目[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)物件。</span><span class="sxs-lookup"><span data-stu-id="13595-135">The following example shows a `WideControl` element that is used to display a property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>...</WideEntries>
  </WideControl>
</View>
```

<span data-ttu-id="13595-136">寬型檢視的完整範例，請參閱[（基本） 的寬型檢視](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="13595-136">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="13595-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13595-137">See Also</span></span>

[<span data-ttu-id="13595-138">Autosize WideControl （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="13595-138">Autosize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)

[<span data-ttu-id="13595-139">ColumnNumber WideControl （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="13595-139">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)

[<span data-ttu-id="13595-140">檢視項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="13595-140">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="13595-141">WideEntries 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="13595-141">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="13595-142">寬型檢視 （基本）</span><span class="sxs-lookup"><span data-stu-id="13595-142">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="13595-143">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="13595-143">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="13595-144">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="13595-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
