---
title: ItemSelectionCondition for CustomControl for View (Format) 的 ScriptBlock 元素Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 31873e886af04f8eedaf859af1d6bc1d5bcfdbf7
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772870"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="78a94-102">檢視之 CustomControl 的 ItemSelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="78a94-102">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="78a94-103">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="78a94-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="78a94-104">當此腳本評估為時 `true` ，會符合條件，並使用控制項。</span><span class="sxs-lookup"><span data-stu-id="78a94-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="78a94-105">定義自訂控制項視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="78a94-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="78a94-106">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) CustomControl 元素 (format) CustomEntries 元素 for CustomControl for view (format) CustomEntry 元素 for CustomEntries element for CustomEntry for View (格式) CustomItem for CustomControl for View 的 ExpressionBinding 元素 (Format) ItemSelectionCondition 元素用於 CustomControl for ItemSelectionCondition for view (格式) ScriptBlock 元素， (</span><span class="sxs-lookup"><span data-stu-id="78a94-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="78a94-107">語法</span><span class="sxs-lookup"><span data-stu-id="78a94-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="78a94-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="78a94-108">Attributes and Elements</span></span>

<span data-ttu-id="78a94-109">下列各節說明屬性、子專案和元素的父元素 `ScriptBlock` 。</span><span class="sxs-lookup"><span data-stu-id="78a94-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="78a94-110">屬性</span><span class="sxs-lookup"><span data-stu-id="78a94-110">Attributes</span></span>

<span data-ttu-id="78a94-111">無。</span><span class="sxs-lookup"><span data-stu-id="78a94-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="78a94-112">子元素</span><span class="sxs-lookup"><span data-stu-id="78a94-112">Child Elements</span></span>

<span data-ttu-id="78a94-113">無。</span><span class="sxs-lookup"><span data-stu-id="78a94-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="78a94-114">父項目</span><span class="sxs-lookup"><span data-stu-id="78a94-114">Parent Elements</span></span>

|<span data-ttu-id="78a94-115">元素</span><span class="sxs-lookup"><span data-stu-id="78a94-115">Element</span></span>|<span data-ttu-id="78a94-116">描述</span><span class="sxs-lookup"><span data-stu-id="78a94-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="78a94-117">CustomControl for View (格式之運算式系結的 ItemSelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="78a94-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="78a94-118">定義必須存在才能使用此控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="78a94-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="78a94-119">文字值</span><span class="sxs-lookup"><span data-stu-id="78a94-119">Text Value</span></span>

<span data-ttu-id="78a94-120">指定要評估的腳本。</span><span class="sxs-lookup"><span data-stu-id="78a94-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="78a94-121">備註</span><span class="sxs-lookup"><span data-stu-id="78a94-121">Remarks</span></span>

<span data-ttu-id="78a94-122">如果使用這個元素，則在定義選取條件時，不能指定[PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="78a94-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="78a94-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78a94-123">See Also</span></span>

[<span data-ttu-id="78a94-124">檢視之 CustomControl 的 ItemSelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="78a94-124">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="78a94-125">CustomControl for View (格式之運算式系結的 ItemSelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="78a94-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="78a94-126">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="78a94-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
