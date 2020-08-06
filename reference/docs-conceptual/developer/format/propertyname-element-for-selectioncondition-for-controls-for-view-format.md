---
title: View (Format) 的控制項之 SelectionCondition 的 PropertyName 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 251fc129896cfa4a6255330e23854b014675ac5f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780809"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="a4101-102">檢視之控制項的 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a4101-102">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="a4101-103">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="a4101-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="a4101-104">當這個屬性存在或評估為時 `true` ，就會符合條件，並使用專案。</span><span class="sxs-lookup"><span data-stu-id="a4101-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="a4101-105">定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="a4101-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="a4101-106">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) 控制項專案 (格式控制項的) 控制項專案 CustomControl 格式 (CustomEntries 元素用於 view 的控制項)  ( (格式) 的控制項適用于 CustomEntries 的 CustomEntry 元素，用於 view (Format) 之 entryselectedby 專案 CustomEntry for view (format) SelectionCondition 元素 for 之 entryselectedby for view (format) 格式控制項</span><span class="sxs-lookup"><span data-stu-id="a4101-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a4101-107">語法</span><span class="sxs-lookup"><span data-stu-id="a4101-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a4101-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a4101-108">Attributes and Elements</span></span>

<span data-ttu-id="a4101-109">下列各節說明屬性、子專案和元素的父元素 `PropertyName` 。</span><span class="sxs-lookup"><span data-stu-id="a4101-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a4101-110">屬性</span><span class="sxs-lookup"><span data-stu-id="a4101-110">Attributes</span></span>

<span data-ttu-id="a4101-111">無。</span><span class="sxs-lookup"><span data-stu-id="a4101-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a4101-112">子元素</span><span class="sxs-lookup"><span data-stu-id="a4101-112">Child Elements</span></span>

<span data-ttu-id="a4101-113">無。</span><span class="sxs-lookup"><span data-stu-id="a4101-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a4101-114">父項目</span><span class="sxs-lookup"><span data-stu-id="a4101-114">Parent Elements</span></span>

|<span data-ttu-id="a4101-115">元素</span><span class="sxs-lookup"><span data-stu-id="a4101-115">Element</span></span>|<span data-ttu-id="a4101-116">描述</span><span class="sxs-lookup"><span data-stu-id="a4101-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a4101-117">檢視之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a4101-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="a4101-118">定義必須存在的條件，才能使用控制項定義。</span><span class="sxs-lookup"><span data-stu-id="a4101-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a4101-119">文字值</span><span class="sxs-lookup"><span data-stu-id="a4101-119">Text Value</span></span>

<span data-ttu-id="a4101-120">指定 .NET 屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="a4101-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="a4101-121">備註</span><span class="sxs-lookup"><span data-stu-id="a4101-121">Remarks</span></span>

<span data-ttu-id="a4101-122">選取條件必須指定至少一個屬性名稱或腳本，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="a4101-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="a4101-123">如需如何使用選取條件的詳細資訊，請參閱[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="a4101-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a4101-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4101-124">See Also</span></span>

[<span data-ttu-id="a4101-125">檢視之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a4101-125">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="a4101-126">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="a4101-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
