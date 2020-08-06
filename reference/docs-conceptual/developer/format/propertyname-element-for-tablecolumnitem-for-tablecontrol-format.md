---
title: 之 tablecolumnitem for TableControl (格式的 PropertyName 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: bf267eeb83aef59abea2d945af12e849252309c8
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772972"
---
# <a name="propertyname-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="bde61-102">TableControl 之 TableColumnItem 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="bde61-102">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="bde61-103">指定屬性，其值會顯示在資料列的資料行中。</span><span class="sxs-lookup"><span data-stu-id="bde61-103">Specifies the property whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="bde61-104">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) TableControl 專案 (格式) TableRowEntries 專案 (格式) TableRowEntry 專案 (格式) TableColumnItems 元素 (格式) 之 tablecolumnitem 元素 (格式) 之 tablecolumnitem (格式的 PropertyName 元素) </span><span class="sxs-lookup"><span data-stu-id="bde61-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) PropertyName Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bde61-105">語法</span><span class="sxs-lookup"><span data-stu-id="bde61-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bde61-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bde61-106">Attributes and Elements</span></span>

<span data-ttu-id="bde61-107">下列各節描述元素的屬性、子專案和父項目 `PropertyName` 。</span><span class="sxs-lookup"><span data-stu-id="bde61-107">The following sections describe attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bde61-108">屬性</span><span class="sxs-lookup"><span data-stu-id="bde61-108">Attributes</span></span>

<span data-ttu-id="bde61-109">無。</span><span class="sxs-lookup"><span data-stu-id="bde61-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bde61-110">子元素</span><span class="sxs-lookup"><span data-stu-id="bde61-110">Child Elements</span></span>

<span data-ttu-id="bde61-111">無。</span><span class="sxs-lookup"><span data-stu-id="bde61-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bde61-112">父項目</span><span class="sxs-lookup"><span data-stu-id="bde61-112">Parent Elements</span></span>

|<span data-ttu-id="bde61-113">元素</span><span class="sxs-lookup"><span data-stu-id="bde61-113">Element</span></span>|<span data-ttu-id="bde61-114">描述</span><span class="sxs-lookup"><span data-stu-id="bde61-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bde61-115">之 tablecolumnitem 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="bde61-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="bde61-116">定義屬性或腳本，其值會顯示在資料列的資料行中。</span><span class="sxs-lookup"><span data-stu-id="bde61-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="bde61-117">文字值</span><span class="sxs-lookup"><span data-stu-id="bde61-117">Text Value</span></span>

<span data-ttu-id="bde61-118">指定顯示其值的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="bde61-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="bde61-119">備註</span><span class="sxs-lookup"><span data-stu-id="bde61-119">Remarks</span></span>

<span data-ttu-id="bde61-120">如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="bde61-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="bde61-121">範例</span><span class="sxs-lookup"><span data-stu-id="bde61-121">Example</span></span>

<span data-ttu-id="bde61-122">這個範例會顯示 `TableColumnItem` 指定 system.servicemodel `Status` 物件之屬性的元素[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) 。</span><span class="sxs-lookup"><span data-stu-id="bde61-122">This example shows a `TableColumnItem` element that specifies the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="bde61-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bde61-123">See Also</span></span>

[<span data-ttu-id="bde61-124">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="bde61-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="bde61-125">之 tablecolumnitem 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="bde61-125">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="bde61-126">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="bde61-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
