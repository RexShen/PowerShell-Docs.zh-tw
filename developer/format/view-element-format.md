---
title: 檢視項目 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856144"
---
# <a name="view-element-format"></a><span data-ttu-id="762a6-102">檢視元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="762a6-102">View Element (Format)</span></span>

<span data-ttu-id="762a6-103">定義顯示一或多個.NET 物件的檢視。</span><span class="sxs-lookup"><span data-stu-id="762a6-103">Defines a view that displays one or more .NET objects.</span></span> <span data-ttu-id="762a6-104">可以格式化檔案中定義的檢視表的數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="762a6-104">There is no limit to the number of views that can be defined in a formatting file.</span></span>

<span data-ttu-id="762a6-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="762a6-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="762a6-106">語法</span><span class="sxs-lookup"><span data-stu-id="762a6-106">Syntax</span></span>

```xml
<View>
  <Name>Friendly name of view.</Name>
  <ViewSelectedBy>...</ViewSelectedBy>
  <Controls>...</Controls>
  <GroupBy>...</GroupBy>
  <TableControl>...</TableControl>
  <ListControl>...</ListControl>
  <WideControl>...</WideControl>
  <CustomControl>...</CustomControl>
</View>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="762a6-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="762a6-107">Attributes and Elements</span></span>

<span data-ttu-id="762a6-108">下列各節說明屬性、 子項目和父項目`View`項目。</span><span class="sxs-lookup"><span data-stu-id="762a6-108">The following sections describe the attributes, child elements, and the parent element of the `View` element.</span></span> <span data-ttu-id="762a6-109">您必須指定其中一個控制項子項目，而且您必須指定名稱的檢視和使用檢視的物件。</span><span class="sxs-lookup"><span data-stu-id="762a6-109">You must specify one and only one of the control child elements, and you must specify the name of the view and the objects that use the view.</span></span> <span data-ttu-id="762a6-110">定義自訂控制項，如何分組的物件，並指定檢視是否超出訊號範圍是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="762a6-110">Defining custom controls, how to group objects, and specifying if the view is out-of-band are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="762a6-111">屬性</span><span class="sxs-lookup"><span data-stu-id="762a6-111">Attributes</span></span>

<span data-ttu-id="762a6-112">無。</span><span class="sxs-lookup"><span data-stu-id="762a6-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="762a6-113">子元素</span><span class="sxs-lookup"><span data-stu-id="762a6-113">Child Elements</span></span>

|<span data-ttu-id="762a6-114">元素</span><span class="sxs-lookup"><span data-stu-id="762a6-114">Element</span></span>|<span data-ttu-id="762a6-115">描述</span><span class="sxs-lookup"><span data-stu-id="762a6-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="762a6-116">檢視 （格式） 的 controls 項目</span><span class="sxs-lookup"><span data-stu-id="762a6-116">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="762a6-117">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="762a6-117">Optional element.</span></span><br /><br /> <span data-ttu-id="762a6-118">定義一組可依據其名稱，從檢視中參考的控制項。</span><span class="sxs-lookup"><span data-stu-id="762a6-118">Defines a set of controls that can be referenced by their name from within the view.</span></span>|
|[<span data-ttu-id="762a6-119">CustomControl 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="762a6-119">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="762a6-120">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="762a6-120">Optional element.</span></span><br /><br /> <span data-ttu-id="762a6-121">定義檢視的自訂控制項格式。</span><span class="sxs-lookup"><span data-stu-id="762a6-121">Defines a custom control format for the view.</span></span>|
|[<span data-ttu-id="762a6-122">檢視 （格式） 的 GroupBy 元素</span><span class="sxs-lookup"><span data-stu-id="762a6-122">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="762a6-123">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="762a6-123">Optional element.</span></span><br /><br /> <span data-ttu-id="762a6-124">定義.NET 物件的成員分組的方式。</span><span class="sxs-lookup"><span data-stu-id="762a6-124">Defines how the members of the .NET objects are grouped.</span></span>|
|[<span data-ttu-id="762a6-125">ListControl 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="762a6-125">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="762a6-126">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="762a6-126">Optional element.</span></span><br /><br /> <span data-ttu-id="762a6-127">定義檢視的清單格式。</span><span class="sxs-lookup"><span data-stu-id="762a6-127">Defines a list format for the view.</span></span>|
|[<span data-ttu-id="762a6-128">檢視 （格式） 的 name 元素</span><span class="sxs-lookup"><span data-stu-id="762a6-128">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)|<span data-ttu-id="762a6-129">必要項目。</span><span class="sxs-lookup"><span data-stu-id="762a6-129">Required element.</span></span><br /><br /> <span data-ttu-id="762a6-130">指定用來參考檢視的名稱。</span><span class="sxs-lookup"><span data-stu-id="762a6-130">Specifies the name used to reference the view.</span></span>|
|[<span data-ttu-id="762a6-131">TableControl 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="762a6-131">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="762a6-132">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="762a6-132">Optional element.</span></span><br /><br /> <span data-ttu-id="762a6-133">定義檢視以資料表格式。</span><span class="sxs-lookup"><span data-stu-id="762a6-133">Defines a table format for the view.</span></span>|
|[<span data-ttu-id="762a6-134">ViewSelectedBy 檢視 （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="762a6-134">ViewSelectedBy Element for View (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="762a6-135">必要項目。</span><span class="sxs-lookup"><span data-stu-id="762a6-135">Required element.</span></span><br /><br /> <span data-ttu-id="762a6-136">定義此檢視會顯示的.NET 物件。</span><span class="sxs-lookup"><span data-stu-id="762a6-136">Defines the .NET objects that this view displays.</span></span>|
|[<span data-ttu-id="762a6-137">WideControl 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="762a6-137">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="762a6-138">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="762a6-138">Optional element.</span></span><br /><br /> <span data-ttu-id="762a6-139">寬 （單一值） 會定義檢視的清單格式。</span><span class="sxs-lookup"><span data-stu-id="762a6-139">Defines a wide (single value) list format for the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="762a6-140">父元素</span><span class="sxs-lookup"><span data-stu-id="762a6-140">Parent Elements</span></span>

|<span data-ttu-id="762a6-141">元素</span><span class="sxs-lookup"><span data-stu-id="762a6-141">Element</span></span>|<span data-ttu-id="762a6-142">描述</span><span class="sxs-lookup"><span data-stu-id="762a6-142">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="762a6-143">ViewDefinitions 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="762a6-143">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="762a6-144">定義用來顯示物件的檢視。</span><span class="sxs-lookup"><span data-stu-id="762a6-144">Defines the views used to display objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="762a6-145">備註</span><span class="sxs-lookup"><span data-stu-id="762a6-145">Remarks</span></span>

<span data-ttu-id="762a6-146">如需詳細的不同檢視和自訂控制項之元件的相關資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="762a6-146">For more information about the components of different views and custom controls, see the following topics:</span></span>

- [<span data-ttu-id="762a6-147">資料表檢視元件</span><span class="sxs-lookup"><span data-stu-id="762a6-147">Table View Components</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="762a6-148">清單檢視元件</span><span class="sxs-lookup"><span data-stu-id="762a6-148">List View Components</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="762a6-149">寬型檢視元件</span><span class="sxs-lookup"><span data-stu-id="762a6-149">Wide View Components</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="762a6-150">自訂控制項</span><span class="sxs-lookup"><span data-stu-id="762a6-150">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="762a6-151">範例</span><span class="sxs-lookup"><span data-stu-id="762a6-151">Example</span></span>

<span data-ttu-id="762a6-152">此範例示範`View`定義的資料表檢視項目[System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)物件。</span><span class="sxs-lookup"><span data-stu-id="762a6-152">This example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>service</Name>
    <ViewSelectedBy>
      <TypeName>System.ServiceProcess.ServiceController</TypeName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a><span data-ttu-id="762a6-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="762a6-153">See Also</span></span>

[<span data-ttu-id="762a6-154">ViewDefinitions 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="762a6-154">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="762a6-155">檢視 （格式） 的 name 元素</span><span class="sxs-lookup"><span data-stu-id="762a6-155">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)

[<span data-ttu-id="762a6-156">ViewSelectedBy 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="762a6-156">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="762a6-157">檢視 （格式） 的 controls 項目</span><span class="sxs-lookup"><span data-stu-id="762a6-157">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="762a6-158">檢視 （格式） 的 GroupBy 元素</span><span class="sxs-lookup"><span data-stu-id="762a6-158">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="762a6-159">TableControl 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="762a6-159">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="762a6-160">ListControl 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="762a6-160">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="762a6-161">WideControl 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="762a6-161">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="762a6-162">CustomControl 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="762a6-162">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="762a6-163">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="762a6-163">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
