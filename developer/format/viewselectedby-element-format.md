---
title: ViewSelectedBy 項目 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acdeef4d-3554-4f39-a7e6-a684e3848fd7
caps.latest.revision: 19
ms.openlocfilehash: efc1c5d1338889ecd0be7150b7733842ce78979e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083819"
---
# <a name="viewselectedby-element-format"></a><span data-ttu-id="345b9-102">ViewSelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="345b9-102">ViewSelectedBy Element (Format)</span></span>

<span data-ttu-id="345b9-103">定義檢視所顯示的.NET 物件。</span><span class="sxs-lookup"><span data-stu-id="345b9-103">Defines the .NET objects that are displayed by the view.</span></span> <span data-ttu-id="345b9-104">每個檢視都必須指定至少一個.NET 物件。</span><span class="sxs-lookup"><span data-stu-id="345b9-104">Each view must specify at least one .NET object.</span></span>

<span data-ttu-id="345b9-105">ViewDefinitions 項目 （格式） 檢視項目 （格式） ViewSelectedBy 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="345b9-105">ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="345b9-106">語法</span><span class="sxs-lookup"><span data-stu-id="345b9-106">Syntax</span></span>

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="345b9-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="345b9-107">Attributes and Elements</span></span>

<span data-ttu-id="345b9-108">下列各節說明屬性、 子項目和父項目`ViewSelectedBy`項目。</span><span class="sxs-lookup"><span data-stu-id="345b9-108">The following sections describe the attributes, child elements, and parent element of the `ViewSelectedBy` element.</span></span> <span data-ttu-id="345b9-109">這個項目必須包含至少一個`TypeName`或`SelectionSetName`子項目。</span><span class="sxs-lookup"><span data-stu-id="345b9-109">This element must contain at least one `TypeName` or `SelectionSetName` child element.</span></span> <span data-ttu-id="345b9-110">您可以指定的子元素的數目沒有限制也不是重要的順序。</span><span class="sxs-lookup"><span data-stu-id="345b9-110">There is no limit to the number of child elements that can be specified nor is their order significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="345b9-111">屬性</span><span class="sxs-lookup"><span data-stu-id="345b9-111">Attributes</span></span>

<span data-ttu-id="345b9-112">無。</span><span class="sxs-lookup"><span data-stu-id="345b9-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="345b9-113">子元素</span><span class="sxs-lookup"><span data-stu-id="345b9-113">Child Elements</span></span>

|<span data-ttu-id="345b9-114">元素</span><span class="sxs-lookup"><span data-stu-id="345b9-114">Element</span></span>|<span data-ttu-id="345b9-115">描述</span><span class="sxs-lookup"><span data-stu-id="345b9-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="345b9-116">TypeName ViewSelectedBy （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="345b9-116">TypeName Element for ViewSelectedBy (Format)</span></span>](./typename-element-for-viewselectedby-format.md)|<span data-ttu-id="345b9-117">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="345b9-117">Optional element.</span></span><br /><br /> <span data-ttu-id="345b9-118">指定檢視所顯示的.NET 物件。</span><span class="sxs-lookup"><span data-stu-id="345b9-118">Specifies a .NET object that is displayed by the view.</span></span>|
|[<span data-ttu-id="345b9-119">SelectionSetName ViewSelectedBy （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="345b9-119">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)|<span data-ttu-id="345b9-120">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="345b9-120">Optional element.</span></span><br /><br /> <span data-ttu-id="345b9-121">指定一份檢視所顯示的.NET 物件。</span><span class="sxs-lookup"><span data-stu-id="345b9-121">Specifies a set of .NET objects that are displayed by the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="345b9-122">父項目</span><span class="sxs-lookup"><span data-stu-id="345b9-122">Parent Elements</span></span>

|<span data-ttu-id="345b9-123">項目</span><span class="sxs-lookup"><span data-stu-id="345b9-123">Element</span></span>|<span data-ttu-id="345b9-124">描述</span><span class="sxs-lookup"><span data-stu-id="345b9-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="345b9-125">檢視項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="345b9-125">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="345b9-126">定義顯示一或多個.NET 物件的檢視。</span><span class="sxs-lookup"><span data-stu-id="345b9-126">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="345b9-127">備註</span><span class="sxs-lookup"><span data-stu-id="345b9-127">Remarks</span></span>

<span data-ttu-id="345b9-128">如需如何在不同的檢視會使用這個元素的詳細資訊，請參閱[資料表的檢視元件](./creating-a-table-view.md)，[清單檢視元件](./creating-a-list-view.md)，[寬型檢視元件](./creating-a-wide-view.md)，以及[自訂控制項元件](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="345b9-128">For more information about how this element is used in different views, see [Table View Components](./creating-a-table-view.md), [List View Components](./creating-a-list-view.md), [Wide View Components](./creating-a-wide-view.md), and [Custom Control Components](./creating-custom-controls.md).</span></span>

<span data-ttu-id="345b9-129">`SelectionSetName`時的格式化檔案會定義一組的多個檢視所顯示的物件，會使用項目。</span><span class="sxs-lookup"><span data-stu-id="345b9-129">The `SelectionSetName` element is used when the formatting file defines a set of objects that are displayed by multiple views.</span></span> <span data-ttu-id="345b9-130">如需有關如何選取項目集所定義，且參考的詳細資訊，請參閱 <<c0> [ 定義設定的物件](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="345b9-130">For more information about how selection sets are defined and referenced, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="345b9-131">範例</span><span class="sxs-lookup"><span data-stu-id="345b9-131">Example</span></span>

<span data-ttu-id="345b9-132">下列範例示範如何指定[System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)針對清單檢視的物件。</span><span class="sxs-lookup"><span data-stu-id="345b9-132">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="345b9-133">相同的結構描述用於資料表，，和自訂檢視。</span><span class="sxs-lookup"><span data-stu-id="345b9-133">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="345b9-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="345b9-134">See Also</span></span>

[<span data-ttu-id="345b9-135">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="345b9-135">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="345b9-136">建立資料表檢視</span><span class="sxs-lookup"><span data-stu-id="345b9-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="345b9-137">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="345b9-137">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="345b9-138">建立自訂控制項</span><span class="sxs-lookup"><span data-stu-id="345b9-138">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="345b9-139">定義選取範圍</span><span class="sxs-lookup"><span data-stu-id="345b9-139">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="345b9-140">SelectionSetName ViewSelectedBy （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="345b9-140">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

[<span data-ttu-id="345b9-141">TypeName 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="345b9-141">TypeName Element (Format)</span></span>](./typename-element-for-viewselectedby-format.md)

[<span data-ttu-id="345b9-142">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="345b9-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
