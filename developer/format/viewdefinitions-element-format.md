---
title: ViewDefinitions 項目 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29840c10-2b30-4bb1-a8a0-ddf84d19c2d0
caps.latest.revision: 18
ms.openlocfilehash: c5ec80350c7707ccd41112ab5e1952e5dc198cca
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083700"
---
# <a name="viewdefinitions-element-format"></a><span data-ttu-id="c02f9-102">ViewDefinitions 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c02f9-102">ViewDefinitions Element (Format)</span></span>

<span data-ttu-id="c02f9-103">定義用來顯示.NET 物件的檢視。</span><span class="sxs-lookup"><span data-stu-id="c02f9-103">Defines the views used to display .NET objects.</span></span> <span data-ttu-id="c02f9-104">這些檢視可以表格格式，清單格式、 寬的格式和自訂控制項格式中顯示的屬性和物件的指令碼值。</span><span class="sxs-lookup"><span data-stu-id="c02f9-104">These views can display the properties and script values of an object  in a table format, list format, wide format, and custom control format.</span></span>

<span data-ttu-id="c02f9-105">組態項目 （格式） ViewDefinitions （格式為 XML） 項目</span><span class="sxs-lookup"><span data-stu-id="c02f9-105">Configuration Element (Format) ViewDefinitions (Format XML) Element</span></span>

## <a name="syntax"></a><span data-ttu-id="c02f9-106">語法</span><span class="sxs-lookup"><span data-stu-id="c02f9-106">Syntax</span></span>

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c02f9-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c02f9-107">Attributes and Elements</span></span>

<span data-ttu-id="c02f9-108">下列各節說明屬性、 子項目和父項目`ViewDefinitions`項目。</span><span class="sxs-lookup"><span data-stu-id="c02f9-108">The following sections describe the attributes, child elements, and parent element of the `ViewDefinitions` element.</span></span> <span data-ttu-id="c02f9-109">可以在格式檔案中，定義的檢視數目沒有限制，並將它們加入以任何順序。</span><span class="sxs-lookup"><span data-stu-id="c02f9-109">There is no limit to the number of views that can be defined in a formatting file, and they can be added in any order.</span></span>

### <a name="attributes"></a><span data-ttu-id="c02f9-110">屬性</span><span class="sxs-lookup"><span data-stu-id="c02f9-110">Attributes</span></span>

<span data-ttu-id="c02f9-111">無。</span><span class="sxs-lookup"><span data-stu-id="c02f9-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c02f9-112">子元素</span><span class="sxs-lookup"><span data-stu-id="c02f9-112">Child Elements</span></span>

|<span data-ttu-id="c02f9-113">元素</span><span class="sxs-lookup"><span data-stu-id="c02f9-113">Element</span></span>|<span data-ttu-id="c02f9-114">描述</span><span class="sxs-lookup"><span data-stu-id="c02f9-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c02f9-115">檢視項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="c02f9-115">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="c02f9-116">定義用來顯示一或多個.NET 物件的檢視。</span><span class="sxs-lookup"><span data-stu-id="c02f9-116">Defines a view that is used to display one or more .NET objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c02f9-117">父項目</span><span class="sxs-lookup"><span data-stu-id="c02f9-117">Parent Elements</span></span>

|<span data-ttu-id="c02f9-118">項目</span><span class="sxs-lookup"><span data-stu-id="c02f9-118">Element</span></span>|<span data-ttu-id="c02f9-119">描述</span><span class="sxs-lookup"><span data-stu-id="c02f9-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c02f9-120">組態項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="c02f9-120">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="c02f9-121">表示格式化檔案的最上層項目。</span><span class="sxs-lookup"><span data-stu-id="c02f9-121">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c02f9-122">備註</span><span class="sxs-lookup"><span data-stu-id="c02f9-122">Remarks</span></span>

<span data-ttu-id="c02f9-123">如需有關不同類型的檢視元件的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="c02f9-123">For more information about the components of the different types of views, see the following topics:</span></span>

- [<span data-ttu-id="c02f9-124">建立資料表檢視</span><span class="sxs-lookup"><span data-stu-id="c02f9-124">Creating a Table View</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="c02f9-125">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="c02f9-125">Creating a List View</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="c02f9-126">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="c02f9-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="c02f9-127">自訂控制項</span><span class="sxs-lookup"><span data-stu-id="c02f9-127">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="c02f9-128">範例</span><span class="sxs-lookup"><span data-stu-id="c02f9-128">Example</span></span>

<span data-ttu-id="c02f9-129">此範例示範`ViewDefinitions`包含父項目資料表檢視] 和 [清單檢視項目。</span><span class="sxs-lookup"><span data-stu-id="c02f9-129">This example shows a `ViewDefinitions` element that contains the parent elements for a table view and a list view.</span></span>

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <TableControl>...</TableControl>
    </View>
    <View>
      <ListControl>...</ListControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

## <a name="see-also"></a><span data-ttu-id="c02f9-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c02f9-130">See Also</span></span>

[<span data-ttu-id="c02f9-131">組態項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="c02f9-131">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="c02f9-132">檢視項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="c02f9-132">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="c02f9-133">建立資料表檢視</span><span class="sxs-lookup"><span data-stu-id="c02f9-133">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="c02f9-134">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="c02f9-134">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="c02f9-135">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="c02f9-135">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="c02f9-136">自訂控制項</span><span class="sxs-lookup"><span data-stu-id="c02f9-136">Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="c02f9-137">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="c02f9-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
