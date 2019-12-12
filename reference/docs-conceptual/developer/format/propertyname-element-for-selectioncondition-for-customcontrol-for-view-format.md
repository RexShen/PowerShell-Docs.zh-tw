---
title: SelectionCondition for CustomControl for View 的 PropertyName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc48a417-2083-46d4-ac38-16c12e65b6b9
caps.latest.revision: 7
ms.openlocfilehash: e08037d5d051d3be51e90193c7e87cc2e738f78a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362347"
---
# <a name="propertyname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="93d51-102">檢視之 CustomControl 的 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="93d51-102">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="93d51-103">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="93d51-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="93d51-104">當這個屬性存在或評估為 `true`時，就會符合條件，並使用定義。</span><span class="sxs-lookup"><span data-stu-id="93d51-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="93d51-105">定義自訂控制項視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="93d51-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="93d51-106">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） CustomControl 元素 for view （format） CustomEntries 元素 for CustomEntry for view （format） CustomEntries 元素Format） CustomItem 元素，用於 CustomControl for view （format） CustomEntry for CustomControl for view （format） SelectionCondition 元素之 entryselectedby for view （格式） PropertyNameCustomControl for View 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="93d51-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="93d51-107">語法</span><span class="sxs-lookup"><span data-stu-id="93d51-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="93d51-108">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="93d51-108">Attributes and Elements</span></span>

<span data-ttu-id="93d51-109">下列各節說明屬性、子專案，以及 `PropertyName` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="93d51-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="93d51-110">屬性</span><span class="sxs-lookup"><span data-stu-id="93d51-110">Attributes</span></span>

<span data-ttu-id="93d51-111">無。</span><span class="sxs-lookup"><span data-stu-id="93d51-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="93d51-112">子元素</span><span class="sxs-lookup"><span data-stu-id="93d51-112">Child Elements</span></span>

<span data-ttu-id="93d51-113">無。</span><span class="sxs-lookup"><span data-stu-id="93d51-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="93d51-114">父元素</span><span class="sxs-lookup"><span data-stu-id="93d51-114">Parent Elements</span></span>

|<span data-ttu-id="93d51-115">元素</span><span class="sxs-lookup"><span data-stu-id="93d51-115">Element</span></span>|<span data-ttu-id="93d51-116">描述</span><span class="sxs-lookup"><span data-stu-id="93d51-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="93d51-117">CustomControl for View 的之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="93d51-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="93d51-118">定義必須存在的條件，才能使用控制項定義。</span><span class="sxs-lookup"><span data-stu-id="93d51-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="93d51-119">文字值</span><span class="sxs-lookup"><span data-stu-id="93d51-119">Text Value</span></span>

<span data-ttu-id="93d51-120">指定 .NET 屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="93d51-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="93d51-121">備註</span><span class="sxs-lookup"><span data-stu-id="93d51-121">Remarks</span></span>

<span data-ttu-id="93d51-122">選取條件必須指定至少一個屬性名稱或腳本，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="93d51-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="93d51-123">如需如何使用選取條件的詳細資訊，請參閱[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="93d51-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="93d51-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93d51-124">See Also</span></span>

[<span data-ttu-id="93d51-125">CustomControl for View 的之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="93d51-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="93d51-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="93d51-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
