---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之 CustomControl 的 SelectionCondition 的 PropertyName 元素 (格式)
description: 檢視之 CustomControl 的 SelectionCondition 的 PropertyName 元素 (格式)
ms.openlocfilehash: 1dd325a58b29a0f13b1341559c2a7dfe251c6b36
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665850"
---
# <a name="propertyname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="5691f-103">檢視之 CustomControl 的 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5691f-103">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="5691f-104">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="5691f-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="5691f-105">當這個屬性存在或評估為時， `true` 就會符合條件，並使用定義。</span><span class="sxs-lookup"><span data-stu-id="5691f-105">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="5691f-106">定義自訂控制項視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="5691f-106">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="5691f-107">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (Format) CustomEntries (format) format (format) 元素 for CustomEntry for CustomEntries for CustomControl for CustomItem for for View (format) 元素若為 CustomEntry for CustomControl for View (Format) 之 entryselectedby 元素 for CustomEntry for CustomControl for View (Format) SelectionCondition 之 entryselectedby for CustomControl for SelectionCondition for view (Format) CustomControl for for View (Format 專案) </span><span class="sxs-lookup"><span data-stu-id="5691f-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5691f-108">語法</span><span class="sxs-lookup"><span data-stu-id="5691f-108">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5691f-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5691f-109">Attributes and Elements</span></span>

<span data-ttu-id="5691f-110">下列各節說明屬性、子專案和元素的父元素 `PropertyName` 。</span><span class="sxs-lookup"><span data-stu-id="5691f-110">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5691f-111">屬性</span><span class="sxs-lookup"><span data-stu-id="5691f-111">Attributes</span></span>

<span data-ttu-id="5691f-112">無。</span><span class="sxs-lookup"><span data-stu-id="5691f-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5691f-113">子元素</span><span class="sxs-lookup"><span data-stu-id="5691f-113">Child Elements</span></span>

<span data-ttu-id="5691f-114">無。</span><span class="sxs-lookup"><span data-stu-id="5691f-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5691f-115">父項目</span><span class="sxs-lookup"><span data-stu-id="5691f-115">Parent Elements</span></span>

|<span data-ttu-id="5691f-116">元素</span><span class="sxs-lookup"><span data-stu-id="5691f-116">Element</span></span>|<span data-ttu-id="5691f-117">描述</span><span class="sxs-lookup"><span data-stu-id="5691f-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5691f-118">適用于 CustomControl 的之 entryselectedby SelectionCondition 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="5691f-118">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="5691f-119">定義必須存在才能使用控制項定義的條件。</span><span class="sxs-lookup"><span data-stu-id="5691f-119">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5691f-120">文字值</span><span class="sxs-lookup"><span data-stu-id="5691f-120">Text Value</span></span>

<span data-ttu-id="5691f-121">指定 .NET 屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="5691f-121">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="5691f-122">備註</span><span class="sxs-lookup"><span data-stu-id="5691f-122">Remarks</span></span>

<span data-ttu-id="5691f-123">選取條件必須指定至少一個屬性名稱或腳本，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="5691f-123">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="5691f-124">如需如何使用選取條件的詳細資訊，請參閱 [定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="5691f-124">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5691f-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5691f-125">See Also</span></span>

[<span data-ttu-id="5691f-126">適用于 CustomControl 的之 entryselectedby SelectionCondition 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="5691f-126">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="5691f-127">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="5691f-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
