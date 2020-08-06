---
title: ListControl (格式的 ListEntry 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d98f0b5215eea7668f866d2733214ade79d748f1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785688"
---
# <a name="listentry-element-for-listcontrol-format"></a><span data-ttu-id="421e9-102">ListControl 的 ListEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="421e9-102">ListEntry Element for ListControl (Format)</span></span>

<span data-ttu-id="421e9-103">提供清單視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="421e9-103">Provides a definition of the list view.</span></span>

<span data-ttu-id="421e9-104">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ListControl 元素 (格式) ListEntries 專案 (格式) ListEntry 專案 (格式) </span><span class="sxs-lookup"><span data-stu-id="421e9-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="421e9-105">語法</span><span class="sxs-lookup"><span data-stu-id="421e9-105">Syntax</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="421e9-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="421e9-106">Attributes and Elements</span></span>

<span data-ttu-id="421e9-107">下列各節說明屬性、子專案和元素的父元素 `ListEntry` 。</span><span class="sxs-lookup"><span data-stu-id="421e9-107">The following sections describe the attributes, child elements, and the parent element of the `ListEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="421e9-108">屬性</span><span class="sxs-lookup"><span data-stu-id="421e9-108">Attributes</span></span>

<span data-ttu-id="421e9-109">無。</span><span class="sxs-lookup"><span data-stu-id="421e9-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="421e9-110">子元素</span><span class="sxs-lookup"><span data-stu-id="421e9-110">Child Elements</span></span>

|<span data-ttu-id="421e9-111">元素</span><span class="sxs-lookup"><span data-stu-id="421e9-111">Element</span></span>|<span data-ttu-id="421e9-112">描述</span><span class="sxs-lookup"><span data-stu-id="421e9-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="421e9-113">ListEntry (格式的之 entryselectedby 元素) </span><span class="sxs-lookup"><span data-stu-id="421e9-113">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="421e9-114">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="421e9-114">Optional element.</span></span><br /><br /> <span data-ttu-id="421e9-115">定義使用此清單視圖定義的 .NET 物件，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="421e9-115">Defines the .NET objects that use this list view definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="421e9-116">ListItems 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="421e9-116">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="421e9-117">必要元素。</span><span class="sxs-lookup"><span data-stu-id="421e9-117">Required element.</span></span><br /><br /> <span data-ttu-id="421e9-118">定義清單視圖會顯示其值的屬性和腳本。</span><span class="sxs-lookup"><span data-stu-id="421e9-118">Defines the properties and scripts whose values are displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="421e9-119">父項目</span><span class="sxs-lookup"><span data-stu-id="421e9-119">Parent Elements</span></span>

|<span data-ttu-id="421e9-120">元素</span><span class="sxs-lookup"><span data-stu-id="421e9-120">Element</span></span>|<span data-ttu-id="421e9-121">描述</span><span class="sxs-lookup"><span data-stu-id="421e9-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="421e9-122">ListEntries 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="421e9-122">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="421e9-123">提供清單視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="421e9-123">Provides the definitions of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="421e9-124">備註</span><span class="sxs-lookup"><span data-stu-id="421e9-124">Remarks</span></span>

<span data-ttu-id="421e9-125">清單視圖是一種清單格式，可顯示每個物件的屬性值或腳本值。</span><span class="sxs-lookup"><span data-stu-id="421e9-125">A list view is a list format that displays property values or script values for each object.</span></span> <span data-ttu-id="421e9-126">如需清單視圖的詳細資訊，請參閱[建立清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="421e9-126">For more information about list views, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="421e9-127">範例</span><span class="sxs-lookup"><span data-stu-id="421e9-127">Example</span></span>

<span data-ttu-id="421e9-128">這個範例會顯示定義[system.serviceprocess.dll. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)物件之清單視圖的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="421e9-128">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="421e9-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="421e9-129">See Also</span></span>

[<span data-ttu-id="421e9-130">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="421e9-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="421e9-131">ListEntry (格式的之 entryselectedby 元素) </span><span class="sxs-lookup"><span data-stu-id="421e9-131">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="421e9-132">ListEntries 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="421e9-132">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="421e9-133">ListItems 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="421e9-133">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="421e9-134">撰寫 Windows PowerShell 格式化和類型檔案</span><span class="sxs-lookup"><span data-stu-id="421e9-134">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
