---
title: ViewSelectedBy 的 TypeName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ad807a9-d7d8-4e96-b799-9c6a7677cc2d
caps.latest.revision: 12
ms.openlocfilehash: e2028c479103cc414295dc24a0f9bb69190bfc66
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361437"
---
# <a name="typename-element-for-viewselectedby-format"></a><span data-ttu-id="50337-102">ViewSelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="50337-102">TypeName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="50337-103">指定由視圖顯示的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="50337-103">Specifies a .NET object that is displayed by the view.</span></span>

<span data-ttu-id="50337-104">ViewSelectedBy 的 Configuration 元素（格式） ViewDefinitions 元素（格式） ViewSelectedBy 元素（格式） TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="50337-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) TypeName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="50337-105">語法</span><span class="sxs-lookup"><span data-stu-id="50337-105">Syntax</span></span>

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="50337-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="50337-106">Attributes and Elements</span></span>

<span data-ttu-id="50337-107">下列各節說明屬性、子專案，以及 `TypeName` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="50337-107">The following sections describe attributes, child elements, and the parent elements of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="50337-108">屬性</span><span class="sxs-lookup"><span data-stu-id="50337-108">Attributes</span></span>

<span data-ttu-id="50337-109">無。</span><span class="sxs-lookup"><span data-stu-id="50337-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="50337-110">子元素</span><span class="sxs-lookup"><span data-stu-id="50337-110">Child Elements</span></span>

<span data-ttu-id="50337-111">無。</span><span class="sxs-lookup"><span data-stu-id="50337-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="50337-112">父元素</span><span class="sxs-lookup"><span data-stu-id="50337-112">Parent Elements</span></span>

|<span data-ttu-id="50337-113">元素</span><span class="sxs-lookup"><span data-stu-id="50337-113">Element</span></span>|<span data-ttu-id="50337-114">描述</span><span class="sxs-lookup"><span data-stu-id="50337-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="50337-115">ViewSelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="50337-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="50337-116">定義視圖所顯示的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="50337-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="50337-117">文字值</span><span class="sxs-lookup"><span data-stu-id="50337-117">Text Value</span></span>

<span data-ttu-id="50337-118">指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="50337-118">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="50337-119">備註</span><span class="sxs-lookup"><span data-stu-id="50337-119">Remarks</span></span>

<span data-ttu-id="50337-120">如需如何在不同的視圖中使用此元素的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)、[建立清單視圖](./creating-a-list-view.md)、[建立寬視圖](./creating-a-wide-view.md)和[自訂視圖元件](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="50337-120">For more information about how this element is used in different views, see [Creating a Table View](./creating-a-table-view.md), [Creating a List View](./creating-a-list-view.md), [Creating a Wide View](./creating-a-wide-view.md), and [Custom View Components](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="50337-121">範例</span><span class="sxs-lookup"><span data-stu-id="50337-121">Example</span></span>

<span data-ttu-id="50337-122">下列範例示範如何指定清單視圖的[system.serviceprocess.dll. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)物件。</span><span class="sxs-lookup"><span data-stu-id="50337-122">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="50337-123">資料表、寬型和自訂視圖會使用相同的架構。</span><span class="sxs-lookup"><span data-stu-id="50337-123">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="50337-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50337-124">See Also</span></span>

[<span data-ttu-id="50337-125">建立清單視圖</span><span class="sxs-lookup"><span data-stu-id="50337-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="50337-126">建立資料表視圖</span><span class="sxs-lookup"><span data-stu-id="50337-126">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="50337-127">建立寬型視圖</span><span class="sxs-lookup"><span data-stu-id="50337-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="50337-128">建立自訂控制項</span><span class="sxs-lookup"><span data-stu-id="50337-128">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="50337-129">ViewSelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="50337-129">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="50337-130">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="50337-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
