---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視的名稱元素 (格式)
description: 檢視的名稱元素 (格式)
ms.openlocfilehash: 5781bcdf7a0e1eb5e9c7e97bb6acc0a383dc0262
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666447"
---
# <a name="name-element-for-view-format"></a><span data-ttu-id="22e2a-103">檢視的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="22e2a-103">Name Element for View (Format)</span></span>

<span data-ttu-id="22e2a-104">指定用來識別視圖的名稱。</span><span class="sxs-lookup"><span data-stu-id="22e2a-104">Specifies the name that is used to identify the view.</span></span>

<span data-ttu-id="22e2a-105">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) 名稱元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="22e2a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Name Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="22e2a-106">語法</span><span class="sxs-lookup"><span data-stu-id="22e2a-106">Syntax</span></span>

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="22e2a-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="22e2a-107">Attributes and Elements</span></span>

<span data-ttu-id="22e2a-108">下列各節說明屬性、子專案和元素的父元素 `Name` 。</span><span class="sxs-lookup"><span data-stu-id="22e2a-108">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span> <span data-ttu-id="22e2a-109">`Name`每個視圖只允許一個元素。</span><span class="sxs-lookup"><span data-stu-id="22e2a-109">Only one `Name` element is allowed for each view.</span></span>

### <a name="attributes"></a><span data-ttu-id="22e2a-110">屬性</span><span class="sxs-lookup"><span data-stu-id="22e2a-110">Attributes</span></span>

<span data-ttu-id="22e2a-111">無。</span><span class="sxs-lookup"><span data-stu-id="22e2a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="22e2a-112">子元素</span><span class="sxs-lookup"><span data-stu-id="22e2a-112">Child Elements</span></span>

<span data-ttu-id="22e2a-113">無。</span><span class="sxs-lookup"><span data-stu-id="22e2a-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="22e2a-114">父項目</span><span class="sxs-lookup"><span data-stu-id="22e2a-114">Parent Elements</span></span>

|<span data-ttu-id="22e2a-115">元素</span><span class="sxs-lookup"><span data-stu-id="22e2a-115">Element</span></span>|<span data-ttu-id="22e2a-116">描述</span><span class="sxs-lookup"><span data-stu-id="22e2a-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="22e2a-117">檢視元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="22e2a-117">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="22e2a-118">定義用來顯示一或多個 .NET 物件成員的視圖。</span><span class="sxs-lookup"><span data-stu-id="22e2a-118">Defines a view that is used to display the members of one or more .NET objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="22e2a-119">文字值</span><span class="sxs-lookup"><span data-stu-id="22e2a-119">Text Value</span></span>

<span data-ttu-id="22e2a-120">為視圖指定唯一的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="22e2a-120">Specify a unique friendly name for the view.</span></span> <span data-ttu-id="22e2a-121">這個名稱可以包含檢視類型的參考 (例如，資料表視圖或清單視圖) 、使用 view 的物件或物件集、哪個命令傳回物件或這些的組合。</span><span class="sxs-lookup"><span data-stu-id="22e2a-121">This name can include a reference to the type of the view (such as a table view or list view), which object or set of objects use the view, what command returns the objects, or a combination of these.</span></span>

## <a name="remarks"></a><span data-ttu-id="22e2a-122">備註</span><span class="sxs-lookup"><span data-stu-id="22e2a-122">Remarks</span></span>

<span data-ttu-id="22e2a-123">如需不同類型之視圖的詳細資訊，請參閱下列主題： [資料表視圖](./creating-a-table-view.md)、 [清單視圖](./creating-a-list-view.md)、 [寬視圖](./creating-a-wide-view.md)和 [自訂視圖](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="22e2a-123">For more information about the different types of views, see the following topics: [Table View](./creating-a-table-view.md), [List View](./creating-a-list-view.md), [Wide View](./creating-a-wide-view.md), and [Custom View](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="22e2a-124">範例</span><span class="sxs-lookup"><span data-stu-id="22e2a-124">Example</span></span>

<span data-ttu-id="22e2a-125">下列範例 `View` 會顯示定義 [system.serviceprocess.dll Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 物件之資料表視圖的元素。</span><span class="sxs-lookup"><span data-stu-id="22e2a-125">The following example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="22e2a-126">視圖的名稱為「服務」。</span><span class="sxs-lookup"><span data-stu-id="22e2a-126">The name of the view is "service".</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="22e2a-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22e2a-127">See Also</span></span>

[<span data-ttu-id="22e2a-128">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="22e2a-128">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="22e2a-129">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="22e2a-129">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="22e2a-130">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="22e2a-130">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="22e2a-131">建立自訂控制項</span><span class="sxs-lookup"><span data-stu-id="22e2a-131">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="22e2a-132">檢視元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="22e2a-132">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="22e2a-133">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="22e2a-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
