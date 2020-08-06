---
title: ViewSelectedBy (格式的 TypeName 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e9a391565c3e66041dd9a340455dccfce9ce929b
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780027"
---
# <a name="typename-element-for-viewselectedby-format"></a><span data-ttu-id="36940-102">ViewSelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="36940-102">TypeName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="36940-103">指定由視圖顯示的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="36940-103">Specifies a .NET object that is displayed by the view.</span></span>

<span data-ttu-id="36940-104">Configuration 元素 (格式) ViewDefinitions 元素 (格式) 視圖專案 (格式) ViewSelectedBy 專案 (格式) ViewSelectedBy (格式的 TypeName 元素) </span><span class="sxs-lookup"><span data-stu-id="36940-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) TypeName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="36940-105">語法</span><span class="sxs-lookup"><span data-stu-id="36940-105">Syntax</span></span>

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="36940-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="36940-106">Attributes and Elements</span></span>

<span data-ttu-id="36940-107">下列各節說明屬性、子專案和元素的父元素 `TypeName` 。</span><span class="sxs-lookup"><span data-stu-id="36940-107">The following sections describe attributes, child elements, and the parent elements of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="36940-108">屬性</span><span class="sxs-lookup"><span data-stu-id="36940-108">Attributes</span></span>

<span data-ttu-id="36940-109">無。</span><span class="sxs-lookup"><span data-stu-id="36940-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="36940-110">子元素</span><span class="sxs-lookup"><span data-stu-id="36940-110">Child Elements</span></span>

<span data-ttu-id="36940-111">無。</span><span class="sxs-lookup"><span data-stu-id="36940-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="36940-112">父項目</span><span class="sxs-lookup"><span data-stu-id="36940-112">Parent Elements</span></span>

|<span data-ttu-id="36940-113">元素</span><span class="sxs-lookup"><span data-stu-id="36940-113">Element</span></span>|<span data-ttu-id="36940-114">描述</span><span class="sxs-lookup"><span data-stu-id="36940-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="36940-115">ViewSelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="36940-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="36940-116">定義視圖所顯示的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="36940-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="36940-117">文字值</span><span class="sxs-lookup"><span data-stu-id="36940-117">Text Value</span></span>

<span data-ttu-id="36940-118">指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo` 。</span><span class="sxs-lookup"><span data-stu-id="36940-118">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="36940-119">備註</span><span class="sxs-lookup"><span data-stu-id="36940-119">Remarks</span></span>

<span data-ttu-id="36940-120">如需如何在不同的視圖中使用此元素的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)、[建立清單視圖](./creating-a-list-view.md)、[建立寬視圖](./creating-a-wide-view.md)和[自訂視圖元件](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="36940-120">For more information about how this element is used in different views, see [Creating a Table View](./creating-a-table-view.md), [Creating a List View](./creating-a-list-view.md), [Creating a Wide View](./creating-a-wide-view.md), and [Custom View Components](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="36940-121">範例</span><span class="sxs-lookup"><span data-stu-id="36940-121">Example</span></span>

<span data-ttu-id="36940-122">下列範例示範如何指定清單視圖的[system.serviceprocess.dll. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)物件。</span><span class="sxs-lookup"><span data-stu-id="36940-122">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="36940-123">資料表、寬型和自訂視圖會使用相同的架構。</span><span class="sxs-lookup"><span data-stu-id="36940-123">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="36940-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36940-124">See Also</span></span>

[<span data-ttu-id="36940-125">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="36940-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="36940-126">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="36940-126">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="36940-127">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="36940-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="36940-128">建立自訂控制項</span><span class="sxs-lookup"><span data-stu-id="36940-128">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="36940-129">ViewSelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="36940-129">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="36940-130">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="36940-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
