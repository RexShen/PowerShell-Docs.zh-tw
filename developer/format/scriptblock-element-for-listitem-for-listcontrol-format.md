---
title: ScriptBlock ListControl （格式） 的 ListItem 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74e30938-00ef-46fd-84e5-f0a83706a50e
caps.latest.revision: 11
ms.openlocfilehash: 76b600256af3f957f7fe0578f9fef810262aa5d5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064572"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="7c58e-102">ListControl 之 ListItem 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7c58e-102">ScriptBlock Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="7c58e-103">指定資料列中顯示其值的指令碼。</span><span class="sxs-lookup"><span data-stu-id="7c58e-103">Specifies the script whose value is displayed in the row.</span></span>

<span data-ttu-id="7c58e-104">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） ListControl 項目 （格式） ListEntries 項目 ListEntry ListControl （格式） ListItems 元素 ListEntries ListControl （格式） ListEntry 項目ListControl （格式） ScriptBlock ListControl （格式） 的 ListItem 元素 ListItems ListControl （格式） ListItem 元素</span><span class="sxs-lookup"><span data-stu-id="7c58e-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ScriptBlock Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7c58e-105">語法</span><span class="sxs-lookup"><span data-stu-id="7c58e-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7c58e-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7c58e-106">Attributes and Elements</span></span>

<span data-ttu-id="7c58e-107">下列各節說明屬性、 子項目和父項目`ScriptBlock`項目。</span><span class="sxs-lookup"><span data-stu-id="7c58e-107">The following sections describe the attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7c58e-108">屬性</span><span class="sxs-lookup"><span data-stu-id="7c58e-108">Attributes</span></span>

<span data-ttu-id="7c58e-109">無。</span><span class="sxs-lookup"><span data-stu-id="7c58e-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7c58e-110">子元素</span><span class="sxs-lookup"><span data-stu-id="7c58e-110">Child Elements</span></span>

<span data-ttu-id="7c58e-111">無。</span><span class="sxs-lookup"><span data-stu-id="7c58e-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7c58e-112">父項目</span><span class="sxs-lookup"><span data-stu-id="7c58e-112">Parent Elements</span></span>

|<span data-ttu-id="7c58e-113">項目</span><span class="sxs-lookup"><span data-stu-id="7c58e-113">Element</span></span>|<span data-ttu-id="7c58e-114">描述</span><span class="sxs-lookup"><span data-stu-id="7c58e-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7c58e-115">ListItem 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="7c58e-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="7c58e-116">定義屬性或其值會顯示 [清單] 檢視的資料列中的指令碼。</span><span class="sxs-lookup"><span data-stu-id="7c58e-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7c58e-117">文字值</span><span class="sxs-lookup"><span data-stu-id="7c58e-117">Text Value</span></span>

<span data-ttu-id="7c58e-118">指定資料列中顯示其值的指令碼。</span><span class="sxs-lookup"><span data-stu-id="7c58e-118">Specify the script whose value is displayed in the row.</span></span>

## <a name="remarks"></a><span data-ttu-id="7c58e-119">備註</span><span class="sxs-lookup"><span data-stu-id="7c58e-119">Remarks</span></span>

<span data-ttu-id="7c58e-120">當指定這個項目時，您無法指定[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)項目。</span><span class="sxs-lookup"><span data-stu-id="7c58e-120">When this element is specified, you cannot specify the [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="7c58e-121">如需指定清單檢視中的指令碼的詳細資訊，請參閱[清單檢視](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="7c58e-121">For more information about specifying scripts in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="7c58e-122">範例</span><span class="sxs-lookup"><span data-stu-id="7c58e-122">Example</span></span>

<span data-ttu-id="7c58e-123">下列範例示範如何指定其值會顯示其屬性。</span><span class="sxs-lookup"><span data-stu-id="7c58e-123">The following example shows how to specify the property whose value is displayed.</span></span>

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="7c58e-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c58e-124">See Also</span></span>

[<span data-ttu-id="7c58e-125">PropertyName ListControl （格式） 的 ListItem 元素</span><span class="sxs-lookup"><span data-stu-id="7c58e-125">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="7c58e-126">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="7c58e-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="7c58e-127">ListItems ListControl （格式） 的 ListItem 項目</span><span class="sxs-lookup"><span data-stu-id="7c58e-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="7c58e-128">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="7c58e-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
