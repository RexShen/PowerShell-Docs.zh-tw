---
title: ListControl 之專案的格式字串元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd2cac66-88bb-449f-9d47-bd2cd4fe1801
caps.latest.revision: 13
ms.openlocfilehash: e6024ec4f7fc490c92408047c8c15c775e45bf9d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363017"
---
# <a name="formatstring-element-for-listitem-for-listcontrol--format"></a><span data-ttu-id="0c3e0-102">ListControl 之 ListItem 的 FormatString 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0c3e0-102">FormatString Element for ListItem for ListControl  (Format)</span></span>

<span data-ttu-id="0c3e0-103">指定定義屬性或腳本值顯示方式的格式模式。</span><span class="sxs-lookup"><span data-stu-id="0c3e0-103">Specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="0c3e0-104">ListEntry （格式） ListControl 元素的 ListControl （format） ListItems 元素的設定元素（格式） ViewDefinitions 元素（格式） ListEntries 元素（格式）適用于 ListControl 之專案的 ListControl （格式）格式（格式）元素的專案專案專案</span><span class="sxs-lookup"><span data-stu-id="0c3e0-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem Element for ListControl (Format) FormatString Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0c3e0-105">語法</span><span class="sxs-lookup"><span data-stu-id="0c3e0-105">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0c3e0-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="0c3e0-106">Attributes and Elements</span></span>

<span data-ttu-id="0c3e0-107">下列各節說明屬性、子專案，以及 `FormatString` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="0c3e0-107">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0c3e0-108">屬性</span><span class="sxs-lookup"><span data-stu-id="0c3e0-108">Attributes</span></span>

<span data-ttu-id="0c3e0-109">無。</span><span class="sxs-lookup"><span data-stu-id="0c3e0-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0c3e0-110">子元素</span><span class="sxs-lookup"><span data-stu-id="0c3e0-110">Child Elements</span></span>

<span data-ttu-id="0c3e0-111">無。</span><span class="sxs-lookup"><span data-stu-id="0c3e0-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0c3e0-112">父元素</span><span class="sxs-lookup"><span data-stu-id="0c3e0-112">Parent Elements</span></span>

|<span data-ttu-id="0c3e0-113">元素</span><span class="sxs-lookup"><span data-stu-id="0c3e0-113">Element</span></span>|<span data-ttu-id="0c3e0-114">描述</span><span class="sxs-lookup"><span data-stu-id="0c3e0-114">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="0c3e0-115">[[專案] 元素（格式）](./listitem-element-for-listitems-for-listcontrol-format.md)</span><span class="sxs-lookup"><span data-stu-id="0c3e0-115">[ListItem Element (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)</span></span>|<span data-ttu-id="0c3e0-116">定義屬性或腳本，其值會顯示在清單視圖的資料列中。</span><span class="sxs-lookup"><span data-stu-id="0c3e0-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0c3e0-117">文字值</span><span class="sxs-lookup"><span data-stu-id="0c3e0-117">Text Value</span></span>

<span data-ttu-id="0c3e0-118">指定用來格式化資料的模式。</span><span class="sxs-lookup"><span data-stu-id="0c3e0-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="0c3e0-119">例如，您可以使用此模式來格式化[System. Timespan](/dotnet/api/System.TimeSpan)： {0： MMM} {0： dd} {0： HH}： {0： mm} 類型之任何屬性的值。</span><span class="sxs-lookup"><span data-stu-id="0c3e0-119">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="0c3e0-120">備註</span><span class="sxs-lookup"><span data-stu-id="0c3e0-120">Remarks</span></span>

<span data-ttu-id="0c3e0-121">建立資料表視圖、清單視圖、寬視圖或自訂視圖時，可以使用格式字串。</span><span class="sxs-lookup"><span data-stu-id="0c3e0-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="0c3e0-122">如需有關格式化顯示在視圖中之值的詳細資訊，請參閱[格式化顯示的資料](./formatting-displayed-data.md)。</span><span class="sxs-lookup"><span data-stu-id="0c3e0-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="0c3e0-123">如需在清單視圖中使用格式字串的詳細資訊，請參閱[建立清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="0c3e0-123">For more information about using format strings in list views, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="0c3e0-124">範例</span><span class="sxs-lookup"><span data-stu-id="0c3e0-124">Example</span></span>

<span data-ttu-id="0c3e0-125">下列範例顯示如何為 `StartTime` 屬性的值定義格式字串。</span><span class="sxs-lookup"><span data-stu-id="0c3e0-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

## <a name="see-also"></a><span data-ttu-id="0c3e0-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c3e0-126">See Also</span></span>

[<span data-ttu-id="0c3e0-127">建立清單視圖</span><span class="sxs-lookup"><span data-stu-id="0c3e0-127">Creating a List View</span></span>](./creating-a-list-view.md)

<span data-ttu-id="0c3e0-128">[[專案] 元素（格式）](./listitem-element-for-listitems-for-listcontrol-format.md)</span><span class="sxs-lookup"><span data-stu-id="0c3e0-128">[ListItem Element (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)</span></span>

[<span data-ttu-id="0c3e0-129">撰寫 Windows PowerShell 格式化和類型檔案</span><span class="sxs-lookup"><span data-stu-id="0c3e0-129">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
