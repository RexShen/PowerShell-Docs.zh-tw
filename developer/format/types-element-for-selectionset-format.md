---
title: 項目類型 （格式） SelectionSet |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4606fec0-ff31-4d36-af68-227405335ec3
caps.latest.revision: 15
ms.openlocfilehash: 0427367efa2c8a7e352d718706d1341a0c8e3621
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862374"
---
# <a name="types-element-for-selectionset-format"></a><span data-ttu-id="6a83a-102">SelectionSet 的類型元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="6a83a-102">Types Element for SelectionSet (Format)</span></span>

<span data-ttu-id="6a83a-103">定義選取範圍中設定的.NET 物件。</span><span class="sxs-lookup"><span data-stu-id="6a83a-103">Defines the .NET objects that are in the selection set.</span></span>

<span data-ttu-id="6a83a-104">組態項目 （格式） SelectionSets 項目 （格式） SelectionSet 項目 （格式） 型別項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="6a83a-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6a83a-105">語法</span><span class="sxs-lookup"><span data-stu-id="6a83a-105">Syntax</span></span>

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="6a83a-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="6a83a-106">Attributes and Elements</span></span>

<span data-ttu-id="6a83a-107">下列各節說明屬性、 子項目和父項目`Types`項目。</span><span class="sxs-lookup"><span data-stu-id="6a83a-107">The following sections describe the attributes, child elements, and the parent element of the `Types` element.</span></span> <span data-ttu-id="6a83a-108">必須有至少一個子元素，但沒有可加入的子項目數目沒有上限限制。</span><span class="sxs-lookup"><span data-stu-id="6a83a-108">There must be at least one child element, but there is no maximum limit to the number of child elements that can be added.</span></span>

### <a name="attributes"></a><span data-ttu-id="6a83a-109">屬性</span><span class="sxs-lookup"><span data-stu-id="6a83a-109">Attributes</span></span>

<span data-ttu-id="6a83a-110">無。</span><span class="sxs-lookup"><span data-stu-id="6a83a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6a83a-111">子元素</span><span class="sxs-lookup"><span data-stu-id="6a83a-111">Child Elements</span></span>

|<span data-ttu-id="6a83a-112">元素</span><span class="sxs-lookup"><span data-stu-id="6a83a-112">Element</span></span>|<span data-ttu-id="6a83a-113">描述</span><span class="sxs-lookup"><span data-stu-id="6a83a-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6a83a-114">TypeName 項目類型 （格式）</span><span class="sxs-lookup"><span data-stu-id="6a83a-114">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)|<span data-ttu-id="6a83a-115">必要項目。</span><span class="sxs-lookup"><span data-stu-id="6a83a-115">Required element.</span></span><br /><br /> <span data-ttu-id="6a83a-116">指定屬於選取項目集的.NET 物件。</span><span class="sxs-lookup"><span data-stu-id="6a83a-116">Specifies the .NET object that belongs to the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6a83a-117">父元素</span><span class="sxs-lookup"><span data-stu-id="6a83a-117">Parent Elements</span></span>

|<span data-ttu-id="6a83a-118">元素</span><span class="sxs-lookup"><span data-stu-id="6a83a-118">Element</span></span>|<span data-ttu-id="6a83a-119">描述</span><span class="sxs-lookup"><span data-stu-id="6a83a-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6a83a-120">SelectionSet 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="6a83a-120">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="6a83a-121">定義一組.NET 物件可以參考的集合的名稱。</span><span class="sxs-lookup"><span data-stu-id="6a83a-121">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6a83a-122">備註</span><span class="sxs-lookup"><span data-stu-id="6a83a-122">Remarks</span></span>

<span data-ttu-id="6a83a-123">這個項目所定義的物件會構成可以檢視的定義所使用的檢視中，選取項目集 （檢視可以有多個定義），或指定選取條件時。</span><span class="sxs-lookup"><span data-stu-id="6a83a-123">The objects defined by this element make up a selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span>  <span data-ttu-id="6a83a-124">如需選取項目集的詳細資訊，請參閱[定義設定的物件](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="6a83a-124">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="6a83a-125">範例</span><span class="sxs-lookup"><span data-stu-id="6a83a-125">Example</span></span>

<span data-ttu-id="6a83a-126">此範例示範`SelectionSet`項目，定義四個.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="6a83a-126">This example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6a83a-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a83a-127">See Also</span></span>

[<span data-ttu-id="6a83a-128">定義物件的集合</span><span class="sxs-lookup"><span data-stu-id="6a83a-128">Defining Sets of Objects</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="6a83a-129">SelectionSet 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="6a83a-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="6a83a-130">TypeName 項目類型 （格式）</span><span class="sxs-lookup"><span data-stu-id="6a83a-130">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)

[<span data-ttu-id="6a83a-131">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="6a83a-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
