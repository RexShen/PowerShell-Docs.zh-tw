---
title: FormatString 元素 WideControl （格式） 的 WideItem |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5bc6ea26-3ca6-4bab-8a13-29189821ba15
caps.latest.revision: 7
ms.openlocfilehash: a1dc145864a6904fd4af6c3b9187819c49e224b0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860934"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="c6dda-102">WideControl 之 WideItem 的 FormatString 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c6dda-102">FormatString Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="c6dda-103">指定之格式模式所定義的屬性或指令碼的值在檢視中的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="c6dda-103">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

<span data-ttu-id="c6dda-104">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） WideControl 項目 （格式） WideEntries 項目 （格式） WideEntry WideControl （格式） WideItem 元素元素 WideControl （格式） FormatString 元素針對 WideControl （格式） 的 WideItem</span><span class="sxs-lookup"><span data-stu-id="c6dda-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element for WideControl (Format) WideItem Element for WideControl (Format) FormatString Element for WideItem for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c6dda-105">語法</span><span class="sxs-lookup"><span data-stu-id="c6dda-105">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c6dda-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="c6dda-106">Attributes and Elements</span></span>

<span data-ttu-id="c6dda-107">下列各節說明屬性、 子項目和父項目`FormatString`項目。</span><span class="sxs-lookup"><span data-stu-id="c6dda-107">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c6dda-108">屬性</span><span class="sxs-lookup"><span data-stu-id="c6dda-108">Attributes</span></span>

<span data-ttu-id="c6dda-109">無。</span><span class="sxs-lookup"><span data-stu-id="c6dda-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c6dda-110">子元素</span><span class="sxs-lookup"><span data-stu-id="c6dda-110">Child Elements</span></span>

<span data-ttu-id="c6dda-111">無。</span><span class="sxs-lookup"><span data-stu-id="c6dda-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c6dda-112">父元素</span><span class="sxs-lookup"><span data-stu-id="c6dda-112">Parent Elements</span></span>

|<span data-ttu-id="c6dda-113">元素</span><span class="sxs-lookup"><span data-stu-id="c6dda-113">Element</span></span>|<span data-ttu-id="c6dda-114">描述</span><span class="sxs-lookup"><span data-stu-id="c6dda-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c6dda-115">WideItem WideControl （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="c6dda-115">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="c6dda-116">定義屬性或其值會顯示 [清單] 檢視的資料列中的指令碼。</span><span class="sxs-lookup"><span data-stu-id="c6dda-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c6dda-117">文字值</span><span class="sxs-lookup"><span data-stu-id="c6dda-117">Text Value</span></span>

<span data-ttu-id="c6dda-118">指定用來將資料格式化的模式。</span><span class="sxs-lookup"><span data-stu-id="c6dda-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="c6dda-119">例如，您可以使用此模式來格式化任何類型的屬性值[System.Timespan](/dotnet/api/System.TimeSpan): {0: MMM} {0:dd} {{0:hh}: {0:mm}。</span><span class="sxs-lookup"><span data-stu-id="c6dda-119">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="c6dda-120">備註</span><span class="sxs-lookup"><span data-stu-id="c6dda-120">Remarks</span></span>

<span data-ttu-id="c6dda-121">建立資料表檢視、 清單檢視、 寬型檢視或自訂的檢視時，就可以使用格式字串。</span><span class="sxs-lookup"><span data-stu-id="c6dda-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="c6dda-122">如需有關如何格式化顯示在檢視值的詳細資訊，請參閱[格式顯示資料](./formatting-displayed-data.md)。</span><span class="sxs-lookup"><span data-stu-id="c6dda-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="c6dda-123">如需在寬型檢視中使用格式字串的詳細資訊，請參閱[建立寬型檢視](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="c6dda-123">For more information about using format strings in wide views, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c6dda-124">範例</span><span class="sxs-lookup"><span data-stu-id="c6dda-124">Example</span></span>

<span data-ttu-id="c6dda-125">下列範例示範如何定義的格式化字串的值，`StartTime`屬性。</span><span class="sxs-lookup"><span data-stu-id="c6dda-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="c6dda-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6dda-126">See Also</span></span>

[<span data-ttu-id="c6dda-127">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="c6dda-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="c6dda-128">WideItem WideControl （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="c6dda-128">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="c6dda-129">撰寫 Windows PowerShell 格式和類型的檔案</span><span class="sxs-lookup"><span data-stu-id="c6dda-129">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
