---
title: TableControl 之之 tablecolumnitem 的 PropertyName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb26d72c-2f77-4801-badf-0537ccc55e31
caps.latest.revision: 10
ms.openlocfilehash: 6e86b6a0874b385703121802bc8108a0410442cd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362247"
---
# <a name="propertyname-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="eb311-102">TableControl 之 TableColumnItem 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="eb311-102">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="eb311-103">指定屬性，其值會顯示在資料列的資料行中。</span><span class="sxs-lookup"><span data-stu-id="eb311-103">Specifies the property whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="eb311-104">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（格式） TableControl 元素（格式） TableRowEntries 元素（格式） TableRowEntry 元素（格式） TableColumnItems 元素（格式）之 tablecolumnitem 元素（格式）之 tablecolumnitem 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="eb311-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) PropertyName Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="eb311-105">語法</span><span class="sxs-lookup"><span data-stu-id="eb311-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="eb311-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="eb311-106">Attributes and Elements</span></span>

<span data-ttu-id="eb311-107">下列各節描述 `PropertyName` 元素的屬性、子專案和父元素。</span><span class="sxs-lookup"><span data-stu-id="eb311-107">The following sections describe attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="eb311-108">屬性</span><span class="sxs-lookup"><span data-stu-id="eb311-108">Attributes</span></span>

<span data-ttu-id="eb311-109">無。</span><span class="sxs-lookup"><span data-stu-id="eb311-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="eb311-110">子元素</span><span class="sxs-lookup"><span data-stu-id="eb311-110">Child Elements</span></span>

<span data-ttu-id="eb311-111">無。</span><span class="sxs-lookup"><span data-stu-id="eb311-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="eb311-112">父元素</span><span class="sxs-lookup"><span data-stu-id="eb311-112">Parent Elements</span></span>

|<span data-ttu-id="eb311-113">元素</span><span class="sxs-lookup"><span data-stu-id="eb311-113">Element</span></span>|<span data-ttu-id="eb311-114">描述</span><span class="sxs-lookup"><span data-stu-id="eb311-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="eb311-115">之 tablecolumnitem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="eb311-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="eb311-116">定義屬性或腳本，其值會顯示在資料列的資料行中。</span><span class="sxs-lookup"><span data-stu-id="eb311-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="eb311-117">文字值</span><span class="sxs-lookup"><span data-stu-id="eb311-117">Text Value</span></span>

<span data-ttu-id="eb311-118">指定顯示其值的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="eb311-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="eb311-119">備註</span><span class="sxs-lookup"><span data-stu-id="eb311-119">Remarks</span></span>

<span data-ttu-id="eb311-120">如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="eb311-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="eb311-121">範例</span><span class="sxs-lookup"><span data-stu-id="eb311-121">Example</span></span>

<span data-ttu-id="eb311-122">這個範例會顯示 `TableColumnItem` 元素，這個專案會指定[system.webserver](/dotnet/api/System.Diagnostics.Process)物件的 `Status` 屬性。</span><span class="sxs-lookup"><span data-stu-id="eb311-122">This example shows a `TableColumnItem` element that specifies the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="eb311-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb311-123">See Also</span></span>

[<span data-ttu-id="eb311-124">建立資料表視圖</span><span class="sxs-lookup"><span data-stu-id="eb311-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="eb311-125">之 tablecolumnitem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="eb311-125">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="eb311-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="eb311-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
