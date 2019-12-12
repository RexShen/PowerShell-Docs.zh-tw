---
title: ViewSelectedBy 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acdeef4d-3554-4f39-a7e6-a684e3848fd7
caps.latest.revision: 19
ms.openlocfilehash: efc1c5d1338889ecd0be7150b7733842ce78979e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367967"
---
# <a name="viewselectedby-element-format"></a><span data-ttu-id="07816-102">ViewSelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="07816-102">ViewSelectedBy Element (Format)</span></span>

<span data-ttu-id="07816-103">定義視圖所顯示的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="07816-103">Defines the .NET objects that are displayed by the view.</span></span> <span data-ttu-id="07816-104">每個視圖都必須指定至少一個 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="07816-104">Each view must specify at least one .NET object.</span></span>

<span data-ttu-id="07816-105">ViewDefinitions 元素（格式） View 元素（Format） ViewSelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="07816-105">ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="07816-106">語法</span><span class="sxs-lookup"><span data-stu-id="07816-106">Syntax</span></span>

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="07816-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="07816-107">Attributes and Elements</span></span>

<span data-ttu-id="07816-108">下列各節描述 `ViewSelectedBy` 專案的屬性、子專案和父項目。</span><span class="sxs-lookup"><span data-stu-id="07816-108">The following sections describe the attributes, child elements, and parent element of the `ViewSelectedBy` element.</span></span> <span data-ttu-id="07816-109">此元素必須包含至少一個 `TypeName` 或 `SelectionSetName` 子項目。</span><span class="sxs-lookup"><span data-stu-id="07816-109">This element must contain at least one `TypeName` or `SelectionSetName` child element.</span></span> <span data-ttu-id="07816-110">可以指定的子項目數目沒有限制，也沒有排序次序。</span><span class="sxs-lookup"><span data-stu-id="07816-110">There is no limit to the number of child elements that can be specified nor is their order significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="07816-111">屬性</span><span class="sxs-lookup"><span data-stu-id="07816-111">Attributes</span></span>

<span data-ttu-id="07816-112">無。</span><span class="sxs-lookup"><span data-stu-id="07816-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="07816-113">子元素</span><span class="sxs-lookup"><span data-stu-id="07816-113">Child Elements</span></span>

|<span data-ttu-id="07816-114">元素</span><span class="sxs-lookup"><span data-stu-id="07816-114">Element</span></span>|<span data-ttu-id="07816-115">描述</span><span class="sxs-lookup"><span data-stu-id="07816-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="07816-116">ViewSelectedBy 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="07816-116">TypeName Element for ViewSelectedBy (Format)</span></span>](./typename-element-for-viewselectedby-format.md)|<span data-ttu-id="07816-117">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="07816-117">Optional element.</span></span><br /><br /> <span data-ttu-id="07816-118">指定由視圖顯示的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="07816-118">Specifies a .NET object that is displayed by the view.</span></span>|
|[<span data-ttu-id="07816-119">ViewSelectedBy 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="07816-119">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)|<span data-ttu-id="07816-120">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="07816-120">Optional element.</span></span><br /><br /> <span data-ttu-id="07816-121">指定由視圖顯示的一組 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="07816-121">Specifies a set of .NET objects that are displayed by the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="07816-122">父元素</span><span class="sxs-lookup"><span data-stu-id="07816-122">Parent Elements</span></span>

|<span data-ttu-id="07816-123">元素</span><span class="sxs-lookup"><span data-stu-id="07816-123">Element</span></span>|<span data-ttu-id="07816-124">描述</span><span class="sxs-lookup"><span data-stu-id="07816-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="07816-125">View 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="07816-125">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="07816-126">定義顯示一或多個 .NET 物件的視圖。</span><span class="sxs-lookup"><span data-stu-id="07816-126">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="07816-127">備註</span><span class="sxs-lookup"><span data-stu-id="07816-127">Remarks</span></span>

<span data-ttu-id="07816-128">如需如何在不同的視圖中使用此元素的詳細資訊，請參閱[資料表視圖元件](./creating-a-table-view.md)、[清單視圖元件](./creating-a-list-view.md)、[寬視圖元件](./creating-a-wide-view.md)和[自訂控制群組件](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="07816-128">For more information about how this element is used in different views, see [Table View Components](./creating-a-table-view.md), [List View Components](./creating-a-list-view.md), [Wide View Components](./creating-a-wide-view.md), and [Custom Control Components](./creating-custom-controls.md).</span></span>

<span data-ttu-id="07816-129">當格式設定檔案定義多個視圖所顯示的一組物件時，會使用 `SelectionSetName` 元素。</span><span class="sxs-lookup"><span data-stu-id="07816-129">The `SelectionSetName` element is used when the formatting file defines a set of objects that are displayed by multiple views.</span></span> <span data-ttu-id="07816-130">如需如何定義和參考選取集的詳細資訊，請參閱[定義物件集合](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="07816-130">For more information about how selection sets are defined and referenced, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="07816-131">範例</span><span class="sxs-lookup"><span data-stu-id="07816-131">Example</span></span>

<span data-ttu-id="07816-132">下列範例示範如何指定清單視圖的[system.serviceprocess.dll. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)物件。</span><span class="sxs-lookup"><span data-stu-id="07816-132">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="07816-133">資料表、寬型和自訂視圖會使用相同的架構。</span><span class="sxs-lookup"><span data-stu-id="07816-133">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="07816-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07816-134">See Also</span></span>

[<span data-ttu-id="07816-135">建立清單視圖</span><span class="sxs-lookup"><span data-stu-id="07816-135">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="07816-136">建立資料表視圖</span><span class="sxs-lookup"><span data-stu-id="07816-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="07816-137">建立寬型視圖</span><span class="sxs-lookup"><span data-stu-id="07816-137">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="07816-138">建立自訂控制項</span><span class="sxs-lookup"><span data-stu-id="07816-138">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="07816-139">定義選取範圍集合</span><span class="sxs-lookup"><span data-stu-id="07816-139">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="07816-140">ViewSelectedBy 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="07816-140">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

[<span data-ttu-id="07816-141">TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="07816-141">TypeName Element (Format)</span></span>](./typename-element-for-viewselectedby-format.md)

[<span data-ttu-id="07816-142">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="07816-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
