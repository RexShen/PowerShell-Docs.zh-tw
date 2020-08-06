---
title: GroupBy (格式的 ItemSelectionCondition 的 ScriptBlock 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 7738b180f328c7360275058cdb9dea01df6ea285
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787643"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="8095f-102">GroupBy 之 ItemSelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8095f-102">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="8095f-103">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="8095f-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="8095f-104">當此腳本評估為時 `true` ，會符合條件，並使用控制項。</span><span class="sxs-lookup"><span data-stu-id="8095f-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="8095f-105">此元素是在定義新物件群組的顯示方式時使用。</span><span class="sxs-lookup"><span data-stu-id="8095f-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="8095f-106">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy 元素的視圖 (格式) CustomEntries 專案的 groupby (格式) CustomEntry 元素用於 CustomControl 若為 GroupBy (格式) 適用于 GroupBy 的 CustomEntry 的 CustomItem 專案 (格式) CustomItem 的 ExpressionBinding 專案為 groupby (格式) ItemSelectionCondition 元素用於 groupby (格式的 ExpressionBinding) ScriptBlock 元素 (</span><span class="sxs-lookup"><span data-stu-id="8095f-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8095f-107">語法</span><span class="sxs-lookup"><span data-stu-id="8095f-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8095f-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8095f-108">Attributes and Elements</span></span>

<span data-ttu-id="8095f-109">下列各節說明屬性、子專案和元素的父元素 `ScriptBlock` 。</span><span class="sxs-lookup"><span data-stu-id="8095f-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8095f-110">屬性</span><span class="sxs-lookup"><span data-stu-id="8095f-110">Attributes</span></span>

<span data-ttu-id="8095f-111">無。</span><span class="sxs-lookup"><span data-stu-id="8095f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8095f-112">子元素</span><span class="sxs-lookup"><span data-stu-id="8095f-112">Child Elements</span></span>

<span data-ttu-id="8095f-113">無。</span><span class="sxs-lookup"><span data-stu-id="8095f-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8095f-114">父項目</span><span class="sxs-lookup"><span data-stu-id="8095f-114">Parent Elements</span></span>

|<span data-ttu-id="8095f-115">元素</span><span class="sxs-lookup"><span data-stu-id="8095f-115">Element</span></span>|<span data-ttu-id="8095f-116">描述</span><span class="sxs-lookup"><span data-stu-id="8095f-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8095f-117">GroupBy 之 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8095f-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="8095f-118">定義必須存在才能使用此控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="8095f-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8095f-119">文字值</span><span class="sxs-lookup"><span data-stu-id="8095f-119">Text Value</span></span>

<span data-ttu-id="8095f-120">指定要評估的腳本。</span><span class="sxs-lookup"><span data-stu-id="8095f-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="8095f-121">備註</span><span class="sxs-lookup"><span data-stu-id="8095f-121">Remarks</span></span>

<span data-ttu-id="8095f-122">如果使用這個元素，則在定義選取條件時，不能指定[PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="8095f-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="8095f-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8095f-123">See Also</span></span>

[<span data-ttu-id="8095f-124">GroupBy 之 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8095f-124">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="8095f-125">GroupBy 之 ItemSelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8095f-125">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="8095f-126">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="8095f-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
