---
title: SelectionSet 的名稱元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914917f7-0efc-4d1f-88bd-de714bedd98f
caps.latest.revision: 15
ms.openlocfilehash: 29dbdbd335511e4ca2706a625541554825838f23
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362667"
---
# <a name="name-element-for-selectionset-format"></a><span data-ttu-id="321af-102">SelectionSet 的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="321af-102">Name Element for SelectionSet (Format)</span></span>

<span data-ttu-id="321af-103">指定用來參考選取集的名稱。</span><span class="sxs-lookup"><span data-stu-id="321af-103">Specifies the name used to reference the selection set.</span></span>

<span data-ttu-id="321af-104">Configuration 元素（格式） SelectionSets 元素（格式） SelectionSet 元素（格式） SelectionSet 的名稱元素（格式）</span><span class="sxs-lookup"><span data-stu-id="321af-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Name Element of SelectionSet (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="321af-105">語法</span><span class="sxs-lookup"><span data-stu-id="321af-105">Syntax</span></span>

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="321af-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="321af-106">Attributes and Elements</span></span>

<span data-ttu-id="321af-107">下列各節說明 `Name` 元素的屬性、子專案和父元素。</span><span class="sxs-lookup"><span data-stu-id="321af-107">The following sections describe the attributes, child elements, and parent element of the `Name` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="321af-108">屬性</span><span class="sxs-lookup"><span data-stu-id="321af-108">Attributes</span></span>

<span data-ttu-id="321af-109">無。</span><span class="sxs-lookup"><span data-stu-id="321af-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="321af-110">子元素</span><span class="sxs-lookup"><span data-stu-id="321af-110">Child Elements</span></span>

<span data-ttu-id="321af-111">無。</span><span class="sxs-lookup"><span data-stu-id="321af-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="321af-112">父元素</span><span class="sxs-lookup"><span data-stu-id="321af-112">Parent Elements</span></span>

|<span data-ttu-id="321af-113">元素</span><span class="sxs-lookup"><span data-stu-id="321af-113">Element</span></span>|<span data-ttu-id="321af-114">描述</span><span class="sxs-lookup"><span data-stu-id="321af-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="321af-115">SelectionSet 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="321af-115">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="321af-116">定義一組可由集合名稱參考的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="321af-116">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="321af-117">文字值</span><span class="sxs-lookup"><span data-stu-id="321af-117">Text Value</span></span>

<span data-ttu-id="321af-118">指定要參考選取集的名稱。</span><span class="sxs-lookup"><span data-stu-id="321af-118">Specify the name to reference the selection set.</span></span> <span data-ttu-id="321af-119">對於可使用的字元沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="321af-119">There are no restrictions as to what characters can be used.</span></span>

## <a name="remarks"></a><span data-ttu-id="321af-120">備註</span><span class="sxs-lookup"><span data-stu-id="321af-120">Remarks</span></span>

<span data-ttu-id="321af-121">此處指定的名稱用於 `SelectionSetName` 元素中。</span><span class="sxs-lookup"><span data-stu-id="321af-121">The name specified here is used in the `SelectionSetName` element.</span></span> <span data-ttu-id="321af-122">可供視圖使用的選取範圍，由視圖的定義（views 可以有多個定義）或指定選取條件。</span><span class="sxs-lookup"><span data-stu-id="321af-122">The selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span> <span data-ttu-id="321af-123">如需選取集的詳細資訊，請參閱[定義物件的集合](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="321af-123">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="321af-124">範例</span><span class="sxs-lookup"><span data-stu-id="321af-124">Example</span></span>

<span data-ttu-id="321af-125">這個範例會顯示定義四個 .NET 類型的 @no__t 0 元素。</span><span class="sxs-lookup"><span data-stu-id="321af-125">This example shows a `SelectionSet` element that defines four .NET types.</span></span> <span data-ttu-id="321af-126">選取集的名稱是 "FileSystemTypes"。</span><span class="sxs-lookup"><span data-stu-id="321af-126">The name of the selection set is "FileSystemTypes".</span></span>

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

## <a name="see-also"></a><span data-ttu-id="321af-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="321af-127">See Also</span></span>

[<span data-ttu-id="321af-128">定義選取範圍集合</span><span class="sxs-lookup"><span data-stu-id="321af-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="321af-129">SelectionSet 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="321af-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="321af-130">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="321af-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
