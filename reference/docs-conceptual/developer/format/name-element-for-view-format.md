---
title: View (格式的 Name 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 670b089f850fa4b39b7b100ca1e1ce45b05ea72d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773227"
---
# <a name="name-element-for-view-format"></a><span data-ttu-id="ccdce-102">檢視的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ccdce-102">Name Element for View (Format)</span></span>

<span data-ttu-id="ccdce-103">指定用來識別此視圖的名稱。</span><span class="sxs-lookup"><span data-stu-id="ccdce-103">Specifies the name that is used to identify the view.</span></span>

<span data-ttu-id="ccdce-104">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) Name 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="ccdce-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Name Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ccdce-105">語法</span><span class="sxs-lookup"><span data-stu-id="ccdce-105">Syntax</span></span>

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ccdce-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ccdce-106">Attributes and Elements</span></span>

<span data-ttu-id="ccdce-107">下列各節說明屬性、子專案和元素的父元素 `Name` 。</span><span class="sxs-lookup"><span data-stu-id="ccdce-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span> <span data-ttu-id="ccdce-108">`Name`每個視圖只允許一個元素。</span><span class="sxs-lookup"><span data-stu-id="ccdce-108">Only one `Name` element is allowed for each view.</span></span>

### <a name="attributes"></a><span data-ttu-id="ccdce-109">屬性</span><span class="sxs-lookup"><span data-stu-id="ccdce-109">Attributes</span></span>

<span data-ttu-id="ccdce-110">無。</span><span class="sxs-lookup"><span data-stu-id="ccdce-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ccdce-111">子元素</span><span class="sxs-lookup"><span data-stu-id="ccdce-111">Child Elements</span></span>

<span data-ttu-id="ccdce-112">無。</span><span class="sxs-lookup"><span data-stu-id="ccdce-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ccdce-113">父項目</span><span class="sxs-lookup"><span data-stu-id="ccdce-113">Parent Elements</span></span>

|<span data-ttu-id="ccdce-114">元素</span><span class="sxs-lookup"><span data-stu-id="ccdce-114">Element</span></span>|<span data-ttu-id="ccdce-115">描述</span><span class="sxs-lookup"><span data-stu-id="ccdce-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ccdce-116">檢視元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ccdce-116">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="ccdce-117">定義用來顯示一或多個 .NET 物件成員的視圖。</span><span class="sxs-lookup"><span data-stu-id="ccdce-117">Defines a view that is used to display the members of one or more .NET objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ccdce-118">文字值</span><span class="sxs-lookup"><span data-stu-id="ccdce-118">Text Value</span></span>

<span data-ttu-id="ccdce-119">為視圖指定唯一的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="ccdce-119">Specify a unique friendly name for the view.</span></span> <span data-ttu-id="ccdce-120">這個名稱可以包含檢視類型的參考 (例如資料表視圖或清單視圖) 、物件或物件集使用此視圖、哪個命令會傳回物件，或其組合。</span><span class="sxs-lookup"><span data-stu-id="ccdce-120">This name can include a reference to the type of the view (such as a table view or list view), which object or set of objects use the view, what command returns the objects, or a combination of these.</span></span>

## <a name="remarks"></a><span data-ttu-id="ccdce-121">備註</span><span class="sxs-lookup"><span data-stu-id="ccdce-121">Remarks</span></span>

<span data-ttu-id="ccdce-122">如需不同類型之視圖的詳細資訊，請參閱下列主題：[資料表視圖](./creating-a-table-view.md)、[清單視圖](./creating-a-list-view.md)、[寬視圖](./creating-a-wide-view.md)和[自訂視圖](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="ccdce-122">For more information about the different types of views, see the following topics: [Table View](./creating-a-table-view.md), [List View](./creating-a-list-view.md), [Wide View](./creating-a-wide-view.md), and [Custom View](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="ccdce-123">範例</span><span class="sxs-lookup"><span data-stu-id="ccdce-123">Example</span></span>

<span data-ttu-id="ccdce-124">下列範例顯示的 `View` 元素會定義[System.serviceprocess.dll. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)物件的資料表視圖。</span><span class="sxs-lookup"><span data-stu-id="ccdce-124">The following example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="ccdce-125">此視圖的名稱為 "service"。</span><span class="sxs-lookup"><span data-stu-id="ccdce-125">The name of the view is "service".</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="ccdce-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ccdce-126">See Also</span></span>

[<span data-ttu-id="ccdce-127">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="ccdce-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="ccdce-128">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="ccdce-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="ccdce-129">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="ccdce-129">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="ccdce-130">建立自訂控制項</span><span class="sxs-lookup"><span data-stu-id="ccdce-130">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="ccdce-131">檢視元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ccdce-131">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="ccdce-132">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="ccdce-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
