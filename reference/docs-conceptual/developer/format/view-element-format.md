---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視元素 (格式)
description: 檢視元素 (格式)
ms.openlocfilehash: 6fed1304d94339cc90b6ae53e06483c08d937c12
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649738"
---
# <a name="view-element-format"></a><span data-ttu-id="5f3e3-103">檢視元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5f3e3-103">View Element (Format)</span></span>

<span data-ttu-id="5f3e3-104">定義顯示一或多個 .NET 物件的視圖。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-104">Defines a view that displays one or more .NET objects.</span></span> <span data-ttu-id="5f3e3-105">在格式化檔案中可定義的視圖數目沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-105">There is no limit to the number of views that can be defined in a formatting file.</span></span>

<span data-ttu-id="5f3e3-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="5f3e3-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5f3e3-107">語法</span><span class="sxs-lookup"><span data-stu-id="5f3e3-107">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="5f3e3-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5f3e3-108">Attributes and Elements</span></span>

<span data-ttu-id="5f3e3-109">下列章節說明屬性、子專案和元素的父元素 `View` 。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-109">The following sections describe the attributes, child elements, and the parent element of the `View` element.</span></span> <span data-ttu-id="5f3e3-110">您只能指定一個控制項子項目，而且您必須指定視圖的名稱和使用此視圖的物件。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-110">You must specify one and only one of the control child elements, and you must specify the name of the view and the objects that use the view.</span></span> <span data-ttu-id="5f3e3-111">定義自訂控制項、如何將物件分組，以及指定視圖是否為頻外的選項。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-111">Defining custom controls, how to group objects, and specifying if the view is out-of-band are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="5f3e3-112">屬性</span><span class="sxs-lookup"><span data-stu-id="5f3e3-112">Attributes</span></span>

<span data-ttu-id="5f3e3-113">無。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5f3e3-114">子元素</span><span class="sxs-lookup"><span data-stu-id="5f3e3-114">Child Elements</span></span>

|<span data-ttu-id="5f3e3-115">元素</span><span class="sxs-lookup"><span data-stu-id="5f3e3-115">Element</span></span>|<span data-ttu-id="5f3e3-116">描述</span><span class="sxs-lookup"><span data-stu-id="5f3e3-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5f3e3-117">檢視的控制項元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5f3e3-117">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="5f3e3-118">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-118">Optional element.</span></span><br /><br /> <span data-ttu-id="5f3e3-119">定義一組可從視圖內依名稱參考的控制項。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-119">Defines a set of controls that can be referenced by their name from within the view.</span></span>|
|[<span data-ttu-id="5f3e3-120">CustomControl 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="5f3e3-120">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="5f3e3-121">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-121">Optional element.</span></span><br /><br /> <span data-ttu-id="5f3e3-122">定義視圖的自訂控制項格式。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-122">Defines a custom control format for the view.</span></span>|
|[<span data-ttu-id="5f3e3-123">檢視的 GroupBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5f3e3-123">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="5f3e3-124">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-124">Optional element.</span></span><br /><br /> <span data-ttu-id="5f3e3-125">定義如何將 .NET 物件的成員分組。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-125">Defines how the members of the .NET objects are grouped.</span></span>|
|[<span data-ttu-id="5f3e3-126">ListControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5f3e3-126">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="5f3e3-127">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-127">Optional element.</span></span><br /><br /> <span data-ttu-id="5f3e3-128">定義視圖的清單格式。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-128">Defines a list format for the view.</span></span>|
|[<span data-ttu-id="5f3e3-129">檢視的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5f3e3-129">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)|<span data-ttu-id="5f3e3-130">必要元素。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-130">Required element.</span></span><br /><br /> <span data-ttu-id="5f3e3-131">指定用來參考視圖的名稱。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-131">Specifies the name used to reference the view.</span></span>|
|[<span data-ttu-id="5f3e3-132">TableControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5f3e3-132">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="5f3e3-133">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-133">Optional element.</span></span><br /><br /> <span data-ttu-id="5f3e3-134">定義視圖的資料表格式。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-134">Defines a table format for the view.</span></span>|
|[<span data-ttu-id="5f3e3-135">View (格式的 ViewSelectedBy 元素) </span><span class="sxs-lookup"><span data-stu-id="5f3e3-135">ViewSelectedBy Element for View (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="5f3e3-136">必要元素。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-136">Required element.</span></span><br /><br /> <span data-ttu-id="5f3e3-137">定義此視圖所顯示的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-137">Defines the .NET objects that this view displays.</span></span>|
|[<span data-ttu-id="5f3e3-138">WideControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5f3e3-138">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="5f3e3-139">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-139">Optional element.</span></span><br /><br /> <span data-ttu-id="5f3e3-140">為視圖定義寬 (單一值) 清單格式。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-140">Defines a wide (single value) list format for the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5f3e3-141">父項目</span><span class="sxs-lookup"><span data-stu-id="5f3e3-141">Parent Elements</span></span>

|<span data-ttu-id="5f3e3-142">元素</span><span class="sxs-lookup"><span data-stu-id="5f3e3-142">Element</span></span>|<span data-ttu-id="5f3e3-143">描述</span><span class="sxs-lookup"><span data-stu-id="5f3e3-143">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5f3e3-144">ViewDefinitions 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5f3e3-144">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="5f3e3-145">定義用來顯示物件的視圖。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-145">Defines the views used to display objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5f3e3-146">備註</span><span class="sxs-lookup"><span data-stu-id="5f3e3-146">Remarks</span></span>

<span data-ttu-id="5f3e3-147">如需不同 views 和自訂控制群組件的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="5f3e3-147">For more information about the components of different views and custom controls, see the following topics:</span></span>

- [<span data-ttu-id="5f3e3-148">資料表視圖元件</span><span class="sxs-lookup"><span data-stu-id="5f3e3-148">Table View Components</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="5f3e3-149">清單視圖元件</span><span class="sxs-lookup"><span data-stu-id="5f3e3-149">List View Components</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="5f3e3-150">寬視圖元件</span><span class="sxs-lookup"><span data-stu-id="5f3e3-150">Wide View Components</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="5f3e3-151">自訂控制項</span><span class="sxs-lookup"><span data-stu-id="5f3e3-151">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="5f3e3-152">範例</span><span class="sxs-lookup"><span data-stu-id="5f3e3-152">Example</span></span>

<span data-ttu-id="5f3e3-153">這個範例會顯示 `View` 定義 [system.serviceprocess.dll Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 物件之資料表視圖的元素。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-153">This example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="5f3e3-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f3e3-154">See Also</span></span>

[<span data-ttu-id="5f3e3-155">ViewDefinitions 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5f3e3-155">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="5f3e3-156">檢視的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5f3e3-156">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)

[<span data-ttu-id="5f3e3-157">ViewSelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5f3e3-157">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="5f3e3-158">檢視的控制項元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5f3e3-158">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="5f3e3-159">檢視的 GroupBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5f3e3-159">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="5f3e3-160">TableControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5f3e3-160">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="5f3e3-161">ListControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5f3e3-161">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="5f3e3-162">WideControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5f3e3-162">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="5f3e3-163">CustomControl 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="5f3e3-163">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="5f3e3-164">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="5f3e3-164">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
