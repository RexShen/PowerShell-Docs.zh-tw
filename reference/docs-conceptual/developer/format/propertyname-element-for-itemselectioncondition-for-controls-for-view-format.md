---
title: View (Format) 的控制項之 ItemSelectionCondition 的 PropertyName 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c6517b8f63e0511ce071926ac3ac39ba82e7ed21
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783478"
---
# <a name="propertyname-element-for-itemselectioncondition-for-controls-for-view-format"></a><span data-ttu-id="b5d13-102">檢視之控制項的 ItemSelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b5d13-102">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="b5d13-103">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="b5d13-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="b5d13-104">當這個屬性存在或評估為時 `true` ，就會符合條件，並使用控制項。</span><span class="sxs-lookup"><span data-stu-id="b5d13-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="b5d13-105">定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="b5d13-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="b5d13-106">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) 控制項專案 (格式控制項的) 控制項專案 CustomControl 格式 (CustomEntries 專案) 格式的控制項 (CustomEntry 元素的 CustomEntries 專案針對 View 的控制項 (格式) CustomItem 元素以用於 view (Format) ExpressionBinding 專案 CustomItem for view (format) ItemSelectionCondition 元素 for view (format) PropertyName 元素 for view (format) 的控制項的 ExpressionBinding 專案</span><span class="sxs-lookup"><span data-stu-id="b5d13-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format) PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b5d13-107">語法</span><span class="sxs-lookup"><span data-stu-id="b5d13-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b5d13-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b5d13-108">Attributes and Elements</span></span>

<span data-ttu-id="b5d13-109">下列各節說明屬性、子專案和元素的父元素 `PropertyName` 。</span><span class="sxs-lookup"><span data-stu-id="b5d13-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b5d13-110">屬性</span><span class="sxs-lookup"><span data-stu-id="b5d13-110">Attributes</span></span>

<span data-ttu-id="b5d13-111">無。</span><span class="sxs-lookup"><span data-stu-id="b5d13-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b5d13-112">子元素</span><span class="sxs-lookup"><span data-stu-id="b5d13-112">Child Elements</span></span>

<span data-ttu-id="b5d13-113">無。</span><span class="sxs-lookup"><span data-stu-id="b5d13-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b5d13-114">父項目</span><span class="sxs-lookup"><span data-stu-id="b5d13-114">Parent Elements</span></span>

|<span data-ttu-id="b5d13-115">元素</span><span class="sxs-lookup"><span data-stu-id="b5d13-115">Element</span></span>|<span data-ttu-id="b5d13-116">描述</span><span class="sxs-lookup"><span data-stu-id="b5d13-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b5d13-117">View (Format) 的控制項之 ExpressionBinding 的 ItemSelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="b5d13-117">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="b5d13-118">定義必須存在才能使用此控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="b5d13-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b5d13-119">文字值</span><span class="sxs-lookup"><span data-stu-id="b5d13-119">Text Value</span></span>

<span data-ttu-id="b5d13-120">指定觸發條件之 .NET 屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="b5d13-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="b5d13-121">備註</span><span class="sxs-lookup"><span data-stu-id="b5d13-121">Remarks</span></span>

<span data-ttu-id="b5d13-122">如果使用這個元素，則在定義選取條件時，不能指定[ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="b5d13-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5d13-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b5d13-123">See Also</span></span>

[<span data-ttu-id="b5d13-124">檢視之控制項的 ItemSelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b5d13-124">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="b5d13-125">View (Format) 的控制項之 ExpressionBinding 的 ItemSelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="b5d13-125">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="b5d13-126">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="b5d13-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
