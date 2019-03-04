---
title: 項目名稱 （格式） SelectionSet |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914917f7-0efc-4d1f-88bd-de714bedd98f
caps.latest.revision: 15
ms.openlocfilehash: 29dbdbd335511e4ca2706a625541554825838f23
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858164"
---
# <a name="name-element-for-selectionset-format"></a><span data-ttu-id="239e0-102">SelectionSet 的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="239e0-102">Name Element for SelectionSet (Format)</span></span>

<span data-ttu-id="239e0-103">指定用來參考選取項目集的名稱。</span><span class="sxs-lookup"><span data-stu-id="239e0-103">Specifies the name used to reference the selection set.</span></span>

<span data-ttu-id="239e0-104">組態項目 （格式） SelectionSets 項目 （格式） SelectionSet 項目 （格式） 名稱項目 SelectionSet （格式）</span><span class="sxs-lookup"><span data-stu-id="239e0-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Name Element of SelectionSet (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="239e0-105">語法</span><span class="sxs-lookup"><span data-stu-id="239e0-105">Syntax</span></span>

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="239e0-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="239e0-106">Attributes and Elements</span></span>

<span data-ttu-id="239e0-107">下列各節說明屬性、 子項目和父項目`Name`項目。</span><span class="sxs-lookup"><span data-stu-id="239e0-107">The following sections describe the attributes, child elements, and parent element of the `Name` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="239e0-108">屬性</span><span class="sxs-lookup"><span data-stu-id="239e0-108">Attributes</span></span>

<span data-ttu-id="239e0-109">無。</span><span class="sxs-lookup"><span data-stu-id="239e0-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="239e0-110">子元素</span><span class="sxs-lookup"><span data-stu-id="239e0-110">Child Elements</span></span>

<span data-ttu-id="239e0-111">無。</span><span class="sxs-lookup"><span data-stu-id="239e0-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="239e0-112">父元素</span><span class="sxs-lookup"><span data-stu-id="239e0-112">Parent Elements</span></span>

|<span data-ttu-id="239e0-113">元素</span><span class="sxs-lookup"><span data-stu-id="239e0-113">Element</span></span>|<span data-ttu-id="239e0-114">描述</span><span class="sxs-lookup"><span data-stu-id="239e0-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="239e0-115">SelectionSet 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="239e0-115">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="239e0-116">定義一組.NET 物件，可以參考集的名稱。</span><span class="sxs-lookup"><span data-stu-id="239e0-116">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="239e0-117">文字值</span><span class="sxs-lookup"><span data-stu-id="239e0-117">Text Value</span></span>

<span data-ttu-id="239e0-118">指定要參考的選取項目集的名稱。</span><span class="sxs-lookup"><span data-stu-id="239e0-118">Specify the name to reference the selection set.</span></span> <span data-ttu-id="239e0-119">有可以使用哪些字元沒有限制。</span><span class="sxs-lookup"><span data-stu-id="239e0-119">There are no restrictions as to what characters can be used.</span></span>

## <a name="remarks"></a><span data-ttu-id="239e0-120">備註</span><span class="sxs-lookup"><span data-stu-id="239e0-120">Remarks</span></span>

<span data-ttu-id="239e0-121">在這裡指定的名稱會在`SelectionSetName`項目。</span><span class="sxs-lookup"><span data-stu-id="239e0-121">The name specified here is used in the `SelectionSetName` element.</span></span> <span data-ttu-id="239e0-122">可以檢視的定義所使用的檢視中，選取項目集 （檢視可以有多個定義），或指定選取條件時。</span><span class="sxs-lookup"><span data-stu-id="239e0-122">The selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span> <span data-ttu-id="239e0-123">如需選取項目集的詳細資訊，請參閱[定義設定的物件](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="239e0-123">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="239e0-124">範例</span><span class="sxs-lookup"><span data-stu-id="239e0-124">Example</span></span>

<span data-ttu-id="239e0-125">此範例示範`SelectionSet`項目，定義四個.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="239e0-125">This example shows a `SelectionSet` element that defines four .NET types.</span></span> <span data-ttu-id="239e0-126">選取項目集的名稱是"FileSystemTypes 」。</span><span class="sxs-lookup"><span data-stu-id="239e0-126">The name of the selection set is "FileSystemTypes".</span></span>

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

## <a name="see-also"></a><span data-ttu-id="239e0-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="239e0-127">See Also</span></span>

[<span data-ttu-id="239e0-128">定義選取範圍</span><span class="sxs-lookup"><span data-stu-id="239e0-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="239e0-129">SelectionSet 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="239e0-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="239e0-130">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="239e0-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
