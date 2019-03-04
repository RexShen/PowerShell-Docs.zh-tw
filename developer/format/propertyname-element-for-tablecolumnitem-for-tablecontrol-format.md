---
title: TableControl （格式） 的 TableColumnItem PropertyName 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb26d72c-2f77-4801-badf-0537ccc55e31
caps.latest.revision: 10
ms.openlocfilehash: 6e86b6a0874b385703121802bc8108a0410442cd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859464"
---
# <a name="propertyname-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="e4e16-102">TableControl 之 TableColumnItem 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e4e16-102">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="e4e16-103">指定其值會顯示在資料列的資料行的屬性。</span><span class="sxs-lookup"><span data-stu-id="e4e16-103">Specifies the property whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="e4e16-104">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） TableControl 項目 （格式） TableRowEntries 項目 （格式） TableRowEntry 項目 （格式） TableColumnItems 項目 （格式） TableColumnItem 項目 （格式）PropertyName TableColumnItem （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="e4e16-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) PropertyName Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e4e16-105">語法</span><span class="sxs-lookup"><span data-stu-id="e4e16-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e4e16-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="e4e16-106">Attributes and Elements</span></span>

<span data-ttu-id="e4e16-107">下列各節說明屬性、 子項目和父項目`PropertyName`項目。</span><span class="sxs-lookup"><span data-stu-id="e4e16-107">The following sections describe attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e4e16-108">屬性</span><span class="sxs-lookup"><span data-stu-id="e4e16-108">Attributes</span></span>

<span data-ttu-id="e4e16-109">無。</span><span class="sxs-lookup"><span data-stu-id="e4e16-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e4e16-110">子元素</span><span class="sxs-lookup"><span data-stu-id="e4e16-110">Child Elements</span></span>

<span data-ttu-id="e4e16-111">無。</span><span class="sxs-lookup"><span data-stu-id="e4e16-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e4e16-112">父元素</span><span class="sxs-lookup"><span data-stu-id="e4e16-112">Parent Elements</span></span>

|<span data-ttu-id="e4e16-113">元素</span><span class="sxs-lookup"><span data-stu-id="e4e16-113">Element</span></span>|<span data-ttu-id="e4e16-114">描述</span><span class="sxs-lookup"><span data-stu-id="e4e16-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e4e16-115">TableColumnItem 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="e4e16-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="e4e16-116">定義屬性或其值會顯示在資料列的資料行的指令碼。</span><span class="sxs-lookup"><span data-stu-id="e4e16-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e4e16-117">文字值</span><span class="sxs-lookup"><span data-stu-id="e4e16-117">Text Value</span></span>

<span data-ttu-id="e4e16-118">指定其值會顯示屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="e4e16-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="e4e16-119">備註</span><span class="sxs-lookup"><span data-stu-id="e4e16-119">Remarks</span></span>

<span data-ttu-id="e4e16-120">資料表檢視元件的相關資訊，請參閱[建立資料表檢視](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="e4e16-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e4e16-121">範例</span><span class="sxs-lookup"><span data-stu-id="e4e16-121">Example</span></span>

<span data-ttu-id="e4e16-122">此範例示範`TableColumnItem`項目，指定`Status`屬性[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)物件。</span><span class="sxs-lookup"><span data-stu-id="e4e16-122">This example shows a `TableColumnItem` element that specifies the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="e4e16-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4e16-123">See Also</span></span>

[<span data-ttu-id="e4e16-124">建立資料表檢視</span><span class="sxs-lookup"><span data-stu-id="e4e16-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="e4e16-125">TableColumnItem 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="e4e16-125">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="e4e16-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="e4e16-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
