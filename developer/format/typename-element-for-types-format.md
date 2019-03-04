---
title: 類型名稱的項目類型 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0595b99e-b438-4240-b47b-555cf0316f33
caps.latest.revision: 15
ms.openlocfilehash: 4f463ac6b70a00f628c5b93b112c5fa510ff3bfb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853574"
---
# <a name="typename-element-for-types-format"></a><span data-ttu-id="7ffda-102">類型的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7ffda-102">TypeName Element for Types (Format)</span></span>

<span data-ttu-id="7ffda-103">指定屬於選取項目集之物件的.NET 類型。</span><span class="sxs-lookup"><span data-stu-id="7ffda-103">Specifies the .NET type of an object that belongs to the selection set.</span></span>

<span data-ttu-id="7ffda-104">組態項目 （格式） SelectionSets 項目 （格式） SelectionSet 項目 （格式） 類型的類型 （格式） 的項目 （格式） 類型名稱項目</span><span class="sxs-lookup"><span data-stu-id="7ffda-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format) TypeName Element of Types (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7ffda-105">語法</span><span class="sxs-lookup"><span data-stu-id="7ffda-105">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7ffda-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="7ffda-106">Attributes and Elements</span></span>

<span data-ttu-id="7ffda-107">下列各節說明屬性、 子項目和父項目`TypeName`項目。</span><span class="sxs-lookup"><span data-stu-id="7ffda-107">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span> <span data-ttu-id="7ffda-108">至少一個`TypeName`元素必須包含在選取項目集。</span><span class="sxs-lookup"><span data-stu-id="7ffda-108">At least one `TypeName` element must be included in the selection set.</span></span>

### <a name="attributes"></a><span data-ttu-id="7ffda-109">屬性</span><span class="sxs-lookup"><span data-stu-id="7ffda-109">Attributes</span></span>

<span data-ttu-id="7ffda-110">無。</span><span class="sxs-lookup"><span data-stu-id="7ffda-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7ffda-111">子元素</span><span class="sxs-lookup"><span data-stu-id="7ffda-111">Child Elements</span></span>

<span data-ttu-id="7ffda-112">無。</span><span class="sxs-lookup"><span data-stu-id="7ffda-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7ffda-113">父元素</span><span class="sxs-lookup"><span data-stu-id="7ffda-113">Parent Elements</span></span>

|<span data-ttu-id="7ffda-114">元素</span><span class="sxs-lookup"><span data-stu-id="7ffda-114">Element</span></span>|<span data-ttu-id="7ffda-115">描述</span><span class="sxs-lookup"><span data-stu-id="7ffda-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7ffda-116">類型項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="7ffda-116">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="7ffda-117">定義選取範圍中設定的.NET 物件。</span><span class="sxs-lookup"><span data-stu-id="7ffda-117">Defines the .NET objects that are in the selection set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7ffda-118">文字值</span><span class="sxs-lookup"><span data-stu-id="7ffda-118">Text Value</span></span>

<span data-ttu-id="7ffda-119">指定的.NET 類型的完整的名稱。</span><span class="sxs-lookup"><span data-stu-id="7ffda-119">Specify the fully qualified name for the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="7ffda-120">備註</span><span class="sxs-lookup"><span data-stu-id="7ffda-120">Remarks</span></span>

<span data-ttu-id="7ffda-121">當您有一組您想要使用單一的名稱，例如一組透過繼承相關聯的物件參考的相關物件時，您可以使用選取項目集。</span><span class="sxs-lookup"><span data-stu-id="7ffda-121">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="7ffda-122">在定義您的檢視時，您可以指定一組物件使用的設定而非列出每個檢視中的所有物件的選取範圍的名稱。</span><span class="sxs-lookup"><span data-stu-id="7ffda-122">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="7ffda-123">常見的選取項目集指定其名稱所定義的格式化檔案的檢視時。</span><span class="sxs-lookup"><span data-stu-id="7ffda-123">Common selection sets are specified by their name when defining the views of the formatting file.</span></span> <span data-ttu-id="7ffda-124">在這些情況下，`SelectionSetName`子項目`ViewSelectedBy`檢視的項目會指定集合。</span><span class="sxs-lookup"><span data-stu-id="7ffda-124">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` element for the view specifies the set.</span></span> <span data-ttu-id="7ffda-125">不過，不同的項目 檢視也可以指定套用至該檢視的項目選取項目集。</span><span class="sxs-lookup"><span data-stu-id="7ffda-125">However, different entries of a view can also specify a selection set that applies to only that entry of the view.</span></span> <span data-ttu-id="7ffda-126">如需選取項目集的詳細資訊，請參閱[定義設定的物件](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="7ffda-126">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="7ffda-127">範例</span><span class="sxs-lookup"><span data-stu-id="7ffda-127">Example</span></span>

<span data-ttu-id="7ffda-128">下列範例所示`SelectionSet`項目，定義四個.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="7ffda-128">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7ffda-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ffda-129">See Also</span></span>

[<span data-ttu-id="7ffda-130">定義選取範圍</span><span class="sxs-lookup"><span data-stu-id="7ffda-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="7ffda-131">SelectionSet 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="7ffda-131">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="7ffda-132">SelectionSets 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="7ffda-132">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="7ffda-133">類型項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="7ffda-133">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="7ffda-134">撰寫 Windows PowDefining 組 ObjecterShell 格式檔案</span><span class="sxs-lookup"><span data-stu-id="7ffda-134">Writing a Windows PowDefining Sets of ObjecterShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
