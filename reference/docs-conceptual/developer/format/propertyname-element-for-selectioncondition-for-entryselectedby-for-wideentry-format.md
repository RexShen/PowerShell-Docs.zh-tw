---
title: SelectionCondition for 之 entryselectedby for WideEntry (Format 的 PropertyName 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: ca2106dbbd8da345e71e83a3ead3cf7a1cb44cb4
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773108"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="b36c3-102">WideEntry 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b36c3-102">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="b36c3-103">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="b36c3-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="b36c3-104">當這個屬性存在或評估為時 `true` ，就會符合條件，並使用定義。</span><span class="sxs-lookup"><span data-stu-id="b36c3-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="b36c3-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) WideControl 專案 (格式) WideEntries 專案 (格式) WideEntry 專案 (格式) 之 entryselectedby 元素（WideEntry 的 SelectionCondition (format) 之 entryselectedby for WideEntry for SelectionCondition (格式) 的 PropertyName 元素）</span><span class="sxs-lookup"><span data-stu-id="b36c3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b36c3-106">語法</span><span class="sxs-lookup"><span data-stu-id="b36c3-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

```csharp

```

## <a name="attributes-and-elements"></a><span data-ttu-id="b36c3-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b36c3-107">Attributes and Elements</span></span>

<span data-ttu-id="b36c3-108">下列各節說明屬性、子專案和元素的父元素 `PropertyName` 。</span><span class="sxs-lookup"><span data-stu-id="b36c3-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b36c3-109">屬性</span><span class="sxs-lookup"><span data-stu-id="b36c3-109">Attributes</span></span>

<span data-ttu-id="b36c3-110">無。</span><span class="sxs-lookup"><span data-stu-id="b36c3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b36c3-111">子元素</span><span class="sxs-lookup"><span data-stu-id="b36c3-111">Child Elements</span></span>

<span data-ttu-id="b36c3-112">無。</span><span class="sxs-lookup"><span data-stu-id="b36c3-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b36c3-113">父項目</span><span class="sxs-lookup"><span data-stu-id="b36c3-113">Parent Elements</span></span>

|<span data-ttu-id="b36c3-114">元素</span><span class="sxs-lookup"><span data-stu-id="b36c3-114">Element</span></span>|<span data-ttu-id="b36c3-115">描述</span><span class="sxs-lookup"><span data-stu-id="b36c3-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b36c3-116">WideEntry (格式的之 entryselectedby 的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="b36c3-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="b36c3-117">定義必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="b36c3-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b36c3-118">文字值</span><span class="sxs-lookup"><span data-stu-id="b36c3-118">Text Value</span></span>

<span data-ttu-id="b36c3-119">指定 .NET 屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="b36c3-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="b36c3-120">備註</span><span class="sxs-lookup"><span data-stu-id="b36c3-120">Remarks</span></span>

<span data-ttu-id="b36c3-121">選取條件必須指定至少一個屬性名稱或要評估的腳本，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="b36c3-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="b36c3-122">如需如何使用選取條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="b36c3-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="b36c3-123">如需有關寬視圖之其他元件的詳細資訊，請參閱[Wide view](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="b36c3-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b36c3-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b36c3-124">See Also</span></span>

[<span data-ttu-id="b36c3-125">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="b36c3-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="b36c3-126">定義資料顯示時的條件</span><span class="sxs-lookup"><span data-stu-id="b36c3-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="b36c3-127">SelectionCondition for 之 entryselectedby for WideEntry (Format 的 ScriptBlock 元素) </span><span class="sxs-lookup"><span data-stu-id="b36c3-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="b36c3-128">WideEntry (格式的之 entryselectedby 的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="b36c3-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="b36c3-129">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="b36c3-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
