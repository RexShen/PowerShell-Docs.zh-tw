---
title: ListControl 之專案名稱的 PropertyName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01ae8cbe-acdc-4043-bd6e-1118a5691a55
caps.latest.revision: 12
ms.openlocfilehash: 405184f7bdbf1955f1df7766bf2723c244dcc27f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362377"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="92336-102">ListControl 之 ListItem 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="92336-102">PropertyName Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="92336-103">指定其值顯示在清單中的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="92336-103">Specifies the .NET property whose value is displayed in the list.</span></span>

<span data-ttu-id="92336-104">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） ListControl 元素（格式） ListEntries 元素（格式） ListEntry 元素（格式） ListItems 元素（格式）的專案名稱元素（格式） PropertyName 元素檔（格式）</span><span class="sxs-lookup"><span data-stu-id="92336-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) ListItems Element (Format) ListItem Element (Format) PropertyName Element for ListItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="92336-105">語法</span><span class="sxs-lookup"><span data-stu-id="92336-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="92336-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="92336-106">Attributes and Elements</span></span>

<span data-ttu-id="92336-107">下列各節說明屬性、子專案，以及 `PropertyName` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="92336-107">The following sections describe the attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="92336-108">屬性</span><span class="sxs-lookup"><span data-stu-id="92336-108">Attributes</span></span>

<span data-ttu-id="92336-109">無。</span><span class="sxs-lookup"><span data-stu-id="92336-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="92336-110">子元素</span><span class="sxs-lookup"><span data-stu-id="92336-110">Child Elements</span></span>

<span data-ttu-id="92336-111">無。</span><span class="sxs-lookup"><span data-stu-id="92336-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="92336-112">父元素</span><span class="sxs-lookup"><span data-stu-id="92336-112">Parent Elements</span></span>

|<span data-ttu-id="92336-113">元素</span><span class="sxs-lookup"><span data-stu-id="92336-113">Element</span></span>|<span data-ttu-id="92336-114">描述</span><span class="sxs-lookup"><span data-stu-id="92336-114">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="92336-115">[[專案] 元素（格式）](./listitem-element-for-listitems-for-listcontrol-format.md)</span><span class="sxs-lookup"><span data-stu-id="92336-115">[ListItem Element (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)</span></span>|<span data-ttu-id="92336-116">定義屬性或腳本，其值會顯示在清單視圖的資料列中。</span><span class="sxs-lookup"><span data-stu-id="92336-116">Defines the property or script whose value is displayed in the row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="92336-117">文字值</span><span class="sxs-lookup"><span data-stu-id="92336-117">Text Value</span></span>

<span data-ttu-id="92336-118">指定顯示其值的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="92336-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="92336-119">備註</span><span class="sxs-lookup"><span data-stu-id="92336-119">Remarks</span></span>

<span data-ttu-id="92336-120">當指定此元素時，您不能指定[ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="92336-120">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="92336-121">除了顯示內容值之外，您也可以指定值的標籤，或可用於變更值顯示的格式字串。</span><span class="sxs-lookup"><span data-stu-id="92336-121">In addition to displaying the property value, you can also specify a label for the value or a format string that can be used to change the display of the value.</span></span> <span data-ttu-id="92336-122">如需在清單視圖中指定資料的詳細資訊，請參閱[建立清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="92336-122">For more information about specifying data in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="92336-123">範例</span><span class="sxs-lookup"><span data-stu-id="92336-123">Example</span></span>

<span data-ttu-id="92336-124">下列範例顯示如何指定其值顯示的標籤和屬性。</span><span class="sxs-lookup"><span data-stu-id="92336-124">The following example shows how to specify the label and property whose value is displayed.</span></span>

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="92336-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92336-125">See Also</span></span>

[<span data-ttu-id="92336-126">ListControl 之專案的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="92336-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="92336-127">建立清單視圖</span><span class="sxs-lookup"><span data-stu-id="92336-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="92336-128">ListControl 的專案元素（格式）</span><span class="sxs-lookup"><span data-stu-id="92336-128">ListItem Element for ListControl(Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="92336-129">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="92336-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
