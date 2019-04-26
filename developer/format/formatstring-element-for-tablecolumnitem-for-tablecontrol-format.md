---
title: TableControl （格式） 的 TableColumnItem 的 FormatString 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a150731-d4b4-4d63-8db5-f14d463c8c37
caps.latest.revision: 13
ms.openlocfilehash: b7e1d0adc43254141056a729e1c1cc9699b6ac9b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065615"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="46135-102">TableControl 之 TableColumnItem 的 FormatString 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="46135-102">FormatString Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="46135-103">指定之格式模式所定義的屬性或指令碼的值之資料表的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="46135-103">Specifies a format pattern that defines how the property or script value of the table is displayed.</span></span>

<span data-ttu-id="46135-104">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） TableControl 項目 （格式） TableRowEntries 項目 （格式） TableRowEntry 項目 （格式） TableColumnItems 項目 （格式） TableColumnItem 項目 （格式）TableColumnItem （格式） 的 FormatString 元素</span><span class="sxs-lookup"><span data-stu-id="46135-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) FormatString Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="46135-105">語法</span><span class="sxs-lookup"><span data-stu-id="46135-105">Syntax</span></span>

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="46135-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="46135-106">Attributes and Elements</span></span>

<span data-ttu-id="46135-107">下列各節說明屬性、 子項目和父項目`FormatString`項目。</span><span class="sxs-lookup"><span data-stu-id="46135-107">The following sections describe attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="46135-108">屬性</span><span class="sxs-lookup"><span data-stu-id="46135-108">Attributes</span></span>

<span data-ttu-id="46135-109">無。</span><span class="sxs-lookup"><span data-stu-id="46135-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="46135-110">子元素</span><span class="sxs-lookup"><span data-stu-id="46135-110">Child Elements</span></span>

<span data-ttu-id="46135-111">無。</span><span class="sxs-lookup"><span data-stu-id="46135-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="46135-112">父項目</span><span class="sxs-lookup"><span data-stu-id="46135-112">Parent Elements</span></span>

|<span data-ttu-id="46135-113">項目</span><span class="sxs-lookup"><span data-stu-id="46135-113">Element</span></span>|<span data-ttu-id="46135-114">描述</span><span class="sxs-lookup"><span data-stu-id="46135-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="46135-115">TableColumnItem 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="46135-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="46135-116">定義屬性或其值會顯示在資料列的資料行的指令碼。</span><span class="sxs-lookup"><span data-stu-id="46135-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="46135-117">文字值</span><span class="sxs-lookup"><span data-stu-id="46135-117">Text Value</span></span>

<span data-ttu-id="46135-118">指定用來將資料格式化的模式。</span><span class="sxs-lookup"><span data-stu-id="46135-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="46135-119">例如，此模式可以用來格式化類型的任何屬性的值[System.Timespan](/dotnet/api/System.TimeSpan): {0: MMM} {0:dd} {{0:hh}: {0:mm}。</span><span class="sxs-lookup"><span data-stu-id="46135-119">For example, this pattern can be used to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="46135-120">備註</span><span class="sxs-lookup"><span data-stu-id="46135-120">Remarks</span></span>

<span data-ttu-id="46135-121">建立資料表檢視、 清單檢視、 寬型檢視或自訂的檢視時，就可以使用格式字串。</span><span class="sxs-lookup"><span data-stu-id="46135-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="46135-122">如需有關如何格式化顯示在檢視值的詳細資訊，請參閱[格式顯示資料](./formatting-displayed-data.md)。</span><span class="sxs-lookup"><span data-stu-id="46135-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="46135-123">資料表檢視元件的相關資訊，請參閱[資料表檢視](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="46135-123">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="46135-124">範例</span><span class="sxs-lookup"><span data-stu-id="46135-124">Example</span></span>

<span data-ttu-id="46135-125">下列範例示範如何定義的格式化字串的值，`StartTime`屬性。</span><span class="sxs-lookup"><span data-stu-id="46135-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a><span data-ttu-id="46135-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46135-126">See Also</span></span>

[<span data-ttu-id="46135-127">建立資料表檢視</span><span class="sxs-lookup"><span data-stu-id="46135-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="46135-128">格式化顯示資料</span><span class="sxs-lookup"><span data-stu-id="46135-128">Formatting Displayed Data</span></span>](./formatting-displayed-data.md)

[<span data-ttu-id="46135-129">TableColumnItem 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="46135-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="46135-130">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="46135-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
