---
title: 適用于 ListControl 之 ListItems 的專案2元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f96f4f5-8bd5-43ed-95e7-a7358115999a
caps.latest.revision: 11
ms.openlocfilehash: 1e0a1b2d20853650328b8cfd1513a08f7e167cd6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365127"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a><span data-ttu-id="d3716-102">ListControl 之 ListItems 的 ListItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d3716-102">ListItem Element for ListItems for ListControl (Format)</span></span>

<span data-ttu-id="d3716-103">定義屬性或腳本，其值會顯示在清單視圖的資料列中。</span><span class="sxs-lookup"><span data-stu-id="d3716-103">Defines the property or script whose value is displayed in a row of the list view.</span></span>

<span data-ttu-id="d3716-104">ListEntry （格式） ListControl 元素的 ListControl （format） ListItems 元素的設定元素（格式） ViewDefinitions 元素（格式） ListEntries 元素（格式）ListControl 元素的專案（格式）</span><span class="sxs-lookup"><span data-stu-id="d3716-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem for ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d3716-105">語法</span><span class="sxs-lookup"><span data-stu-id="d3716-105">Syntax</span></span>

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d3716-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="d3716-106">Attributes and Elements</span></span>

<span data-ttu-id="d3716-107">下列各節描述 `ListItem` 專案的屬性、子專案和父項目。</span><span class="sxs-lookup"><span data-stu-id="d3716-107">The following sections describe the attributes, child elements, and parent element of the `ListItem` element.</span></span> <span data-ttu-id="d3716-108">只能指定一個屬性或腳本。</span><span class="sxs-lookup"><span data-stu-id="d3716-108">Only one property or script can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="d3716-109">屬性</span><span class="sxs-lookup"><span data-stu-id="d3716-109">Attributes</span></span>

<span data-ttu-id="d3716-110">無</span><span class="sxs-lookup"><span data-stu-id="d3716-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="d3716-111">子元素</span><span class="sxs-lookup"><span data-stu-id="d3716-111">Child Elements</span></span>

|<span data-ttu-id="d3716-112">元素</span><span class="sxs-lookup"><span data-stu-id="d3716-112">Element</span></span>|<span data-ttu-id="d3716-113">描述</span><span class="sxs-lookup"><span data-stu-id="d3716-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d3716-114">ListControl 之專案的格式字串元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d3716-114">FormatString Element for ListItem for ListControl (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="d3716-115">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="d3716-115">Optional element.</span></span><br /><br /> <span data-ttu-id="d3716-116">指定定義屬性或腳本值顯示方式的格式字串。</span><span class="sxs-lookup"><span data-stu-id="d3716-116">Specifies a format string that defines how the property or script value is displayed.</span></span>|
|[<span data-ttu-id="d3716-117">ListControl 之專案的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d3716-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="d3716-118">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="d3716-118">Optional element.</span></span><br /><br /> <span data-ttu-id="d3716-119">定義必須存在才能使用此清單專案的條件。</span><span class="sxs-lookup"><span data-stu-id="d3716-119">Defines the condition that must exist for this list item to be used.</span></span>|
|[<span data-ttu-id="d3716-120">ListControl 之專案的標籤元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d3716-120">Label Element for ListItem for ListControl (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="d3716-121">選擇性元素</span><span class="sxs-lookup"><span data-stu-id="d3716-121">Optional element</span></span><br /><br /> <span data-ttu-id="d3716-122">指定顯示在資料列中屬性或腳本值左邊的標籤。</span><span class="sxs-lookup"><span data-stu-id="d3716-122">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>|
|[<span data-ttu-id="d3716-123">ListControl 之專案名稱的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d3716-123">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="d3716-124">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="d3716-124">Optional element.</span></span><br /><br /> <span data-ttu-id="d3716-125">指定其值顯示在資料列中的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="d3716-125">Specifies the .NET property whose value is displayed in the row.</span></span>|
|[<span data-ttu-id="d3716-126">ListControl 之專案的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d3716-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="d3716-127">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="d3716-127">Optional element.</span></span><br /><br /> <span data-ttu-id="d3716-128">指定其值顯示在資料列中的腳本。</span><span class="sxs-lookup"><span data-stu-id="d3716-128">Specifies the script whose value is displayed in the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d3716-129">父元素</span><span class="sxs-lookup"><span data-stu-id="d3716-129">Parent Elements</span></span>

|<span data-ttu-id="d3716-130">元素</span><span class="sxs-lookup"><span data-stu-id="d3716-130">Element</span></span>|<span data-ttu-id="d3716-131">描述</span><span class="sxs-lookup"><span data-stu-id="d3716-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d3716-132">清單控制項的 ListItems 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d3716-132">ListItems Element for List Control (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="d3716-133">定義其值會顯示在清單視圖中的屬性和腳本。</span><span class="sxs-lookup"><span data-stu-id="d3716-133">Defines the properties and scripts whose values are displayed in the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d3716-134">備註</span><span class="sxs-lookup"><span data-stu-id="d3716-134">Remarks</span></span>

<span data-ttu-id="d3716-135">如需清單視圖之元件的詳細資訊，請參閱[建立清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="d3716-135">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="d3716-136">範例</span><span class="sxs-lookup"><span data-stu-id="d3716-136">Example</span></span>

<span data-ttu-id="d3716-137">這個範例會顯示定義清單視圖之三個數據列的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="d3716-137">This example shows the XML elements that define three rows of the list view.</span></span> <span data-ttu-id="d3716-138">前兩個數據列會顯示 .NET 屬性的值，而最後一個資料列則會顯示腳本所產生的值。</span><span class="sxs-lookup"><span data-stu-id="d3716-138">The first two rows display the value of a .NET property, and the last row displays a value generated by a script.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d3716-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3716-139">See Also</span></span>

[<span data-ttu-id="d3716-140">ListItems 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d3716-140">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="d3716-141">專案的字串格式元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d3716-141">FormatString Element for ListItem (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="d3716-142">專案標示的標籤元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d3716-142">Label Element for ListItem (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="d3716-143">專案名稱的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d3716-143">PropertyName Element for ListItem (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="d3716-144">專案的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d3716-144">ScriptBlock Element for ListItem (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="d3716-145">建立清單視圖</span><span class="sxs-lookup"><span data-stu-id="d3716-145">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="d3716-146">撰寫 Windows PowerShell 格式化和類型檔案</span><span class="sxs-lookup"><span data-stu-id="d3716-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
