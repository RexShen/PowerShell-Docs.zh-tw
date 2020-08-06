---
title: ListControl 元素 (格式) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0173b9797bffcca74f1a32903686f771366ebb1b
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785722"
---
# <a name="listcontrol-element-format"></a><span data-ttu-id="4cc43-102">ListControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4cc43-102">ListControl Element (Format)</span></span>

<span data-ttu-id="4cc43-103">定義視圖的清單格式。</span><span class="sxs-lookup"><span data-stu-id="4cc43-103">Defines a list format for the view.</span></span>

<span data-ttu-id="4cc43-104">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ListControl 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="4cc43-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4cc43-105">語法</span><span class="sxs-lookup"><span data-stu-id="4cc43-105">Syntax</span></span>

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="4cc43-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4cc43-106">Attributes and Elements</span></span>

<span data-ttu-id="4cc43-107">下列各節說明屬性、子專案和元素的父元素 `ListControl` 。</span><span class="sxs-lookup"><span data-stu-id="4cc43-107">The following sections describe the attributes, child elements, and the parent element of the `ListControl` element.</span></span> <span data-ttu-id="4cc43-108">此元素必須只包含單一子專案。</span><span class="sxs-lookup"><span data-stu-id="4cc43-108">This element must contain only a single child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4cc43-109">屬性</span><span class="sxs-lookup"><span data-stu-id="4cc43-109">Attributes</span></span>

<span data-ttu-id="4cc43-110">無。</span><span class="sxs-lookup"><span data-stu-id="4cc43-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4cc43-111">子元素</span><span class="sxs-lookup"><span data-stu-id="4cc43-111">Child Elements</span></span>

|<span data-ttu-id="4cc43-112">元素</span><span class="sxs-lookup"><span data-stu-id="4cc43-112">Element</span></span>|<span data-ttu-id="4cc43-113">描述</span><span class="sxs-lookup"><span data-stu-id="4cc43-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4cc43-114">ListEntries 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="4cc43-114">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="4cc43-115">必要元素。</span><span class="sxs-lookup"><span data-stu-id="4cc43-115">Required element.</span></span><br /><br /> <span data-ttu-id="4cc43-116">提供清單視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="4cc43-116">Provides the definitions of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4cc43-117">父項目</span><span class="sxs-lookup"><span data-stu-id="4cc43-117">Parent Elements</span></span>

|<span data-ttu-id="4cc43-118">元素</span><span class="sxs-lookup"><span data-stu-id="4cc43-118">Element</span></span>|<span data-ttu-id="4cc43-119">描述</span><span class="sxs-lookup"><span data-stu-id="4cc43-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4cc43-120">檢視元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4cc43-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="4cc43-121">定義用來顯示一或多個物件成員的視圖。</span><span class="sxs-lookup"><span data-stu-id="4cc43-121">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4cc43-122">備註</span><span class="sxs-lookup"><span data-stu-id="4cc43-122">Remarks</span></span>

<span data-ttu-id="4cc43-123">如需建立清單視圖的詳細資訊，請參閱[建立清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="4cc43-123">For more information about creating a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="4cc43-124">範例</span><span class="sxs-lookup"><span data-stu-id="4cc43-124">Example</span></span>

<span data-ttu-id="4cc43-125">這個範例會顯示[system.serviceprocess.dll. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)物件的清單視圖。</span><span class="sxs-lookup"><span data-stu-id="4cc43-125">This example shows a list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4cc43-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4cc43-126">See Also</span></span>

[<span data-ttu-id="4cc43-127">檢視元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4cc43-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="4cc43-128">ListEntries 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="4cc43-128">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="4cc43-129">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="4cc43-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="4cc43-130">撰寫 Windows PowerShell 格式化和類型檔案</span><span class="sxs-lookup"><span data-stu-id="4cc43-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
