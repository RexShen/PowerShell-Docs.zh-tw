---
title: 設定 (格式) 之控制項的 SelectionCondition 的 PropertyName 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 7730951a840fcfcd8bf819fff5182049bd6b6c23
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773125"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="f2bce-102">設定之控制項的 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="f2bce-102">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="f2bce-103">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="f2bce-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="f2bce-104">當這個屬性存在或評估為時 `true` ，就會符合條件，並使用專案。</span><span class="sxs-lookup"><span data-stu-id="f2bce-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="f2bce-105">此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。</span><span class="sxs-lookup"><span data-stu-id="f2bce-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="f2bce-106">Configuration 元素 (格式) Controls 設定的控制項元素 (格式設定 (格式的控制項) 控制項專案，) 設定 (格式的 CustomControl 的 CustomEntries 元素) 格式 (CustomEntry 元素設定 (格式的控制項的 CustomControl) 之 entryselectedby 元素，用於 CustomEntry 的之 entryselectedby for CustomEntry for Configuration (Format) SelectionCondition 元素 (SelectionCondition for 之 entryselectedby for ListEntry 的) 格式 (</span><span class="sxs-lookup"><span data-stu-id="f2bce-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f2bce-107">語法</span><span class="sxs-lookup"><span data-stu-id="f2bce-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f2bce-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f2bce-108">Attributes and Elements</span></span>

<span data-ttu-id="f2bce-109">下列各節說明屬性、子專案和元素的父元素 `PropertyName` 。</span><span class="sxs-lookup"><span data-stu-id="f2bce-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f2bce-110">屬性</span><span class="sxs-lookup"><span data-stu-id="f2bce-110">Attributes</span></span>

<span data-ttu-id="f2bce-111">無。</span><span class="sxs-lookup"><span data-stu-id="f2bce-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f2bce-112">子元素</span><span class="sxs-lookup"><span data-stu-id="f2bce-112">Child Elements</span></span>

<span data-ttu-id="f2bce-113">無。</span><span class="sxs-lookup"><span data-stu-id="f2bce-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f2bce-114">父項目</span><span class="sxs-lookup"><span data-stu-id="f2bce-114">Parent Elements</span></span>

|<span data-ttu-id="f2bce-115">元素</span><span class="sxs-lookup"><span data-stu-id="f2bce-115">Element</span></span>|<span data-ttu-id="f2bce-116">描述</span><span class="sxs-lookup"><span data-stu-id="f2bce-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f2bce-117">設定之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="f2bce-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="f2bce-118">定義必須存在的條件，才能使用通用控制項定義。</span><span class="sxs-lookup"><span data-stu-id="f2bce-118">Defines a condition that must exist for a common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f2bce-119">文字值</span><span class="sxs-lookup"><span data-stu-id="f2bce-119">Text Value</span></span>

<span data-ttu-id="f2bce-120">指定 .NET 屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="f2bce-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="f2bce-121">備註</span><span class="sxs-lookup"><span data-stu-id="f2bce-121">Remarks</span></span>

<span data-ttu-id="f2bce-122">選取條件必須指定至少一個屬性名稱或腳本，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="f2bce-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="f2bce-123">如需如何使用選取條件的詳細資訊，請參閱[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="f2bce-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f2bce-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2bce-124">See Also</span></span>

[<span data-ttu-id="f2bce-125">設定之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="f2bce-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="f2bce-126">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="f2bce-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
