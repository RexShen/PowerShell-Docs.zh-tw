---
ms.date: 09/13/2016
ms.topic: reference
title: ViewSelectedBy 的 SelectionSetName 元素 (格式)
description: ViewSelectedBy 的 SelectionSetName 元素 (格式)
ms.openlocfilehash: a1a1816761715a138bcb3c2bd4cb9dbbb2f9cb92
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654909"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a><span data-ttu-id="7fe5c-103">ViewSelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7fe5c-103">SelectionSetName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="7fe5c-104">指定由視圖顯示的一組 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="7fe5c-104">Specifies a set of .NET objects that are displayed by the view.</span></span>

<span data-ttu-id="7fe5c-105">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) ViewSelectedBy 元素 (格式) ViewSelectedBy (格式的 SelectionSetName 元素) </span><span class="sxs-lookup"><span data-stu-id="7fe5c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) SelectionSetName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7fe5c-106">語法</span><span class="sxs-lookup"><span data-stu-id="7fe5c-106">Syntax</span></span>

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7fe5c-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7fe5c-107">Attributes and Elements</span></span>

<span data-ttu-id="7fe5c-108">下列章節說明屬性、子專案和元素的父元素 `SelectionSetName` 。</span><span class="sxs-lookup"><span data-stu-id="7fe5c-108">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7fe5c-109">屬性</span><span class="sxs-lookup"><span data-stu-id="7fe5c-109">Attributes</span></span>

<span data-ttu-id="7fe5c-110">無。</span><span class="sxs-lookup"><span data-stu-id="7fe5c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7fe5c-111">子元素</span><span class="sxs-lookup"><span data-stu-id="7fe5c-111">Child Elements</span></span>

<span data-ttu-id="7fe5c-112">無。</span><span class="sxs-lookup"><span data-stu-id="7fe5c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7fe5c-113">父項目</span><span class="sxs-lookup"><span data-stu-id="7fe5c-113">Parent Elements</span></span>

|<span data-ttu-id="7fe5c-114">元素</span><span class="sxs-lookup"><span data-stu-id="7fe5c-114">Element</span></span>|<span data-ttu-id="7fe5c-115">描述</span><span class="sxs-lookup"><span data-stu-id="7fe5c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7fe5c-116">ViewSelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7fe5c-116">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="7fe5c-117">定義由視圖顯示的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="7fe5c-117">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7fe5c-118">文字值</span><span class="sxs-lookup"><span data-stu-id="7fe5c-118">Text Value</span></span>

<span data-ttu-id="7fe5c-119">指定選項群組的名稱，此選項群組是由 `Name` 選取專案集合的元素所定義。</span><span class="sxs-lookup"><span data-stu-id="7fe5c-119">Specify the name of the selection set that is defined by the `Name` element for the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="7fe5c-120">備註</span><span class="sxs-lookup"><span data-stu-id="7fe5c-120">Remarks</span></span>

<span data-ttu-id="7fe5c-121">當您有一組要使用單一名稱來參考的相關物件時，例如一組透過繼承相關的物件，您可以使用選取集。</span><span class="sxs-lookup"><span data-stu-id="7fe5c-121">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="7fe5c-122">如需定義和參考選取集的詳細資訊，請參閱 [定義物件集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="7fe5c-122">For more information about defining and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="7fe5c-123">範例</span><span class="sxs-lookup"><span data-stu-id="7fe5c-123">Example</span></span>

<span data-ttu-id="7fe5c-124">下列範例示範如何指定清單視圖的選取集合。</span><span class="sxs-lookup"><span data-stu-id="7fe5c-124">The following example shows how to specify a selection set for a list view.</span></span> <span data-ttu-id="7fe5c-125">資料表、寬和自訂視圖都使用相同的架構。</span><span class="sxs-lookup"><span data-stu-id="7fe5c-125">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="7fe5c-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7fe5c-126">See Also</span></span>

[<span data-ttu-id="7fe5c-127">定義選取範圍集合</span><span class="sxs-lookup"><span data-stu-id="7fe5c-127">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="7fe5c-128">ViewSelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7fe5c-128">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="7fe5c-129">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="7fe5c-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
