---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl 之 ListItem 的 ItemSelectionCondition 元素 (格式)
description: ListControl 之 ListItem 的 ItemSelectionCondition 元素 (格式)
ms.openlocfilehash: 13d925da10c2386123983d52b109c03a0c3c63ab
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667805"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="855d6-103">ListControl 之 ListItem 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="855d6-103">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="855d6-104">定義必須存在才能使用此清單專案的條件。</span><span class="sxs-lookup"><span data-stu-id="855d6-104">Defines the condition that must exist for this list item to be used.</span></span>

<span data-ttu-id="855d6-105">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) ListControl 元素 (format) ListEntries 元素 for ListControl (Format) ListEntry for ListEntries for ListControl (ListItems 專案 ListEntry) 格式 (ListControl 元素適用于 ListItems 的 ListControl) 格式 (</span><span class="sxs-lookup"><span data-stu-id="855d6-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="855d6-106">語法</span><span class="sxs-lookup"><span data-stu-id="855d6-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="855d6-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="855d6-107">Attributes and Elements</span></span>

<span data-ttu-id="855d6-108">下列各節說明屬性、子專案和元素的父元素 `ItemSelectionCondition` 。</span><span class="sxs-lookup"><span data-stu-id="855d6-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="855d6-109">屬性</span><span class="sxs-lookup"><span data-stu-id="855d6-109">Attributes</span></span>

<span data-ttu-id="855d6-110">無。</span><span class="sxs-lookup"><span data-stu-id="855d6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="855d6-111">子元素</span><span class="sxs-lookup"><span data-stu-id="855d6-111">Child Elements</span></span>

|<span data-ttu-id="855d6-112">元素</span><span class="sxs-lookup"><span data-stu-id="855d6-112">Element</span></span>|<span data-ttu-id="855d6-113">描述</span><span class="sxs-lookup"><span data-stu-id="855d6-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="855d6-114">ListControl 之 ItemSelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="855d6-114">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="855d6-115">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="855d6-115">Optional element.</span></span><br /><br /> <span data-ttu-id="855d6-116">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="855d6-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="855d6-117">ListControl 之 ItemSelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="855d6-117">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="855d6-118">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="855d6-118">Optional element.</span></span><br /><br /> <span data-ttu-id="855d6-119">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="855d6-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="855d6-120">父項目</span><span class="sxs-lookup"><span data-stu-id="855d6-120">Parent Elements</span></span>

|<span data-ttu-id="855d6-121">元素</span><span class="sxs-lookup"><span data-stu-id="855d6-121">Element</span></span>|<span data-ttu-id="855d6-122">描述</span><span class="sxs-lookup"><span data-stu-id="855d6-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="855d6-123">ListControl 之 ListItems 的 ListItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="855d6-123">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="855d6-124">定義屬性或腳本，其值會顯示在清單視圖的資料列中。</span><span class="sxs-lookup"><span data-stu-id="855d6-124">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="855d6-125">備註</span><span class="sxs-lookup"><span data-stu-id="855d6-125">Remarks</span></span>

<span data-ttu-id="855d6-126">您可以為此條件指定一個屬性名稱或腳本，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="855d6-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="855d6-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="855d6-127">See Also</span></span>

[<span data-ttu-id="855d6-128">ListControl 之 ListItems 的 ListItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="855d6-128">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="855d6-129">ListControl 之 ItemSelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="855d6-129">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="855d6-130">ListControl 之 ItemSelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="855d6-130">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="855d6-131">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="855d6-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
