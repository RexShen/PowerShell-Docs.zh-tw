---
title: ListControl 的 ListEntry 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d16bca8-d025-432d-aa84-8b607b8af3ae
caps.latest.revision: 12
ms.openlocfilehash: 1a3bafd4ca94aee70e869c699f7a4ef8befc5511
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362747"
---
# <a name="listentry-element-for-listcontrol-format"></a><span data-ttu-id="c0996-102">ListControl 的 ListEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c0996-102">ListEntry Element for ListControl (Format)</span></span>

<span data-ttu-id="c0996-103">提供清單視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="c0996-103">Provides a definition of the list view.</span></span>

<span data-ttu-id="c0996-104">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（格式） ListControl 元素（格式） ListEntries 元素（格式） ListEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c0996-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c0996-105">語法</span><span class="sxs-lookup"><span data-stu-id="c0996-105">Syntax</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c0996-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="c0996-106">Attributes and Elements</span></span>

<span data-ttu-id="c0996-107">下列各節說明屬性、子專案，以及 `ListEntry` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="c0996-107">The following sections describe the attributes, child elements, and the parent element of the `ListEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c0996-108">屬性</span><span class="sxs-lookup"><span data-stu-id="c0996-108">Attributes</span></span>

<span data-ttu-id="c0996-109">無。</span><span class="sxs-lookup"><span data-stu-id="c0996-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c0996-110">子元素</span><span class="sxs-lookup"><span data-stu-id="c0996-110">Child Elements</span></span>

|<span data-ttu-id="c0996-111">元素</span><span class="sxs-lookup"><span data-stu-id="c0996-111">Element</span></span>|<span data-ttu-id="c0996-112">描述</span><span class="sxs-lookup"><span data-stu-id="c0996-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c0996-113">ListEntry 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c0996-113">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="c0996-114">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="c0996-114">Optional element.</span></span><br /><br /> <span data-ttu-id="c0996-115">定義使用此清單視圖定義的 .NET 物件，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="c0996-115">Defines the .NET objects that use this list view definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="c0996-116">ListItems 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c0996-116">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="c0996-117">必要元素。</span><span class="sxs-lookup"><span data-stu-id="c0996-117">Required element.</span></span><br /><br /> <span data-ttu-id="c0996-118">定義清單視圖會顯示其值的屬性和腳本。</span><span class="sxs-lookup"><span data-stu-id="c0996-118">Defines the properties and scripts whose values are displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c0996-119">父元素</span><span class="sxs-lookup"><span data-stu-id="c0996-119">Parent Elements</span></span>

|<span data-ttu-id="c0996-120">元素</span><span class="sxs-lookup"><span data-stu-id="c0996-120">Element</span></span>|<span data-ttu-id="c0996-121">描述</span><span class="sxs-lookup"><span data-stu-id="c0996-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c0996-122">ListEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c0996-122">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="c0996-123">提供清單視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="c0996-123">Provides the definitions of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c0996-124">備註</span><span class="sxs-lookup"><span data-stu-id="c0996-124">Remarks</span></span>

<span data-ttu-id="c0996-125">清單視圖是一種清單格式，可顯示每個物件的屬性值或腳本值。</span><span class="sxs-lookup"><span data-stu-id="c0996-125">A list view is a list format that displays property values or script values for each object.</span></span> <span data-ttu-id="c0996-126">如需清單視圖的詳細資訊，請參閱[建立清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="c0996-126">For more information about list views, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c0996-127">範例</span><span class="sxs-lookup"><span data-stu-id="c0996-127">Example</span></span>

<span data-ttu-id="c0996-128">這個範例會顯示定義[system.serviceprocess.dll. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)物件之清單視圖的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="c0996-128">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c0996-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0996-129">See Also</span></span>

[<span data-ttu-id="c0996-130">建立清單視圖</span><span class="sxs-lookup"><span data-stu-id="c0996-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="c0996-131">ListEntry 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c0996-131">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="c0996-132">ListEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c0996-132">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="c0996-133">ListItems 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c0996-133">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="c0996-134">撰寫 Windows PowerShell 格式化和類型檔案</span><span class="sxs-lookup"><span data-stu-id="c0996-134">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
