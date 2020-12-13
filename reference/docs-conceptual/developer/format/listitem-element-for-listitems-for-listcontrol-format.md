---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl 之 ListItems 的 ListItem 元素 (格式)
description: ListControl 之 ListItems 的 ListItem 元素 (格式)
ms.openlocfilehash: 999491b7851aa4fa21667ad376d7e9853500ca08
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666547"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a><span data-ttu-id="119e9-103">ListControl 之 ListItems 的 ListItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="119e9-103">ListItem Element for ListItems for ListControl (Format)</span></span>

<span data-ttu-id="119e9-104">定義屬性或腳本，其值會顯示在清單視圖的資料列中。</span><span class="sxs-lookup"><span data-stu-id="119e9-104">Defines the property or script whose value is displayed in a row of the list view.</span></span>

<span data-ttu-id="119e9-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) ListControl 元素 (format) ListEntries 元素 for ListControl (format) ListEntry 元素 for ListControl (format) ListItems 專案 (格式) 專案 (格式) </span><span class="sxs-lookup"><span data-stu-id="119e9-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem for ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="119e9-106">語法</span><span class="sxs-lookup"><span data-stu-id="119e9-106">Syntax</span></span>

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="119e9-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="119e9-107">Attributes and Elements</span></span>

<span data-ttu-id="119e9-108">下列各節描述專案的屬性、子項目和父元素 `ListItem` 。</span><span class="sxs-lookup"><span data-stu-id="119e9-108">The following sections describe the attributes, child elements, and parent element of the `ListItem` element.</span></span> <span data-ttu-id="119e9-109">只能指定一個屬性或腳本。</span><span class="sxs-lookup"><span data-stu-id="119e9-109">Only one property or script can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="119e9-110">屬性</span><span class="sxs-lookup"><span data-stu-id="119e9-110">Attributes</span></span>

<span data-ttu-id="119e9-111">無</span><span class="sxs-lookup"><span data-stu-id="119e9-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="119e9-112">子元素</span><span class="sxs-lookup"><span data-stu-id="119e9-112">Child Elements</span></span>

|<span data-ttu-id="119e9-113">元素</span><span class="sxs-lookup"><span data-stu-id="119e9-113">Element</span></span>|<span data-ttu-id="119e9-114">描述</span><span class="sxs-lookup"><span data-stu-id="119e9-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="119e9-115">ListControl (格式的專案代表的格式格式元素) </span><span class="sxs-lookup"><span data-stu-id="119e9-115">FormatString Element for ListItem for ListControl (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="119e9-116">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="119e9-116">Optional element.</span></span><br /><br /> <span data-ttu-id="119e9-117">指定定義如何顯示內容或腳本值的格式字串。</span><span class="sxs-lookup"><span data-stu-id="119e9-117">Specifies a format string that defines how the property or script value is displayed.</span></span>|
|[<span data-ttu-id="119e9-118">ListControl 之 ListItem 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="119e9-118">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="119e9-119">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="119e9-119">Optional element.</span></span><br /><br /> <span data-ttu-id="119e9-120">定義必須存在才能使用此清單專案的條件。</span><span class="sxs-lookup"><span data-stu-id="119e9-120">Defines the condition that must exist for this list item to be used.</span></span>|
|[<span data-ttu-id="119e9-121">ListControl 之 ListItem 的標籤元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="119e9-121">Label Element for ListItem for ListControl (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="119e9-122">選擇性元素</span><span class="sxs-lookup"><span data-stu-id="119e9-122">Optional element</span></span><br /><br /> <span data-ttu-id="119e9-123">指定在資料列中屬性或腳本值的左邊顯示的標籤。</span><span class="sxs-lookup"><span data-stu-id="119e9-123">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>|
|[<span data-ttu-id="119e9-124">ListControl 之 ListItem 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="119e9-124">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="119e9-125">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="119e9-125">Optional element.</span></span><br /><br /> <span data-ttu-id="119e9-126">指定其值會顯示在資料列中的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="119e9-126">Specifies the .NET property whose value is displayed in the row.</span></span>|
|[<span data-ttu-id="119e9-127">ListControl 之 ListItem 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="119e9-127">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="119e9-128">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="119e9-128">Optional element.</span></span><br /><br /> <span data-ttu-id="119e9-129">指定其值會顯示在資料列中的腳本。</span><span class="sxs-lookup"><span data-stu-id="119e9-129">Specifies the script whose value is displayed in the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="119e9-130">父項目</span><span class="sxs-lookup"><span data-stu-id="119e9-130">Parent Elements</span></span>

|<span data-ttu-id="119e9-131">元素</span><span class="sxs-lookup"><span data-stu-id="119e9-131">Element</span></span>|<span data-ttu-id="119e9-132">描述</span><span class="sxs-lookup"><span data-stu-id="119e9-132">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="119e9-133">清單控制項 (格式的 ListItems 元素) </span><span class="sxs-lookup"><span data-stu-id="119e9-133">ListItems Element for List Control (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="119e9-134">定義其值顯示在清單視圖中的屬性和腳本。</span><span class="sxs-lookup"><span data-stu-id="119e9-134">Defines the properties and scripts whose values are displayed in the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="119e9-135">備註</span><span class="sxs-lookup"><span data-stu-id="119e9-135">Remarks</span></span>

<span data-ttu-id="119e9-136">如需清單視圖元件的詳細資訊，請參閱 [建立清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="119e9-136">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="119e9-137">範例</span><span class="sxs-lookup"><span data-stu-id="119e9-137">Example</span></span>

<span data-ttu-id="119e9-138">這個範例會示範定義清單視圖之三個數據列的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="119e9-138">This example shows the XML elements that define three rows of the list view.</span></span> <span data-ttu-id="119e9-139">前兩個數據列會顯示 .NET 屬性的值，而最後一個資料列會顯示腳本所產生的值。</span><span class="sxs-lookup"><span data-stu-id="119e9-139">The first two rows display the value of a .NET property, and the last row displays a value generated by a script.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="119e9-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="119e9-140">See Also</span></span>

[<span data-ttu-id="119e9-141">ListItems 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="119e9-141">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="119e9-142">專案的格式字串專案 (格式) </span><span class="sxs-lookup"><span data-stu-id="119e9-142">FormatString Element for ListItem (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="119e9-143">專案標記的標籤元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="119e9-143">Label Element for ListItem (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="119e9-144">專案名稱的 PropertyName 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="119e9-144">PropertyName Element for ListItem (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="119e9-145">專案專案的 ScriptBlock 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="119e9-145">ScriptBlock Element for ListItem (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="119e9-146">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="119e9-146">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="119e9-147">寫入 Windows PowerShell 格式和類型檔案</span><span class="sxs-lookup"><span data-stu-id="119e9-147">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
