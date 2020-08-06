---
title: ViewSelectedBy (格式的 SelectionSetName 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: f6410b463bcb00d2758849c2f7e13cd839277e50
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772598"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a><span data-ttu-id="527fc-102">ViewSelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="527fc-102">SelectionSetName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="527fc-103">指定由視圖顯示的一組 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="527fc-103">Specifies a set of .NET objects that are displayed by the view.</span></span>

<span data-ttu-id="527fc-104">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ViewSelectedBy 元素 (格式) ViewSelectedBy (格式的 SelectionSetName 元素) </span><span class="sxs-lookup"><span data-stu-id="527fc-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) SelectionSetName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="527fc-105">語法</span><span class="sxs-lookup"><span data-stu-id="527fc-105">Syntax</span></span>

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="527fc-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="527fc-106">Attributes and Elements</span></span>

<span data-ttu-id="527fc-107">下列各節說明屬性、子專案和元素的父元素 `SelectionSetName` 。</span><span class="sxs-lookup"><span data-stu-id="527fc-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="527fc-108">屬性</span><span class="sxs-lookup"><span data-stu-id="527fc-108">Attributes</span></span>

<span data-ttu-id="527fc-109">無。</span><span class="sxs-lookup"><span data-stu-id="527fc-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="527fc-110">子元素</span><span class="sxs-lookup"><span data-stu-id="527fc-110">Child Elements</span></span>

<span data-ttu-id="527fc-111">無。</span><span class="sxs-lookup"><span data-stu-id="527fc-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="527fc-112">父項目</span><span class="sxs-lookup"><span data-stu-id="527fc-112">Parent Elements</span></span>

|<span data-ttu-id="527fc-113">元素</span><span class="sxs-lookup"><span data-stu-id="527fc-113">Element</span></span>|<span data-ttu-id="527fc-114">描述</span><span class="sxs-lookup"><span data-stu-id="527fc-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="527fc-115">ViewSelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="527fc-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="527fc-116">定義視圖所顯示的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="527fc-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="527fc-117">文字值</span><span class="sxs-lookup"><span data-stu-id="527fc-117">Text Value</span></span>

<span data-ttu-id="527fc-118">針對選取集指定專案所定義的選取範圍名稱 `Name` 。</span><span class="sxs-lookup"><span data-stu-id="527fc-118">Specify the name of the selection set that is defined by the `Name` element for the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="527fc-119">備註</span><span class="sxs-lookup"><span data-stu-id="527fc-119">Remarks</span></span>

<span data-ttu-id="527fc-120">當您有一組想要使用單一名稱來參考的相關物件（例如透過繼承相關的一組物件）時，您可以使用 [選擇集]。</span><span class="sxs-lookup"><span data-stu-id="527fc-120">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="527fc-121">如需定義和參考選取集的詳細資訊，請參閱[定義物件的集合](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="527fc-121">For more information about defining and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="527fc-122">範例</span><span class="sxs-lookup"><span data-stu-id="527fc-122">Example</span></span>

<span data-ttu-id="527fc-123">下列範例顯示如何指定清單視圖的選擇集。</span><span class="sxs-lookup"><span data-stu-id="527fc-123">The following example shows how to specify a selection set for a list view.</span></span> <span data-ttu-id="527fc-124">資料表、寬型和自訂視圖會使用相同的架構。</span><span class="sxs-lookup"><span data-stu-id="527fc-124">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="527fc-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="527fc-125">See Also</span></span>

[<span data-ttu-id="527fc-126">定義選取範圍集合</span><span class="sxs-lookup"><span data-stu-id="527fc-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="527fc-127">ViewSelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="527fc-127">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="527fc-128">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="527fc-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
