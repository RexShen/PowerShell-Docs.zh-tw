---
ms.date: 09/13/2016
ms.topic: reference
title: ViewSelectedBy 的 TypeName 元素 (格式)
description: ViewSelectedBy 的 TypeName 元素 (格式)
ms.openlocfilehash: 62edc2fe4b4c1c5f1b17dd2f8b0943f28ff5dfb7
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667720"
---
# <a name="typename-element-for-viewselectedby-format"></a><span data-ttu-id="287cb-103">ViewSelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="287cb-103">TypeName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="287cb-104">指定由視圖顯示的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="287cb-104">Specifies a .NET object that is displayed by the view.</span></span>

<span data-ttu-id="287cb-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (Format) ViewSelectedBy 元素 (format) ViewSelectedBy (格式的 TypeName 元素) </span><span class="sxs-lookup"><span data-stu-id="287cb-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) TypeName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="287cb-106">語法</span><span class="sxs-lookup"><span data-stu-id="287cb-106">Syntax</span></span>

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="287cb-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="287cb-107">Attributes and Elements</span></span>

<span data-ttu-id="287cb-108">下列各節說明屬性、子專案和元素的父元素 `TypeName` 。</span><span class="sxs-lookup"><span data-stu-id="287cb-108">The following sections describe attributes, child elements, and the parent elements of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="287cb-109">屬性</span><span class="sxs-lookup"><span data-stu-id="287cb-109">Attributes</span></span>

<span data-ttu-id="287cb-110">無。</span><span class="sxs-lookup"><span data-stu-id="287cb-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="287cb-111">子元素</span><span class="sxs-lookup"><span data-stu-id="287cb-111">Child Elements</span></span>

<span data-ttu-id="287cb-112">無。</span><span class="sxs-lookup"><span data-stu-id="287cb-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="287cb-113">父項目</span><span class="sxs-lookup"><span data-stu-id="287cb-113">Parent Elements</span></span>

|<span data-ttu-id="287cb-114">元素</span><span class="sxs-lookup"><span data-stu-id="287cb-114">Element</span></span>|<span data-ttu-id="287cb-115">描述</span><span class="sxs-lookup"><span data-stu-id="287cb-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="287cb-116">ViewSelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="287cb-116">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="287cb-117">定義由視圖顯示的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="287cb-117">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="287cb-118">文字值</span><span class="sxs-lookup"><span data-stu-id="287cb-118">Text Value</span></span>

<span data-ttu-id="287cb-119">指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo` 。</span><span class="sxs-lookup"><span data-stu-id="287cb-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="287cb-120">備註</span><span class="sxs-lookup"><span data-stu-id="287cb-120">Remarks</span></span>

<span data-ttu-id="287cb-121">如需如何在不同的視圖中使用這個元素的詳細資訊，請參閱 [建立資料表視圖](./creating-a-table-view.md)、 [建立清單視圖](./creating-a-list-view.md)、 [建立寬視圖](./creating-a-wide-view.md)，以及 [自訂視圖元件](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="287cb-121">For more information about how this element is used in different views, see [Creating a Table View](./creating-a-table-view.md), [Creating a List View](./creating-a-list-view.md), [Creating a Wide View](./creating-a-wide-view.md), and [Custom View Components](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="287cb-122">範例</span><span class="sxs-lookup"><span data-stu-id="287cb-122">Example</span></span>

<span data-ttu-id="287cb-123">下列範例示範如何指定清單視圖的 [system.serviceprocess.dll. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 物件。</span><span class="sxs-lookup"><span data-stu-id="287cb-123">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="287cb-124">資料表、寬和自訂視圖都使用相同的架構。</span><span class="sxs-lookup"><span data-stu-id="287cb-124">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="287cb-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="287cb-125">See Also</span></span>

[<span data-ttu-id="287cb-126">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="287cb-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="287cb-127">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="287cb-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="287cb-128">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="287cb-128">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="287cb-129">建立自訂控制項</span><span class="sxs-lookup"><span data-stu-id="287cb-129">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="287cb-130">ViewSelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="287cb-130">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="287cb-131">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="287cb-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
