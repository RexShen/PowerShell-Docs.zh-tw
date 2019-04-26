---
title: PropertyName ListControl （格式） 的 ListItem 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01ae8cbe-acdc-4043-bd6e-1118a5691a55
caps.latest.revision: 12
ms.openlocfilehash: 405184f7bdbf1955f1df7766bf2723c244dcc27f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064898"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="c4f23-102">ListControl 之 ListItem 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c4f23-102">PropertyName Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="c4f23-103">指定其值會顯示在清單中的.NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="c4f23-103">Specifies the .NET property whose value is displayed in the list.</span></span>

<span data-ttu-id="c4f23-104">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） ListControl 項目 （格式） ListEntries 項目 （格式） ListEntry 項目 （格式） ListItems 項目 （格式） ListItem 項目 （格式） PropertyName 項目ListItem （格式）</span><span class="sxs-lookup"><span data-stu-id="c4f23-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) ListItems Element (Format) ListItem Element (Format) PropertyName Element for ListItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c4f23-105">語法</span><span class="sxs-lookup"><span data-stu-id="c4f23-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c4f23-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c4f23-106">Attributes and Elements</span></span>

<span data-ttu-id="c4f23-107">下列各節說明屬性、 子項目和父項目`PropertyName`項目。</span><span class="sxs-lookup"><span data-stu-id="c4f23-107">The following sections describe the attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c4f23-108">屬性</span><span class="sxs-lookup"><span data-stu-id="c4f23-108">Attributes</span></span>

<span data-ttu-id="c4f23-109">無。</span><span class="sxs-lookup"><span data-stu-id="c4f23-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c4f23-110">子元素</span><span class="sxs-lookup"><span data-stu-id="c4f23-110">Child Elements</span></span>

<span data-ttu-id="c4f23-111">無。</span><span class="sxs-lookup"><span data-stu-id="c4f23-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c4f23-112">父項目</span><span class="sxs-lookup"><span data-stu-id="c4f23-112">Parent Elements</span></span>

|<span data-ttu-id="c4f23-113">項目</span><span class="sxs-lookup"><span data-stu-id="c4f23-113">Element</span></span>|<span data-ttu-id="c4f23-114">描述</span><span class="sxs-lookup"><span data-stu-id="c4f23-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c4f23-115">ListItem 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="c4f23-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="c4f23-116">定義屬性或其值會顯示 [清單] 檢視的資料列中的指令碼。</span><span class="sxs-lookup"><span data-stu-id="c4f23-116">Defines the property or script whose value is displayed in the row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c4f23-117">文字值</span><span class="sxs-lookup"><span data-stu-id="c4f23-117">Text Value</span></span>

<span data-ttu-id="c4f23-118">指定其值會顯示屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="c4f23-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="c4f23-119">備註</span><span class="sxs-lookup"><span data-stu-id="c4f23-119">Remarks</span></span>

<span data-ttu-id="c4f23-120">當指定這個項目時，您無法指定[ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md)項目。</span><span class="sxs-lookup"><span data-stu-id="c4f23-120">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="c4f23-121">除了顯示的屬性值，您也可以指定的值或可用來變更值的顯示格式字串的標籤。</span><span class="sxs-lookup"><span data-stu-id="c4f23-121">In addition to displaying the property value, you can also specify a label for the value or a format string that can be used to change the display of the value.</span></span> <span data-ttu-id="c4f23-122">如需在清單檢視中指定資料的詳細資訊，請參閱[建立清單檢視](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="c4f23-122">For more information about specifying data in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c4f23-123">範例</span><span class="sxs-lookup"><span data-stu-id="c4f23-123">Example</span></span>

<span data-ttu-id="c4f23-124">下列範例示範如何指定標籤和其值會顯示的屬性。</span><span class="sxs-lookup"><span data-stu-id="c4f23-124">The following example shows how to specify the label and property whose value is displayed.</span></span>

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="c4f23-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4f23-125">See Also</span></span>

[<span data-ttu-id="c4f23-126">ScriptBlock ListControl （格式） 的 ListItem 元素</span><span class="sxs-lookup"><span data-stu-id="c4f23-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="c4f23-127">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="c4f23-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="c4f23-128">ListControl(Format) 的 ListItem 項目</span><span class="sxs-lookup"><span data-stu-id="c4f23-128">ListItem Element for ListControl(Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="c4f23-129">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="c4f23-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
