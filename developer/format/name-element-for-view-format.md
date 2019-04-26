---
title: 項目名稱 （格式） 檢視 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a31010d-1db9-44ae-a7f3-6ed32cb641cb
caps.latest.revision: 16
ms.openlocfilehash: 097d20cb6a04635124d1f96823248df6095ca1af
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065065"
---
# <a name="name-element-for-view-format"></a><span data-ttu-id="8ad5c-102">檢視的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8ad5c-102">Name Element for View (Format)</span></span>

<span data-ttu-id="8ad5c-103">指定用來識別檢視的名稱。</span><span class="sxs-lookup"><span data-stu-id="8ad5c-103">Specifies the name that is used to identify the view.</span></span>

<span data-ttu-id="8ad5c-104">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） 名稱項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="8ad5c-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Name Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8ad5c-105">語法</span><span class="sxs-lookup"><span data-stu-id="8ad5c-105">Syntax</span></span>

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8ad5c-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8ad5c-106">Attributes and Elements</span></span>

<span data-ttu-id="8ad5c-107">下列各節說明屬性、 子項目和父項目`Name`項目。</span><span class="sxs-lookup"><span data-stu-id="8ad5c-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span> <span data-ttu-id="8ad5c-108">只有一個`Name`元素可在每個檢視。</span><span class="sxs-lookup"><span data-stu-id="8ad5c-108">Only one `Name` element is allowed for each view.</span></span>

### <a name="attributes"></a><span data-ttu-id="8ad5c-109">屬性</span><span class="sxs-lookup"><span data-stu-id="8ad5c-109">Attributes</span></span>

<span data-ttu-id="8ad5c-110">無。</span><span class="sxs-lookup"><span data-stu-id="8ad5c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8ad5c-111">子元素</span><span class="sxs-lookup"><span data-stu-id="8ad5c-111">Child Elements</span></span>

<span data-ttu-id="8ad5c-112">無。</span><span class="sxs-lookup"><span data-stu-id="8ad5c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8ad5c-113">父項目</span><span class="sxs-lookup"><span data-stu-id="8ad5c-113">Parent Elements</span></span>

|<span data-ttu-id="8ad5c-114">項目</span><span class="sxs-lookup"><span data-stu-id="8ad5c-114">Element</span></span>|<span data-ttu-id="8ad5c-115">描述</span><span class="sxs-lookup"><span data-stu-id="8ad5c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8ad5c-116">檢視項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="8ad5c-116">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="8ad5c-117">定義用來顯示的一或多個.NET 物件成員的檢視。</span><span class="sxs-lookup"><span data-stu-id="8ad5c-117">Defines a view that is used to display the members of one or more .NET objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8ad5c-118">文字值</span><span class="sxs-lookup"><span data-stu-id="8ad5c-118">Text Value</span></span>

<span data-ttu-id="8ad5c-119">指定檢視的唯一易記名稱。</span><span class="sxs-lookup"><span data-stu-id="8ad5c-119">Specify a unique friendly name for the view.</span></span> <span data-ttu-id="8ad5c-120">此名稱可以包含的哪些物件或一組物件使用的檢視中，哪些命令可傳回物件或這些項目的組合 （例如以資料表或清單檢視），檢視類型的參考。</span><span class="sxs-lookup"><span data-stu-id="8ad5c-120">This name can include a reference to the type of the view (such as a table view or list view), which object or set of objects use the view, what command returns the objects, or a combination of these.</span></span>

## <a name="remarks"></a><span data-ttu-id="8ad5c-121">備註</span><span class="sxs-lookup"><span data-stu-id="8ad5c-121">Remarks</span></span>

<span data-ttu-id="8ad5c-122">如需有關檢視的不同類型的詳細資訊，請參閱下列主題：[資料表檢視](./creating-a-table-view.md)，[清單檢視](./creating-a-list-view.md)，[寬型檢視](./creating-a-wide-view.md)，和[自訂檢視](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="8ad5c-122">For more information about the different types of views, see the following topics: [Table View](./creating-a-table-view.md), [List View](./creating-a-list-view.md), [Wide View](./creating-a-wide-view.md), and [Custom View](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="8ad5c-123">範例</span><span class="sxs-lookup"><span data-stu-id="8ad5c-123">Example</span></span>

<span data-ttu-id="8ad5c-124">下列範例所示`View`定義的資料表檢視項目[System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)物件。</span><span class="sxs-lookup"><span data-stu-id="8ad5c-124">The following example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="8ad5c-125">檢視的名稱是 「 服務 」。</span><span class="sxs-lookup"><span data-stu-id="8ad5c-125">The name of the view is "service".</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="8ad5c-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ad5c-126">See Also</span></span>

[<span data-ttu-id="8ad5c-127">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="8ad5c-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="8ad5c-128">建立資料表檢視</span><span class="sxs-lookup"><span data-stu-id="8ad5c-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="8ad5c-129">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="8ad5c-129">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="8ad5c-130">建立自訂控制項</span><span class="sxs-lookup"><span data-stu-id="8ad5c-130">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="8ad5c-131">檢視項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="8ad5c-131">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="8ad5c-132">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="8ad5c-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
