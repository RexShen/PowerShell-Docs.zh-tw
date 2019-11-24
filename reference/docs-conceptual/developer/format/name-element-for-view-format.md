---
title: View 的 Name 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a31010d-1db9-44ae-a7f3-6ed32cb641cb
caps.latest.revision: 16
ms.openlocfilehash: 097d20cb6a04635124d1f96823248df6095ca1af
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362637"
---
# <a name="name-element-for-view-format"></a><span data-ttu-id="e91b3-102">檢視的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e91b3-102">Name Element for View (Format)</span></span>

<span data-ttu-id="e91b3-103">指定用來識別此視圖的名稱。</span><span class="sxs-lookup"><span data-stu-id="e91b3-103">Specifies the name that is used to identify the view.</span></span>

<span data-ttu-id="e91b3-104">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） Name 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e91b3-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Name Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e91b3-105">語法</span><span class="sxs-lookup"><span data-stu-id="e91b3-105">Syntax</span></span>

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e91b3-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="e91b3-106">Attributes and Elements</span></span>

<span data-ttu-id="e91b3-107">下列各節說明屬性、子專案，以及 `Name` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="e91b3-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span> <span data-ttu-id="e91b3-108">每個視圖只允許一個 `Name` 元素。</span><span class="sxs-lookup"><span data-stu-id="e91b3-108">Only one `Name` element is allowed for each view.</span></span>

### <a name="attributes"></a><span data-ttu-id="e91b3-109">屬性</span><span class="sxs-lookup"><span data-stu-id="e91b3-109">Attributes</span></span>

<span data-ttu-id="e91b3-110">無。</span><span class="sxs-lookup"><span data-stu-id="e91b3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e91b3-111">子元素</span><span class="sxs-lookup"><span data-stu-id="e91b3-111">Child Elements</span></span>

<span data-ttu-id="e91b3-112">無。</span><span class="sxs-lookup"><span data-stu-id="e91b3-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e91b3-113">父元素</span><span class="sxs-lookup"><span data-stu-id="e91b3-113">Parent Elements</span></span>

|<span data-ttu-id="e91b3-114">項目</span><span class="sxs-lookup"><span data-stu-id="e91b3-114">Element</span></span>|<span data-ttu-id="e91b3-115">說明</span><span class="sxs-lookup"><span data-stu-id="e91b3-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e91b3-116">View 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e91b3-116">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="e91b3-117">定義用來顯示一或多個 .NET 物件成員的視圖。</span><span class="sxs-lookup"><span data-stu-id="e91b3-117">Defines a view that is used to display the members of one or more .NET objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e91b3-118">文字值</span><span class="sxs-lookup"><span data-stu-id="e91b3-118">Text Value</span></span>

<span data-ttu-id="e91b3-119">為視圖指定唯一的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="e91b3-119">Specify a unique friendly name for the view.</span></span> <span data-ttu-id="e91b3-120">這個名稱可以包含對檢視類型的參考（例如，資料表視圖或清單視圖）、物件或物件集使用此視圖、哪個命令會傳回物件，或這些的組合。</span><span class="sxs-lookup"><span data-stu-id="e91b3-120">This name can include a reference to the type of the view (such as a table view or list view), which object or set of objects use the view, what command returns the objects, or a combination of these.</span></span>

## <a name="remarks"></a><span data-ttu-id="e91b3-121">備註</span><span class="sxs-lookup"><span data-stu-id="e91b3-121">Remarks</span></span>

<span data-ttu-id="e91b3-122">如需不同類型之視圖的詳細資訊，請參閱下列主題：[資料表視圖](./creating-a-table-view.md)、[清單視圖](./creating-a-list-view.md)、[寬視圖](./creating-a-wide-view.md)和[自訂視圖](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="e91b3-122">For more information about the different types of views, see the following topics: [Table View](./creating-a-table-view.md), [List View](./creating-a-list-view.md), [Wide View](./creating-a-wide-view.md), and [Custom View](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="e91b3-123">範例</span><span class="sxs-lookup"><span data-stu-id="e91b3-123">Example</span></span>

<span data-ttu-id="e91b3-124">下列範例會顯示定義[system.serviceprocess.dll. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)物件之資料表視圖的 `View` 元素。</span><span class="sxs-lookup"><span data-stu-id="e91b3-124">The following example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="e91b3-125">此視圖的名稱為 "service"。</span><span class="sxs-lookup"><span data-stu-id="e91b3-125">The name of the view is "service".</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="e91b3-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e91b3-126">See Also</span></span>

[<span data-ttu-id="e91b3-127">建立清單視圖</span><span class="sxs-lookup"><span data-stu-id="e91b3-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="e91b3-128">建立資料表視圖</span><span class="sxs-lookup"><span data-stu-id="e91b3-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="e91b3-129">建立寬型視圖</span><span class="sxs-lookup"><span data-stu-id="e91b3-129">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="e91b3-130">建立自訂控制項</span><span class="sxs-lookup"><span data-stu-id="e91b3-130">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="e91b3-131">View 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e91b3-131">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="e91b3-132">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="e91b3-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
