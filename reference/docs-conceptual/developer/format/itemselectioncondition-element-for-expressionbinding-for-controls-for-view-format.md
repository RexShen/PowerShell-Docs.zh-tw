---
title: View (Format) 的控制項之 ExpressionBinding 的 ItemSelectionCondition 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e8e3ea64fd947fbb2b98c410ac08533f386c9505
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781200"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="4802d-102">檢視之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4802d-102">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="4802d-103">定義必須存在才能使用此控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="4802d-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="4802d-104">定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="4802d-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="4802d-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) 控制項專案 (格式控制項的) 控制項專案 CustomControl， (格式控制項的控制項) CustomEntries 元素用於 view (針對 (格式的控制項，) CustomEntry 元素格式) CustomItem 專案的 CustomEntry for view (Format) ExpressionBinding 元素 for view (format) CustomItem 元素 for view 的控制項 (格式) </span><span class="sxs-lookup"><span data-stu-id="4802d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4802d-106">語法</span><span class="sxs-lookup"><span data-stu-id="4802d-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4802d-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4802d-107">Attributes and Elements</span></span>

<span data-ttu-id="4802d-108">下列各節說明屬性、子專案和元素的父元素 `ItemSelectionCondition` 。</span><span class="sxs-lookup"><span data-stu-id="4802d-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4802d-109">屬性</span><span class="sxs-lookup"><span data-stu-id="4802d-109">Attributes</span></span>

<span data-ttu-id="4802d-110">無。</span><span class="sxs-lookup"><span data-stu-id="4802d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4802d-111">子元素</span><span class="sxs-lookup"><span data-stu-id="4802d-111">Child Elements</span></span>

|<span data-ttu-id="4802d-112">元素</span><span class="sxs-lookup"><span data-stu-id="4802d-112">Element</span></span>|<span data-ttu-id="4802d-113">描述</span><span class="sxs-lookup"><span data-stu-id="4802d-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4802d-114">檢視之控制項的 ItemSelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4802d-114">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="4802d-115">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="4802d-115">Optional element.</span></span><br /><br /> <span data-ttu-id="4802d-116">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="4802d-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="4802d-117">檢視之控制項的 ItemSelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4802d-117">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="4802d-118">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="4802d-118">Optional element.</span></span><br /><br /> <span data-ttu-id="4802d-119">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="4802d-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4802d-120">父項目</span><span class="sxs-lookup"><span data-stu-id="4802d-120">Parent Elements</span></span>

|<span data-ttu-id="4802d-121">元素</span><span class="sxs-lookup"><span data-stu-id="4802d-121">Element</span></span>|<span data-ttu-id="4802d-122">描述</span><span class="sxs-lookup"><span data-stu-id="4802d-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4802d-123">檢視之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4802d-123">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="4802d-124">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="4802d-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4802d-125">備註</span><span class="sxs-lookup"><span data-stu-id="4802d-125">Remarks</span></span>

<span data-ttu-id="4802d-126">您可以為此條件指定一個屬性名稱或腳本，但不能同時指定這兩者。</span><span class="sxs-lookup"><span data-stu-id="4802d-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="4802d-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4802d-127">See Also</span></span>

[<span data-ttu-id="4802d-128">檢視之控制項的 ItemSelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4802d-128">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="4802d-129">檢視之控制項的 ItemSelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4802d-129">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="4802d-130">檢視之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4802d-130">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="4802d-131">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="4802d-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
