---
title: 類型的 TypeName 元素 (格式) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 40fad73c66124d6c3b0d969b4268713a492c963a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772530"
---
# <a name="typename-element-for-types-format"></a><span data-ttu-id="845bd-102">類型的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="845bd-102">TypeName Element for Types (Format)</span></span>

<span data-ttu-id="845bd-103">指定屬於選取集之物件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="845bd-103">Specifies the .NET type of an object that belongs to the selection set.</span></span>

<span data-ttu-id="845bd-104">Configuration 元素 (格式) SelectionSets 元素 (格式) SelectionSet 專案 (格式) 類型元素 (格式) 格式的類型名稱元素 (</span><span class="sxs-lookup"><span data-stu-id="845bd-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format) TypeName Element of Types (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="845bd-105">語法</span><span class="sxs-lookup"><span data-stu-id="845bd-105">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="845bd-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="845bd-106">Attributes and Elements</span></span>

<span data-ttu-id="845bd-107">下列各節說明屬性、子專案和元素的父元素 `TypeName` 。</span><span class="sxs-lookup"><span data-stu-id="845bd-107">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span> <span data-ttu-id="845bd-108">`TypeName`選取範圍中至少必須包含一個元素。</span><span class="sxs-lookup"><span data-stu-id="845bd-108">At least one `TypeName` element must be included in the selection set.</span></span>

### <a name="attributes"></a><span data-ttu-id="845bd-109">屬性</span><span class="sxs-lookup"><span data-stu-id="845bd-109">Attributes</span></span>

<span data-ttu-id="845bd-110">無。</span><span class="sxs-lookup"><span data-stu-id="845bd-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="845bd-111">子元素</span><span class="sxs-lookup"><span data-stu-id="845bd-111">Child Elements</span></span>

<span data-ttu-id="845bd-112">無。</span><span class="sxs-lookup"><span data-stu-id="845bd-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="845bd-113">父項目</span><span class="sxs-lookup"><span data-stu-id="845bd-113">Parent Elements</span></span>

|<span data-ttu-id="845bd-114">元素</span><span class="sxs-lookup"><span data-stu-id="845bd-114">Element</span></span>|<span data-ttu-id="845bd-115">描述</span><span class="sxs-lookup"><span data-stu-id="845bd-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="845bd-116">Types 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="845bd-116">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="845bd-117">定義選取集中的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="845bd-117">Defines the .NET objects that are in the selection set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="845bd-118">文字值</span><span class="sxs-lookup"><span data-stu-id="845bd-118">Text Value</span></span>

<span data-ttu-id="845bd-119">指定 .NET 類型的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="845bd-119">Specify the fully qualified name for the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="845bd-120">備註</span><span class="sxs-lookup"><span data-stu-id="845bd-120">Remarks</span></span>

<span data-ttu-id="845bd-121">當您有一組想要使用單一名稱來參考的相關物件（例如透過繼承相關的一組物件）時，您可以使用 [選擇集]。</span><span class="sxs-lookup"><span data-stu-id="845bd-121">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="845bd-122">定義您的視圖時，您可以使用選取範圍的名稱來指定物件集合，而不會列出每個視圖內的所有物件。</span><span class="sxs-lookup"><span data-stu-id="845bd-122">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="845bd-123">定義格式設定檔案的視圖時，會以名稱指定一般選取範圍。</span><span class="sxs-lookup"><span data-stu-id="845bd-123">Common selection sets are specified by their name when defining the views of the formatting file.</span></span> <span data-ttu-id="845bd-124">在這些情況下， `SelectionSetName` view 元素的子項目會 `ViewSelectedBy` 指定集合。</span><span class="sxs-lookup"><span data-stu-id="845bd-124">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` element for the view specifies the set.</span></span> <span data-ttu-id="845bd-125">不過，不同的視圖專案也可以指定僅適用于該視圖專案的選擇集。</span><span class="sxs-lookup"><span data-stu-id="845bd-125">However, different entries of a view can also specify a selection set that applies to only that entry of the view.</span></span> <span data-ttu-id="845bd-126">如需選取集的詳細資訊，請參閱[定義物件的集合](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="845bd-126">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="845bd-127">範例</span><span class="sxs-lookup"><span data-stu-id="845bd-127">Example</span></span>

<span data-ttu-id="845bd-128">下列範例顯示 `SelectionSet` 定義四個 .net 類型的元素。</span><span class="sxs-lookup"><span data-stu-id="845bd-128">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

```
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

## <a name="see-also"></a><span data-ttu-id="845bd-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="845bd-129">See Also</span></span>

[<span data-ttu-id="845bd-130">定義選取範圍集合</span><span class="sxs-lookup"><span data-stu-id="845bd-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="845bd-131">SelectionSet 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="845bd-131">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="845bd-132">SelectionSets 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="845bd-132">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="845bd-133">Types 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="845bd-133">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="845bd-134">撰寫 Windows PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="845bd-134">Writing a Windows PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
