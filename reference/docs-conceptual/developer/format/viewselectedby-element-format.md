---
title: ViewSelectedBy 元素 (格式) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c8704c1504c6e24c9cac6bc8bc25e92a0d9110cc
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785008"
---
# <a name="viewselectedby-element-format"></a><span data-ttu-id="2e254-102">ViewSelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2e254-102">ViewSelectedBy Element (Format)</span></span>

<span data-ttu-id="2e254-103">定義視圖所顯示的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="2e254-103">Defines the .NET objects that are displayed by the view.</span></span> <span data-ttu-id="2e254-104">每個視圖都必須指定至少一個 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="2e254-104">Each view must specify at least one .NET object.</span></span>

<span data-ttu-id="2e254-105">ViewDefinitions 元素 (格式) View 元素 (格式) ViewSelectedBy 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="2e254-105">ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2e254-106">語法</span><span class="sxs-lookup"><span data-stu-id="2e254-106">Syntax</span></span>

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2e254-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2e254-107">Attributes and Elements</span></span>

<span data-ttu-id="2e254-108">下列各節描述元素的屬性、子專案和父項目 `ViewSelectedBy` 。</span><span class="sxs-lookup"><span data-stu-id="2e254-108">The following sections describe the attributes, child elements, and parent element of the `ViewSelectedBy` element.</span></span> <span data-ttu-id="2e254-109">此元素必須包含至少一個 `TypeName` 或 `SelectionSetName` 子項目。</span><span class="sxs-lookup"><span data-stu-id="2e254-109">This element must contain at least one `TypeName` or `SelectionSetName` child element.</span></span> <span data-ttu-id="2e254-110">可以指定的子項目數目沒有限制，也沒有排序次序。</span><span class="sxs-lookup"><span data-stu-id="2e254-110">There is no limit to the number of child elements that can be specified nor is their order significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="2e254-111">屬性</span><span class="sxs-lookup"><span data-stu-id="2e254-111">Attributes</span></span>

<span data-ttu-id="2e254-112">無。</span><span class="sxs-lookup"><span data-stu-id="2e254-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2e254-113">子元素</span><span class="sxs-lookup"><span data-stu-id="2e254-113">Child Elements</span></span>

|<span data-ttu-id="2e254-114">元素</span><span class="sxs-lookup"><span data-stu-id="2e254-114">Element</span></span>|<span data-ttu-id="2e254-115">描述</span><span class="sxs-lookup"><span data-stu-id="2e254-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2e254-116">ViewSelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2e254-116">TypeName Element for ViewSelectedBy (Format)</span></span>](./typename-element-for-viewselectedby-format.md)|<span data-ttu-id="2e254-117">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="2e254-117">Optional element.</span></span><br /><br /> <span data-ttu-id="2e254-118">指定由視圖顯示的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="2e254-118">Specifies a .NET object that is displayed by the view.</span></span>|
|[<span data-ttu-id="2e254-119">ViewSelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2e254-119">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)|<span data-ttu-id="2e254-120">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="2e254-120">Optional element.</span></span><br /><br /> <span data-ttu-id="2e254-121">指定由視圖顯示的一組 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="2e254-121">Specifies a set of .NET objects that are displayed by the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2e254-122">父項目</span><span class="sxs-lookup"><span data-stu-id="2e254-122">Parent Elements</span></span>

|<span data-ttu-id="2e254-123">元素</span><span class="sxs-lookup"><span data-stu-id="2e254-123">Element</span></span>|<span data-ttu-id="2e254-124">描述</span><span class="sxs-lookup"><span data-stu-id="2e254-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2e254-125">檢視元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2e254-125">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="2e254-126">定義顯示一或多個 .NET 物件的視圖。</span><span class="sxs-lookup"><span data-stu-id="2e254-126">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2e254-127">備註</span><span class="sxs-lookup"><span data-stu-id="2e254-127">Remarks</span></span>

<span data-ttu-id="2e254-128">如需如何在不同的視圖中使用此元素的詳細資訊，請參閱[資料表視圖元件](./creating-a-table-view.md)、[清單視圖元件](./creating-a-list-view.md)、[寬視圖元件](./creating-a-wide-view.md)和[自訂控制群組件](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="2e254-128">For more information about how this element is used in different views, see [Table View Components](./creating-a-table-view.md), [List View Components](./creating-a-list-view.md), [Wide View Components](./creating-a-wide-view.md), and [Custom Control Components](./creating-custom-controls.md).</span></span>

<span data-ttu-id="2e254-129">`SelectionSetName`當格式化檔案定義多個視圖所顯示的一組物件時，便會使用此元素。</span><span class="sxs-lookup"><span data-stu-id="2e254-129">The `SelectionSetName` element is used when the formatting file defines a set of objects that are displayed by multiple views.</span></span> <span data-ttu-id="2e254-130">如需如何定義和參考選取集的詳細資訊，請參閱[定義物件集合](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="2e254-130">For more information about how selection sets are defined and referenced, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="2e254-131">範例</span><span class="sxs-lookup"><span data-stu-id="2e254-131">Example</span></span>

<span data-ttu-id="2e254-132">下列範例示範如何指定清單視圖的[system.serviceprocess.dll. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)物件。</span><span class="sxs-lookup"><span data-stu-id="2e254-132">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="2e254-133">資料表、寬型和自訂視圖會使用相同的架構。</span><span class="sxs-lookup"><span data-stu-id="2e254-133">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="2e254-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e254-134">See Also</span></span>

[<span data-ttu-id="2e254-135">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="2e254-135">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="2e254-136">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="2e254-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="2e254-137">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="2e254-137">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="2e254-138">建立自訂控制項</span><span class="sxs-lookup"><span data-stu-id="2e254-138">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="2e254-139">定義選取範圍集合</span><span class="sxs-lookup"><span data-stu-id="2e254-139">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="2e254-140">ViewSelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2e254-140">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

[<span data-ttu-id="2e254-141">TypeName 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="2e254-141">TypeName Element (Format)</span></span>](./typename-element-for-viewselectedby-format.md)

[<span data-ttu-id="2e254-142">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="2e254-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
