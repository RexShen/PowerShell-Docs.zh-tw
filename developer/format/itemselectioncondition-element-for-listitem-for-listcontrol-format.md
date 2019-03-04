---
title: ItemSelectionCondition ListControl （格式） 的 ListItem 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2668aea-37e9-4753-a4e9-7980ae5ec2eb
caps.latest.revision: 10
ms.openlocfilehash: 6bc0ccbcc5bd62429f63ed220da66dc66f44f7ca
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861864"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="c8ee7-102">ListControl 之 ListItem 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c8ee7-102">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="c8ee7-103">定義要使用此清單項目必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="c8ee7-103">Defines the condition that must exist for this list item to be used.</span></span>

<span data-ttu-id="c8ee7-104">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） ListControl 項目 （格式） ListEntries 項目 ListEntry ListControl （格式） ListItems 元素 ListEntries ListControl （格式） ListEntry 項目ListControl （格式） ItemSelectionCondition ListControl （格式） 的 ListItem 元素 ListItems ListControl （格式） ListItem 元素</span><span class="sxs-lookup"><span data-stu-id="c8ee7-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c8ee7-105">語法</span><span class="sxs-lookup"><span data-stu-id="c8ee7-105">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c8ee7-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="c8ee7-106">Attributes and Elements</span></span>

<span data-ttu-id="c8ee7-107">下列各節說明屬性、 子項目和父項目`ItemSelectionCondition`項目。</span><span class="sxs-lookup"><span data-stu-id="c8ee7-107">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c8ee7-108">屬性</span><span class="sxs-lookup"><span data-stu-id="c8ee7-108">Attributes</span></span>

<span data-ttu-id="c8ee7-109">無。</span><span class="sxs-lookup"><span data-stu-id="c8ee7-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c8ee7-110">子元素</span><span class="sxs-lookup"><span data-stu-id="c8ee7-110">Child Elements</span></span>

|<span data-ttu-id="c8ee7-111">元素</span><span class="sxs-lookup"><span data-stu-id="c8ee7-111">Element</span></span>|<span data-ttu-id="c8ee7-112">描述</span><span class="sxs-lookup"><span data-stu-id="c8ee7-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c8ee7-113">PropertyName ItemSelectionCondition 如 ListControl （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="c8ee7-113">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="c8ee7-114">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="c8ee7-114">Optional element.</span></span><br /><br /> <span data-ttu-id="c8ee7-115">指定觸發條件的.NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="c8ee7-115">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="c8ee7-116">ItemSelectionCondition ListControl （格式） 的指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="c8ee7-116">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="c8ee7-117">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="c8ee7-117">Optional element.</span></span><br /><br /> <span data-ttu-id="c8ee7-118">指定的指令碼，就會觸發條件。</span><span class="sxs-lookup"><span data-stu-id="c8ee7-118">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c8ee7-119">父元素</span><span class="sxs-lookup"><span data-stu-id="c8ee7-119">Parent Elements</span></span>

|<span data-ttu-id="c8ee7-120">元素</span><span class="sxs-lookup"><span data-stu-id="c8ee7-120">Element</span></span>|<span data-ttu-id="c8ee7-121">描述</span><span class="sxs-lookup"><span data-stu-id="c8ee7-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c8ee7-122">ListItems ListControl （格式） 的 ListItem 項目</span><span class="sxs-lookup"><span data-stu-id="c8ee7-122">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="c8ee7-123">定義屬性或其值會顯示 [清單] 檢視的資料列中的指令碼。</span><span class="sxs-lookup"><span data-stu-id="c8ee7-123">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c8ee7-124">備註</span><span class="sxs-lookup"><span data-stu-id="c8ee7-124">Remarks</span></span>

<span data-ttu-id="c8ee7-125">您可以指定一個屬性名稱或用於這種狀況的指令碼，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="c8ee7-125">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="c8ee7-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8ee7-126">See Also</span></span>

[<span data-ttu-id="c8ee7-127">ListItems ListControl （格式） 的 ListItem 項目</span><span class="sxs-lookup"><span data-stu-id="c8ee7-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="c8ee7-128">PropertyName ItemSelectionCondition 如 ListControl （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="c8ee7-128">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="c8ee7-129">ItemSelectionCondition ListControl （格式） 的指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="c8ee7-129">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="c8ee7-130">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="c8ee7-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
