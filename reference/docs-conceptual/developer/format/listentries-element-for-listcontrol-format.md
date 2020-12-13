---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl 的 ListEntries 元素 (格式)
description: ListControl 的 ListEntries 元素 (格式)
ms.openlocfilehash: d4d6625bb92ea27863fc30d5bf5625f9275e4f69
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666598"
---
# <a name="listentries-element-for-listcontrol-format"></a><span data-ttu-id="ee6b2-103">ListControl 的 ListEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ee6b2-103">ListEntries Element for ListControl (Format)</span></span>

<span data-ttu-id="ee6b2-104">提供清單視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="ee6b2-104">Provides the definitions of the list view.</span></span> <span data-ttu-id="ee6b2-105">清單視圖必須指定一或多個定義。</span><span class="sxs-lookup"><span data-stu-id="ee6b2-105">The list view must specify one or more definitions.</span></span>

<span data-ttu-id="ee6b2-106">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) ListEntries 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="ee6b2-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ee6b2-107">語法</span><span class="sxs-lookup"><span data-stu-id="ee6b2-107">Syntax</span></span>

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ee6b2-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ee6b2-108">Attributes and Elements</span></span>

<span data-ttu-id="ee6b2-109">下列章節說明屬性、子專案和元素的父元素 `ListEntries` 。</span><span class="sxs-lookup"><span data-stu-id="ee6b2-109">The following sections describe the attributes, child elements, and the parent element of the `ListEntries` element.</span></span> <span data-ttu-id="ee6b2-110">至少必須指定一個子項目。</span><span class="sxs-lookup"><span data-stu-id="ee6b2-110">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="ee6b2-111">屬性</span><span class="sxs-lookup"><span data-stu-id="ee6b2-111">Attributes</span></span>

<span data-ttu-id="ee6b2-112">無。</span><span class="sxs-lookup"><span data-stu-id="ee6b2-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ee6b2-113">子元素</span><span class="sxs-lookup"><span data-stu-id="ee6b2-113">Child Elements</span></span>

|<span data-ttu-id="ee6b2-114">元素</span><span class="sxs-lookup"><span data-stu-id="ee6b2-114">Element</span></span>|<span data-ttu-id="ee6b2-115">描述</span><span class="sxs-lookup"><span data-stu-id="ee6b2-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ee6b2-116">ListEntry 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="ee6b2-116">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="ee6b2-117">提供清單視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="ee6b2-117">Provides a definition of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ee6b2-118">父項目</span><span class="sxs-lookup"><span data-stu-id="ee6b2-118">Parent Elements</span></span>

|<span data-ttu-id="ee6b2-119">元素</span><span class="sxs-lookup"><span data-stu-id="ee6b2-119">Element</span></span>|<span data-ttu-id="ee6b2-120">描述</span><span class="sxs-lookup"><span data-stu-id="ee6b2-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ee6b2-121">ListControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ee6b2-121">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="ee6b2-122">定義視圖的清單格式。</span><span class="sxs-lookup"><span data-stu-id="ee6b2-122">Defines a list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ee6b2-123">備註</span><span class="sxs-lookup"><span data-stu-id="ee6b2-123">Remarks</span></span>

<span data-ttu-id="ee6b2-124">如需清單視圖的詳細資訊，請參閱 [清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="ee6b2-124">For more information about list views, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="ee6b2-125">範例</span><span class="sxs-lookup"><span data-stu-id="ee6b2-125">Example</span></span>

<span data-ttu-id="ee6b2-126">這個範例會顯示定義 [System.serviceprocess.dll Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 物件清單視圖的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="ee6b2-126">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ee6b2-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee6b2-127">See Also</span></span>

[<span data-ttu-id="ee6b2-128">ListControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ee6b2-128">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="ee6b2-129">ListEntry 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="ee6b2-129">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="ee6b2-130">清單視圖</span><span class="sxs-lookup"><span data-stu-id="ee6b2-130">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="ee6b2-131">寫入 Windows PowerShell 格式和類型檔案</span><span class="sxs-lookup"><span data-stu-id="ee6b2-131">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
