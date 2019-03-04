---
title: ListEntry ListControl （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d16bca8-d025-432d-aa84-8b607b8af3ae
caps.latest.revision: 12
ms.openlocfilehash: 1a3bafd4ca94aee70e869c699f7a4ef8befc5511
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862244"
---
# <a name="listentry-element-for-listcontrol-format"></a><span data-ttu-id="aa4ab-102">ListControl 的 ListEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="aa4ab-102">ListEntry Element for ListControl (Format)</span></span>

<span data-ttu-id="aa4ab-103">提供清單檢視的定義。</span><span class="sxs-lookup"><span data-stu-id="aa4ab-103">Provides a definition of the list view.</span></span>

<span data-ttu-id="aa4ab-104">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） ListControl 項目 （格式） ListEntries 項目 （格式） ListEntry 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="aa4ab-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="aa4ab-105">語法</span><span class="sxs-lookup"><span data-stu-id="aa4ab-105">Syntax</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="aa4ab-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="aa4ab-106">Attributes and Elements</span></span>

<span data-ttu-id="aa4ab-107">下列各節說明屬性、 子項目和父項目`ListEntry`項目。</span><span class="sxs-lookup"><span data-stu-id="aa4ab-107">The following sections describe the attributes, child elements, and the parent element of the `ListEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="aa4ab-108">屬性</span><span class="sxs-lookup"><span data-stu-id="aa4ab-108">Attributes</span></span>

<span data-ttu-id="aa4ab-109">無。</span><span class="sxs-lookup"><span data-stu-id="aa4ab-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="aa4ab-110">子元素</span><span class="sxs-lookup"><span data-stu-id="aa4ab-110">Child Elements</span></span>

|<span data-ttu-id="aa4ab-111">元素</span><span class="sxs-lookup"><span data-stu-id="aa4ab-111">Element</span></span>|<span data-ttu-id="aa4ab-112">描述</span><span class="sxs-lookup"><span data-stu-id="aa4ab-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="aa4ab-113">EntrySelectedBy ListEntry （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="aa4ab-113">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="aa4ab-114">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="aa4ab-114">Optional element.</span></span><br /><br /> <span data-ttu-id="aa4ab-115">定義使用此清單檢視定義或必須存在於要使用此定義條件的.NET 物件。</span><span class="sxs-lookup"><span data-stu-id="aa4ab-115">Defines the .NET objects that use this list view definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="aa4ab-116">ListItems 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="aa4ab-116">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="aa4ab-117">必要項目。</span><span class="sxs-lookup"><span data-stu-id="aa4ab-117">Required element.</span></span><br /><br /> <span data-ttu-id="aa4ab-118">定義屬性和其值會顯示 [清單] 檢視的指令碼。</span><span class="sxs-lookup"><span data-stu-id="aa4ab-118">Defines the properties and scripts whose values are displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="aa4ab-119">父元素</span><span class="sxs-lookup"><span data-stu-id="aa4ab-119">Parent Elements</span></span>

|<span data-ttu-id="aa4ab-120">元素</span><span class="sxs-lookup"><span data-stu-id="aa4ab-120">Element</span></span>|<span data-ttu-id="aa4ab-121">描述</span><span class="sxs-lookup"><span data-stu-id="aa4ab-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="aa4ab-122">ListEntries 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="aa4ab-122">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="aa4ab-123">提供清單檢視的定義。</span><span class="sxs-lookup"><span data-stu-id="aa4ab-123">Provides the definitions of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="aa4ab-124">備註</span><span class="sxs-lookup"><span data-stu-id="aa4ab-124">Remarks</span></span>

<span data-ttu-id="aa4ab-125">清單檢視會顯示屬性值或每個物件的指令碼值以清單格式。</span><span class="sxs-lookup"><span data-stu-id="aa4ab-125">A list view is a list format that displays property values or script values for each object.</span></span> <span data-ttu-id="aa4ab-126">如需清單檢視的詳細資訊，請參閱[建立清單檢視](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="aa4ab-126">For more information about list views, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="aa4ab-127">範例</span><span class="sxs-lookup"><span data-stu-id="aa4ab-127">Example</span></span>

<span data-ttu-id="aa4ab-128">此範例示範定義的清單檢視的 XML 項目[System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)物件。</span><span class="sxs-lookup"><span data-stu-id="aa4ab-128">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="aa4ab-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aa4ab-129">See Also</span></span>

[<span data-ttu-id="aa4ab-130">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="aa4ab-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="aa4ab-131">EntrySelectedBy ListEntry （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="aa4ab-131">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="aa4ab-132">ListEntries 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="aa4ab-132">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="aa4ab-133">ListItems 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="aa4ab-133">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="aa4ab-134">撰寫 Windows PowerShell 格式和類型的檔案</span><span class="sxs-lookup"><span data-stu-id="aa4ab-134">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
