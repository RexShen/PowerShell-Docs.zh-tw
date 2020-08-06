---
title: SelectionCondition for 之 entryselectedby 的 ScriptBlock 元素，用於 GroupBy (格式) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e70e1555a8f2fe0d15d3e864d80d35527af81b03
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785382"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="dba96-102">GroupBy 之 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="dba96-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="dba96-103">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="dba96-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="dba96-104">當此腳本評估為時 `true` ，會符合條件，並使用定義。</span><span class="sxs-lookup"><span data-stu-id="dba96-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="dba96-105">此元素是在定義新物件群組的顯示方式時使用。</span><span class="sxs-lookup"><span data-stu-id="dba96-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="dba96-106">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (Format) GroupBy 元素以取得 (格式) CustomEntries 專案（適用于 groupby (format）) CustomEntry 元素（適用于 CustomControl 的 groupby (格式) 之 entryselectedby 元素，適用于 groupby (格式的 CustomEntry) ScriptBlock 元素） (</span><span class="sxs-lookup"><span data-stu-id="dba96-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dba96-107">語法</span><span class="sxs-lookup"><span data-stu-id="dba96-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dba96-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="dba96-108">Attributes and Elements</span></span>

<span data-ttu-id="dba96-109">下列各節說明屬性、子專案和元素的父元素 `ScriptBlock` 。</span><span class="sxs-lookup"><span data-stu-id="dba96-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dba96-110">屬性</span><span class="sxs-lookup"><span data-stu-id="dba96-110">Attributes</span></span>

<span data-ttu-id="dba96-111">無。</span><span class="sxs-lookup"><span data-stu-id="dba96-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dba96-112">子元素</span><span class="sxs-lookup"><span data-stu-id="dba96-112">Child Elements</span></span>

<span data-ttu-id="dba96-113">無。</span><span class="sxs-lookup"><span data-stu-id="dba96-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="dba96-114">父項目</span><span class="sxs-lookup"><span data-stu-id="dba96-114">Parent Elements</span></span>

|<span data-ttu-id="dba96-115">元素</span><span class="sxs-lookup"><span data-stu-id="dba96-115">Element</span></span>|<span data-ttu-id="dba96-116">描述</span><span class="sxs-lookup"><span data-stu-id="dba96-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dba96-117">GroupBy 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="dba96-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="dba96-118">定義必須存在的條件，才能使用控制項定義。</span><span class="sxs-lookup"><span data-stu-id="dba96-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="dba96-119">文字值</span><span class="sxs-lookup"><span data-stu-id="dba96-119">Text Value</span></span>

<span data-ttu-id="dba96-120">指定要評估的腳本。</span><span class="sxs-lookup"><span data-stu-id="dba96-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="dba96-121">備註</span><span class="sxs-lookup"><span data-stu-id="dba96-121">Remarks</span></span>

<span data-ttu-id="dba96-122">選取條件必須指定至少一個要評估的腳本或屬性名稱，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="dba96-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="dba96-123">如需如何使用選取條件的詳細資訊，請參閱[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="dba96-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dba96-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dba96-124">See Also</span></span>

[<span data-ttu-id="dba96-125">GroupBy 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="dba96-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="dba96-126">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="dba96-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
