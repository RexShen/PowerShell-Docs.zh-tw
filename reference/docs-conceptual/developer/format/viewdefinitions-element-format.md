---
ms.date: 09/13/2016
ms.topic: reference
title: ViewDefinitions 元素 (格式)
description: ViewDefinitions 元素 (格式)
ms.openlocfilehash: fceef0e5ec91e8c59a7b2b90fd31ca422ff0c94d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664573"
---
# <a name="viewdefinitions-element-format"></a><span data-ttu-id="7e639-103">ViewDefinitions 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7e639-103">ViewDefinitions Element (Format)</span></span>

<span data-ttu-id="7e639-104">定義用來顯示 .NET 物件的視圖。</span><span class="sxs-lookup"><span data-stu-id="7e639-104">Defines the views used to display .NET objects.</span></span> <span data-ttu-id="7e639-105">這些視圖可以用資料表格式、清單格式、寬格式和自訂控制項格式來顯示物件的屬性和腳本值。</span><span class="sxs-lookup"><span data-stu-id="7e639-105">These views can display the properties and script values of an object  in a table format, list format, wide format, and custom control format.</span></span>

<span data-ttu-id="7e639-106">Configuration 元素 (格式) ViewDefinitions (格式 XML) 元素</span><span class="sxs-lookup"><span data-stu-id="7e639-106">Configuration Element (Format) ViewDefinitions (Format XML) Element</span></span>

## <a name="syntax"></a><span data-ttu-id="7e639-107">語法</span><span class="sxs-lookup"><span data-stu-id="7e639-107">Syntax</span></span>

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7e639-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7e639-108">Attributes and Elements</span></span>

<span data-ttu-id="7e639-109">下列各節描述專案的屬性、子項目和父元素 `ViewDefinitions` 。</span><span class="sxs-lookup"><span data-stu-id="7e639-109">The following sections describe the attributes, child elements, and parent element of the `ViewDefinitions` element.</span></span> <span data-ttu-id="7e639-110">在格式化檔案中可定義的視圖數目沒有任何限制，而且可以依任何順序加入。</span><span class="sxs-lookup"><span data-stu-id="7e639-110">There is no limit to the number of views that can be defined in a formatting file, and they can be added in any order.</span></span>

### <a name="attributes"></a><span data-ttu-id="7e639-111">屬性</span><span class="sxs-lookup"><span data-stu-id="7e639-111">Attributes</span></span>

<span data-ttu-id="7e639-112">無。</span><span class="sxs-lookup"><span data-stu-id="7e639-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7e639-113">子元素</span><span class="sxs-lookup"><span data-stu-id="7e639-113">Child Elements</span></span>

|<span data-ttu-id="7e639-114">元素</span><span class="sxs-lookup"><span data-stu-id="7e639-114">Element</span></span>|<span data-ttu-id="7e639-115">描述</span><span class="sxs-lookup"><span data-stu-id="7e639-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7e639-116">檢視元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7e639-116">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="7e639-117">定義用來顯示一或多個 .NET 物件的視圖。</span><span class="sxs-lookup"><span data-stu-id="7e639-117">Defines a view that is used to display one or more .NET objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7e639-118">父項目</span><span class="sxs-lookup"><span data-stu-id="7e639-118">Parent Elements</span></span>

|<span data-ttu-id="7e639-119">元素</span><span class="sxs-lookup"><span data-stu-id="7e639-119">Element</span></span>|<span data-ttu-id="7e639-120">描述</span><span class="sxs-lookup"><span data-stu-id="7e639-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7e639-121">設定元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7e639-121">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="7e639-122">代表格式化檔案的最上層元素。</span><span class="sxs-lookup"><span data-stu-id="7e639-122">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7e639-123">備註</span><span class="sxs-lookup"><span data-stu-id="7e639-123">Remarks</span></span>

<span data-ttu-id="7e639-124">如需不同檢視類型元件的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="7e639-124">For more information about the components of the different types of views, see the following topics:</span></span>

- [<span data-ttu-id="7e639-125">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="7e639-125">Creating a Table View</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="7e639-126">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="7e639-126">Creating a List View</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="7e639-127">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="7e639-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="7e639-128">自訂控制項</span><span class="sxs-lookup"><span data-stu-id="7e639-128">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="7e639-129">範例</span><span class="sxs-lookup"><span data-stu-id="7e639-129">Example</span></span>

<span data-ttu-id="7e639-130">這個範例顯示一個專案 `ViewDefinitions` ，其中包含資料表視圖和清單視圖的父元素。</span><span class="sxs-lookup"><span data-stu-id="7e639-130">This example shows a `ViewDefinitions` element that contains the parent elements for a table view and a list view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7e639-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e639-131">See Also</span></span>

[<span data-ttu-id="7e639-132">設定元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7e639-132">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="7e639-133">檢視元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7e639-133">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="7e639-134">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="7e639-134">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="7e639-135">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="7e639-135">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="7e639-136">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="7e639-136">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="7e639-137">自訂控制項</span><span class="sxs-lookup"><span data-stu-id="7e639-137">Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="7e639-138">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="7e639-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
