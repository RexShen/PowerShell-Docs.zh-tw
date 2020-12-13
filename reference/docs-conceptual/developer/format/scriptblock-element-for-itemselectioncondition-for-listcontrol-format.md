---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl 之 ItemSelectionCondition 的 ScriptBlock 元素 (格式)
description: ListControl 之 ItemSelectionCondition 的 ScriptBlock 元素 (格式)
ms.openlocfilehash: 1e518f898e0e1e62ca64f9897b1323cc6dd89ae9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665061"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="487ad-103">ListControl 之 ItemSelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="487ad-103">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="487ad-104">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="487ad-104">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="487ad-105">當此腳本評估為時 `true` ，就會符合條件，並且會使用清單專案。</span><span class="sxs-lookup"><span data-stu-id="487ad-105">When this script is evaluated to `true`, the condition is met, and the list item is used.</span></span> <span data-ttu-id="487ad-106">定義清單視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="487ad-106">This element is used when defining a list view.</span></span>

<span data-ttu-id="487ad-107">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) ListControl 元素 (format) ListEntries 元素 for ListControl (Format) ListEntry 專案 for ListEntries for ListControl (format) ListItems for ListEntry for ListControl 的 ListItems 專案 (格式) ItemSelectionCondition 的 ListControl 專案 (格式) ItemSelectionCondition 專案的 ListControl (格式) 元素 (</span><span class="sxs-lookup"><span data-stu-id="487ad-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for List Control (Format) ItemSelectionCondition Element for ListItem for ListControl (Format) ScriptBlock Element for ItemSelectionCondition for ListControl  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="487ad-108">語法</span><span class="sxs-lookup"><span data-stu-id="487ad-108">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="487ad-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="487ad-109">Attributes and Elements</span></span>

<span data-ttu-id="487ad-110">下列各節說明屬性、子專案和元素的父元素 `ScriptBlock` 。</span><span class="sxs-lookup"><span data-stu-id="487ad-110">The following sections describe attributes, child elements, and the parent elements of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="487ad-111">屬性</span><span class="sxs-lookup"><span data-stu-id="487ad-111">Attributes</span></span>

<span data-ttu-id="487ad-112">無。</span><span class="sxs-lookup"><span data-stu-id="487ad-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="487ad-113">子元素</span><span class="sxs-lookup"><span data-stu-id="487ad-113">Child Elements</span></span>

<span data-ttu-id="487ad-114">無。</span><span class="sxs-lookup"><span data-stu-id="487ad-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="487ad-115">父項目</span><span class="sxs-lookup"><span data-stu-id="487ad-115">Parent Elements</span></span>

|<span data-ttu-id="487ad-116">元素</span><span class="sxs-lookup"><span data-stu-id="487ad-116">Element</span></span>|<span data-ttu-id="487ad-117">描述</span><span class="sxs-lookup"><span data-stu-id="487ad-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="487ad-118">ListControl 之 ListItem 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="487ad-118">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="487ad-119">定義必須存在才能使用此清單專案的條件。</span><span class="sxs-lookup"><span data-stu-id="487ad-119">Defines the condition that must exist for this list item to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="487ad-120">文字值</span><span class="sxs-lookup"><span data-stu-id="487ad-120">Text Value</span></span>

<span data-ttu-id="487ad-121">指定要評估的腳本。</span><span class="sxs-lookup"><span data-stu-id="487ad-121">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="487ad-122">備註</span><span class="sxs-lookup"><span data-stu-id="487ad-122">Remarks</span></span>

<span data-ttu-id="487ad-123">如果使用此元素，則在 `PropertyName` 定義選取條件時，不能指定元素。</span><span class="sxs-lookup"><span data-stu-id="487ad-123">If this element is used, you cannot specify the `PropertyName` element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="487ad-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="487ad-124">See Also</span></span>

[<span data-ttu-id="487ad-125">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="487ad-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
