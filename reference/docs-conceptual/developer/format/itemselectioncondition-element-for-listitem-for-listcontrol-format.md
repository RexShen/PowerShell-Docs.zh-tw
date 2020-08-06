---
title: ListControl (格式之專案的 ItemSelectionCondition 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: f5c388928668e03b96923130fb5849f637548f12
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783614"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="c366a-102">ListControl 之 ListItem 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c366a-102">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="c366a-103">定義必須存在才能使用此清單專案的條件。</span><span class="sxs-lookup"><span data-stu-id="c366a-103">Defines the condition that must exist for this list item to be used.</span></span>

<span data-ttu-id="c366a-104">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ListControl 專案 (格式) ListControl (格式) ListEntry 元素，ListEntries for ListControl (format) ListItems 元素用於 ListEntry 的 ListControl (format) ListItems 元素的 ListControl (format) </span><span class="sxs-lookup"><span data-stu-id="c366a-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c366a-105">語法</span><span class="sxs-lookup"><span data-stu-id="c366a-105">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c366a-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c366a-106">Attributes and Elements</span></span>

<span data-ttu-id="c366a-107">下列各節說明屬性、子專案和元素的父元素 `ItemSelectionCondition` 。</span><span class="sxs-lookup"><span data-stu-id="c366a-107">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c366a-108">屬性</span><span class="sxs-lookup"><span data-stu-id="c366a-108">Attributes</span></span>

<span data-ttu-id="c366a-109">無。</span><span class="sxs-lookup"><span data-stu-id="c366a-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c366a-110">子元素</span><span class="sxs-lookup"><span data-stu-id="c366a-110">Child Elements</span></span>

|<span data-ttu-id="c366a-111">元素</span><span class="sxs-lookup"><span data-stu-id="c366a-111">Element</span></span>|<span data-ttu-id="c366a-112">描述</span><span class="sxs-lookup"><span data-stu-id="c366a-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c366a-113">ListControl 之 ItemSelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c366a-113">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="c366a-114">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="c366a-114">Optional element.</span></span><br /><br /> <span data-ttu-id="c366a-115">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="c366a-115">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="c366a-116">ListControl 之 ItemSelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c366a-116">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="c366a-117">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="c366a-117">Optional element.</span></span><br /><br /> <span data-ttu-id="c366a-118">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="c366a-118">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c366a-119">父項目</span><span class="sxs-lookup"><span data-stu-id="c366a-119">Parent Elements</span></span>

|<span data-ttu-id="c366a-120">元素</span><span class="sxs-lookup"><span data-stu-id="c366a-120">Element</span></span>|<span data-ttu-id="c366a-121">描述</span><span class="sxs-lookup"><span data-stu-id="c366a-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c366a-122">ListControl 之 ListItems 的 ListItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c366a-122">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="c366a-123">定義屬性或腳本，其值會顯示在清單視圖的資料列中。</span><span class="sxs-lookup"><span data-stu-id="c366a-123">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c366a-124">備註</span><span class="sxs-lookup"><span data-stu-id="c366a-124">Remarks</span></span>

<span data-ttu-id="c366a-125">您可以為此條件指定一個屬性名稱或腳本，但不能同時指定這兩者。</span><span class="sxs-lookup"><span data-stu-id="c366a-125">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="c366a-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c366a-126">See Also</span></span>

[<span data-ttu-id="c366a-127">ListControl 之 ListItems 的 ListItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c366a-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="c366a-128">ListControl 之 ItemSelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c366a-128">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="c366a-129">ListControl 之 ItemSelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c366a-129">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="c366a-130">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="c366a-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
