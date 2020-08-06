---
title: WideControl 元素 (格式) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: b6f19cf94dcb440eeaf53547db407287e5462520
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784974"
---
# <a name="widecontrol-element-format"></a><span data-ttu-id="1c402-102">WideControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1c402-102">WideControl Element (Format)</span></span>

<span data-ttu-id="1c402-103">定義視圖的寬 (單一值) 清單格式。</span><span class="sxs-lookup"><span data-stu-id="1c402-103">Defines a wide (single value) list format for the view.</span></span> <span data-ttu-id="1c402-104">此視圖會顯示每個物件的單一屬性值或腳本值。</span><span class="sxs-lookup"><span data-stu-id="1c402-104">This view displays a single property value or script value for each object.</span></span>

<span data-ttu-id="1c402-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) WideControl 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="1c402-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1c402-106">語法</span><span class="sxs-lookup"><span data-stu-id="1c402-106">Syntax</span></span>

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1c402-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1c402-107">Attributes and Elements</span></span>

<span data-ttu-id="1c402-108">下列各節描述元素的屬性、子專案和父項目 `WideControl` 。</span><span class="sxs-lookup"><span data-stu-id="1c402-108">The following sections describe the attributes, child elements, and parent element of the `WideControl` element.</span></span> <span data-ttu-id="1c402-109">您不能 `AutoSize` 同時指定和 `ColumnNumber` 元素。</span><span class="sxs-lookup"><span data-stu-id="1c402-109">You cannot specify the `AutoSize` and `ColumnNumber` elements at the same time.</span></span>

### <a name="attributes"></a><span data-ttu-id="1c402-110">屬性</span><span class="sxs-lookup"><span data-stu-id="1c402-110">Attributes</span></span>

<span data-ttu-id="1c402-111">無。</span><span class="sxs-lookup"><span data-stu-id="1c402-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1c402-112">子元素</span><span class="sxs-lookup"><span data-stu-id="1c402-112">Child Elements</span></span>

|<span data-ttu-id="1c402-113">元素</span><span class="sxs-lookup"><span data-stu-id="1c402-113">Element</span></span>|<span data-ttu-id="1c402-114">描述</span><span class="sxs-lookup"><span data-stu-id="1c402-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1c402-115">WideControl 的 AutoSize 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1c402-115">AutoSize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)|<span data-ttu-id="1c402-116">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="1c402-116">Optional element.</span></span><br /><br /> <span data-ttu-id="1c402-117">指定是否根據資料大小來調整資料行大小和資料行數目。</span><span class="sxs-lookup"><span data-stu-id="1c402-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="1c402-118">WideControl 的 ColumnNumber 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1c402-118">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)|<span data-ttu-id="1c402-119">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="1c402-119">Optional element.</span></span><br /><br /> <span data-ttu-id="1c402-120">指定在寬視圖中顯示的資料行數目。</span><span class="sxs-lookup"><span data-stu-id="1c402-120">Specifies the number of columns displayed in the wide view.</span></span>|
|[<span data-ttu-id="1c402-121">WideEntries 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="1c402-121">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="1c402-122">必要元素。</span><span class="sxs-lookup"><span data-stu-id="1c402-122">Required element.</span></span><br /><br /> <span data-ttu-id="1c402-123">提供寬視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="1c402-123">Provides the definitions of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1c402-124">父項目</span><span class="sxs-lookup"><span data-stu-id="1c402-124">Parent Elements</span></span>

|<span data-ttu-id="1c402-125">元素</span><span class="sxs-lookup"><span data-stu-id="1c402-125">Element</span></span>|<span data-ttu-id="1c402-126">描述</span><span class="sxs-lookup"><span data-stu-id="1c402-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1c402-127">檢視元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1c402-127">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="1c402-128">定義用來顯示一個或多個 .NET 物件的視圖。</span><span class="sxs-lookup"><span data-stu-id="1c402-128">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1c402-129">備註</span><span class="sxs-lookup"><span data-stu-id="1c402-129">Remarks</span></span>

<span data-ttu-id="1c402-130">定義寬視圖時，您可以加入 `AutoSize` 元素或， `ColumnNumber` 但無法同時新增兩者。</span><span class="sxs-lookup"><span data-stu-id="1c402-130">When defining a wide view, you can add the `AutoSize` element or the `ColumnNumber` but you cannot add both.</span></span>

<span data-ttu-id="1c402-131">在大部分情況下，每個寬視圖只需要一個定義，但是如果您想要使用相同的視圖來顯示不同的 .NET 物件，則可能會有多個定義。</span><span class="sxs-lookup"><span data-stu-id="1c402-131">In most cases, only one definition is required for each wide view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="1c402-132">在這些情況下，您可以為每個物件或一組物件提供個別的定義。</span><span class="sxs-lookup"><span data-stu-id="1c402-132">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

<span data-ttu-id="1c402-133">如需有關寬視圖元件的詳細資訊，請參閱[寬視圖元件](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="1c402-133">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="1c402-134">範例</span><span class="sxs-lookup"><span data-stu-id="1c402-134">Example</span></span>

<span data-ttu-id="1c402-135">下列範例顯示 `WideControl` 用來顯示 system.servicemodel 物件之屬性的元素。 [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)</span><span class="sxs-lookup"><span data-stu-id="1c402-135">The following example shows a `WideControl` element that is used to display a property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

<span data-ttu-id="1c402-136">如需寬視圖的完整範例，請參閱[寬視圖 (基本) ](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="1c402-136">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1c402-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c402-137">See Also</span></span>

[<span data-ttu-id="1c402-138">WideControl (格式的 Autosize 元素) </span><span class="sxs-lookup"><span data-stu-id="1c402-138">Autosize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)

[<span data-ttu-id="1c402-139">WideControl 的 ColumnNumber 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1c402-139">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)

[<span data-ttu-id="1c402-140">檢視元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1c402-140">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="1c402-141">WideEntries 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="1c402-141">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="1c402-142">寬型檢視 (基本)</span><span class="sxs-lookup"><span data-stu-id="1c402-142">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="1c402-143">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="1c402-143">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="1c402-144">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="1c402-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
