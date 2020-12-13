---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl 元素 (格式)
description: ListControl 元素 (格式)
ms.openlocfilehash: cd5687ac8e94e2245d1ae2de8b2206185e5b8ca4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666581"
---
# <a name="listcontrol-element-format"></a><span data-ttu-id="88fcf-103">ListControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="88fcf-103">ListControl Element (Format)</span></span>

<span data-ttu-id="88fcf-104">定義視圖的清單格式。</span><span class="sxs-lookup"><span data-stu-id="88fcf-104">Defines a list format for the view.</span></span>

<span data-ttu-id="88fcf-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (Format) ListControl 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="88fcf-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="88fcf-106">語法</span><span class="sxs-lookup"><span data-stu-id="88fcf-106">Syntax</span></span>

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="88fcf-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="88fcf-107">Attributes and Elements</span></span>

<span data-ttu-id="88fcf-108">下列章節說明屬性、子專案和元素的父元素 `ListControl` 。</span><span class="sxs-lookup"><span data-stu-id="88fcf-108">The following sections describe the attributes, child elements, and the parent element of the `ListControl` element.</span></span> <span data-ttu-id="88fcf-109">這個元素必須只包含單一子項目。</span><span class="sxs-lookup"><span data-stu-id="88fcf-109">This element must contain only a single child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="88fcf-110">屬性</span><span class="sxs-lookup"><span data-stu-id="88fcf-110">Attributes</span></span>

<span data-ttu-id="88fcf-111">無。</span><span class="sxs-lookup"><span data-stu-id="88fcf-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="88fcf-112">子元素</span><span class="sxs-lookup"><span data-stu-id="88fcf-112">Child Elements</span></span>

|<span data-ttu-id="88fcf-113">元素</span><span class="sxs-lookup"><span data-stu-id="88fcf-113">Element</span></span>|<span data-ttu-id="88fcf-114">描述</span><span class="sxs-lookup"><span data-stu-id="88fcf-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="88fcf-115">ListEntries 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="88fcf-115">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="88fcf-116">必要元素。</span><span class="sxs-lookup"><span data-stu-id="88fcf-116">Required element.</span></span><br /><br /> <span data-ttu-id="88fcf-117">提供清單視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="88fcf-117">Provides the definitions of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="88fcf-118">父項目</span><span class="sxs-lookup"><span data-stu-id="88fcf-118">Parent Elements</span></span>

|<span data-ttu-id="88fcf-119">元素</span><span class="sxs-lookup"><span data-stu-id="88fcf-119">Element</span></span>|<span data-ttu-id="88fcf-120">描述</span><span class="sxs-lookup"><span data-stu-id="88fcf-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="88fcf-121">檢視元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="88fcf-121">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="88fcf-122">定義用來顯示一或多個物件成員的視圖。</span><span class="sxs-lookup"><span data-stu-id="88fcf-122">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="88fcf-123">備註</span><span class="sxs-lookup"><span data-stu-id="88fcf-123">Remarks</span></span>

<span data-ttu-id="88fcf-124">如需建立清單視圖的詳細資訊，請參閱 [建立清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="88fcf-124">For more information about creating a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="88fcf-125">範例</span><span class="sxs-lookup"><span data-stu-id="88fcf-125">Example</span></span>

<span data-ttu-id="88fcf-126">此範例顯示 [system.serviceprocess.dll. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 物件的清單視圖。</span><span class="sxs-lookup"><span data-stu-id="88fcf-126">This example shows a list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>...</ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="88fcf-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88fcf-127">See Also</span></span>

[<span data-ttu-id="88fcf-128">檢視元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="88fcf-128">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="88fcf-129">ListEntries 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="88fcf-129">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="88fcf-130">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="88fcf-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="88fcf-131">寫入 Windows PowerShell 格式和類型檔案</span><span class="sxs-lookup"><span data-stu-id="88fcf-131">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
