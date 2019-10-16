---
title: ViewSelectedBy 的 SelectionSetName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ab0f033-df09-4435-a8bd-76ec2d01f13b
caps.latest.revision: 13
ms.openlocfilehash: d1de2b30860bac80bf17508f40eec33c2794c4b2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368257"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a><span data-ttu-id="b9e83-102">ViewSelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b9e83-102">SelectionSetName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="b9e83-103">指定由視圖顯示的一組 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="b9e83-103">Specifies a set of .NET objects that are displayed by the view.</span></span>

<span data-ttu-id="b9e83-104">ViewSelectedBy （格式）的設定元素（格式） ViewDefinitions 元素（格式） ViewSelectedBy 元素（格式） SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="b9e83-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) SelectionSetName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b9e83-105">語法</span><span class="sxs-lookup"><span data-stu-id="b9e83-105">Syntax</span></span>

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b9e83-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="b9e83-106">Attributes and Elements</span></span>

<span data-ttu-id="b9e83-107">下列各節說明屬性、子專案，以及 `SelectionSetName` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="b9e83-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b9e83-108">屬性</span><span class="sxs-lookup"><span data-stu-id="b9e83-108">Attributes</span></span>

<span data-ttu-id="b9e83-109">無。</span><span class="sxs-lookup"><span data-stu-id="b9e83-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b9e83-110">子元素</span><span class="sxs-lookup"><span data-stu-id="b9e83-110">Child Elements</span></span>

<span data-ttu-id="b9e83-111">無。</span><span class="sxs-lookup"><span data-stu-id="b9e83-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b9e83-112">父元素</span><span class="sxs-lookup"><span data-stu-id="b9e83-112">Parent Elements</span></span>

|<span data-ttu-id="b9e83-113">元素</span><span class="sxs-lookup"><span data-stu-id="b9e83-113">Element</span></span>|<span data-ttu-id="b9e83-114">描述</span><span class="sxs-lookup"><span data-stu-id="b9e83-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b9e83-115">ViewSelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="b9e83-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="b9e83-116">定義視圖所顯示的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="b9e83-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b9e83-117">文字值</span><span class="sxs-lookup"><span data-stu-id="b9e83-117">Text Value</span></span>

<span data-ttu-id="b9e83-118">指定選取集的 `Name` 元素所定義的選取範圍名稱。</span><span class="sxs-lookup"><span data-stu-id="b9e83-118">Specify the name of the selection set that is defined by the `Name` element for the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="b9e83-119">備註</span><span class="sxs-lookup"><span data-stu-id="b9e83-119">Remarks</span></span>

<span data-ttu-id="b9e83-120">當您有一組想要使用單一名稱來參考的相關物件（例如透過繼承相關的一組物件）時，您可以使用 [選擇集]。</span><span class="sxs-lookup"><span data-stu-id="b9e83-120">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="b9e83-121">如需定義和參考選取集的詳細資訊，請參閱[定義物件的集合](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="b9e83-121">For more information about defining and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="b9e83-122">範例</span><span class="sxs-lookup"><span data-stu-id="b9e83-122">Example</span></span>

<span data-ttu-id="b9e83-123">下列範例顯示如何指定清單視圖的選擇集。</span><span class="sxs-lookup"><span data-stu-id="b9e83-123">The following example shows how to specify a selection set for a list view.</span></span> <span data-ttu-id="b9e83-124">資料表、寬型和自訂視圖會使用相同的架構。</span><span class="sxs-lookup"><span data-stu-id="b9e83-124">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="b9e83-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9e83-125">See Also</span></span>

[<span data-ttu-id="b9e83-126">定義選取範圍集合</span><span class="sxs-lookup"><span data-stu-id="b9e83-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="b9e83-127">ViewSelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="b9e83-127">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="b9e83-128">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="b9e83-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
