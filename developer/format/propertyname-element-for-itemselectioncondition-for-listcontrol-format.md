---
title: PropertyName ItemSelectionCondition 如 ListControl （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5e707ae-3c84-4ceb-ba31-56b3ffde6d6c
caps.latest.revision: 7
ms.openlocfilehash: b15e26e18126f69eee7c3a857f9a461d4bdf5848
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855534"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="e6f4b-102">ListControl 之 ItemSelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e6f4b-102">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="e6f4b-103">指定觸發條件的.NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="e6f4b-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="e6f4b-104">當這個屬性是存在，或當其評估結果為`true`、 符合條件，和在所用的檢視。</span><span class="sxs-lookup"><span data-stu-id="e6f4b-104">When this property is present or when it evaluates to `true`, the condition is met, and the view is used.</span></span> <span data-ttu-id="e6f4b-105">定義清單檢視時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="e6f4b-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="e6f4b-106">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） ListControl 項目 （格式） ListEntries 項目 （格式） ListEntry 項目如 ListControl （格式） 的 ListItem ListEntry ListControl （格式） ListItems 項目ListControl （格式） ItemSelectionCondition ListControls PropertyName 元素 ItemSelectionCondition ListControl （格式） 的 ListItem 元素 ListItems 的項目</span><span class="sxs-lookup"><span data-stu-id="e6f4b-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControls PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e6f4b-107">語法</span><span class="sxs-lookup"><span data-stu-id="e6f4b-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e6f4b-108">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="e6f4b-108">Attributes and Elements</span></span>

<span data-ttu-id="e6f4b-109">下列各節說明屬性、 子項目，以及的父項目`PropertyName`項目。</span><span class="sxs-lookup"><span data-stu-id="e6f4b-109">The following sections describe attributes, child elements, and the parent elements of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e6f4b-110">屬性</span><span class="sxs-lookup"><span data-stu-id="e6f4b-110">Attributes</span></span>

<span data-ttu-id="e6f4b-111">無。</span><span class="sxs-lookup"><span data-stu-id="e6f4b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e6f4b-112">子元素</span><span class="sxs-lookup"><span data-stu-id="e6f4b-112">Child Elements</span></span>

<span data-ttu-id="e6f4b-113">無。</span><span class="sxs-lookup"><span data-stu-id="e6f4b-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e6f4b-114">父元素</span><span class="sxs-lookup"><span data-stu-id="e6f4b-114">Parent Elements</span></span>

|<span data-ttu-id="e6f4b-115">元素</span><span class="sxs-lookup"><span data-stu-id="e6f4b-115">Element</span></span>|<span data-ttu-id="e6f4b-116">描述</span><span class="sxs-lookup"><span data-stu-id="e6f4b-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e6f4b-117">ItemSelectionCondition ListControl （格式） 的 ListItem 元素</span><span class="sxs-lookup"><span data-stu-id="e6f4b-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a><span data-ttu-id="e6f4b-118">文字值</span><span class="sxs-lookup"><span data-stu-id="e6f4b-118">Text Value</span></span>

<span data-ttu-id="e6f4b-119">指定其值會顯示屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="e6f4b-119">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="e6f4b-120">備註</span><span class="sxs-lookup"><span data-stu-id="e6f4b-120">Remarks</span></span>

<span data-ttu-id="e6f4b-121">如果會使用這個項目，您無法指定[ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)時定義的選取項目條件的項目。</span><span class="sxs-lookup"><span data-stu-id="e6f4b-121">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6f4b-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6f4b-122">See Also</span></span>

[<span data-ttu-id="e6f4b-123">ItemSelectionCondition ListIControl （格式） 的指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="e6f4b-123">ScriptBlock Element for ItemSelectionCondition for ListIControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="e6f4b-124">ItemSelectionCondition ListControl （格式） 的 ListItem 元素</span><span class="sxs-lookup"><span data-stu-id="e6f4b-124">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="e6f4b-125">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="e6f4b-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
