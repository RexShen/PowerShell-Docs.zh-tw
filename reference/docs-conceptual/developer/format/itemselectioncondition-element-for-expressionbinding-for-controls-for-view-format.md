---
title: View 之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82c15014-2440-410d-b02d-b7f1a49240a0
caps.latest.revision: 7
ms.openlocfilehash: 80f375c53c205c793600655fa6031d114871618e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362937"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="7cb5a-102">檢視之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7cb5a-102">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="7cb5a-103">定義必須存在才能使用此控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="7cb5a-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="7cb5a-104">定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="7cb5a-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="7cb5a-105">設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 專案（格式）控制項的控制項專案（格式） CustomControl 元素，用於控制項的 View （Format） CustomEntries 元素CustomControl for View （format） CustomEntry 元素 for CustomEntries for view （format） CustomItem 元素 for view （format） CustomEntry 元素 for view （format） ExpressionBinding 的控制項View 之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="7cb5a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7cb5a-106">語法</span><span class="sxs-lookup"><span data-stu-id="7cb5a-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7cb5a-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="7cb5a-107">Attributes and Elements</span></span>

<span data-ttu-id="7cb5a-108">下列各節說明屬性、子專案，以及 `ItemSelectionCondition` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="7cb5a-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7cb5a-109">屬性</span><span class="sxs-lookup"><span data-stu-id="7cb5a-109">Attributes</span></span>

<span data-ttu-id="7cb5a-110">無。</span><span class="sxs-lookup"><span data-stu-id="7cb5a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7cb5a-111">子元素</span><span class="sxs-lookup"><span data-stu-id="7cb5a-111">Child Elements</span></span>

|<span data-ttu-id="7cb5a-112">元素</span><span class="sxs-lookup"><span data-stu-id="7cb5a-112">Element</span></span>|<span data-ttu-id="7cb5a-113">描述</span><span class="sxs-lookup"><span data-stu-id="7cb5a-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7cb5a-114">View 之控制項的 ItemSelectionCondition 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="7cb5a-114">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="7cb5a-115">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="7cb5a-115">Optional element.</span></span><br /><br /> <span data-ttu-id="7cb5a-116">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="7cb5a-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="7cb5a-117">View 之控制項的 ItemSelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="7cb5a-117">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="7cb5a-118">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="7cb5a-118">Optional element.</span></span><br /><br /> <span data-ttu-id="7cb5a-119">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="7cb5a-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7cb5a-120">父元素</span><span class="sxs-lookup"><span data-stu-id="7cb5a-120">Parent Elements</span></span>

|<span data-ttu-id="7cb5a-121">元素</span><span class="sxs-lookup"><span data-stu-id="7cb5a-121">Element</span></span>|<span data-ttu-id="7cb5a-122">描述</span><span class="sxs-lookup"><span data-stu-id="7cb5a-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7cb5a-123">View 之控制項的 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="7cb5a-123">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="7cb5a-124">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="7cb5a-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7cb5a-125">備註</span><span class="sxs-lookup"><span data-stu-id="7cb5a-125">Remarks</span></span>

<span data-ttu-id="7cb5a-126">您可以為此條件指定一個屬性名稱或腳本，但不能同時指定這兩者。</span><span class="sxs-lookup"><span data-stu-id="7cb5a-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="7cb5a-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7cb5a-127">See Also</span></span>

[<span data-ttu-id="7cb5a-128">View 之控制項的 ItemSelectionCondition 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="7cb5a-128">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="7cb5a-129">View 之控制項的 ItemSelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="7cb5a-129">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="7cb5a-130">View 之控制項的 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="7cb5a-130">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="7cb5a-131">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="7cb5a-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
