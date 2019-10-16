---
title: CustomControl for View 的 ItemSelectionCondition 的 ScriptBlock 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 946cd2b5-ac37-4a13-bb49-29fbc70ec8d7
caps.latest.revision: 6
ms.openlocfilehash: 0c07ab0e5d04c4056a7e7215bfa55773bfccb41d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362067"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="6c7ae-102">檢視之 CustomControl 的 ItemSelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="6c7ae-102">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="6c7ae-103">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="6c7ae-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="6c7ae-104">當此腳本評估為 `true` 時，就會符合條件，並使用控制項。</span><span class="sxs-lookup"><span data-stu-id="6c7ae-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="6c7ae-105">定義自訂控制項視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="6c7ae-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="6c7ae-106">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） CustomControl 元素（format） CustomEntries 元素，用於 CustomEntry for View （Format） CustomEntries 元素的 CustomControl for view （format） CustomItem 元素CustomEntry for view （Format） ExpressionBinding 元素 for CustomControl for view （format） ItemSelectionCondition 元素 for CustomControl for View （Format） ScriptBlock 元素CustomControl for View （格式）</span><span class="sxs-lookup"><span data-stu-id="6c7ae-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6c7ae-107">語法</span><span class="sxs-lookup"><span data-stu-id="6c7ae-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6c7ae-108">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="6c7ae-108">Attributes and Elements</span></span>

<span data-ttu-id="6c7ae-109">下列各節說明屬性、子專案，以及 `ScriptBlock` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="6c7ae-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6c7ae-110">屬性</span><span class="sxs-lookup"><span data-stu-id="6c7ae-110">Attributes</span></span>

<span data-ttu-id="6c7ae-111">無。</span><span class="sxs-lookup"><span data-stu-id="6c7ae-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6c7ae-112">子元素</span><span class="sxs-lookup"><span data-stu-id="6c7ae-112">Child Elements</span></span>

<span data-ttu-id="6c7ae-113">無。</span><span class="sxs-lookup"><span data-stu-id="6c7ae-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6c7ae-114">父元素</span><span class="sxs-lookup"><span data-stu-id="6c7ae-114">Parent Elements</span></span>

|<span data-ttu-id="6c7ae-115">元素</span><span class="sxs-lookup"><span data-stu-id="6c7ae-115">Element</span></span>|<span data-ttu-id="6c7ae-116">描述</span><span class="sxs-lookup"><span data-stu-id="6c7ae-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6c7ae-117">CustomControl for View 的運算式系結的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6c7ae-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="6c7ae-118">定義必須存在才能使用此控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="6c7ae-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6c7ae-119">文字值</span><span class="sxs-lookup"><span data-stu-id="6c7ae-119">Text Value</span></span>

<span data-ttu-id="6c7ae-120">指定要評估的腳本。</span><span class="sxs-lookup"><span data-stu-id="6c7ae-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="6c7ae-121">備註</span><span class="sxs-lookup"><span data-stu-id="6c7ae-121">Remarks</span></span>

<span data-ttu-id="6c7ae-122">如果使用這個元素，則在定義選取條件時，不能指定[PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="6c7ae-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="6c7ae-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c7ae-123">See Also</span></span>

[<span data-ttu-id="6c7ae-124">ItemSelectionCondition for CustomControl for View 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6c7ae-124">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="6c7ae-125">CustomControl for View 的運算式系結的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6c7ae-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="6c7ae-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="6c7ae-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
