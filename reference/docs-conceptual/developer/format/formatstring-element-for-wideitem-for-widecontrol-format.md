---
title: WideControl 之之 wideitem 的格式字串元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5bc6ea26-3ca6-4bab-8a13-29189821ba15
caps.latest.revision: 7
ms.openlocfilehash: a1dc145864a6904fd4af6c3b9187819c49e224b0
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363027"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="d261e-102">WideControl 之 WideItem 的 FormatString 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d261e-102">FormatString Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="d261e-103">指定定義屬性或腳本值在視圖中顯示方式的格式模式。</span><span class="sxs-lookup"><span data-stu-id="d261e-103">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

<span data-ttu-id="d261e-104">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） WideControl 元素（格式） WideEntries 專案（格式） WideEntry 元素（適用于 WideControl 的之 wideitem 元素（格式）適用于 WideControl 的之 wideitem （格式）</span><span class="sxs-lookup"><span data-stu-id="d261e-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element for WideControl (Format) WideItem Element for WideControl (Format) FormatString Element for WideItem for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d261e-105">語法</span><span class="sxs-lookup"><span data-stu-id="d261e-105">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d261e-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="d261e-106">Attributes and Elements</span></span>

<span data-ttu-id="d261e-107">下列各節說明屬性、子專案，以及 `FormatString` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="d261e-107">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d261e-108">屬性</span><span class="sxs-lookup"><span data-stu-id="d261e-108">Attributes</span></span>

<span data-ttu-id="d261e-109">無。</span><span class="sxs-lookup"><span data-stu-id="d261e-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d261e-110">子元素</span><span class="sxs-lookup"><span data-stu-id="d261e-110">Child Elements</span></span>

<span data-ttu-id="d261e-111">無。</span><span class="sxs-lookup"><span data-stu-id="d261e-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d261e-112">父元素</span><span class="sxs-lookup"><span data-stu-id="d261e-112">Parent Elements</span></span>

|<span data-ttu-id="d261e-113">元素</span><span class="sxs-lookup"><span data-stu-id="d261e-113">Element</span></span>|<span data-ttu-id="d261e-114">描述</span><span class="sxs-lookup"><span data-stu-id="d261e-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d261e-115">WideControl 的之 wideitem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d261e-115">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="d261e-116">定義屬性或腳本，其值會顯示在清單視圖的資料列中。</span><span class="sxs-lookup"><span data-stu-id="d261e-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d261e-117">文字值</span><span class="sxs-lookup"><span data-stu-id="d261e-117">Text Value</span></span>

<span data-ttu-id="d261e-118">指定用來格式化資料的模式。</span><span class="sxs-lookup"><span data-stu-id="d261e-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="d261e-119">例如，您可以使用此模式來格式化[System. Timespan](/dotnet/api/System.TimeSpan)： {0： MMM} {0： dd} {0： HH}： {0： mm} 類型之任何屬性的值。</span><span class="sxs-lookup"><span data-stu-id="d261e-119">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="d261e-120">備註</span><span class="sxs-lookup"><span data-stu-id="d261e-120">Remarks</span></span>

<span data-ttu-id="d261e-121">建立資料表視圖、清單視圖、寬視圖或自訂視圖時，可以使用格式字串。</span><span class="sxs-lookup"><span data-stu-id="d261e-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="d261e-122">如需有關格式化顯示在視圖中之值的詳細資訊，請參閱[格式化顯示的資料](./formatting-displayed-data.md)。</span><span class="sxs-lookup"><span data-stu-id="d261e-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="d261e-123">如需在寬視圖中使用格式字串的詳細資訊，請參閱[建立寬視圖](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="d261e-123">For more information about using format strings in wide views, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="d261e-124">範例</span><span class="sxs-lookup"><span data-stu-id="d261e-124">Example</span></span>

<span data-ttu-id="d261e-125">下列範例顯示如何為 `StartTime` 屬性的值定義格式字串。</span><span class="sxs-lookup"><span data-stu-id="d261e-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="d261e-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d261e-126">See Also</span></span>

[<span data-ttu-id="d261e-127">建立寬型視圖</span><span class="sxs-lookup"><span data-stu-id="d261e-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="d261e-128">WideControl 的之 wideitem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d261e-128">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="d261e-129">撰寫 Windows PowerShell 格式化和類型檔案</span><span class="sxs-lookup"><span data-stu-id="d261e-129">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
