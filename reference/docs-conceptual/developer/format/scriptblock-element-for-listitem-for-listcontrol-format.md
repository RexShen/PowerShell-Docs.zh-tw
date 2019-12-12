---
title: ListControl 之專案的 ScriptBlock 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74e30938-00ef-46fd-84e5-f0a83706a50e
caps.latest.revision: 11
ms.openlocfilehash: 76b600256af3f957f7fe0578f9fef810262aa5d5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364807"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="0463f-102">ListControl 之 ListItem 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0463f-102">ScriptBlock Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="0463f-103">指定其值顯示在資料列中的腳本。</span><span class="sxs-lookup"><span data-stu-id="0463f-103">Specifies the script whose value is displayed in the row.</span></span>

<span data-ttu-id="0463f-104">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） ListControl 元素（format） ListEntries 元素（適用于 ListEntry 的 ListEntries for ListControl （Format） ListItems 元素） ListControl （Format） ListEntry 元素針對 ListControl （格式）之 ListControl 的 ListItems for ListControl （Format） ScriptBlock 元素的（格式）</span><span class="sxs-lookup"><span data-stu-id="0463f-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ScriptBlock Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0463f-105">語法</span><span class="sxs-lookup"><span data-stu-id="0463f-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0463f-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="0463f-106">Attributes and Elements</span></span>

<span data-ttu-id="0463f-107">下列各節說明屬性、子專案，以及 `ScriptBlock` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="0463f-107">The following sections describe the attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0463f-108">屬性</span><span class="sxs-lookup"><span data-stu-id="0463f-108">Attributes</span></span>

<span data-ttu-id="0463f-109">無。</span><span class="sxs-lookup"><span data-stu-id="0463f-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0463f-110">子元素</span><span class="sxs-lookup"><span data-stu-id="0463f-110">Child Elements</span></span>

<span data-ttu-id="0463f-111">無。</span><span class="sxs-lookup"><span data-stu-id="0463f-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0463f-112">父元素</span><span class="sxs-lookup"><span data-stu-id="0463f-112">Parent Elements</span></span>

|<span data-ttu-id="0463f-113">元素</span><span class="sxs-lookup"><span data-stu-id="0463f-113">Element</span></span>|<span data-ttu-id="0463f-114">描述</span><span class="sxs-lookup"><span data-stu-id="0463f-114">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="0463f-115">[[專案] 元素（格式）](./listitem-element-for-listitems-for-listcontrol-format.md)</span><span class="sxs-lookup"><span data-stu-id="0463f-115">[ListItem Element (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)</span></span>|<span data-ttu-id="0463f-116">定義屬性或腳本，其值會顯示在清單視圖的資料列中。</span><span class="sxs-lookup"><span data-stu-id="0463f-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0463f-117">文字值</span><span class="sxs-lookup"><span data-stu-id="0463f-117">Text Value</span></span>

<span data-ttu-id="0463f-118">指定其值顯示在資料列中的腳本。</span><span class="sxs-lookup"><span data-stu-id="0463f-118">Specify the script whose value is displayed in the row.</span></span>

## <a name="remarks"></a><span data-ttu-id="0463f-119">備註</span><span class="sxs-lookup"><span data-stu-id="0463f-119">Remarks</span></span>

<span data-ttu-id="0463f-120">當指定此元素時，您無法指定[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="0463f-120">When this element is specified, you cannot specify the [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="0463f-121">如需在清單視圖中指定腳本的詳細資訊，請參閱[清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="0463f-121">For more information about specifying scripts in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="0463f-122">範例</span><span class="sxs-lookup"><span data-stu-id="0463f-122">Example</span></span>

<span data-ttu-id="0463f-123">下列範例顯示如何指定屬性，其值會顯示。</span><span class="sxs-lookup"><span data-stu-id="0463f-123">The following example shows how to specify the property whose value is displayed.</span></span>

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="0463f-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0463f-124">See Also</span></span>

[<span data-ttu-id="0463f-125">ListControl 之專案名稱的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="0463f-125">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="0463f-126">建立清單視圖</span><span class="sxs-lookup"><span data-stu-id="0463f-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="0463f-127">適用于 ListControl 之 ListItems 的專案專案元素（格式）</span><span class="sxs-lookup"><span data-stu-id="0463f-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="0463f-128">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="0463f-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
