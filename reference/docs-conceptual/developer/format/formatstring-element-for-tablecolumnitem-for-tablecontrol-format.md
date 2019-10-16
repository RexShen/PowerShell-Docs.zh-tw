---
title: TableControl 之之 tablecolumnitem 的格式字串元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a150731-d4b4-4d63-8db5-f14d463c8c37
caps.latest.revision: 13
ms.openlocfilehash: b7e1d0adc43254141056a729e1c1cc9699b6ac9b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363707"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="04d0c-102">TableControl 之 TableColumnItem 的 FormatString 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="04d0c-102">FormatString Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="04d0c-103">指定定義如何顯示資料表之屬性或腳本值的格式模式。</span><span class="sxs-lookup"><span data-stu-id="04d0c-103">Specifies a format pattern that defines how the property or script value of the table is displayed.</span></span>

<span data-ttu-id="04d0c-104">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（格式） TableControl 元素（格式） TableRowEntries 元素（格式） TableRowEntry 元素（格式） TableColumnItems 元素（格式）之 tablecolumnitem 元素（格式）之 tablecolumnitem 的格式字串元素（格式）</span><span class="sxs-lookup"><span data-stu-id="04d0c-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) FormatString Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="04d0c-105">語法</span><span class="sxs-lookup"><span data-stu-id="04d0c-105">Syntax</span></span>

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="04d0c-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="04d0c-106">Attributes and Elements</span></span>

<span data-ttu-id="04d0c-107">下列各節說明屬性、子專案，以及 `FormatString` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="04d0c-107">The following sections describe attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="04d0c-108">屬性</span><span class="sxs-lookup"><span data-stu-id="04d0c-108">Attributes</span></span>

<span data-ttu-id="04d0c-109">無。</span><span class="sxs-lookup"><span data-stu-id="04d0c-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="04d0c-110">子元素</span><span class="sxs-lookup"><span data-stu-id="04d0c-110">Child Elements</span></span>

<span data-ttu-id="04d0c-111">無。</span><span class="sxs-lookup"><span data-stu-id="04d0c-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="04d0c-112">父元素</span><span class="sxs-lookup"><span data-stu-id="04d0c-112">Parent Elements</span></span>

|<span data-ttu-id="04d0c-113">元素</span><span class="sxs-lookup"><span data-stu-id="04d0c-113">Element</span></span>|<span data-ttu-id="04d0c-114">描述</span><span class="sxs-lookup"><span data-stu-id="04d0c-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="04d0c-115">之 tablecolumnitem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="04d0c-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="04d0c-116">定義屬性或腳本，其值會顯示在資料列的資料行中。</span><span class="sxs-lookup"><span data-stu-id="04d0c-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="04d0c-117">文字值</span><span class="sxs-lookup"><span data-stu-id="04d0c-117">Text Value</span></span>

<span data-ttu-id="04d0c-118">指定用來格式化資料的模式。</span><span class="sxs-lookup"><span data-stu-id="04d0c-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="04d0c-119">例如，您可以使用此模式來格式化[System. Timespan](/dotnet/api/System.TimeSpan)： {0： MMM} {0： dd} {0： HH}： {0： mm} 類型之任何屬性的值。</span><span class="sxs-lookup"><span data-stu-id="04d0c-119">For example, this pattern can be used to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="04d0c-120">備註</span><span class="sxs-lookup"><span data-stu-id="04d0c-120">Remarks</span></span>

<span data-ttu-id="04d0c-121">建立資料表視圖、清單視圖、寬視圖或自訂視圖時，可以使用格式字串。</span><span class="sxs-lookup"><span data-stu-id="04d0c-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="04d0c-122">如需有關格式化顯示在視圖中之值的詳細資訊，請參閱[格式化顯示的資料](./formatting-displayed-data.md)。</span><span class="sxs-lookup"><span data-stu-id="04d0c-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="04d0c-123">如需有關資料表視圖之元件的詳細資訊，請參閱[資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="04d0c-123">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="04d0c-124">範例</span><span class="sxs-lookup"><span data-stu-id="04d0c-124">Example</span></span>

<span data-ttu-id="04d0c-125">下列範例顯示如何為 `StartTime` 屬性的值定義格式字串。</span><span class="sxs-lookup"><span data-stu-id="04d0c-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a><span data-ttu-id="04d0c-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04d0c-126">See Also</span></span>

[<span data-ttu-id="04d0c-127">建立資料表視圖</span><span class="sxs-lookup"><span data-stu-id="04d0c-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="04d0c-128">格式化顯示的資料</span><span class="sxs-lookup"><span data-stu-id="04d0c-128">Formatting Displayed Data</span></span>](./formatting-displayed-data.md)

[<span data-ttu-id="04d0c-129">之 tablecolumnitem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="04d0c-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="04d0c-130">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="04d0c-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
