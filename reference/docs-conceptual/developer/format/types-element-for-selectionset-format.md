---
title: SelectionSet (格式) 的 Types 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 9978daefb3e97ab131774ca4dff633dde6b4dfbf
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772513"
---
# <a name="types-element-for-selectionset-format"></a><span data-ttu-id="70628-102">SelectionSet 的類型元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="70628-102">Types Element for SelectionSet (Format)</span></span>

<span data-ttu-id="70628-103">定義選取集中的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="70628-103">Defines the .NET objects that are in the selection set.</span></span>

<span data-ttu-id="70628-104">Configuration 元素 (格式) SelectionSets 元素 (格式) SelectionSet 元素 (格式) 類型元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="70628-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="70628-105">語法</span><span class="sxs-lookup"><span data-stu-id="70628-105">Syntax</span></span>

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="70628-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="70628-106">Attributes and Elements</span></span>

<span data-ttu-id="70628-107">下列各節說明屬性、子專案和元素的父元素 `Types` 。</span><span class="sxs-lookup"><span data-stu-id="70628-107">The following sections describe the attributes, child elements, and the parent element of the `Types` element.</span></span> <span data-ttu-id="70628-108">必須至少有一個子專案，但可以加入的子專案數目沒有上限。</span><span class="sxs-lookup"><span data-stu-id="70628-108">There must be at least one child element, but there is no maximum limit to the number of child elements that can be added.</span></span>

### <a name="attributes"></a><span data-ttu-id="70628-109">屬性</span><span class="sxs-lookup"><span data-stu-id="70628-109">Attributes</span></span>

<span data-ttu-id="70628-110">無。</span><span class="sxs-lookup"><span data-stu-id="70628-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="70628-111">子元素</span><span class="sxs-lookup"><span data-stu-id="70628-111">Child Elements</span></span>

|<span data-ttu-id="70628-112">元素</span><span class="sxs-lookup"><span data-stu-id="70628-112">Element</span></span>|<span data-ttu-id="70628-113">描述</span><span class="sxs-lookup"><span data-stu-id="70628-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="70628-114">類型的 TypeName 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="70628-114">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)|<span data-ttu-id="70628-115">必要元素。</span><span class="sxs-lookup"><span data-stu-id="70628-115">Required element.</span></span><br /><br /> <span data-ttu-id="70628-116">指定屬於選取集的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="70628-116">Specifies the .NET object that belongs to the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="70628-117">父項目</span><span class="sxs-lookup"><span data-stu-id="70628-117">Parent Elements</span></span>

|<span data-ttu-id="70628-118">元素</span><span class="sxs-lookup"><span data-stu-id="70628-118">Element</span></span>|<span data-ttu-id="70628-119">描述</span><span class="sxs-lookup"><span data-stu-id="70628-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="70628-120">SelectionSet 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="70628-120">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="70628-121">定義一組可由集合名稱參考的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="70628-121">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="remarks"></a><span data-ttu-id="70628-122">備註</span><span class="sxs-lookup"><span data-stu-id="70628-122">Remarks</span></span>

<span data-ttu-id="70628-123">這個專案所定義的物件組成一個可供視圖使用的選擇集，而 view 的定義 (views 可以) 多個定義，或指定選取條件。</span><span class="sxs-lookup"><span data-stu-id="70628-123">The objects defined by this element make up a selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span>  <span data-ttu-id="70628-124">如需選取集的詳細資訊，請參閱[定義物件的集合](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="70628-124">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="70628-125">範例</span><span class="sxs-lookup"><span data-stu-id="70628-125">Example</span></span>

<span data-ttu-id="70628-126">這個範例會顯示 `SelectionSet` 定義四個 .net 類型的元素。</span><span class="sxs-lookup"><span data-stu-id="70628-126">This example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="70628-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70628-127">See Also</span></span>

[<span data-ttu-id="70628-128">定義物件的集合</span><span class="sxs-lookup"><span data-stu-id="70628-128">Defining Sets of Objects</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="70628-129">SelectionSet 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="70628-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="70628-130">類型的 TypeName 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="70628-130">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)

[<span data-ttu-id="70628-131">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="70628-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
