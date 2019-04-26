---
title: ListEntries ListControl （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b62e81cc-4175-40fa-829f-634245b09f86
caps.latest.revision: 12
ms.openlocfilehash: aaf16702e485135b5299ccb43a2b62db2d9f5762
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065385"
---
# <a name="listentries-element-for-listcontrol-format"></a><span data-ttu-id="0622d-102">ListControl 的 ListEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0622d-102">ListEntries Element for ListControl (Format)</span></span>

<span data-ttu-id="0622d-103">提供清單檢視的定義。</span><span class="sxs-lookup"><span data-stu-id="0622d-103">Provides the definitions of the list view.</span></span> <span data-ttu-id="0622d-104">清單檢視中必須指定一個或多個定義。</span><span class="sxs-lookup"><span data-stu-id="0622d-104">The list view must specify one or more definitions.</span></span>

<span data-ttu-id="0622d-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） ListControl 項目 （格式） ListEntries 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="0622d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0622d-106">語法</span><span class="sxs-lookup"><span data-stu-id="0622d-106">Syntax</span></span>

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0622d-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0622d-107">Attributes and Elements</span></span>

<span data-ttu-id="0622d-108">下列各節說明屬性、 子項目和父項目`ListEntries`項目。</span><span class="sxs-lookup"><span data-stu-id="0622d-108">The following sections describe the attributes, child elements, and the parent element of the `ListEntries` element.</span></span> <span data-ttu-id="0622d-109">必須指定至少一個子系項目。</span><span class="sxs-lookup"><span data-stu-id="0622d-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="0622d-110">屬性</span><span class="sxs-lookup"><span data-stu-id="0622d-110">Attributes</span></span>

<span data-ttu-id="0622d-111">無。</span><span class="sxs-lookup"><span data-stu-id="0622d-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0622d-112">子元素</span><span class="sxs-lookup"><span data-stu-id="0622d-112">Child Elements</span></span>

|<span data-ttu-id="0622d-113">元素</span><span class="sxs-lookup"><span data-stu-id="0622d-113">Element</span></span>|<span data-ttu-id="0622d-114">描述</span><span class="sxs-lookup"><span data-stu-id="0622d-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0622d-115">ListEntry 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="0622d-115">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="0622d-116">提供清單檢視的定義。</span><span class="sxs-lookup"><span data-stu-id="0622d-116">Provides a definition of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0622d-117">父項目</span><span class="sxs-lookup"><span data-stu-id="0622d-117">Parent Elements</span></span>

|<span data-ttu-id="0622d-118">項目</span><span class="sxs-lookup"><span data-stu-id="0622d-118">Element</span></span>|<span data-ttu-id="0622d-119">描述</span><span class="sxs-lookup"><span data-stu-id="0622d-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0622d-120">ListControl 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="0622d-120">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="0622d-121">定義檢視的清單格式。</span><span class="sxs-lookup"><span data-stu-id="0622d-121">Defines a list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0622d-122">備註</span><span class="sxs-lookup"><span data-stu-id="0622d-122">Remarks</span></span>

<span data-ttu-id="0622d-123">如需清單檢視的詳細資訊，請參閱[清單檢視](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="0622d-123">For more information about list views, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="0622d-124">範例</span><span class="sxs-lookup"><span data-stu-id="0622d-124">Example</span></span>

<span data-ttu-id="0622d-125">此範例示範定義的清單檢視的 XML 項目[System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)物件。</span><span class="sxs-lookup"><span data-stu-id="0622d-125">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0622d-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0622d-126">See Also</span></span>

[<span data-ttu-id="0622d-127">ListControl 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="0622d-127">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="0622d-128">ListEntry 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="0622d-128">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="0622d-129">清單檢視</span><span class="sxs-lookup"><span data-stu-id="0622d-129">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="0622d-130">撰寫 Windows PowerShell 格式和類型的檔案</span><span class="sxs-lookup"><span data-stu-id="0622d-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
