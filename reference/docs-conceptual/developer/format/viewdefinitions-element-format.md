---
title: ViewDefinitions 元素 (格式) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a108c4f8b03e3dec3905181b390aee2c82ab0028
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772479"
---
# <a name="viewdefinitions-element-format"></a><span data-ttu-id="98879-102">ViewDefinitions 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="98879-102">ViewDefinitions Element (Format)</span></span>

<span data-ttu-id="98879-103">定義用來顯示 .NET 物件的視圖。</span><span class="sxs-lookup"><span data-stu-id="98879-103">Defines the views used to display .NET objects.</span></span> <span data-ttu-id="98879-104">這些視圖可以使用資料表格式、清單格式、寬格式和自訂控制項格式來顯示物件的屬性和腳本值。</span><span class="sxs-lookup"><span data-stu-id="98879-104">These views can display the properties and script values of an object  in a table format, list format, wide format, and custom control format.</span></span>

<span data-ttu-id="98879-105">Configuration 元素 (格式) ViewDefinitions (格式 XML) 元素</span><span class="sxs-lookup"><span data-stu-id="98879-105">Configuration Element (Format) ViewDefinitions (Format XML) Element</span></span>

## <a name="syntax"></a><span data-ttu-id="98879-106">語法</span><span class="sxs-lookup"><span data-stu-id="98879-106">Syntax</span></span>

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="98879-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="98879-107">Attributes and Elements</span></span>

<span data-ttu-id="98879-108">下列各節描述元素的屬性、子專案和父項目 `ViewDefinitions` 。</span><span class="sxs-lookup"><span data-stu-id="98879-108">The following sections describe the attributes, child elements, and parent element of the `ViewDefinitions` element.</span></span> <span data-ttu-id="98879-109">可以在格式化檔案中定義的視圖數目沒有限制，而且可以依任何順序加入。</span><span class="sxs-lookup"><span data-stu-id="98879-109">There is no limit to the number of views that can be defined in a formatting file, and they can be added in any order.</span></span>

### <a name="attributes"></a><span data-ttu-id="98879-110">屬性</span><span class="sxs-lookup"><span data-stu-id="98879-110">Attributes</span></span>

<span data-ttu-id="98879-111">無。</span><span class="sxs-lookup"><span data-stu-id="98879-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="98879-112">子元素</span><span class="sxs-lookup"><span data-stu-id="98879-112">Child Elements</span></span>

|<span data-ttu-id="98879-113">元素</span><span class="sxs-lookup"><span data-stu-id="98879-113">Element</span></span>|<span data-ttu-id="98879-114">描述</span><span class="sxs-lookup"><span data-stu-id="98879-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="98879-115">檢視元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="98879-115">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="98879-116">定義用來顯示一個或多個 .NET 物件的視圖。</span><span class="sxs-lookup"><span data-stu-id="98879-116">Defines a view that is used to display one or more .NET objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="98879-117">父項目</span><span class="sxs-lookup"><span data-stu-id="98879-117">Parent Elements</span></span>

|<span data-ttu-id="98879-118">元素</span><span class="sxs-lookup"><span data-stu-id="98879-118">Element</span></span>|<span data-ttu-id="98879-119">描述</span><span class="sxs-lookup"><span data-stu-id="98879-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="98879-120">設定元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="98879-120">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="98879-121">代表格式化檔案的最上層元素。</span><span class="sxs-lookup"><span data-stu-id="98879-121">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="98879-122">備註</span><span class="sxs-lookup"><span data-stu-id="98879-122">Remarks</span></span>

<span data-ttu-id="98879-123">如需不同類型之視圖元件的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="98879-123">For more information about the components of the different types of views, see the following topics:</span></span>

- [<span data-ttu-id="98879-124">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="98879-124">Creating a Table View</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="98879-125">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="98879-125">Creating a List View</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="98879-126">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="98879-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="98879-127">自訂控制項</span><span class="sxs-lookup"><span data-stu-id="98879-127">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="98879-128">範例</span><span class="sxs-lookup"><span data-stu-id="98879-128">Example</span></span>

<span data-ttu-id="98879-129">這個範例會顯示一個 `ViewDefinitions` 元素，其中包含資料表視圖和清單視圖的父元素。</span><span class="sxs-lookup"><span data-stu-id="98879-129">This example shows a `ViewDefinitions` element that contains the parent elements for a table view and a list view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="98879-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98879-130">See Also</span></span>

[<span data-ttu-id="98879-131">設定元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="98879-131">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="98879-132">檢視元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="98879-132">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="98879-133">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="98879-133">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="98879-134">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="98879-134">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="98879-135">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="98879-135">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="98879-136">自訂控制項</span><span class="sxs-lookup"><span data-stu-id="98879-136">Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="98879-137">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="98879-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
