---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl 之 ItemSelectionCondition 的 PropertyName 元素 (格式)
description: ListControl 之 ItemSelectionCondition 的 PropertyName 元素 (格式)
ms.openlocfilehash: c515efe70afdb1c1186c0a07fe1f52dc49ad57b9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665986"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="47977-103">ListControl 之 ItemSelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="47977-103">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="47977-104">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="47977-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="47977-105">當這個屬性存在或評估為時， `true` 就會符合條件，並使用 view。</span><span class="sxs-lookup"><span data-stu-id="47977-105">When this property is present or when it evaluates to `true`, the condition is met, and the view is used.</span></span> <span data-ttu-id="47977-106">定義清單視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="47977-106">This element is used when defining a list view.</span></span>

<span data-ttu-id="47977-107">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) ListControl 元素 (format) ListEntries 專案 (format) ListEntry (格式) ListControl 專案的 ListItems (格式) ListEntry 專案的 ListControl (格式) ListItems 專案 ListControl 的 ItemSelectionCondition 屬性 (格式) </span><span class="sxs-lookup"><span data-stu-id="47977-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControls PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="47977-108">語法</span><span class="sxs-lookup"><span data-stu-id="47977-108">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="47977-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="47977-109">Attributes and Elements</span></span>

<span data-ttu-id="47977-110">下列各節說明屬性、子專案和元素的父元素 `PropertyName` 。</span><span class="sxs-lookup"><span data-stu-id="47977-110">The following sections describe attributes, child elements, and the parent elements of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="47977-111">屬性</span><span class="sxs-lookup"><span data-stu-id="47977-111">Attributes</span></span>

<span data-ttu-id="47977-112">無。</span><span class="sxs-lookup"><span data-stu-id="47977-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="47977-113">子元素</span><span class="sxs-lookup"><span data-stu-id="47977-113">Child Elements</span></span>

<span data-ttu-id="47977-114">無。</span><span class="sxs-lookup"><span data-stu-id="47977-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="47977-115">父項目</span><span class="sxs-lookup"><span data-stu-id="47977-115">Parent Elements</span></span>

|<span data-ttu-id="47977-116">元素</span><span class="sxs-lookup"><span data-stu-id="47977-116">Element</span></span>|<span data-ttu-id="47977-117">描述</span><span class="sxs-lookup"><span data-stu-id="47977-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="47977-118">ListControl 之 ListItem 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="47977-118">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a><span data-ttu-id="47977-119">文字值</span><span class="sxs-lookup"><span data-stu-id="47977-119">Text Value</span></span>

<span data-ttu-id="47977-120">指定顯示其值的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="47977-120">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="47977-121">備註</span><span class="sxs-lookup"><span data-stu-id="47977-121">Remarks</span></span>

<span data-ttu-id="47977-122">如果使用此元素，則在定義選取條件時，不能指定 [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="47977-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="47977-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47977-123">See Also</span></span>

[<span data-ttu-id="47977-124">適用于 ListIControl 的 ItemSelectionCondition 的 ScriptBlock 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="47977-124">ScriptBlock Element for ItemSelectionCondition for ListIControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="47977-125">ListControl 之 ListItem 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="47977-125">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="47977-126">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="47977-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
