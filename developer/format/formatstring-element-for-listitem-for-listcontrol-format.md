---
title: FormatString 元素 ListControl （格式） 的 ListItem |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd2cac66-88bb-449f-9d47-bd2cd4fe1801
caps.latest.revision: 13
ms.openlocfilehash: e6024ec4f7fc490c92408047c8c15c775e45bf9d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065610"
---
# <a name="formatstring-element-for-listitem-for-listcontrol--format"></a><span data-ttu-id="62fad-102">ListControl 之 ListItem 的 FormatString 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="62fad-102">FormatString Element for ListItem for ListControl  (Format)</span></span>

<span data-ttu-id="62fad-103">指定之格式模式所定義的屬性或指令碼的值的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="62fad-103">Specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="62fad-104">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） ListControl 項目 （格式） ListEntries ListControl （格式） ListEntry 元素元素 ListControl （格式） 的 ListControl （格式） ListItems 元素ListItem 項目 ListControl （格式） 的 ListItem ListControl （格式） FormatString 元素</span><span class="sxs-lookup"><span data-stu-id="62fad-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem Element for ListControl (Format) FormatString Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="62fad-105">語法</span><span class="sxs-lookup"><span data-stu-id="62fad-105">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="62fad-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="62fad-106">Attributes and Elements</span></span>

<span data-ttu-id="62fad-107">下列各節說明屬性、 子項目和父項目`FormatString`項目。</span><span class="sxs-lookup"><span data-stu-id="62fad-107">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="62fad-108">屬性</span><span class="sxs-lookup"><span data-stu-id="62fad-108">Attributes</span></span>

<span data-ttu-id="62fad-109">無。</span><span class="sxs-lookup"><span data-stu-id="62fad-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="62fad-110">子元素</span><span class="sxs-lookup"><span data-stu-id="62fad-110">Child Elements</span></span>

<span data-ttu-id="62fad-111">無。</span><span class="sxs-lookup"><span data-stu-id="62fad-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="62fad-112">父項目</span><span class="sxs-lookup"><span data-stu-id="62fad-112">Parent Elements</span></span>

|<span data-ttu-id="62fad-113">項目</span><span class="sxs-lookup"><span data-stu-id="62fad-113">Element</span></span>|<span data-ttu-id="62fad-114">描述</span><span class="sxs-lookup"><span data-stu-id="62fad-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="62fad-115">ListItem 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="62fad-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="62fad-116">定義屬性或其值會顯示 [清單] 檢視的資料列中的指令碼。</span><span class="sxs-lookup"><span data-stu-id="62fad-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="62fad-117">文字值</span><span class="sxs-lookup"><span data-stu-id="62fad-117">Text Value</span></span>

<span data-ttu-id="62fad-118">指定用來將資料格式化的模式。</span><span class="sxs-lookup"><span data-stu-id="62fad-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="62fad-119">例如，您可以使用此模式來格式化任何類型的屬性值[System.Timespan](/dotnet/api/System.TimeSpan): {0: MMM} {0:dd} {{0:hh}: {0:mm}。</span><span class="sxs-lookup"><span data-stu-id="62fad-119">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="62fad-120">備註</span><span class="sxs-lookup"><span data-stu-id="62fad-120">Remarks</span></span>

<span data-ttu-id="62fad-121">建立資料表檢視、 清單檢視、 寬型檢視或自訂的檢視時，就可以使用格式字串。</span><span class="sxs-lookup"><span data-stu-id="62fad-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="62fad-122">如需有關如何格式化顯示在檢視值的詳細資訊，請參閱[格式顯示資料](./formatting-displayed-data.md)。</span><span class="sxs-lookup"><span data-stu-id="62fad-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="62fad-123">如需在清單檢視中使用格式字串的詳細資訊，請參閱[建立清單檢視](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="62fad-123">For more information about using format strings in list views, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="62fad-124">範例</span><span class="sxs-lookup"><span data-stu-id="62fad-124">Example</span></span>

<span data-ttu-id="62fad-125">下列範例示範如何定義的格式化字串的值，`StartTime`屬性。</span><span class="sxs-lookup"><span data-stu-id="62fad-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

## <a name="see-also"></a><span data-ttu-id="62fad-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62fad-126">See Also</span></span>

[<span data-ttu-id="62fad-127">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="62fad-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="62fad-128">ListItem 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="62fad-128">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="62fad-129">撰寫 Windows PowerShell 格式和類型的檔案</span><span class="sxs-lookup"><span data-stu-id="62fad-129">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
