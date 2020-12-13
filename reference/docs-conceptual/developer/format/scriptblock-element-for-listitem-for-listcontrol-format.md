---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl 之 ListItem 的 ScriptBlock 元素 (格式)
description: ListControl 之 ListItem 的 ScriptBlock 元素 (格式)
ms.openlocfilehash: 0635ac2622cc203a2dc895873621901d956f87da
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664979"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="4b353-103">ListControl 之 ListItem 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4b353-103">ScriptBlock Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="4b353-104">指定其值會顯示在資料列中的腳本。</span><span class="sxs-lookup"><span data-stu-id="4b353-104">Specifies the script whose value is displayed in the row.</span></span>

<span data-ttu-id="4b353-105">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) ListControl 元素 (format) ListEntries 元素 for ListControl (Format) ListEntry for ListEntries for ListControl (ListItems 專案) ListEntry 的 ListControl 專案 ListItems (格式) 專案的 ListControl 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="4b353-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ScriptBlock Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4b353-106">語法</span><span class="sxs-lookup"><span data-stu-id="4b353-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4b353-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4b353-107">Attributes and Elements</span></span>

<span data-ttu-id="4b353-108">下列章節說明屬性、子專案和元素的父元素 `ScriptBlock` 。</span><span class="sxs-lookup"><span data-stu-id="4b353-108">The following sections describe the attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4b353-109">屬性</span><span class="sxs-lookup"><span data-stu-id="4b353-109">Attributes</span></span>

<span data-ttu-id="4b353-110">無。</span><span class="sxs-lookup"><span data-stu-id="4b353-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4b353-111">子元素</span><span class="sxs-lookup"><span data-stu-id="4b353-111">Child Elements</span></span>

<span data-ttu-id="4b353-112">無。</span><span class="sxs-lookup"><span data-stu-id="4b353-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4b353-113">父項目</span><span class="sxs-lookup"><span data-stu-id="4b353-113">Parent Elements</span></span>

|<span data-ttu-id="4b353-114">元素</span><span class="sxs-lookup"><span data-stu-id="4b353-114">Element</span></span>|<span data-ttu-id="4b353-115">描述</span><span class="sxs-lookup"><span data-stu-id="4b353-115">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="4b353-116">[ (格式) 的 [專案] 元素 ](./listitem-element-for-listitems-for-listcontrol-format.md)</span><span class="sxs-lookup"><span data-stu-id="4b353-116">[ListItem Element (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)</span></span>|<span data-ttu-id="4b353-117">定義屬性或腳本，其值會顯示在清單視圖的資料列中。</span><span class="sxs-lookup"><span data-stu-id="4b353-117">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4b353-118">文字值</span><span class="sxs-lookup"><span data-stu-id="4b353-118">Text Value</span></span>

<span data-ttu-id="4b353-119">指定其值會顯示在資料列中的腳本。</span><span class="sxs-lookup"><span data-stu-id="4b353-119">Specify the script whose value is displayed in the row.</span></span>

## <a name="remarks"></a><span data-ttu-id="4b353-120">備註</span><span class="sxs-lookup"><span data-stu-id="4b353-120">Remarks</span></span>

<span data-ttu-id="4b353-121">當指定這個專案時，您無法指定 [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="4b353-121">When this element is specified, you cannot specify the [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="4b353-122">如需在清單視圖中指定腳本的詳細資訊，請參閱 [清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="4b353-122">For more information about specifying scripts in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="4b353-123">範例</span><span class="sxs-lookup"><span data-stu-id="4b353-123">Example</span></span>

<span data-ttu-id="4b353-124">下列範例示範如何指定顯示其值的屬性。</span><span class="sxs-lookup"><span data-stu-id="4b353-124">The following example shows how to specify the property whose value is displayed.</span></span>

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="4b353-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b353-125">See Also</span></span>

[<span data-ttu-id="4b353-126">ListControl 之 ListItem 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4b353-126">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="4b353-127">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="4b353-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="4b353-128">ListControl 之 ListItems 的 ListItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4b353-128">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="4b353-129">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="4b353-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
