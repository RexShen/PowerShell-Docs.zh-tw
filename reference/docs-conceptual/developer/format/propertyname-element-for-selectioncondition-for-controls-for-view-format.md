---
title: View 之控制項的 SelectionCondition 的 PropertyName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92c4237d-c2b2-4908-82ac-f36070f89d26
caps.latest.revision: 6
ms.openlocfilehash: 79859bed3d762948182e03babf71d4270278bae7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362357"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="592c9-102">檢視之控制項的 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="592c9-102">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="592c9-103">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="592c9-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="592c9-104">當這個屬性存在或評估為 `true`時，就會符合條件，並使用專案。</span><span class="sxs-lookup"><span data-stu-id="592c9-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="592c9-105">定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="592c9-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="592c9-106">設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 專案（格式）控制項的控制項專案（格式） CustomControl 元素，用於控制項的 View （Format） CustomEntries 元素CustomControl for view （format） CustomEntry 元素的 CustomEntries for view （format）之 entryselectedby 元素 for CustomEntry for view （format） SelectionCondition 元素 for controls 的控制項（格式）Format）控制項的 SelectionCondition 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="592c9-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="592c9-107">語法</span><span class="sxs-lookup"><span data-stu-id="592c9-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="592c9-108">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="592c9-108">Attributes and Elements</span></span>

<span data-ttu-id="592c9-109">下列各節說明屬性、子專案，以及 `PropertyName` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="592c9-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="592c9-110">屬性</span><span class="sxs-lookup"><span data-stu-id="592c9-110">Attributes</span></span>

<span data-ttu-id="592c9-111">無。</span><span class="sxs-lookup"><span data-stu-id="592c9-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="592c9-112">子元素</span><span class="sxs-lookup"><span data-stu-id="592c9-112">Child Elements</span></span>

<span data-ttu-id="592c9-113">無。</span><span class="sxs-lookup"><span data-stu-id="592c9-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="592c9-114">父元素</span><span class="sxs-lookup"><span data-stu-id="592c9-114">Parent Elements</span></span>

|<span data-ttu-id="592c9-115">元素</span><span class="sxs-lookup"><span data-stu-id="592c9-115">Element</span></span>|<span data-ttu-id="592c9-116">描述</span><span class="sxs-lookup"><span data-stu-id="592c9-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="592c9-117">View 之控制項的之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="592c9-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="592c9-118">定義必須存在的條件，才能使用控制項定義。</span><span class="sxs-lookup"><span data-stu-id="592c9-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="592c9-119">文字值</span><span class="sxs-lookup"><span data-stu-id="592c9-119">Text Value</span></span>

<span data-ttu-id="592c9-120">指定 .NET 屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="592c9-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="592c9-121">備註</span><span class="sxs-lookup"><span data-stu-id="592c9-121">Remarks</span></span>

<span data-ttu-id="592c9-122">選取條件必須指定至少一個屬性名稱或腳本，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="592c9-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="592c9-123">如需如何使用選取條件的詳細資訊，請參閱[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="592c9-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="592c9-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="592c9-124">See Also</span></span>

[<span data-ttu-id="592c9-125">View 之控制項的之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="592c9-125">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="592c9-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="592c9-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
