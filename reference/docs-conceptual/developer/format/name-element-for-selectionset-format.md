---
title: SelectionSet (格式) 的 Name 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1fc33eeb87a6912ed6793629ab1969cd65b5f0c5
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773295"
---
# <a name="name-element-for-selectionset-format"></a><span data-ttu-id="455bf-102">SelectionSet 的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="455bf-102">Name Element for SelectionSet (Format)</span></span>

<span data-ttu-id="455bf-103">指定用來參考選取集的名稱。</span><span class="sxs-lookup"><span data-stu-id="455bf-103">Specifies the name used to reference the selection set.</span></span>

<span data-ttu-id="455bf-104">Configuration 元素 (格式) SelectionSets 元素 (格式) SelectionSet 元素 (格式) SelectionSet 的 Name 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="455bf-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Name Element of SelectionSet (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="455bf-105">語法</span><span class="sxs-lookup"><span data-stu-id="455bf-105">Syntax</span></span>

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="455bf-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="455bf-106">Attributes and Elements</span></span>

<span data-ttu-id="455bf-107">下列各節描述元素的屬性、子專案和父項目 `Name` 。</span><span class="sxs-lookup"><span data-stu-id="455bf-107">The following sections describe the attributes, child elements, and parent element of the `Name` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="455bf-108">屬性</span><span class="sxs-lookup"><span data-stu-id="455bf-108">Attributes</span></span>

<span data-ttu-id="455bf-109">無。</span><span class="sxs-lookup"><span data-stu-id="455bf-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="455bf-110">子元素</span><span class="sxs-lookup"><span data-stu-id="455bf-110">Child Elements</span></span>

<span data-ttu-id="455bf-111">無。</span><span class="sxs-lookup"><span data-stu-id="455bf-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="455bf-112">父項目</span><span class="sxs-lookup"><span data-stu-id="455bf-112">Parent Elements</span></span>

|<span data-ttu-id="455bf-113">元素</span><span class="sxs-lookup"><span data-stu-id="455bf-113">Element</span></span>|<span data-ttu-id="455bf-114">描述</span><span class="sxs-lookup"><span data-stu-id="455bf-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="455bf-115">SelectionSet 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="455bf-115">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="455bf-116">定義一組可由集合名稱參考的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="455bf-116">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="455bf-117">文字值</span><span class="sxs-lookup"><span data-stu-id="455bf-117">Text Value</span></span>

<span data-ttu-id="455bf-118">指定要參考選取集的名稱。</span><span class="sxs-lookup"><span data-stu-id="455bf-118">Specify the name to reference the selection set.</span></span> <span data-ttu-id="455bf-119">對於可使用的字元沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="455bf-119">There are no restrictions as to what characters can be used.</span></span>

## <a name="remarks"></a><span data-ttu-id="455bf-120">備註</span><span class="sxs-lookup"><span data-stu-id="455bf-120">Remarks</span></span>

<span data-ttu-id="455bf-121">此處指定的名稱用於 `SelectionSetName` 元素中。</span><span class="sxs-lookup"><span data-stu-id="455bf-121">The name specified here is used in the `SelectionSetName` element.</span></span> <span data-ttu-id="455bf-122">View 所能使用的選取範圍 (views 的定義可以) 多個定義，或指定選取條件時。</span><span class="sxs-lookup"><span data-stu-id="455bf-122">The selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span> <span data-ttu-id="455bf-123">如需選取集的詳細資訊，請參閱[定義物件的集合](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="455bf-123">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="455bf-124">範例</span><span class="sxs-lookup"><span data-stu-id="455bf-124">Example</span></span>

<span data-ttu-id="455bf-125">這個範例會顯示 `SelectionSet` 定義四個 .net 類型的元素。</span><span class="sxs-lookup"><span data-stu-id="455bf-125">This example shows a `SelectionSet` element that defines four .NET types.</span></span> <span data-ttu-id="455bf-126">選取集的名稱是 "FileSystemTypes"。</span><span class="sxs-lookup"><span data-stu-id="455bf-126">The name of the selection set is "FileSystemTypes".</span></span>

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

## <a name="see-also"></a><span data-ttu-id="455bf-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="455bf-127">See Also</span></span>

[<span data-ttu-id="455bf-128">定義選取範圍集合</span><span class="sxs-lookup"><span data-stu-id="455bf-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="455bf-129">SelectionSet 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="455bf-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="455bf-130">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="455bf-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
