---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl 之 ListItem 的 PropertyName 元素 (格式)
description: ListControl 之 ListItem 的 PropertyName 元素 (格式)
ms.openlocfilehash: 30cd48f9549e1a091776cd5f8395e1a71314ea1b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665969"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="abca0-103">ListControl 之 ListItem 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="abca0-103">PropertyName Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="abca0-104">指定其值會顯示在清單中的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="abca0-104">Specifies the .NET property whose value is displayed in the list.</span></span>

<span data-ttu-id="abca0-105">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ListControl 元素 (格式) ListEntries 元素 (格式) ListEntry 專案 (格式) 專案名稱 (格式) 專案名稱 (格式) </span><span class="sxs-lookup"><span data-stu-id="abca0-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) ListItems Element (Format) ListItem Element (Format) PropertyName Element for ListItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="abca0-106">語法</span><span class="sxs-lookup"><span data-stu-id="abca0-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="abca0-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="abca0-107">Attributes and Elements</span></span>

<span data-ttu-id="abca0-108">下列章節說明屬性、子專案和元素的父元素 `PropertyName` 。</span><span class="sxs-lookup"><span data-stu-id="abca0-108">The following sections describe the attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="abca0-109">屬性</span><span class="sxs-lookup"><span data-stu-id="abca0-109">Attributes</span></span>

<span data-ttu-id="abca0-110">無。</span><span class="sxs-lookup"><span data-stu-id="abca0-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="abca0-111">子元素</span><span class="sxs-lookup"><span data-stu-id="abca0-111">Child Elements</span></span>

<span data-ttu-id="abca0-112">無。</span><span class="sxs-lookup"><span data-stu-id="abca0-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="abca0-113">父項目</span><span class="sxs-lookup"><span data-stu-id="abca0-113">Parent Elements</span></span>

|<span data-ttu-id="abca0-114">元素</span><span class="sxs-lookup"><span data-stu-id="abca0-114">Element</span></span>|<span data-ttu-id="abca0-115">描述</span><span class="sxs-lookup"><span data-stu-id="abca0-115">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="abca0-116">[ (格式) 的 [專案] 元素 ](./listitem-element-for-listitems-for-listcontrol-format.md)</span><span class="sxs-lookup"><span data-stu-id="abca0-116">[ListItem Element (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)</span></span>|<span data-ttu-id="abca0-117">定義屬性或腳本，其值會顯示在清單視圖的資料列中。</span><span class="sxs-lookup"><span data-stu-id="abca0-117">Defines the property or script whose value is displayed in the row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="abca0-118">文字值</span><span class="sxs-lookup"><span data-stu-id="abca0-118">Text Value</span></span>

<span data-ttu-id="abca0-119">指定顯示其值的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="abca0-119">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="abca0-120">備註</span><span class="sxs-lookup"><span data-stu-id="abca0-120">Remarks</span></span>

<span data-ttu-id="abca0-121">當指定這個專案時，您無法指定 [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="abca0-121">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="abca0-122">除了顯示內容值，您也可以指定值的標籤，或可用於變更值顯示的格式字串。</span><span class="sxs-lookup"><span data-stu-id="abca0-122">In addition to displaying the property value, you can also specify a label for the value or a format string that can be used to change the display of the value.</span></span> <span data-ttu-id="abca0-123">如需在清單視圖中指定資料的詳細資訊，請參閱 [建立清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="abca0-123">For more information about specifying data in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="abca0-124">範例</span><span class="sxs-lookup"><span data-stu-id="abca0-124">Example</span></span>

<span data-ttu-id="abca0-125">下列範例示範如何指定會顯示其值的標籤和屬性。</span><span class="sxs-lookup"><span data-stu-id="abca0-125">The following example shows how to specify the label and property whose value is displayed.</span></span>

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="abca0-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="abca0-126">See Also</span></span>

[<span data-ttu-id="abca0-127">ListControl 之 ListItem 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="abca0-127">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="abca0-128">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="abca0-128">Creating a List View</span></span>](./creating-a-list-view.md)

<span data-ttu-id="abca0-129">[ListControl (格式的 [專案] 元素) ](./listitem-element-for-listitems-for-listcontrol-format.md)</span><span class="sxs-lookup"><span data-stu-id="abca0-129">[ListItem Element for ListControl(Format)](./listitem-element-for-listitems-for-listcontrol-format.md)</span></span>

[<span data-ttu-id="abca0-130">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="abca0-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
