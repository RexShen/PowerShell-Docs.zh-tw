---
title: 適用于 ExpressionBinding 之 GroupBy (格式的 ItemSelectionCondition 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a9b74f1882efc578f7d9ab27b8cd2f8a52833ab8
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773431"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="90234-102">GroupBy 之 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="90234-102">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="90234-103">定義必須存在才能使用此控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="90234-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="90234-104">可以針對控制項專案指定的選取條件數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="90234-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="90234-105">此元素是在定義新物件群組的顯示方式時使用。</span><span class="sxs-lookup"><span data-stu-id="90234-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="90234-106">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (Format) GroupBy 元素以取得 (格式) CustomEntries 專案（適用于 groupby (format）) CustomEntry 元素（適用于 CustomControl 的 groupby (格式) CustomItem 元素，適用于 groupby (格式的 CustomEntry) ExpressionBinding 專案 (]</span><span class="sxs-lookup"><span data-stu-id="90234-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="90234-107">語法</span><span class="sxs-lookup"><span data-stu-id="90234-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="90234-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="90234-108">Attributes and Elements</span></span>

<span data-ttu-id="90234-109">下列各節說明屬性、子專案和元素的父元素 `ItemSelectionCondition` 。</span><span class="sxs-lookup"><span data-stu-id="90234-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="90234-110">屬性</span><span class="sxs-lookup"><span data-stu-id="90234-110">Attributes</span></span>

<span data-ttu-id="90234-111">無。</span><span class="sxs-lookup"><span data-stu-id="90234-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="90234-112">子元素</span><span class="sxs-lookup"><span data-stu-id="90234-112">Child Elements</span></span>

|<span data-ttu-id="90234-113">元素</span><span class="sxs-lookup"><span data-stu-id="90234-113">Element</span></span>|<span data-ttu-id="90234-114">描述</span><span class="sxs-lookup"><span data-stu-id="90234-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="90234-115">GroupBy 之 ItemSelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="90234-115">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="90234-116">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="90234-116">Optional element.</span></span><br /><br /> <span data-ttu-id="90234-117">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="90234-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="90234-118">GroupBy 之 ItemSelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="90234-118">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="90234-119">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="90234-119">Optional element.</span></span><br /><br /> <span data-ttu-id="90234-120">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="90234-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="90234-121">父項目</span><span class="sxs-lookup"><span data-stu-id="90234-121">Parent Elements</span></span>

|<span data-ttu-id="90234-122">元素</span><span class="sxs-lookup"><span data-stu-id="90234-122">Element</span></span>|<span data-ttu-id="90234-123">描述</span><span class="sxs-lookup"><span data-stu-id="90234-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="90234-124">GroupBy 之 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="90234-124">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="90234-125">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="90234-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="90234-126">備註</span><span class="sxs-lookup"><span data-stu-id="90234-126">Remarks</span></span>

<span data-ttu-id="90234-127">您可以為此條件指定一個屬性名稱或腳本，但不能同時指定這兩者。</span><span class="sxs-lookup"><span data-stu-id="90234-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="90234-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90234-128">See Also</span></span>

[<span data-ttu-id="90234-129">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="90234-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="90234-130">GroupBy 之 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="90234-130">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)
