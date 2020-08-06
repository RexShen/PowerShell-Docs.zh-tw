---
title: ItemSelectionCondition for ListControl (格式的 PropertyName 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 8bdbb05326f7ff5ccffa46215631a5c954080dc1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780860"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="d95bd-102">ListControl 之 ItemSelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d95bd-102">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="d95bd-103">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="d95bd-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="d95bd-104">當這個屬性存在或評估為時 `true` ，就會符合條件，並使用此視圖。</span><span class="sxs-lookup"><span data-stu-id="d95bd-104">When this property is present or when it evaluates to `true`, the condition is met, and the view is used.</span></span> <span data-ttu-id="d95bd-105">定義清單視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="d95bd-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="d95bd-106">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ListControl 專案 (格式) ListEntries 專案 (格式) ListControl (格式) ListItems 專案（ListEntry 的 ListControl 的 ListItems 專案 (格式) ListControl 元素，ItemSelectionCondition 的 ListControls 的 PropertyName 元素 (格式 ItemSelectionCondition) </span><span class="sxs-lookup"><span data-stu-id="d95bd-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControls PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d95bd-107">語法</span><span class="sxs-lookup"><span data-stu-id="d95bd-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d95bd-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d95bd-108">Attributes and Elements</span></span>

<span data-ttu-id="d95bd-109">下列各節說明屬性、子專案和元素的父元素 `PropertyName` 。</span><span class="sxs-lookup"><span data-stu-id="d95bd-109">The following sections describe attributes, child elements, and the parent elements of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d95bd-110">屬性</span><span class="sxs-lookup"><span data-stu-id="d95bd-110">Attributes</span></span>

<span data-ttu-id="d95bd-111">無。</span><span class="sxs-lookup"><span data-stu-id="d95bd-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d95bd-112">子元素</span><span class="sxs-lookup"><span data-stu-id="d95bd-112">Child Elements</span></span>

<span data-ttu-id="d95bd-113">無。</span><span class="sxs-lookup"><span data-stu-id="d95bd-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d95bd-114">父項目</span><span class="sxs-lookup"><span data-stu-id="d95bd-114">Parent Elements</span></span>

|<span data-ttu-id="d95bd-115">元素</span><span class="sxs-lookup"><span data-stu-id="d95bd-115">Element</span></span>|<span data-ttu-id="d95bd-116">描述</span><span class="sxs-lookup"><span data-stu-id="d95bd-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d95bd-117">ListControl 之 ListItem 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d95bd-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a><span data-ttu-id="d95bd-118">文字值</span><span class="sxs-lookup"><span data-stu-id="d95bd-118">Text Value</span></span>

<span data-ttu-id="d95bd-119">指定顯示其值的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="d95bd-119">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="d95bd-120">備註</span><span class="sxs-lookup"><span data-stu-id="d95bd-120">Remarks</span></span>

<span data-ttu-id="d95bd-121">如果使用這個元素，則在定義選取條件時，不能指定[ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="d95bd-121">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="d95bd-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d95bd-122">See Also</span></span>

[<span data-ttu-id="d95bd-123">ItemSelectionCondition for ListIControl (格式的 ScriptBlock 元素) </span><span class="sxs-lookup"><span data-stu-id="d95bd-123">ScriptBlock Element for ItemSelectionCondition for ListIControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="d95bd-124">ListControl 之 ListItem 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d95bd-124">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="d95bd-125">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="d95bd-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
