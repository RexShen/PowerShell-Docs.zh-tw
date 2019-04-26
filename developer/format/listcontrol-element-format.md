---
title: ListControl 項目 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37beeb0b-7a81-4747-becb-e309e17278fb
caps.latest.revision: 12
ms.openlocfilehash: 7a117c25b0d117dc846ba8e060e31e838b5edd52
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065252"
---
# <a name="listcontrol-element-format"></a><span data-ttu-id="b91c7-102">ListControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b91c7-102">ListControl Element (Format)</span></span>

<span data-ttu-id="b91c7-103">定義檢視的清單格式。</span><span class="sxs-lookup"><span data-stu-id="b91c7-103">Defines a list format for the view.</span></span>

<span data-ttu-id="b91c7-104">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） ListControl 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="b91c7-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b91c7-105">語法</span><span class="sxs-lookup"><span data-stu-id="b91c7-105">Syntax</span></span>

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="b91c7-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b91c7-106">Attributes and Elements</span></span>

<span data-ttu-id="b91c7-107">下列各節說明屬性、 子項目和父項目`ListControl`項目。</span><span class="sxs-lookup"><span data-stu-id="b91c7-107">The following sections describe the attributes, child elements, and the parent element of the `ListControl` element.</span></span> <span data-ttu-id="b91c7-108">此元素必須包含單一子項目。</span><span class="sxs-lookup"><span data-stu-id="b91c7-108">This element must contain only a single child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b91c7-109">屬性</span><span class="sxs-lookup"><span data-stu-id="b91c7-109">Attributes</span></span>

<span data-ttu-id="b91c7-110">無。</span><span class="sxs-lookup"><span data-stu-id="b91c7-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b91c7-111">子元素</span><span class="sxs-lookup"><span data-stu-id="b91c7-111">Child Elements</span></span>

|<span data-ttu-id="b91c7-112">元素</span><span class="sxs-lookup"><span data-stu-id="b91c7-112">Element</span></span>|<span data-ttu-id="b91c7-113">描述</span><span class="sxs-lookup"><span data-stu-id="b91c7-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b91c7-114">ListEntries 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="b91c7-114">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="b91c7-115">必要項目。</span><span class="sxs-lookup"><span data-stu-id="b91c7-115">Required element.</span></span><br /><br /> <span data-ttu-id="b91c7-116">提供清單檢視的定義。</span><span class="sxs-lookup"><span data-stu-id="b91c7-116">Provides the definitions of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b91c7-117">父項目</span><span class="sxs-lookup"><span data-stu-id="b91c7-117">Parent Elements</span></span>

|<span data-ttu-id="b91c7-118">項目</span><span class="sxs-lookup"><span data-stu-id="b91c7-118">Element</span></span>|<span data-ttu-id="b91c7-119">描述</span><span class="sxs-lookup"><span data-stu-id="b91c7-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b91c7-120">檢視項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="b91c7-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="b91c7-121">定義的檢視，用來顯示一或多個物件的成員。</span><span class="sxs-lookup"><span data-stu-id="b91c7-121">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b91c7-122">備註</span><span class="sxs-lookup"><span data-stu-id="b91c7-122">Remarks</span></span>

<span data-ttu-id="b91c7-123">如需建立清單檢視的詳細資訊，請參閱 <<c0> [ 建立清單檢視](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="b91c7-123">For more information about creating a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="b91c7-124">範例</span><span class="sxs-lookup"><span data-stu-id="b91c7-124">Example</span></span>

<span data-ttu-id="b91c7-125">此範例中顯示的清單檢視[System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)物件。</span><span class="sxs-lookup"><span data-stu-id="b91c7-125">This example shows a list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b91c7-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b91c7-126">See Also</span></span>

[<span data-ttu-id="b91c7-127">檢視項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="b91c7-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="b91c7-128">ListEntries 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="b91c7-128">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="b91c7-129">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="b91c7-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="b91c7-130">撰寫 Windows PowerShell 格式和類型的檔案</span><span class="sxs-lookup"><span data-stu-id="b91c7-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
