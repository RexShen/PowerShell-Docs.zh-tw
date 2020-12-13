---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl 之 TableColumnItem 的 FormatString 元素 (格式)
description: TableControl 之 TableColumnItem 的 FormatString 元素 (格式)
ms.openlocfilehash: 3d386e61ac321c05e0b298019c2298f76b391b21
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667890"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="7a8b7-103">TableControl 之 TableColumnItem 的 FormatString 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7a8b7-103">FormatString Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="7a8b7-104">指定格式模式，定義資料表的屬性或腳本值的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="7a8b7-104">Specifies a format pattern that defines how the property or script value of the table is displayed.</span></span>

<span data-ttu-id="7a8b7-105">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) TableControl 元素 (格式) TableRowEntries 元素 (格式) TableRowEntry 專案 (格式)  (格式專案) 格式 () </span><span class="sxs-lookup"><span data-stu-id="7a8b7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) FormatString Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7a8b7-106">語法</span><span class="sxs-lookup"><span data-stu-id="7a8b7-106">Syntax</span></span>

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7a8b7-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7a8b7-107">Attributes and Elements</span></span>

<span data-ttu-id="7a8b7-108">下列各節說明屬性、子專案和元素的父元素 `FormatString` 。</span><span class="sxs-lookup"><span data-stu-id="7a8b7-108">The following sections describe attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7a8b7-109">屬性</span><span class="sxs-lookup"><span data-stu-id="7a8b7-109">Attributes</span></span>

<span data-ttu-id="7a8b7-110">無。</span><span class="sxs-lookup"><span data-stu-id="7a8b7-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7a8b7-111">子元素</span><span class="sxs-lookup"><span data-stu-id="7a8b7-111">Child Elements</span></span>

<span data-ttu-id="7a8b7-112">無。</span><span class="sxs-lookup"><span data-stu-id="7a8b7-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7a8b7-113">父項目</span><span class="sxs-lookup"><span data-stu-id="7a8b7-113">Parent Elements</span></span>

|<span data-ttu-id="7a8b7-114">元素</span><span class="sxs-lookup"><span data-stu-id="7a8b7-114">Element</span></span>|<span data-ttu-id="7a8b7-115">描述</span><span class="sxs-lookup"><span data-stu-id="7a8b7-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7a8b7-116">之 tablecolumnitem 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="7a8b7-116">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="7a8b7-117">定義其值會顯示在資料列的資料行中的屬性或腳本。</span><span class="sxs-lookup"><span data-stu-id="7a8b7-117">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7a8b7-118">文字值</span><span class="sxs-lookup"><span data-stu-id="7a8b7-118">Text Value</span></span>

<span data-ttu-id="7a8b7-119">指定用於格式化資料的模式。</span><span class="sxs-lookup"><span data-stu-id="7a8b7-119">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="7a8b7-120">例如，您可以使用此模式來格式化 [任何類型為](/dotnet/api/System.TimeSpan)system.string： {0： MMM} {0： dd} {0： HH}： {0： mm} 的屬性值。</span><span class="sxs-lookup"><span data-stu-id="7a8b7-120">For example, this pattern can be used to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="7a8b7-121">備註</span><span class="sxs-lookup"><span data-stu-id="7a8b7-121">Remarks</span></span>

<span data-ttu-id="7a8b7-122">您可以在建立資料表視圖、清單視圖、寬視圖或自訂視圖時使用格式字串。</span><span class="sxs-lookup"><span data-stu-id="7a8b7-122">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="7a8b7-123">如需有關如何將顯示在視圖中的值格式化的詳細資訊，請參閱 [格式化顯示的資料](./formatting-displayed-data.md)。</span><span class="sxs-lookup"><span data-stu-id="7a8b7-123">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="7a8b7-124">如需有關資料表視圖元件的詳細資訊，請參閱 [資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="7a8b7-124">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="7a8b7-125">範例</span><span class="sxs-lookup"><span data-stu-id="7a8b7-125">Example</span></span>

<span data-ttu-id="7a8b7-126">下列範例顯示如何定義屬性值的格式化字串 `StartTime` 。</span><span class="sxs-lookup"><span data-stu-id="7a8b7-126">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a><span data-ttu-id="7a8b7-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a8b7-127">See Also</span></span>

[<span data-ttu-id="7a8b7-128">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="7a8b7-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="7a8b7-129">設定已顯示之資料的格式</span><span class="sxs-lookup"><span data-stu-id="7a8b7-129">Formatting Displayed Data</span></span>](./formatting-displayed-data.md)

[<span data-ttu-id="7a8b7-130">之 tablecolumnitem 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="7a8b7-130">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="7a8b7-131">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="7a8b7-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
