---
ms.date: 09/13/2016
ms.topic: reference
title: WideControl 元素 (格式)
description: WideControl 元素 (格式)
ms.openlocfilehash: f88e1ce18f87e5e47de473298b3ecf070b71c192
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651267"
---
# <a name="widecontrol-element-format"></a><span data-ttu-id="c4eca-103">WideControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c4eca-103">WideControl Element (Format)</span></span>

<span data-ttu-id="c4eca-104">為視圖定義寬 (單一值) 清單格式。</span><span class="sxs-lookup"><span data-stu-id="c4eca-104">Defines a wide (single value) list format for the view.</span></span> <span data-ttu-id="c4eca-105">這個視圖會顯示每個物件的單一屬性值或腳本值。</span><span class="sxs-lookup"><span data-stu-id="c4eca-105">This view displays a single property value or script value for each object.</span></span>

<span data-ttu-id="c4eca-106">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (Format) WideControl 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="c4eca-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c4eca-107">語法</span><span class="sxs-lookup"><span data-stu-id="c4eca-107">Syntax</span></span>

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c4eca-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c4eca-108">Attributes and Elements</span></span>

<span data-ttu-id="c4eca-109">下列各節描述專案的屬性、子項目和父元素 `WideControl` 。</span><span class="sxs-lookup"><span data-stu-id="c4eca-109">The following sections describe the attributes, child elements, and parent element of the `WideControl` element.</span></span> <span data-ttu-id="c4eca-110">您無法同時指定 `AutoSize` 和 `ColumnNumber` 元素。</span><span class="sxs-lookup"><span data-stu-id="c4eca-110">You cannot specify the `AutoSize` and `ColumnNumber` elements at the same time.</span></span>

### <a name="attributes"></a><span data-ttu-id="c4eca-111">屬性</span><span class="sxs-lookup"><span data-stu-id="c4eca-111">Attributes</span></span>

<span data-ttu-id="c4eca-112">無。</span><span class="sxs-lookup"><span data-stu-id="c4eca-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c4eca-113">子元素</span><span class="sxs-lookup"><span data-stu-id="c4eca-113">Child Elements</span></span>

|<span data-ttu-id="c4eca-114">元素</span><span class="sxs-lookup"><span data-stu-id="c4eca-114">Element</span></span>|<span data-ttu-id="c4eca-115">描述</span><span class="sxs-lookup"><span data-stu-id="c4eca-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c4eca-116">WideControl 的 AutoSize 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c4eca-116">AutoSize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)|<span data-ttu-id="c4eca-117">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="c4eca-117">Optional element.</span></span><br /><br /> <span data-ttu-id="c4eca-118">指定是否根據資料的大小調整資料行大小和資料行數目。</span><span class="sxs-lookup"><span data-stu-id="c4eca-118">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="c4eca-119">WideControl 的 ColumnNumber 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c4eca-119">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)|<span data-ttu-id="c4eca-120">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="c4eca-120">Optional element.</span></span><br /><br /> <span data-ttu-id="c4eca-121">指定以寬視圖顯示的資料行數目。</span><span class="sxs-lookup"><span data-stu-id="c4eca-121">Specifies the number of columns displayed in the wide view.</span></span>|
|[<span data-ttu-id="c4eca-122">WideEntries 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="c4eca-122">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="c4eca-123">必要元素。</span><span class="sxs-lookup"><span data-stu-id="c4eca-123">Required element.</span></span><br /><br /> <span data-ttu-id="c4eca-124">提供寬視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="c4eca-124">Provides the definitions of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c4eca-125">父項目</span><span class="sxs-lookup"><span data-stu-id="c4eca-125">Parent Elements</span></span>

|<span data-ttu-id="c4eca-126">元素</span><span class="sxs-lookup"><span data-stu-id="c4eca-126">Element</span></span>|<span data-ttu-id="c4eca-127">描述</span><span class="sxs-lookup"><span data-stu-id="c4eca-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c4eca-128">檢視元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c4eca-128">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="c4eca-129">定義用來顯示一或多個 .NET 物件的視圖。</span><span class="sxs-lookup"><span data-stu-id="c4eca-129">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c4eca-130">備註</span><span class="sxs-lookup"><span data-stu-id="c4eca-130">Remarks</span></span>

<span data-ttu-id="c4eca-131">定義廣泛的視圖時，您可以加入 `AutoSize` 元素或， `ColumnNumber` 但無法同時加入兩者。</span><span class="sxs-lookup"><span data-stu-id="c4eca-131">When defining a wide view, you can add the `AutoSize` element or the `ColumnNumber` but you cannot add both.</span></span>

<span data-ttu-id="c4eca-132">在大部分的情況下，每個寬視圖都只需要一個定義，但如果您想要使用相同的視圖來顯示不同的 .NET 物件，則可以有多個定義。</span><span class="sxs-lookup"><span data-stu-id="c4eca-132">In most cases, only one definition is required for each wide view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="c4eca-133">在這些情況下，您可以為每個物件或一組物件提供個別的定義。</span><span class="sxs-lookup"><span data-stu-id="c4eca-133">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

<span data-ttu-id="c4eca-134">如需廣泛視圖元件的詳細資訊，請參閱 [Wide View 元件](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="c4eca-134">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c4eca-135">範例</span><span class="sxs-lookup"><span data-stu-id="c4eca-135">Example</span></span>

<span data-ttu-id="c4eca-136">下列範例顯示的專案 `WideControl` 是用來顯示 [system.object](/dotnet/api/System.Diagnostics.Process) 物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="c4eca-136">The following example shows a `WideControl` element that is used to display a property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

<span data-ttu-id="c4eca-137">如需完整的完整範例，請參閱 [ (基本) 的寬量視圖 ](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="c4eca-137">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c4eca-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4eca-138">See Also</span></span>

[<span data-ttu-id="c4eca-139">WideControl (格式的 Autosize 元素) </span><span class="sxs-lookup"><span data-stu-id="c4eca-139">Autosize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)

[<span data-ttu-id="c4eca-140">WideControl 的 ColumnNumber 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c4eca-140">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)

[<span data-ttu-id="c4eca-141">檢視元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c4eca-141">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="c4eca-142">WideEntries 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="c4eca-142">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="c4eca-143">寬型檢視 (基本)</span><span class="sxs-lookup"><span data-stu-id="c4eca-143">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="c4eca-144">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="c4eca-144">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="c4eca-145">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="c4eca-145">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
