---
title: ItemSelectionCondition for ListControl (格式的 ScriptBlock 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 38dc952bfadd6aed24bae8cbef05adcd22e61dd4
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787626"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="64938-102">ListControl 之 ItemSelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="64938-102">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="64938-103">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="64938-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="64938-104">當此腳本評估為時 `true` ，會符合條件，且會使用清單專案。</span><span class="sxs-lookup"><span data-stu-id="64938-104">When this script is evaluated to `true`, the condition is met, and the list item is used.</span></span> <span data-ttu-id="64938-105">定義清單視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="64938-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="64938-106">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ListControl 元素 (格式) ListEntry for ListEntries 的 ListControl 專案的 ListControl (format) ListItems 元素（ListEntry for ListControl (format) ListItems 專案 for ItemSelectionCondition for ListControl (format) ScriptBlock 元素 for ItemSelectionCondition 的 ListControl (format) </span><span class="sxs-lookup"><span data-stu-id="64938-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for List Control (Format) ItemSelectionCondition Element for ListItem for ListControl (Format) ScriptBlock Element for ItemSelectionCondition for ListControl  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="64938-107">語法</span><span class="sxs-lookup"><span data-stu-id="64938-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="64938-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="64938-108">Attributes and Elements</span></span>

<span data-ttu-id="64938-109">下列各節說明屬性、子專案和元素的父元素 `ScriptBlock` 。</span><span class="sxs-lookup"><span data-stu-id="64938-109">The following sections describe attributes, child elements, and the parent elements of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="64938-110">屬性</span><span class="sxs-lookup"><span data-stu-id="64938-110">Attributes</span></span>

<span data-ttu-id="64938-111">無。</span><span class="sxs-lookup"><span data-stu-id="64938-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="64938-112">子元素</span><span class="sxs-lookup"><span data-stu-id="64938-112">Child Elements</span></span>

<span data-ttu-id="64938-113">無。</span><span class="sxs-lookup"><span data-stu-id="64938-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="64938-114">父項目</span><span class="sxs-lookup"><span data-stu-id="64938-114">Parent Elements</span></span>

|<span data-ttu-id="64938-115">元素</span><span class="sxs-lookup"><span data-stu-id="64938-115">Element</span></span>|<span data-ttu-id="64938-116">描述</span><span class="sxs-lookup"><span data-stu-id="64938-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="64938-117">ListControl 之 ListItem 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="64938-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="64938-118">定義必須存在才能使用此清單專案的條件。</span><span class="sxs-lookup"><span data-stu-id="64938-118">Defines the condition that must exist for this list item to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="64938-119">文字值</span><span class="sxs-lookup"><span data-stu-id="64938-119">Text Value</span></span>

<span data-ttu-id="64938-120">指定要評估的腳本。</span><span class="sxs-lookup"><span data-stu-id="64938-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="64938-121">備註</span><span class="sxs-lookup"><span data-stu-id="64938-121">Remarks</span></span>

<span data-ttu-id="64938-122">如果使用這個元素，則在 `PropertyName` 定義選取條件時，不能指定元素。</span><span class="sxs-lookup"><span data-stu-id="64938-122">If this element is used, you cannot specify the `PropertyName` element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="64938-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64938-123">See Also</span></span>

[<span data-ttu-id="64938-124">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="64938-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
