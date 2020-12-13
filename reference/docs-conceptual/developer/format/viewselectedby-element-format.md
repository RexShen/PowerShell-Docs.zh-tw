---
ms.date: 09/13/2016
ms.topic: reference
title: ViewSelectedBy 元素 (格式)
description: ViewSelectedBy 元素 (格式)
ms.openlocfilehash: ac3c7de299b3009a067a476a024c6a6fcb5dce02
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667703"
---
# <a name="viewselectedby-element-format"></a><span data-ttu-id="521e1-103">ViewSelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="521e1-103">ViewSelectedBy Element (Format)</span></span>

<span data-ttu-id="521e1-104">定義由視圖顯示的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="521e1-104">Defines the .NET objects that are displayed by the view.</span></span> <span data-ttu-id="521e1-105">每個視圖都必須指定至少一個 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="521e1-105">Each view must specify at least one .NET object.</span></span>

<span data-ttu-id="521e1-106">ViewDefinitions 元素 (格式) View 元素 (格式) ViewSelectedBy 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="521e1-106">ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="521e1-107">語法</span><span class="sxs-lookup"><span data-stu-id="521e1-107">Syntax</span></span>

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="521e1-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="521e1-108">Attributes and Elements</span></span>

<span data-ttu-id="521e1-109">下列各節描述專案的屬性、子項目和父元素 `ViewSelectedBy` 。</span><span class="sxs-lookup"><span data-stu-id="521e1-109">The following sections describe the attributes, child elements, and parent element of the `ViewSelectedBy` element.</span></span> <span data-ttu-id="521e1-110">此元素必須包含至少一個 `TypeName` 或 `SelectionSetName` 子項目。</span><span class="sxs-lookup"><span data-stu-id="521e1-110">This element must contain at least one `TypeName` or `SelectionSetName` child element.</span></span> <span data-ttu-id="521e1-111">您可以指定的子專案數目和順序沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="521e1-111">There is no limit to the number of child elements that can be specified nor is their order significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="521e1-112">屬性</span><span class="sxs-lookup"><span data-stu-id="521e1-112">Attributes</span></span>

<span data-ttu-id="521e1-113">無。</span><span class="sxs-lookup"><span data-stu-id="521e1-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="521e1-114">子元素</span><span class="sxs-lookup"><span data-stu-id="521e1-114">Child Elements</span></span>

|<span data-ttu-id="521e1-115">元素</span><span class="sxs-lookup"><span data-stu-id="521e1-115">Element</span></span>|<span data-ttu-id="521e1-116">描述</span><span class="sxs-lookup"><span data-stu-id="521e1-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="521e1-117">ViewSelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="521e1-117">TypeName Element for ViewSelectedBy (Format)</span></span>](./typename-element-for-viewselectedby-format.md)|<span data-ttu-id="521e1-118">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="521e1-118">Optional element.</span></span><br /><br /> <span data-ttu-id="521e1-119">指定由視圖顯示的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="521e1-119">Specifies a .NET object that is displayed by the view.</span></span>|
|[<span data-ttu-id="521e1-120">ViewSelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="521e1-120">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)|<span data-ttu-id="521e1-121">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="521e1-121">Optional element.</span></span><br /><br /> <span data-ttu-id="521e1-122">指定由視圖顯示的一組 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="521e1-122">Specifies a set of .NET objects that are displayed by the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="521e1-123">父項目</span><span class="sxs-lookup"><span data-stu-id="521e1-123">Parent Elements</span></span>

|<span data-ttu-id="521e1-124">元素</span><span class="sxs-lookup"><span data-stu-id="521e1-124">Element</span></span>|<span data-ttu-id="521e1-125">描述</span><span class="sxs-lookup"><span data-stu-id="521e1-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="521e1-126">檢視元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="521e1-126">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="521e1-127">定義顯示一或多個 .NET 物件的視圖。</span><span class="sxs-lookup"><span data-stu-id="521e1-127">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="521e1-128">備註</span><span class="sxs-lookup"><span data-stu-id="521e1-128">Remarks</span></span>

<span data-ttu-id="521e1-129">如需如何在不同的視圖中使用這個元素的詳細資訊，請參閱 [資料表視圖元件](./creating-a-table-view.md)、 [清單視圖元件](./creating-a-list-view.md)、 [寬視圖元件](./creating-a-wide-view.md)和 [自訂控制群組件](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="521e1-129">For more information about how this element is used in different views, see [Table View Components](./creating-a-table-view.md), [List View Components](./creating-a-list-view.md), [Wide View Components](./creating-a-wide-view.md), and [Custom Control Components](./creating-custom-controls.md).</span></span>

<span data-ttu-id="521e1-130">`SelectionSetName`當格式化檔案定義多個視圖所顯示的一組物件時，會使用元素。</span><span class="sxs-lookup"><span data-stu-id="521e1-130">The `SelectionSetName` element is used when the formatting file defines a set of objects that are displayed by multiple views.</span></span> <span data-ttu-id="521e1-131">如需如何定義和參考選取集的詳細資訊，請參閱 [定義物件集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="521e1-131">For more information about how selection sets are defined and referenced, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="521e1-132">範例</span><span class="sxs-lookup"><span data-stu-id="521e1-132">Example</span></span>

<span data-ttu-id="521e1-133">下列範例示範如何指定清單視圖的 [system.serviceprocess.dll. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 物件。</span><span class="sxs-lookup"><span data-stu-id="521e1-133">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="521e1-134">資料表、寬和自訂視圖都使用相同的架構。</span><span class="sxs-lookup"><span data-stu-id="521e1-134">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="521e1-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="521e1-135">See Also</span></span>

[<span data-ttu-id="521e1-136">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="521e1-136">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="521e1-137">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="521e1-137">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="521e1-138">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="521e1-138">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="521e1-139">建立自訂控制項</span><span class="sxs-lookup"><span data-stu-id="521e1-139">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="521e1-140">定義選取範圍集合</span><span class="sxs-lookup"><span data-stu-id="521e1-140">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="521e1-141">ViewSelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="521e1-141">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

[<span data-ttu-id="521e1-142">TypeName 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="521e1-142">TypeName Element (Format)</span></span>](./typename-element-for-viewselectedby-format.md)

[<span data-ttu-id="521e1-143">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="521e1-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
