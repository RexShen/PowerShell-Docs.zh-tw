---
title: 標籤 ListControl （格式） 的 ListItem 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c693ff46-d1ad-4dc7-93ac-41ff2fc6c103
caps.latest.revision: 9
ms.openlocfilehash: c1293d5a1f942704ac01388c66bd9009fd340e82
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854774"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="2bfa9-102">ListControl 之 ListItem 的標籤元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2bfa9-102">Label Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="2bfa9-103">指定顯示屬性或指令碼中值的資料列左邊的標籤。</span><span class="sxs-lookup"><span data-stu-id="2bfa9-103">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>

<span data-ttu-id="2bfa9-104">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） ListControl 項目 （格式） ListEntries 項目 ListEntry ListControl 項目 （如的 ListControl （格式） ListItems ListControl （格式） ListEntry 項目ListItems ListControl （格式） 的 ListItem ListControl （格式） 標籤元素的格式） ListItem 項目</span><span class="sxs-lookup"><span data-stu-id="2bfa9-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems for ListEntry for ListControl Element (Format) ListItem Element for ListItems for ListControl (Format) Label Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2bfa9-105">語法</span><span class="sxs-lookup"><span data-stu-id="2bfa9-105">Syntax</span></span>

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2bfa9-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="2bfa9-106">Attributes and Elements</span></span>

<span data-ttu-id="2bfa9-107">下列各節說明屬性、 子項目和父項目`Label`項目。</span><span class="sxs-lookup"><span data-stu-id="2bfa9-107">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2bfa9-108">屬性</span><span class="sxs-lookup"><span data-stu-id="2bfa9-108">Attributes</span></span>

<span data-ttu-id="2bfa9-109">無。</span><span class="sxs-lookup"><span data-stu-id="2bfa9-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2bfa9-110">子元素</span><span class="sxs-lookup"><span data-stu-id="2bfa9-110">Child Elements</span></span>

<span data-ttu-id="2bfa9-111">無。</span><span class="sxs-lookup"><span data-stu-id="2bfa9-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2bfa9-112">父元素</span><span class="sxs-lookup"><span data-stu-id="2bfa9-112">Parent Elements</span></span>

|<span data-ttu-id="2bfa9-113">元素</span><span class="sxs-lookup"><span data-stu-id="2bfa9-113">Element</span></span>|<span data-ttu-id="2bfa9-114">描述</span><span class="sxs-lookup"><span data-stu-id="2bfa9-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2bfa9-115">ListItems ListControl （格式） 的 ListItem 項目</span><span class="sxs-lookup"><span data-stu-id="2bfa9-115">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="2bfa9-116">定義屬性或其值會顯示 [清單] 檢視的資料列中的指令碼。</span><span class="sxs-lookup"><span data-stu-id="2bfa9-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2bfa9-117">文字值</span><span class="sxs-lookup"><span data-stu-id="2bfa9-117">Text Value</span></span>

<span data-ttu-id="2bfa9-118">指定要顯示的屬性或指令碼的值的左邊的標籤。</span><span class="sxs-lookup"><span data-stu-id="2bfa9-118">Specify the label to be display to the left of the property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="2bfa9-119">備註</span><span class="sxs-lookup"><span data-stu-id="2bfa9-119">Remarks</span></span>

<span data-ttu-id="2bfa9-120">如果未指定標籤，則會顯示屬性或指令碼的名稱。</span><span class="sxs-lookup"><span data-stu-id="2bfa9-120">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="2bfa9-121">如需在清單檢視中使用標籤的詳細資訊，請參閱[建立清單檢視](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="2bfa9-121">For more information about using labels in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="2bfa9-122">範例</span><span class="sxs-lookup"><span data-stu-id="2bfa9-122">Example</span></span>

<span data-ttu-id="2bfa9-123">下列範例示範如何將標籤新增至一個資料列。</span><span class="sxs-lookup"><span data-stu-id="2bfa9-123">The following example shows how to add a label to a row.</span></span>

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="2bfa9-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2bfa9-124">See Also</span></span>

[<span data-ttu-id="2bfa9-125">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="2bfa9-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="2bfa9-126">ListItem 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="2bfa9-126">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="2bfa9-127">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="2bfa9-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
