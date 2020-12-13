---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl 之 ListItem 的標籤元素 (格式)
description: ListControl 之 ListItem 的標籤元素 (格式)
ms.openlocfilehash: 01ff34c4129abe2c76a0a21794e756b77bff12bf
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666649"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="8999e-103">ListControl 之 ListItem 的標籤元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8999e-103">Label Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="8999e-104">指定在資料列中屬性或腳本值的左邊顯示的標籤。</span><span class="sxs-lookup"><span data-stu-id="8999e-104">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>

<span data-ttu-id="8999e-105">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) ListControl 元素 (format) ListEntries 元素 for ListControl (Format) ListEntry 專案 (格式) ListControl 專案的 ListItems (格式) ListEntry 的 ListControl 專案 (格式) 的 ListItems 專案 ListControl (格式) </span><span class="sxs-lookup"><span data-stu-id="8999e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems for ListEntry for ListControl Element (Format) ListItem Element for ListItems for ListControl (Format) Label Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8999e-106">語法</span><span class="sxs-lookup"><span data-stu-id="8999e-106">Syntax</span></span>

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8999e-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8999e-107">Attributes and Elements</span></span>

<span data-ttu-id="8999e-108">下列章節說明屬性、子專案和元素的父元素 `Label` 。</span><span class="sxs-lookup"><span data-stu-id="8999e-108">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8999e-109">屬性</span><span class="sxs-lookup"><span data-stu-id="8999e-109">Attributes</span></span>

<span data-ttu-id="8999e-110">無。</span><span class="sxs-lookup"><span data-stu-id="8999e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8999e-111">子元素</span><span class="sxs-lookup"><span data-stu-id="8999e-111">Child Elements</span></span>

<span data-ttu-id="8999e-112">無。</span><span class="sxs-lookup"><span data-stu-id="8999e-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8999e-113">父項目</span><span class="sxs-lookup"><span data-stu-id="8999e-113">Parent Elements</span></span>

|<span data-ttu-id="8999e-114">元素</span><span class="sxs-lookup"><span data-stu-id="8999e-114">Element</span></span>|<span data-ttu-id="8999e-115">描述</span><span class="sxs-lookup"><span data-stu-id="8999e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8999e-116">ListControl 之 ListItems 的 ListItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8999e-116">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="8999e-117">定義屬性或腳本，其值會顯示在清單視圖的資料列中。</span><span class="sxs-lookup"><span data-stu-id="8999e-117">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8999e-118">文字值</span><span class="sxs-lookup"><span data-stu-id="8999e-118">Text Value</span></span>

<span data-ttu-id="8999e-119">指定要在屬性或腳本值的左邊顯示的標籤。</span><span class="sxs-lookup"><span data-stu-id="8999e-119">Specify the label to be display to the left of the property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="8999e-120">備註</span><span class="sxs-lookup"><span data-stu-id="8999e-120">Remarks</span></span>

<span data-ttu-id="8999e-121">如果未指定標籤，則會顯示內容或腳本的名稱。</span><span class="sxs-lookup"><span data-stu-id="8999e-121">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="8999e-122">如需在清單視圖中使用標籤的詳細資訊，請參閱 [建立清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="8999e-122">For more information about using labels in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="8999e-123">範例</span><span class="sxs-lookup"><span data-stu-id="8999e-123">Example</span></span>

<span data-ttu-id="8999e-124">下列範例顯示如何將標籤加入至資料列。</span><span class="sxs-lookup"><span data-stu-id="8999e-124">The following example shows how to add a label to a row.</span></span>

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="8999e-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8999e-125">See Also</span></span>

[<span data-ttu-id="8999e-126">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="8999e-126">Creating a List View</span></span>](./creating-a-list-view.md)

<span data-ttu-id="8999e-127">[ (格式) 的 [專案] 元素 ](./listitem-element-for-listitems-for-listcontrol-format.md)</span><span class="sxs-lookup"><span data-stu-id="8999e-127">[ListItem Element (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)</span></span>

[<span data-ttu-id="8999e-128">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="8999e-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
