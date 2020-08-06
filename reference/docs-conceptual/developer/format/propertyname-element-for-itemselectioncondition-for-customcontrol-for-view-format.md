---
title: ItemSelectionCondition for CustomControl for View (格式的 PropertyName 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0131fa86be4be4daec1d9d24b50397fb8529f050
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785569"
---
# <a name="propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="7f3d5-102">檢視之 CustomControl 的 ItemSelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7f3d5-102">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="7f3d5-103">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="7f3d5-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="7f3d5-104">當這個屬性存在或評估為時 `true` ，就會符合條件，並使用控制項。</span><span class="sxs-lookup"><span data-stu-id="7f3d5-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="7f3d5-105">定義自訂控制項視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="7f3d5-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="7f3d5-106">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) CustomControl 元素 (format) CustomEntries 元素 for CustomControl for view (format) CustomEntry 元素 for CustomEntries element for CustomEntry for View (格式) ExpressionBinding 元素用於 CustomItem 的 CustomControl for view (格式) ItemSelectionCondition 元素用於 CustomControl for ItemSelectionCondition for view (格式) PropertyName 元素</span><span class="sxs-lookup"><span data-stu-id="7f3d5-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>

## <a name="syntax"></a><span data-ttu-id="7f3d5-107">語法</span><span class="sxs-lookup"><span data-stu-id="7f3d5-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7f3d5-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7f3d5-108">Attributes and Elements</span></span>

<span data-ttu-id="7f3d5-109">下列各節說明屬性、子專案和元素的父元素 `PropertyName` 。</span><span class="sxs-lookup"><span data-stu-id="7f3d5-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7f3d5-110">屬性</span><span class="sxs-lookup"><span data-stu-id="7f3d5-110">Attributes</span></span>

<span data-ttu-id="7f3d5-111">無。</span><span class="sxs-lookup"><span data-stu-id="7f3d5-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7f3d5-112">子元素</span><span class="sxs-lookup"><span data-stu-id="7f3d5-112">Child Elements</span></span>

<span data-ttu-id="7f3d5-113">無。</span><span class="sxs-lookup"><span data-stu-id="7f3d5-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7f3d5-114">父項目</span><span class="sxs-lookup"><span data-stu-id="7f3d5-114">Parent Elements</span></span>

|<span data-ttu-id="7f3d5-115">元素</span><span class="sxs-lookup"><span data-stu-id="7f3d5-115">Element</span></span>|<span data-ttu-id="7f3d5-116">描述</span><span class="sxs-lookup"><span data-stu-id="7f3d5-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7f3d5-117">CustomControl for View (格式之運算式系結的 ItemSelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="7f3d5-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="7f3d5-118">定義必須存在才能使用此控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="7f3d5-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7f3d5-119">文字值</span><span class="sxs-lookup"><span data-stu-id="7f3d5-119">Text Value</span></span>

<span data-ttu-id="7f3d5-120">指定觸發條件之 .NET 屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="7f3d5-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="7f3d5-121">備註</span><span class="sxs-lookup"><span data-stu-id="7f3d5-121">Remarks</span></span>

<span data-ttu-id="7f3d5-122">如果使用這個元素，則在定義選取條件時，不能指定[ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="7f3d5-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="7f3d5-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f3d5-123">See Also</span></span>

[<span data-ttu-id="7f3d5-124">檢視之 CustomControl 的 ItemSelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7f3d5-124">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="7f3d5-125">CustomControl for View (格式之運算式系結的 ItemSelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="7f3d5-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="7f3d5-126">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="7f3d5-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
