---
title: ListItems ListControl （格式） 的 ListItem 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f96f4f5-8bd5-43ed-95e7-a7358115999a
caps.latest.revision: 11
ms.openlocfilehash: 1e0a1b2d20853650328b8cfd1513a08f7e167cd6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065762"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a><span data-ttu-id="c84f1-102">ListControl 之 ListItems 的 ListItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c84f1-102">ListItem Element for ListItems for ListControl (Format)</span></span>

<span data-ttu-id="c84f1-103">定義屬性或其值會顯示 [清單] 檢視的資料列中的指令碼。</span><span class="sxs-lookup"><span data-stu-id="c84f1-103">Defines the property or script whose value is displayed in a row of the list view.</span></span>

<span data-ttu-id="c84f1-104">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） ListControl 項目 （格式） ListEntries ListControl （格式） ListEntry 元素元素 ListControl （格式） 的 ListControl （格式） ListItems 元素ListItem ListControl 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="c84f1-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem for ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c84f1-105">語法</span><span class="sxs-lookup"><span data-stu-id="c84f1-105">Syntax</span></span>

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c84f1-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c84f1-106">Attributes and Elements</span></span>

<span data-ttu-id="c84f1-107">下列各節說明屬性、 子項目和父項目`ListItem`項目。</span><span class="sxs-lookup"><span data-stu-id="c84f1-107">The following sections describe the attributes, child elements, and parent element of the `ListItem` element.</span></span> <span data-ttu-id="c84f1-108">可以指定只有一個屬性或指令碼。</span><span class="sxs-lookup"><span data-stu-id="c84f1-108">Only one property or script can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="c84f1-109">屬性</span><span class="sxs-lookup"><span data-stu-id="c84f1-109">Attributes</span></span>

<span data-ttu-id="c84f1-110">無</span><span class="sxs-lookup"><span data-stu-id="c84f1-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="c84f1-111">子元素</span><span class="sxs-lookup"><span data-stu-id="c84f1-111">Child Elements</span></span>

|<span data-ttu-id="c84f1-112">元素</span><span class="sxs-lookup"><span data-stu-id="c84f1-112">Element</span></span>|<span data-ttu-id="c84f1-113">描述</span><span class="sxs-lookup"><span data-stu-id="c84f1-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c84f1-114">ListControl （格式） 的 ListItem 的 FormatString 元素</span><span class="sxs-lookup"><span data-stu-id="c84f1-114">FormatString Element for ListItem for ListControl (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="c84f1-115">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="c84f1-115">Optional element.</span></span><br /><br /> <span data-ttu-id="c84f1-116">指定的格式字串，定義的屬性或指令碼的值的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="c84f1-116">Specifies a format string that defines how the property or script value is displayed.</span></span>|
|[<span data-ttu-id="c84f1-117">ItemSelectionCondition ListControl （格式） 的 ListItem 元素</span><span class="sxs-lookup"><span data-stu-id="c84f1-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="c84f1-118">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="c84f1-118">Optional element.</span></span><br /><br /> <span data-ttu-id="c84f1-119">定義要使用此清單項目必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="c84f1-119">Defines the condition that must exist for this list item to be used.</span></span>|
|[<span data-ttu-id="c84f1-120">ListControl （格式） 的 ListItem label 項目</span><span class="sxs-lookup"><span data-stu-id="c84f1-120">Label Element for ListItem for ListControl (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="c84f1-121">選擇性的項目</span><span class="sxs-lookup"><span data-stu-id="c84f1-121">Optional element</span></span><br /><br /> <span data-ttu-id="c84f1-122">指定顯示屬性或指令碼中值的資料列左邊的標籤。</span><span class="sxs-lookup"><span data-stu-id="c84f1-122">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>|
|[<span data-ttu-id="c84f1-123">PropertyName ListControl （格式） 的 ListItem 元素</span><span class="sxs-lookup"><span data-stu-id="c84f1-123">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="c84f1-124">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="c84f1-124">Optional element.</span></span><br /><br /> <span data-ttu-id="c84f1-125">指定其值會顯示資料列中的.NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="c84f1-125">Specifies the .NET property whose value is displayed in the row.</span></span>|
|[<span data-ttu-id="c84f1-126">ScriptBlock ListControl （格式） 的 ListItem 元素</span><span class="sxs-lookup"><span data-stu-id="c84f1-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="c84f1-127">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="c84f1-127">Optional element.</span></span><br /><br /> <span data-ttu-id="c84f1-128">指定資料列中顯示其值的指令碼。</span><span class="sxs-lookup"><span data-stu-id="c84f1-128">Specifies the script whose value is displayed in the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c84f1-129">父項目</span><span class="sxs-lookup"><span data-stu-id="c84f1-129">Parent Elements</span></span>

|<span data-ttu-id="c84f1-130">項目</span><span class="sxs-lookup"><span data-stu-id="c84f1-130">Element</span></span>|<span data-ttu-id="c84f1-131">描述</span><span class="sxs-lookup"><span data-stu-id="c84f1-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c84f1-132">清單控制項 （格式） 的 ListItems 項目</span><span class="sxs-lookup"><span data-stu-id="c84f1-132">ListItems Element for List Control (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="c84f1-133">定義屬性和其值會顯示在清單檢視中的指令碼。</span><span class="sxs-lookup"><span data-stu-id="c84f1-133">Defines the properties and scripts whose values are displayed in the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c84f1-134">備註</span><span class="sxs-lookup"><span data-stu-id="c84f1-134">Remarks</span></span>

<span data-ttu-id="c84f1-135">清單檢視元件的相關資訊，請參閱[建立清單檢視](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="c84f1-135">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c84f1-136">範例</span><span class="sxs-lookup"><span data-stu-id="c84f1-136">Example</span></span>

<span data-ttu-id="c84f1-137">這個範例示範定義清單檢視的三個資料列的 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="c84f1-137">This example shows the XML elements that define three rows of the list view.</span></span> <span data-ttu-id="c84f1-138">前兩個資料列顯示值的.NET 屬性，以及最後一個資料列會顯示指令碼所產生的值。</span><span class="sxs-lookup"><span data-stu-id="c84f1-138">The first two rows display the value of a .NET property, and the last row displays a value generated by a script.</span></span>

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>DotNetProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>DotNetProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
    </ListItems>
</ListEntry>

```

## <a name="see-also"></a><span data-ttu-id="c84f1-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c84f1-139">See Also</span></span>

[<span data-ttu-id="c84f1-140">ListItems 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="c84f1-140">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="c84f1-141">ListItem （格式） 的 FormatString 元素</span><span class="sxs-lookup"><span data-stu-id="c84f1-141">FormatString Element for ListItem (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="c84f1-142">ListItem （格式） 的 label 項目</span><span class="sxs-lookup"><span data-stu-id="c84f1-142">Label Element for ListItem (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="c84f1-143">ListItem （格式） 的屬性名稱項目</span><span class="sxs-lookup"><span data-stu-id="c84f1-143">PropertyName Element for ListItem (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="c84f1-144">ListItem （格式） 的指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="c84f1-144">ScriptBlock Element for ListItem (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="c84f1-145">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="c84f1-145">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="c84f1-146">撰寫 Windows PowerShell 格式和類型的檔案</span><span class="sxs-lookup"><span data-stu-id="c84f1-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
