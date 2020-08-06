---
title: 設定 (格式) 之控制項的 Itemselectioncondition 的 PropertyName 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0e304af1dbe816753d6dcd1dd8149f950f2a0941
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785586"
---
# <a name="propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="22560-102">設定之控制項的 ItemSelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="22560-102">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="22560-103">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="22560-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="22560-104">當這個屬性存在或評估為時 `true` ，就會符合條件，並使用控制項。</span><span class="sxs-lookup"><span data-stu-id="22560-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="22560-105">此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。</span><span class="sxs-lookup"><span data-stu-id="22560-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="22560-106">Configuration 專案 (格式) Controls 設定的控制項元素 (格式設定的控制項) 控制項專案 (格式) 設定 (格式的 CustomControl 的 CustomEntries 元素) 格式 (CustomEntry 元素適用于 CustomControl 的控制項設定 (格式) CustomItem 元素，用於 CustomEntry 的 Configuration ExpressionBinding 專案的 CustomItem for 控制項設定 (格式) ItemSelectionCondition 元素（針對設定 (格式的控制項) PropertyName 元素） (</span><span class="sxs-lookup"><span data-stu-id="22560-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="22560-107">語法</span><span class="sxs-lookup"><span data-stu-id="22560-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="22560-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="22560-108">Attributes and Elements</span></span>

<span data-ttu-id="22560-109">下列各節說明屬性、子專案和元素的父元素 `PropertyName` 。</span><span class="sxs-lookup"><span data-stu-id="22560-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="22560-110">屬性</span><span class="sxs-lookup"><span data-stu-id="22560-110">Attributes</span></span>

<span data-ttu-id="22560-111">無。</span><span class="sxs-lookup"><span data-stu-id="22560-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="22560-112">子元素</span><span class="sxs-lookup"><span data-stu-id="22560-112">Child Elements</span></span>

<span data-ttu-id="22560-113">無。</span><span class="sxs-lookup"><span data-stu-id="22560-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="22560-114">父項目</span><span class="sxs-lookup"><span data-stu-id="22560-114">Parent Elements</span></span>

|<span data-ttu-id="22560-115">元素</span><span class="sxs-lookup"><span data-stu-id="22560-115">Element</span></span>|<span data-ttu-id="22560-116">描述</span><span class="sxs-lookup"><span data-stu-id="22560-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="22560-117">設定之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="22560-117">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="22560-118">定義必須存在才能使用此控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="22560-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="22560-119">文字值</span><span class="sxs-lookup"><span data-stu-id="22560-119">Text Value</span></span>

<span data-ttu-id="22560-120">指定觸發條件之 .NET 屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="22560-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="22560-121">備註</span><span class="sxs-lookup"><span data-stu-id="22560-121">Remarks</span></span>

<span data-ttu-id="22560-122">如果使用這個元素，則在定義選取條件時，不能指定[ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="22560-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="22560-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22560-123">See Also</span></span>

[<span data-ttu-id="22560-124">設定之控制項的 ItemSelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="22560-124">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="22560-125">設定之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="22560-125">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="22560-126">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="22560-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
