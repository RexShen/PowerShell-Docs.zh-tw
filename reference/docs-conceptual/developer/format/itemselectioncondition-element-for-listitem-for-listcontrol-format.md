---
title: ListControl 之專案的 ItemSelectionCondition 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2668aea-37e9-4753-a4e9-7980ae5ec2eb
caps.latest.revision: 10
ms.openlocfilehash: 6bc0ccbcc5bd62429f63ed220da66dc66f44f7ca
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365187"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="5e62b-102">ListControl 之 ListItem 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5e62b-102">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="5e62b-103">定義必須存在才能使用此清單專案的條件。</span><span class="sxs-lookup"><span data-stu-id="5e62b-103">Defines the condition that must exist for this list item to be used.</span></span>

<span data-ttu-id="5e62b-104">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） ListControl 元素（format） ListEntries 元素（適用于 ListEntry 的 ListEntries for ListControl （Format） ListItems 元素） ListControl （Format） ListEntry 元素適用于 ListItems 之 ListControl （Format） ItemSelectionCondition 元素的 ListControl （格式）專案專案，適用于 ListControl 的專案（格式）</span><span class="sxs-lookup"><span data-stu-id="5e62b-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5e62b-105">語法</span><span class="sxs-lookup"><span data-stu-id="5e62b-105">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5e62b-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="5e62b-106">Attributes and Elements</span></span>

<span data-ttu-id="5e62b-107">下列各節說明屬性、子專案，以及 `ItemSelectionCondition` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="5e62b-107">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5e62b-108">屬性</span><span class="sxs-lookup"><span data-stu-id="5e62b-108">Attributes</span></span>

<span data-ttu-id="5e62b-109">無。</span><span class="sxs-lookup"><span data-stu-id="5e62b-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5e62b-110">子元素</span><span class="sxs-lookup"><span data-stu-id="5e62b-110">Child Elements</span></span>

|<span data-ttu-id="5e62b-111">元素</span><span class="sxs-lookup"><span data-stu-id="5e62b-111">Element</span></span>|<span data-ttu-id="5e62b-112">描述</span><span class="sxs-lookup"><span data-stu-id="5e62b-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5e62b-113">ListControl 之 ItemSelectionCondition 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5e62b-113">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="5e62b-114">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="5e62b-114">Optional element.</span></span><br /><br /> <span data-ttu-id="5e62b-115">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="5e62b-115">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="5e62b-116">ListControl 之 ItemSelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5e62b-116">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="5e62b-117">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="5e62b-117">Optional element.</span></span><br /><br /> <span data-ttu-id="5e62b-118">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="5e62b-118">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5e62b-119">父元素</span><span class="sxs-lookup"><span data-stu-id="5e62b-119">Parent Elements</span></span>

|<span data-ttu-id="5e62b-120">元素</span><span class="sxs-lookup"><span data-stu-id="5e62b-120">Element</span></span>|<span data-ttu-id="5e62b-121">描述</span><span class="sxs-lookup"><span data-stu-id="5e62b-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5e62b-122">適用于 ListControl 之 ListItems 的專案專案元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5e62b-122">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="5e62b-123">定義屬性或腳本，其值會顯示在清單視圖的資料列中。</span><span class="sxs-lookup"><span data-stu-id="5e62b-123">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5e62b-124">備註</span><span class="sxs-lookup"><span data-stu-id="5e62b-124">Remarks</span></span>

<span data-ttu-id="5e62b-125">您可以為此條件指定一個屬性名稱或腳本，但不能同時指定這兩者。</span><span class="sxs-lookup"><span data-stu-id="5e62b-125">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="5e62b-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e62b-126">See Also</span></span>

[<span data-ttu-id="5e62b-127">適用于 ListControl 之 ListItems 的專案專案元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5e62b-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="5e62b-128">ListControl 之 ItemSelectionCondition 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5e62b-128">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="5e62b-129">ListControl 之 ItemSelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5e62b-129">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="5e62b-130">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="5e62b-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
