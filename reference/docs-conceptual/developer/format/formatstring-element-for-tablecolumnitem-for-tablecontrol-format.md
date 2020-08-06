---
title: 之 tablecolumnitem for TableControl (Format) 的格式字串元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 848583e697d0ab7bd5b017c14c47aba3c51a3c17
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781540"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="45a98-102">TableControl 之 TableColumnItem 的 FormatString 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="45a98-102">FormatString Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="45a98-103">指定定義如何顯示資料表之屬性或腳本值的格式模式。</span><span class="sxs-lookup"><span data-stu-id="45a98-103">Specifies a format pattern that defines how the property or script value of the table is displayed.</span></span>

<span data-ttu-id="45a98-104">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) TableControl 專案 (格式) TableRowEntries 專案 (格式) TableRowEntry 專案 (格式) TableColumnItems 元素 (格式) 之 tablecolumnitem 元素 (格式) 之 tablecolumnitem (格式的字串格式) </span><span class="sxs-lookup"><span data-stu-id="45a98-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) FormatString Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="45a98-105">語法</span><span class="sxs-lookup"><span data-stu-id="45a98-105">Syntax</span></span>

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="45a98-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="45a98-106">Attributes and Elements</span></span>

<span data-ttu-id="45a98-107">下列各節說明屬性、子專案和元素的父元素 `FormatString` 。</span><span class="sxs-lookup"><span data-stu-id="45a98-107">The following sections describe attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="45a98-108">屬性</span><span class="sxs-lookup"><span data-stu-id="45a98-108">Attributes</span></span>

<span data-ttu-id="45a98-109">無。</span><span class="sxs-lookup"><span data-stu-id="45a98-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="45a98-110">子元素</span><span class="sxs-lookup"><span data-stu-id="45a98-110">Child Elements</span></span>

<span data-ttu-id="45a98-111">無。</span><span class="sxs-lookup"><span data-stu-id="45a98-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="45a98-112">父項目</span><span class="sxs-lookup"><span data-stu-id="45a98-112">Parent Elements</span></span>

|<span data-ttu-id="45a98-113">元素</span><span class="sxs-lookup"><span data-stu-id="45a98-113">Element</span></span>|<span data-ttu-id="45a98-114">描述</span><span class="sxs-lookup"><span data-stu-id="45a98-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="45a98-115">之 tablecolumnitem 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="45a98-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="45a98-116">定義屬性或腳本，其值會顯示在資料列的資料行中。</span><span class="sxs-lookup"><span data-stu-id="45a98-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="45a98-117">文字值</span><span class="sxs-lookup"><span data-stu-id="45a98-117">Text Value</span></span>

<span data-ttu-id="45a98-118">指定用來格式化資料的模式。</span><span class="sxs-lookup"><span data-stu-id="45a98-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="45a98-119">例如，您可以使用此模式來格式化[System. Timespan](/dotnet/api/System.TimeSpan)： {0： MMM} {0： dd} {0： HH}： {0： mm} 類型之任何屬性的值。</span><span class="sxs-lookup"><span data-stu-id="45a98-119">For example, this pattern can be used to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="45a98-120">備註</span><span class="sxs-lookup"><span data-stu-id="45a98-120">Remarks</span></span>

<span data-ttu-id="45a98-121">建立資料表視圖、清單視圖、寬視圖或自訂視圖時，可以使用格式字串。</span><span class="sxs-lookup"><span data-stu-id="45a98-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="45a98-122">如需有關格式化顯示在視圖中之值的詳細資訊，請參閱[格式化顯示的資料](./formatting-displayed-data.md)。</span><span class="sxs-lookup"><span data-stu-id="45a98-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="45a98-123">如需有關資料表視圖之元件的詳細資訊，請參閱[資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="45a98-123">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="45a98-124">範例</span><span class="sxs-lookup"><span data-stu-id="45a98-124">Example</span></span>

<span data-ttu-id="45a98-125">下列範例顯示如何為屬性的值定義格式化字串 `StartTime` 。</span><span class="sxs-lookup"><span data-stu-id="45a98-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a><span data-ttu-id="45a98-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45a98-126">See Also</span></span>

[<span data-ttu-id="45a98-127">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="45a98-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="45a98-128">設定已顯示之資料的格式</span><span class="sxs-lookup"><span data-stu-id="45a98-128">Formatting Displayed Data</span></span>](./formatting-displayed-data.md)

[<span data-ttu-id="45a98-129">之 tablecolumnitem 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="45a98-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="45a98-130">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="45a98-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
