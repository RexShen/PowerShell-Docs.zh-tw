---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl 的 ListEntry 元素 (格式)
description: ListControl 的 ListEntry 元素 (格式)
ms.openlocfilehash: 96ae5fcdd837d2491d6c7ff6a375fef1d83ae3e9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666564"
---
# <a name="listentry-element-for-listcontrol-format"></a><span data-ttu-id="bea07-103">ListControl 的 ListEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="bea07-103">ListEntry Element for ListControl (Format)</span></span>

<span data-ttu-id="bea07-104">提供清單視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="bea07-104">Provides a definition of the list view.</span></span>

<span data-ttu-id="bea07-105">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) ListControl 元素 (格式) ListEntries 元素 (格式) ListEntry 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="bea07-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bea07-106">語法</span><span class="sxs-lookup"><span data-stu-id="bea07-106">Syntax</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bea07-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bea07-107">Attributes and Elements</span></span>

<span data-ttu-id="bea07-108">下列章節說明屬性、子專案和元素的父元素 `ListEntry` 。</span><span class="sxs-lookup"><span data-stu-id="bea07-108">The following sections describe the attributes, child elements, and the parent element of the `ListEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bea07-109">屬性</span><span class="sxs-lookup"><span data-stu-id="bea07-109">Attributes</span></span>

<span data-ttu-id="bea07-110">無。</span><span class="sxs-lookup"><span data-stu-id="bea07-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bea07-111">子元素</span><span class="sxs-lookup"><span data-stu-id="bea07-111">Child Elements</span></span>

|<span data-ttu-id="bea07-112">元素</span><span class="sxs-lookup"><span data-stu-id="bea07-112">Element</span></span>|<span data-ttu-id="bea07-113">描述</span><span class="sxs-lookup"><span data-stu-id="bea07-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bea07-114">ListEntry (格式的之 entryselectedby 元素) </span><span class="sxs-lookup"><span data-stu-id="bea07-114">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="bea07-115">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="bea07-115">Optional element.</span></span><br /><br /> <span data-ttu-id="bea07-116">定義使用此清單視圖定義或必須存在才能使用此定義之條件的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="bea07-116">Defines the .NET objects that use this list view definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="bea07-117">ListItems 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="bea07-117">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="bea07-118">必要元素。</span><span class="sxs-lookup"><span data-stu-id="bea07-118">Required element.</span></span><br /><br /> <span data-ttu-id="bea07-119">定義清單視圖顯示其值的屬性和腳本。</span><span class="sxs-lookup"><span data-stu-id="bea07-119">Defines the properties and scripts whose values are displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="bea07-120">父項目</span><span class="sxs-lookup"><span data-stu-id="bea07-120">Parent Elements</span></span>

|<span data-ttu-id="bea07-121">元素</span><span class="sxs-lookup"><span data-stu-id="bea07-121">Element</span></span>|<span data-ttu-id="bea07-122">描述</span><span class="sxs-lookup"><span data-stu-id="bea07-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bea07-123">ListEntries 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="bea07-123">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="bea07-124">提供清單視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="bea07-124">Provides the definitions of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bea07-125">備註</span><span class="sxs-lookup"><span data-stu-id="bea07-125">Remarks</span></span>

<span data-ttu-id="bea07-126">清單視圖是一種清單格式，可顯示每個物件的屬性值或腳本值。</span><span class="sxs-lookup"><span data-stu-id="bea07-126">A list view is a list format that displays property values or script values for each object.</span></span> <span data-ttu-id="bea07-127">如需清單視圖的詳細資訊，請參閱 [建立清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="bea07-127">For more information about list views, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="bea07-128">範例</span><span class="sxs-lookup"><span data-stu-id="bea07-128">Example</span></span>

<span data-ttu-id="bea07-129">這個範例會顯示定義 [System.serviceprocess.dll Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 物件清單視圖的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="bea07-129">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>...</ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="bea07-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bea07-130">See Also</span></span>

[<span data-ttu-id="bea07-131">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="bea07-131">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="bea07-132">ListEntry (格式的之 entryselectedby 元素) </span><span class="sxs-lookup"><span data-stu-id="bea07-132">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="bea07-133">ListEntries 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="bea07-133">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="bea07-134">ListItems 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="bea07-134">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="bea07-135">寫入 Windows PowerShell 格式和類型檔案</span><span class="sxs-lookup"><span data-stu-id="bea07-135">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
