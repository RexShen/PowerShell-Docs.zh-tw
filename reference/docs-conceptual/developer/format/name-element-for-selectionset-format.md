---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSet 的名稱元素 (格式)
description: SelectionSet 的名稱元素 (格式)
ms.openlocfilehash: 98c13be6ea352055231fbdb3a60f0eb508f661b8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666448"
---
# <a name="name-element-for-selectionset-format"></a><span data-ttu-id="7f437-103">SelectionSet 的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7f437-103">Name Element for SelectionSet (Format)</span></span>

<span data-ttu-id="7f437-104">指定用來參考選取集的名稱。</span><span class="sxs-lookup"><span data-stu-id="7f437-104">Specifies the name used to reference the selection set.</span></span>

<span data-ttu-id="7f437-105">設定元素 (格式) SelectionSets 元素 (格式) SelectionSet 元素 (格式) SelectionSet (格式) 名稱元素</span><span class="sxs-lookup"><span data-stu-id="7f437-105">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Name Element of SelectionSet (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7f437-106">語法</span><span class="sxs-lookup"><span data-stu-id="7f437-106">Syntax</span></span>

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7f437-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7f437-107">Attributes and Elements</span></span>

<span data-ttu-id="7f437-108">下列各節描述專案的屬性、子項目和父元素 `Name` 。</span><span class="sxs-lookup"><span data-stu-id="7f437-108">The following sections describe the attributes, child elements, and parent element of the `Name` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7f437-109">屬性</span><span class="sxs-lookup"><span data-stu-id="7f437-109">Attributes</span></span>

<span data-ttu-id="7f437-110">無。</span><span class="sxs-lookup"><span data-stu-id="7f437-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7f437-111">子元素</span><span class="sxs-lookup"><span data-stu-id="7f437-111">Child Elements</span></span>

<span data-ttu-id="7f437-112">無。</span><span class="sxs-lookup"><span data-stu-id="7f437-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7f437-113">父項目</span><span class="sxs-lookup"><span data-stu-id="7f437-113">Parent Elements</span></span>

|<span data-ttu-id="7f437-114">元素</span><span class="sxs-lookup"><span data-stu-id="7f437-114">Element</span></span>|<span data-ttu-id="7f437-115">描述</span><span class="sxs-lookup"><span data-stu-id="7f437-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7f437-116">SelectionSet 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7f437-116">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="7f437-117">定義可由集合名稱參考的一組 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="7f437-117">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7f437-118">文字值</span><span class="sxs-lookup"><span data-stu-id="7f437-118">Text Value</span></span>

<span data-ttu-id="7f437-119">指定參考選取集的名稱。</span><span class="sxs-lookup"><span data-stu-id="7f437-119">Specify the name to reference the selection set.</span></span> <span data-ttu-id="7f437-120">可以使用的字元沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="7f437-120">There are no restrictions as to what characters can be used.</span></span>

## <a name="remarks"></a><span data-ttu-id="7f437-121">備註</span><span class="sxs-lookup"><span data-stu-id="7f437-121">Remarks</span></span>

<span data-ttu-id="7f437-122">此處指定的名稱用於 `SelectionSetName` 元素中。</span><span class="sxs-lookup"><span data-stu-id="7f437-122">The name specified here is used in the `SelectionSetName` element.</span></span> <span data-ttu-id="7f437-123">可供視圖使用的選取範圍， (views 的 view 定義可以有多個定義) 或指定選取條件。</span><span class="sxs-lookup"><span data-stu-id="7f437-123">The selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span> <span data-ttu-id="7f437-124">如需選取集的詳細資訊，請參閱 [定義物件集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="7f437-124">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="7f437-125">範例</span><span class="sxs-lookup"><span data-stu-id="7f437-125">Example</span></span>

<span data-ttu-id="7f437-126">此範例顯示 `SelectionSet` 定義四個 .net 類型的元素。</span><span class="sxs-lookup"><span data-stu-id="7f437-126">This example shows a `SelectionSet` element that defines four .NET types.</span></span> <span data-ttu-id="7f437-127">選擇組的名稱為 "FileSystemTypes"。</span><span class="sxs-lookup"><span data-stu-id="7f437-127">The name of the selection set is "FileSystemTypes".</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7f437-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f437-128">See Also</span></span>

[<span data-ttu-id="7f437-129">定義選取範圍集合</span><span class="sxs-lookup"><span data-stu-id="7f437-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="7f437-130">SelectionSet 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7f437-130">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="7f437-131">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="7f437-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
