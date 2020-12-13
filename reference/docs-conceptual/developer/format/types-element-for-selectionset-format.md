---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSet 的類型元素 (格式)
description: SelectionSet 的類型元素 (格式)
ms.openlocfilehash: ff3c24e7f52f862dc416b88d50983196ce907012
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645462"
---
# <a name="types-element-for-selectionset-format"></a><span data-ttu-id="2e427-103">SelectionSet 的類型元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2e427-103">Types Element for SelectionSet (Format)</span></span>

<span data-ttu-id="2e427-104">定義選取專案集中的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="2e427-104">Defines the .NET objects that are in the selection set.</span></span>

<span data-ttu-id="2e427-105">Configuration 元素 (格式) SelectionSets 元素 (格式) SelectionSet 專案 (格式) 類型元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="2e427-105">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2e427-106">語法</span><span class="sxs-lookup"><span data-stu-id="2e427-106">Syntax</span></span>

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="2e427-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2e427-107">Attributes and Elements</span></span>

<span data-ttu-id="2e427-108">下列章節說明屬性、子專案和元素的父元素 `Types` 。</span><span class="sxs-lookup"><span data-stu-id="2e427-108">The following sections describe the attributes, child elements, and the parent element of the `Types` element.</span></span> <span data-ttu-id="2e427-109">至少必須有一個子項目，但可加入的子專案數目沒有最大限制。</span><span class="sxs-lookup"><span data-stu-id="2e427-109">There must be at least one child element, but there is no maximum limit to the number of child elements that can be added.</span></span>

### <a name="attributes"></a><span data-ttu-id="2e427-110">屬性</span><span class="sxs-lookup"><span data-stu-id="2e427-110">Attributes</span></span>

<span data-ttu-id="2e427-111">無。</span><span class="sxs-lookup"><span data-stu-id="2e427-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2e427-112">子元素</span><span class="sxs-lookup"><span data-stu-id="2e427-112">Child Elements</span></span>

|<span data-ttu-id="2e427-113">元素</span><span class="sxs-lookup"><span data-stu-id="2e427-113">Element</span></span>|<span data-ttu-id="2e427-114">描述</span><span class="sxs-lookup"><span data-stu-id="2e427-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2e427-115">類型的 TypeName 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="2e427-115">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)|<span data-ttu-id="2e427-116">必要元素。</span><span class="sxs-lookup"><span data-stu-id="2e427-116">Required element.</span></span><br /><br /> <span data-ttu-id="2e427-117">指定屬於選取集的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="2e427-117">Specifies the .NET object that belongs to the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2e427-118">父項目</span><span class="sxs-lookup"><span data-stu-id="2e427-118">Parent Elements</span></span>

|<span data-ttu-id="2e427-119">元素</span><span class="sxs-lookup"><span data-stu-id="2e427-119">Element</span></span>|<span data-ttu-id="2e427-120">描述</span><span class="sxs-lookup"><span data-stu-id="2e427-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2e427-121">SelectionSet 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2e427-121">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="2e427-122">定義一組可由集合名稱參考的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="2e427-122">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2e427-123">備註</span><span class="sxs-lookup"><span data-stu-id="2e427-123">Remarks</span></span>

<span data-ttu-id="2e427-124">這個專案所定義的物件會組成一個可供視圖使用的選取範圍， (views 可以有多個定義) 或指定選取條件。</span><span class="sxs-lookup"><span data-stu-id="2e427-124">The objects defined by this element make up a selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span>  <span data-ttu-id="2e427-125">如需選取集的詳細資訊，請參閱 [定義物件集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="2e427-125">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="2e427-126">範例</span><span class="sxs-lookup"><span data-stu-id="2e427-126">Example</span></span>

<span data-ttu-id="2e427-127">此範例顯示 `SelectionSet` 定義四個 .net 類型的元素。</span><span class="sxs-lookup"><span data-stu-id="2e427-127">This example shows a `SelectionSet` element that defines four .NET types.</span></span>

```xml
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

## <a name="see-also"></a><span data-ttu-id="2e427-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e427-128">See Also</span></span>

[<span data-ttu-id="2e427-129">定義物件集</span><span class="sxs-lookup"><span data-stu-id="2e427-129">Defining Sets of Objects</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="2e427-130">SelectionSet 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2e427-130">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="2e427-131">類型的 TypeName 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="2e427-131">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)

[<span data-ttu-id="2e427-132">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="2e427-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
