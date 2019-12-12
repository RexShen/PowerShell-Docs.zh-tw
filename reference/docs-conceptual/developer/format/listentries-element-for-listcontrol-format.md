---
title: ListControl 的 ListEntries 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b62e81cc-4175-40fa-829f-634245b09f86
caps.latest.revision: 12
ms.openlocfilehash: aaf16702e485135b5299ccb43a2b62db2d9f5762
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362757"
---
# <a name="listentries-element-for-listcontrol-format"></a><span data-ttu-id="4f1e3-102">ListControl 的 ListEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4f1e3-102">ListEntries Element for ListControl (Format)</span></span>

<span data-ttu-id="4f1e3-103">提供清單視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="4f1e3-103">Provides the definitions of the list view.</span></span> <span data-ttu-id="4f1e3-104">清單視圖必須指定一或多個定義。</span><span class="sxs-lookup"><span data-stu-id="4f1e3-104">The list view must specify one or more definitions.</span></span>

<span data-ttu-id="4f1e3-105">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） ListControl 元素（格式） ListEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4f1e3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4f1e3-106">語法</span><span class="sxs-lookup"><span data-stu-id="4f1e3-106">Syntax</span></span>

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4f1e3-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="4f1e3-107">Attributes and Elements</span></span>

<span data-ttu-id="4f1e3-108">下列各節說明屬性、子專案，以及 `ListEntries` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="4f1e3-108">The following sections describe the attributes, child elements, and the parent element of the `ListEntries` element.</span></span> <span data-ttu-id="4f1e3-109">至少必須指定一個子項目。</span><span class="sxs-lookup"><span data-stu-id="4f1e3-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="4f1e3-110">屬性</span><span class="sxs-lookup"><span data-stu-id="4f1e3-110">Attributes</span></span>

<span data-ttu-id="4f1e3-111">無。</span><span class="sxs-lookup"><span data-stu-id="4f1e3-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4f1e3-112">子元素</span><span class="sxs-lookup"><span data-stu-id="4f1e3-112">Child Elements</span></span>

|<span data-ttu-id="4f1e3-113">元素</span><span class="sxs-lookup"><span data-stu-id="4f1e3-113">Element</span></span>|<span data-ttu-id="4f1e3-114">描述</span><span class="sxs-lookup"><span data-stu-id="4f1e3-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4f1e3-115">ListEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4f1e3-115">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="4f1e3-116">提供清單視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="4f1e3-116">Provides a definition of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4f1e3-117">父元素</span><span class="sxs-lookup"><span data-stu-id="4f1e3-117">Parent Elements</span></span>

|<span data-ttu-id="4f1e3-118">元素</span><span class="sxs-lookup"><span data-stu-id="4f1e3-118">Element</span></span>|<span data-ttu-id="4f1e3-119">描述</span><span class="sxs-lookup"><span data-stu-id="4f1e3-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4f1e3-120">ListControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4f1e3-120">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="4f1e3-121">定義視圖的清單格式。</span><span class="sxs-lookup"><span data-stu-id="4f1e3-121">Defines a list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4f1e3-122">備註</span><span class="sxs-lookup"><span data-stu-id="4f1e3-122">Remarks</span></span>

<span data-ttu-id="4f1e3-123">如需清單視圖的詳細資訊，請參閱[清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="4f1e3-123">For more information about list views, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="4f1e3-124">範例</span><span class="sxs-lookup"><span data-stu-id="4f1e3-124">Example</span></span>

<span data-ttu-id="4f1e3-125">這個範例會顯示定義[system.serviceprocess.dll. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)物件之清單視圖的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="4f1e3-125">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4f1e3-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f1e3-126">See Also</span></span>

[<span data-ttu-id="4f1e3-127">ListControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4f1e3-127">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="4f1e3-128">ListEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4f1e3-128">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="4f1e3-129">清單檢視</span><span class="sxs-lookup"><span data-stu-id="4f1e3-129">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="4f1e3-130">撰寫 Windows PowerShell 格式化和類型檔案</span><span class="sxs-lookup"><span data-stu-id="4f1e3-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
