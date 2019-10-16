---
title: ListControl 之 ItemSelectionCondition 的 PropertyName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5e707ae-3c84-4ceb-ba31-56b3ffde6d6c
caps.latest.revision: 7
ms.openlocfilehash: b15e26e18126f69eee7c3a857f9a461d4bdf5848
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362387"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="3a10d-102">ListControl 之 ItemSelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="3a10d-102">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="3a10d-103">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="3a10d-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="3a10d-104">當這個屬性存在或評估為 `true` 時，就會符合條件，並使用此視圖。</span><span class="sxs-lookup"><span data-stu-id="3a10d-104">When this property is present or when it evaluates to `true`, the condition is met, and the view is used.</span></span> <span data-ttu-id="3a10d-105">定義清單視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="3a10d-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="3a10d-106">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） ListControl 專案（格式） ListEntries 元素（格式） ListEntry 元素（用於 ListControl 的 ListItems （格式） ListEntry 元素）ListItems for ListControl （Format） ItemSelectionCondition 元素的元素，適用于 ItemSelectionCondition for ListControl 的 ListControls PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="3a10d-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControls PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3a10d-107">語法</span><span class="sxs-lookup"><span data-stu-id="3a10d-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3a10d-108">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="3a10d-108">Attributes and Elements</span></span>

<span data-ttu-id="3a10d-109">下列各節說明屬性、子專案，以及 `PropertyName` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="3a10d-109">The following sections describe attributes, child elements, and the parent elements of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3a10d-110">屬性</span><span class="sxs-lookup"><span data-stu-id="3a10d-110">Attributes</span></span>

<span data-ttu-id="3a10d-111">無。</span><span class="sxs-lookup"><span data-stu-id="3a10d-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3a10d-112">子元素</span><span class="sxs-lookup"><span data-stu-id="3a10d-112">Child Elements</span></span>

<span data-ttu-id="3a10d-113">無。</span><span class="sxs-lookup"><span data-stu-id="3a10d-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3a10d-114">父元素</span><span class="sxs-lookup"><span data-stu-id="3a10d-114">Parent Elements</span></span>

|<span data-ttu-id="3a10d-115">元素</span><span class="sxs-lookup"><span data-stu-id="3a10d-115">Element</span></span>|<span data-ttu-id="3a10d-116">描述</span><span class="sxs-lookup"><span data-stu-id="3a10d-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3a10d-117">ListControl 之專案的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="3a10d-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a><span data-ttu-id="3a10d-118">文字值</span><span class="sxs-lookup"><span data-stu-id="3a10d-118">Text Value</span></span>

<span data-ttu-id="3a10d-119">指定顯示其值的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="3a10d-119">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="3a10d-120">備註</span><span class="sxs-lookup"><span data-stu-id="3a10d-120">Remarks</span></span>

<span data-ttu-id="3a10d-121">如果使用這個元素，則在定義選取條件時，不能指定[ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="3a10d-121">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="3a10d-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a10d-122">See Also</span></span>

[<span data-ttu-id="3a10d-123">ListIControl 之 ItemSelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="3a10d-123">ScriptBlock Element for ItemSelectionCondition for ListIControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="3a10d-124">ListControl 之專案的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="3a10d-124">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="3a10d-125">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="3a10d-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
