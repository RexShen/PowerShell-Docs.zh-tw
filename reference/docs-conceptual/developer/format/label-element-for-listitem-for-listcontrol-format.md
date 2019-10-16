---
title: ListControl 之專案的標籤元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c693ff46-d1ad-4dc7-93ac-41ff2fc6c103
caps.latest.revision: 9
ms.openlocfilehash: c1293d5a1f942704ac01388c66bd9009fd340e82
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362887"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="49ef1-102">ListControl 之 ListItem 的標籤元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="49ef1-102">Label Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="49ef1-103">指定顯示在資料列中屬性或腳本值左邊的標籤。</span><span class="sxs-lookup"><span data-stu-id="49ef1-103">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>

<span data-ttu-id="49ef1-104">ListEntry for ListControl 元素的 ListItems （Format） ListEntry 專案之 ListControl （format） ListControl 元素的設定元素（格式） ViewDefinitions 元素（格式） ListEntries 元素（格式）專案（Format） ListControl 的 ListControl （format） Label 元素的 ListItems 的專案。</span><span class="sxs-lookup"><span data-stu-id="49ef1-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems for ListEntry for ListControl Element (Format) ListItem Element for ListItems for ListControl (Format) Label Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="49ef1-105">語法</span><span class="sxs-lookup"><span data-stu-id="49ef1-105">Syntax</span></span>

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="49ef1-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="49ef1-106">Attributes and Elements</span></span>

<span data-ttu-id="49ef1-107">下列各節說明屬性、子專案，以及 `Label` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="49ef1-107">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="49ef1-108">屬性</span><span class="sxs-lookup"><span data-stu-id="49ef1-108">Attributes</span></span>

<span data-ttu-id="49ef1-109">無。</span><span class="sxs-lookup"><span data-stu-id="49ef1-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="49ef1-110">子元素</span><span class="sxs-lookup"><span data-stu-id="49ef1-110">Child Elements</span></span>

<span data-ttu-id="49ef1-111">無。</span><span class="sxs-lookup"><span data-stu-id="49ef1-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="49ef1-112">父元素</span><span class="sxs-lookup"><span data-stu-id="49ef1-112">Parent Elements</span></span>

|<span data-ttu-id="49ef1-113">元素</span><span class="sxs-lookup"><span data-stu-id="49ef1-113">Element</span></span>|<span data-ttu-id="49ef1-114">描述</span><span class="sxs-lookup"><span data-stu-id="49ef1-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="49ef1-115">適用于 ListControl 之 ListItems 的專案專案元素（格式）</span><span class="sxs-lookup"><span data-stu-id="49ef1-115">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="49ef1-116">定義屬性或腳本，其值會顯示在清單視圖的資料列中。</span><span class="sxs-lookup"><span data-stu-id="49ef1-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="49ef1-117">文字值</span><span class="sxs-lookup"><span data-stu-id="49ef1-117">Text Value</span></span>

<span data-ttu-id="49ef1-118">指定要在屬性或腳本值左邊顯示的標籤。</span><span class="sxs-lookup"><span data-stu-id="49ef1-118">Specify the label to be display to the left of the property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="49ef1-119">備註</span><span class="sxs-lookup"><span data-stu-id="49ef1-119">Remarks</span></span>

<span data-ttu-id="49ef1-120">如果未指定標籤，則會顯示內容或腳本的名稱。</span><span class="sxs-lookup"><span data-stu-id="49ef1-120">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="49ef1-121">如需在清單視圖中使用標籤的詳細資訊，請參閱[建立清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="49ef1-121">For more information about using labels in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="49ef1-122">範例</span><span class="sxs-lookup"><span data-stu-id="49ef1-122">Example</span></span>

<span data-ttu-id="49ef1-123">下列範例顯示如何將標籤加入至資料列。</span><span class="sxs-lookup"><span data-stu-id="49ef1-123">The following example shows how to add a label to a row.</span></span>

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="49ef1-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49ef1-124">See Also</span></span>

[<span data-ttu-id="49ef1-125">建立清單視圖</span><span class="sxs-lookup"><span data-stu-id="49ef1-125">Creating a List View</span></span>](./creating-a-list-view.md)

<span data-ttu-id="49ef1-126">[[專案] 元素（格式）](./listitem-element-for-listitems-for-listcontrol-format.md)</span><span class="sxs-lookup"><span data-stu-id="49ef1-126">[ListItem Element (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)</span></span>

[<span data-ttu-id="49ef1-127">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="49ef1-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
