---
ms.date: 09/13/2016
ms.topic: reference
title: WideControl 之 WideItem 的 FormatString 元素 (格式)
description: WideControl 之 WideItem 的 FormatString 元素 (格式)
ms.openlocfilehash: f67a18e3ec4f1323e7f9be8904db518c679d53e5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667873"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="e4880-103">WideControl 之 WideItem 的 FormatString 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e4880-103">FormatString Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="e4880-104">指定格式模式，定義屬性或腳本值在視圖中的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="e4880-104">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

<span data-ttu-id="e4880-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) WideControl 元素 (format) WideEntries 元素 (format) WideControl (format) format 元素 (format 專案) 格式 (之 wideitem 的 WideControl) 格式</span><span class="sxs-lookup"><span data-stu-id="e4880-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element for WideControl (Format) WideItem Element for WideControl (Format) FormatString Element for WideItem for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e4880-106">語法</span><span class="sxs-lookup"><span data-stu-id="e4880-106">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e4880-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e4880-107">Attributes and Elements</span></span>

<span data-ttu-id="e4880-108">下列章節說明屬性、子專案和元素的父元素 `FormatString` 。</span><span class="sxs-lookup"><span data-stu-id="e4880-108">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e4880-109">屬性</span><span class="sxs-lookup"><span data-stu-id="e4880-109">Attributes</span></span>

<span data-ttu-id="e4880-110">無。</span><span class="sxs-lookup"><span data-stu-id="e4880-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e4880-111">子元素</span><span class="sxs-lookup"><span data-stu-id="e4880-111">Child Elements</span></span>

<span data-ttu-id="e4880-112">無。</span><span class="sxs-lookup"><span data-stu-id="e4880-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e4880-113">父項目</span><span class="sxs-lookup"><span data-stu-id="e4880-113">Parent Elements</span></span>

|<span data-ttu-id="e4880-114">元素</span><span class="sxs-lookup"><span data-stu-id="e4880-114">Element</span></span>|<span data-ttu-id="e4880-115">描述</span><span class="sxs-lookup"><span data-stu-id="e4880-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e4880-116">WideControl 的 WideItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e4880-116">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="e4880-117">定義屬性或腳本，其值會顯示在清單視圖的資料列中。</span><span class="sxs-lookup"><span data-stu-id="e4880-117">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e4880-118">文字值</span><span class="sxs-lookup"><span data-stu-id="e4880-118">Text Value</span></span>

<span data-ttu-id="e4880-119">指定用於格式化資料的模式。</span><span class="sxs-lookup"><span data-stu-id="e4880-119">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="e4880-120">例如，您可以使用此模式來格式化屬於 [system.string： {](/dotnet/api/System.TimeSpan)0： MMM} {0： dd} {0： HH}： {0： mm} 類型之任何屬性的值。</span><span class="sxs-lookup"><span data-stu-id="e4880-120">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="e4880-121">備註</span><span class="sxs-lookup"><span data-stu-id="e4880-121">Remarks</span></span>

<span data-ttu-id="e4880-122">您可以在建立資料表視圖、清單視圖、寬視圖或自訂視圖時使用格式字串。</span><span class="sxs-lookup"><span data-stu-id="e4880-122">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="e4880-123">如需有關如何將顯示在視圖中的值格式化的詳細資訊，請參閱 [格式化顯示的資料](./formatting-displayed-data.md)。</span><span class="sxs-lookup"><span data-stu-id="e4880-123">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="e4880-124">如需在寬型視圖中使用格式字串的詳細資訊，請參閱 [建立廣泛的視圖](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="e4880-124">For more information about using format strings in wide views, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e4880-125">範例</span><span class="sxs-lookup"><span data-stu-id="e4880-125">Example</span></span>

<span data-ttu-id="e4880-126">下列範例顯示如何定義屬性值的格式化字串 `StartTime` 。</span><span class="sxs-lookup"><span data-stu-id="e4880-126">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="e4880-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4880-127">See Also</span></span>

[<span data-ttu-id="e4880-128">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="e4880-128">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="e4880-129">WideControl 的 WideItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e4880-129">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="e4880-130">寫入 Windows PowerShell 格式和類型檔案</span><span class="sxs-lookup"><span data-stu-id="e4880-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
