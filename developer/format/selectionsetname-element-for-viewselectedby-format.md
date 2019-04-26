---
title: SelectionSetName ViewSelectedBy （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ab0f033-df09-4435-a8bd-76ec2d01f13b
caps.latest.revision: 13
ms.openlocfilehash: d1de2b30860bac80bf17508f40eec33c2794c4b2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076220"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a><span data-ttu-id="ce35f-102">ViewSelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ce35f-102">SelectionSetName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="ce35f-103">指定一份檢視所顯示的.NET 物件。</span><span class="sxs-lookup"><span data-stu-id="ce35f-103">Specifies a set of .NET objects that are displayed by the view.</span></span>

<span data-ttu-id="ce35f-104">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） ViewSelectedBy 項目 （格式） SelectionSetName 項目 ViewSelectedBy （格式）</span><span class="sxs-lookup"><span data-stu-id="ce35f-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) SelectionSetName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ce35f-105">語法</span><span class="sxs-lookup"><span data-stu-id="ce35f-105">Syntax</span></span>

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ce35f-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ce35f-106">Attributes and Elements</span></span>

<span data-ttu-id="ce35f-107">下列各節說明屬性、 子項目和父項目`SelectionSetName`項目。</span><span class="sxs-lookup"><span data-stu-id="ce35f-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ce35f-108">屬性</span><span class="sxs-lookup"><span data-stu-id="ce35f-108">Attributes</span></span>

<span data-ttu-id="ce35f-109">無。</span><span class="sxs-lookup"><span data-stu-id="ce35f-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ce35f-110">子元素</span><span class="sxs-lookup"><span data-stu-id="ce35f-110">Child Elements</span></span>

<span data-ttu-id="ce35f-111">無。</span><span class="sxs-lookup"><span data-stu-id="ce35f-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ce35f-112">父項目</span><span class="sxs-lookup"><span data-stu-id="ce35f-112">Parent Elements</span></span>

|<span data-ttu-id="ce35f-113">項目</span><span class="sxs-lookup"><span data-stu-id="ce35f-113">Element</span></span>|<span data-ttu-id="ce35f-114">描述</span><span class="sxs-lookup"><span data-stu-id="ce35f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ce35f-115">ViewSelectedBy 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="ce35f-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="ce35f-116">定義檢視所顯示的.NET 物件。</span><span class="sxs-lookup"><span data-stu-id="ce35f-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ce35f-117">文字值</span><span class="sxs-lookup"><span data-stu-id="ce35f-117">Text Value</span></span>

<span data-ttu-id="ce35f-118">指定選取項目集所定義的名稱`Name`選取項目集的項目。</span><span class="sxs-lookup"><span data-stu-id="ce35f-118">Specify the name of the selection set that is defined by the `Name` element for the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="ce35f-119">備註</span><span class="sxs-lookup"><span data-stu-id="ce35f-119">Remarks</span></span>

<span data-ttu-id="ce35f-120">當您有一組您想要使用單一的名稱，例如一組透過繼承相關聯的物件參考的相關物件時，您可以使用選取項目集。</span><span class="sxs-lookup"><span data-stu-id="ce35f-120">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="ce35f-121">如需有關定義和參考選取項目集的詳細資訊，請參閱[定義設定的物件](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="ce35f-121">For more information about defining and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="ce35f-122">範例</span><span class="sxs-lookup"><span data-stu-id="ce35f-122">Example</span></span>

<span data-ttu-id="ce35f-123">下列範例示範如何指定設定的清單檢視的選取範圍。</span><span class="sxs-lookup"><span data-stu-id="ce35f-123">The following example shows how to specify a selection set for a list view.</span></span> <span data-ttu-id="ce35f-124">相同的結構描述用於資料表，，和自訂檢視。</span><span class="sxs-lookup"><span data-stu-id="ce35f-124">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="ce35f-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce35f-125">See Also</span></span>

[<span data-ttu-id="ce35f-126">定義選取範圍</span><span class="sxs-lookup"><span data-stu-id="ce35f-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="ce35f-127">ViewSelectedBy 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="ce35f-127">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="ce35f-128">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="ce35f-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
