---
title: View 之控制項的 ItemSelectionCondition 的 PropertyName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3955bc-f3a1-4ef6-86ac-80ffc133ad1b
caps.latest.revision: 6
ms.openlocfilehash: 28ad31be4be7be20f1f43ea1b69ad5d294de86f6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362477"
---
# <a name="propertyname-element-for-itemselectioncondition-for-controls-for-view-format"></a><span data-ttu-id="667cc-102">檢視之控制項的 ItemSelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="667cc-102">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="667cc-103">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="667cc-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="667cc-104">當這個屬性存在或評估為 `true`時，就會符合條件，並使用控制項。</span><span class="sxs-lookup"><span data-stu-id="667cc-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="667cc-105">定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="667cc-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="667cc-106">設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 專案（格式）控制項的控制項專案（格式） CustomControl 元素，用於控制項的 View （Format） CustomEntries 元素CustomControl for View （format） CustomEntry 元素 for CustomEntries for view （format） CustomItem 元素 for view （format） CustomEntry 元素 for view （format） ExpressionBinding 的控制項ExpressionBinding 的 ItemSelectionCondition 元素，用於 ItemSelectionCondition 的 view （Format） PropertyName 元素，用於 View 的控制項（格式）</span><span class="sxs-lookup"><span data-stu-id="667cc-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format) PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="667cc-107">語法</span><span class="sxs-lookup"><span data-stu-id="667cc-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="667cc-108">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="667cc-108">Attributes and Elements</span></span>

<span data-ttu-id="667cc-109">下列各節說明屬性、子專案，以及 `PropertyName` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="667cc-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="667cc-110">屬性</span><span class="sxs-lookup"><span data-stu-id="667cc-110">Attributes</span></span>

<span data-ttu-id="667cc-111">無。</span><span class="sxs-lookup"><span data-stu-id="667cc-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="667cc-112">子元素</span><span class="sxs-lookup"><span data-stu-id="667cc-112">Child Elements</span></span>

<span data-ttu-id="667cc-113">無。</span><span class="sxs-lookup"><span data-stu-id="667cc-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="667cc-114">父元素</span><span class="sxs-lookup"><span data-stu-id="667cc-114">Parent Elements</span></span>

|<span data-ttu-id="667cc-115">元素</span><span class="sxs-lookup"><span data-stu-id="667cc-115">Element</span></span>|<span data-ttu-id="667cc-116">描述</span><span class="sxs-lookup"><span data-stu-id="667cc-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="667cc-117">View 之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="667cc-117">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="667cc-118">定義必須存在才能使用此控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="667cc-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="667cc-119">文字值</span><span class="sxs-lookup"><span data-stu-id="667cc-119">Text Value</span></span>

<span data-ttu-id="667cc-120">指定觸發條件之 .NET 屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="667cc-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="667cc-121">備註</span><span class="sxs-lookup"><span data-stu-id="667cc-121">Remarks</span></span>

<span data-ttu-id="667cc-122">如果使用這個元素，則在定義選取條件時，不能指定[ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="667cc-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="667cc-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="667cc-123">See Also</span></span>

[<span data-ttu-id="667cc-124">View 之控制項的 ItemSelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="667cc-124">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="667cc-125">View 之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="667cc-125">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="667cc-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="667cc-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
