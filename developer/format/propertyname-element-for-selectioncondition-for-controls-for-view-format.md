---
title: PropertyName SelectionCondition 用於檢視 （格式） 的控制項的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92c4237d-c2b2-4908-82ac-f36070f89d26
caps.latest.revision: 6
ms.openlocfilehash: 79859bed3d762948182e03babf71d4270278bae7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065014"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="299cb-102">檢視之控制項的 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="299cb-102">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="299cb-103">指定觸發條件的.NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="299cb-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="299cb-104">當這個屬性是存在，或當其評估結果為`true`、 符合條件，和使用的項目。</span><span class="sxs-lookup"><span data-stu-id="299cb-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="299cb-105">定義可供檢視的控制項時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="299cb-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="299cb-106">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） 項目 （格式） 控制項的 Controls 項目控制項的檢視 （格式） CustomEntries 項目控制項的控制項的檢視 （格式） CustomControl 項目CustomControl CustomEntries CustomEntry EntrySelectedBy 的檢視 （控制項的檢視 （格式） SelectionCondition 元素的控制項的檢視 （格式） EntrySelectedBy 元素的控制項的檢視 （格式） CustomEntry 元素的控制項用於檢視 （格式） 的控制項 SelectionCondition 的格式） PropertyName 項目</span><span class="sxs-lookup"><span data-stu-id="299cb-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="299cb-107">語法</span><span class="sxs-lookup"><span data-stu-id="299cb-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="299cb-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="299cb-108">Attributes and Elements</span></span>

<span data-ttu-id="299cb-109">下列各節說明屬性、 子項目和父項目`PropertyName`項目。</span><span class="sxs-lookup"><span data-stu-id="299cb-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="299cb-110">屬性</span><span class="sxs-lookup"><span data-stu-id="299cb-110">Attributes</span></span>

<span data-ttu-id="299cb-111">無。</span><span class="sxs-lookup"><span data-stu-id="299cb-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="299cb-112">子元素</span><span class="sxs-lookup"><span data-stu-id="299cb-112">Child Elements</span></span>

<span data-ttu-id="299cb-113">無。</span><span class="sxs-lookup"><span data-stu-id="299cb-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="299cb-114">父項目</span><span class="sxs-lookup"><span data-stu-id="299cb-114">Parent Elements</span></span>

|<span data-ttu-id="299cb-115">項目</span><span class="sxs-lookup"><span data-stu-id="299cb-115">Element</span></span>|<span data-ttu-id="299cb-116">描述</span><span class="sxs-lookup"><span data-stu-id="299cb-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="299cb-117">用於檢視 （格式） 的控制項 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="299cb-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="299cb-118">定義必須存在，要使用的控制項定義的條件。</span><span class="sxs-lookup"><span data-stu-id="299cb-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="299cb-119">文字值</span><span class="sxs-lookup"><span data-stu-id="299cb-119">Text Value</span></span>

<span data-ttu-id="299cb-120">指定.NET 屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="299cb-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="299cb-121">備註</span><span class="sxs-lookup"><span data-stu-id="299cb-121">Remarks</span></span>

<span data-ttu-id="299cb-122">選取條件必須指定至少一個屬性名稱或指令碼，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="299cb-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="299cb-123">如需如何使用選擇條件的詳細資訊，請參閱[定義的條件，顯示資料](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="299cb-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="299cb-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="299cb-124">See Also</span></span>

[<span data-ttu-id="299cb-125">用於檢視 （格式） 的控制項 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="299cb-125">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="299cb-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="299cb-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
