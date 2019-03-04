---
title: SelectionSet 項目 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 848e7acd-d578-4fd1-a575-c0c3b9b5e68a
caps.latest.revision: 17
ms.openlocfilehash: c809aa6c3a40d16cfd2fd99065a846d265ec0f61
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861154"
---
# <a name="selectionset-element-format"></a><span data-ttu-id="ecf47-102">SelectionSet 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ecf47-102">SelectionSet Element (Format)</span></span>

<span data-ttu-id="ecf47-103">定義一組.NET 物件可以參考的集合的名稱。</span><span class="sxs-lookup"><span data-stu-id="ecf47-103">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>

<span data-ttu-id="ecf47-104">組態項目 （格式） SelectionSets 項目 （格式） SelectionSet 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="ecf47-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ecf47-105">語法</span><span class="sxs-lookup"><span data-stu-id="ecf47-105">Syntax</span></span>

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ecf47-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="ecf47-106">Attributes and Elements</span></span>

<span data-ttu-id="ecf47-107">下列各節說明屬性、 子項目和父項目`SelectionSet`項目。</span><span class="sxs-lookup"><span data-stu-id="ecf47-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSet` element.</span></span> <span data-ttu-id="ecf47-108">每個選取項目集必須具有名稱，而且必須指定.NET 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="ecf47-108">Each selection set must have a name, and it must specify the .NET objects of the set.</span></span>

### <a name="attributes"></a><span data-ttu-id="ecf47-109">屬性</span><span class="sxs-lookup"><span data-stu-id="ecf47-109">Attributes</span></span>

<span data-ttu-id="ecf47-110">無。</span><span class="sxs-lookup"><span data-stu-id="ecf47-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ecf47-111">子元素</span><span class="sxs-lookup"><span data-stu-id="ecf47-111">Child Elements</span></span>

|<span data-ttu-id="ecf47-112">元素</span><span class="sxs-lookup"><span data-stu-id="ecf47-112">Element</span></span>|<span data-ttu-id="ecf47-113">描述</span><span class="sxs-lookup"><span data-stu-id="ecf47-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ecf47-114">SelectionSet （格式） 的 name 元素</span><span class="sxs-lookup"><span data-stu-id="ecf47-114">Name Element for SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)|<span data-ttu-id="ecf47-115">必要項目。</span><span class="sxs-lookup"><span data-stu-id="ecf47-115">Required element.</span></span><br /><br /> <span data-ttu-id="ecf47-116">指定用來參考選取項目集的名稱。</span><span class="sxs-lookup"><span data-stu-id="ecf47-116">Specifies the name used to reference the selection set.</span></span>|
|[<span data-ttu-id="ecf47-117">類型項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="ecf47-117">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="ecf47-118">必要項目。</span><span class="sxs-lookup"><span data-stu-id="ecf47-118">Required element.</span></span><br /><br /> <span data-ttu-id="ecf47-119">定義選取範圍中設定的.NET 物件。</span><span class="sxs-lookup"><span data-stu-id="ecf47-119">Defines the .NET objects that are in the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ecf47-120">父元素</span><span class="sxs-lookup"><span data-stu-id="ecf47-120">Parent Elements</span></span>

|<span data-ttu-id="ecf47-121">元素</span><span class="sxs-lookup"><span data-stu-id="ecf47-121">Element</span></span>|<span data-ttu-id="ecf47-122">描述</span><span class="sxs-lookup"><span data-stu-id="ecf47-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ecf47-123">SelectionSets 項目格式</span><span class="sxs-lookup"><span data-stu-id="ecf47-123">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="ecf47-124">定義通用的集合，可供所有檢視的格式化檔案的.NET 物件。</span><span class="sxs-lookup"><span data-stu-id="ecf47-124">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ecf47-125">備註</span><span class="sxs-lookup"><span data-stu-id="ecf47-125">Remarks</span></span>

<span data-ttu-id="ecf47-126">當您有一組您想要使用單一的名稱，例如一組透過繼承相關聯的物件參考的相關物件時，您可以使用選取項目集。</span><span class="sxs-lookup"><span data-stu-id="ecf47-126">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="ecf47-127">在定義您的檢視時，您可以指定一組物件使用的設定而非列出每個檢視中的所有物件的選取範圍的名稱。</span><span class="sxs-lookup"><span data-stu-id="ecf47-127">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="ecf47-128">定義格式化檔案的檢視或檢視的定義時常見的選取項目集指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="ecf47-128">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="ecf47-129">在這些情況下，`SelectionSetName`子元素`ViewSelectedBy`和`EntrySelectedBy`元素指定要使用的集合。</span><span class="sxs-lookup"><span data-stu-id="ecf47-129">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="ecf47-130">如需選取項目集的詳細資訊，請參閱[定義設定的物件](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="ecf47-130">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="ecf47-131">範例</span><span class="sxs-lookup"><span data-stu-id="ecf47-131">Example</span></span>

<span data-ttu-id="ecf47-132">下列範例所示`SelectionSet`項目，定義四個.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="ecf47-132">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ecf47-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ecf47-133">See Also</span></span>

[<span data-ttu-id="ecf47-134">定義選取範圍</span><span class="sxs-lookup"><span data-stu-id="ecf47-134">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="ecf47-135">Name 元素 SelectionSet （格式）</span><span class="sxs-lookup"><span data-stu-id="ecf47-135">Name Element of SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="ecf47-136">SelectionSets 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="ecf47-136">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="ecf47-137">類型項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="ecf47-137">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="ecf47-138">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="ecf47-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
