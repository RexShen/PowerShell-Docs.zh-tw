---
title: SelectionSet 的 Types 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4606fec0-ff31-4d36-af68-227405335ec3
caps.latest.revision: 15
ms.openlocfilehash: 0427367efa2c8a7e352d718706d1341a0c8e3621
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367957"
---
# <a name="types-element-for-selectionset-format"></a><span data-ttu-id="d458c-102">SelectionSet 的類型元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d458c-102">Types Element for SelectionSet (Format)</span></span>

<span data-ttu-id="d458c-103">定義選取集中的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="d458c-103">Defines the .NET objects that are in the selection set.</span></span>

<span data-ttu-id="d458c-104">Configuration 元素（格式） SelectionSets 元素（格式） SelectionSet 元素（格式）類型元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d458c-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d458c-105">語法</span><span class="sxs-lookup"><span data-stu-id="d458c-105">Syntax</span></span>

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="d458c-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="d458c-106">Attributes and Elements</span></span>

<span data-ttu-id="d458c-107">下列各節說明屬性、子專案，以及 `Types` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="d458c-107">The following sections describe the attributes, child elements, and the parent element of the `Types` element.</span></span> <span data-ttu-id="d458c-108">必須至少有一個子專案，但可以加入的子專案數目沒有上限。</span><span class="sxs-lookup"><span data-stu-id="d458c-108">There must be at least one child element, but there is no maximum limit to the number of child elements that can be added.</span></span>

### <a name="attributes"></a><span data-ttu-id="d458c-109">屬性</span><span class="sxs-lookup"><span data-stu-id="d458c-109">Attributes</span></span>

<span data-ttu-id="d458c-110">無。</span><span class="sxs-lookup"><span data-stu-id="d458c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d458c-111">子元素</span><span class="sxs-lookup"><span data-stu-id="d458c-111">Child Elements</span></span>

|<span data-ttu-id="d458c-112">元素</span><span class="sxs-lookup"><span data-stu-id="d458c-112">Element</span></span>|<span data-ttu-id="d458c-113">描述</span><span class="sxs-lookup"><span data-stu-id="d458c-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d458c-114">類型的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d458c-114">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)|<span data-ttu-id="d458c-115">必要元素。</span><span class="sxs-lookup"><span data-stu-id="d458c-115">Required element.</span></span><br /><br /> <span data-ttu-id="d458c-116">指定屬於選取集的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="d458c-116">Specifies the .NET object that belongs to the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d458c-117">父元素</span><span class="sxs-lookup"><span data-stu-id="d458c-117">Parent Elements</span></span>

|<span data-ttu-id="d458c-118">元素</span><span class="sxs-lookup"><span data-stu-id="d458c-118">Element</span></span>|<span data-ttu-id="d458c-119">描述</span><span class="sxs-lookup"><span data-stu-id="d458c-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d458c-120">SelectionSet 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d458c-120">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="d458c-121">定義一組可由集合名稱參考的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="d458c-121">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d458c-122">備註</span><span class="sxs-lookup"><span data-stu-id="d458c-122">Remarks</span></span>

<span data-ttu-id="d458c-123">這個專案所定義的物件組成一個可供視圖使用的選擇集，由視圖的定義（views 可以有多個定義）或指定選取條件。</span><span class="sxs-lookup"><span data-stu-id="d458c-123">The objects defined by this element make up a selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span>  <span data-ttu-id="d458c-124">如需選取集的詳細資訊，請參閱[定義物件的集合](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="d458c-124">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="d458c-125">範例</span><span class="sxs-lookup"><span data-stu-id="d458c-125">Example</span></span>

<span data-ttu-id="d458c-126">這個範例會顯示定義四個 .NET 類型的 @no__t 0 元素。</span><span class="sxs-lookup"><span data-stu-id="d458c-126">This example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d458c-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d458c-127">See Also</span></span>

[<span data-ttu-id="d458c-128">定義物件的集合</span><span class="sxs-lookup"><span data-stu-id="d458c-128">Defining Sets of Objects</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="d458c-129">SelectionSet 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d458c-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="d458c-130">類型的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d458c-130">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)

[<span data-ttu-id="d458c-131">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="d458c-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
