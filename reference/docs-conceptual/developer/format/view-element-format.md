---
title: View 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361457"
---
# <a name="view-element-format"></a><span data-ttu-id="17aaf-102">檢視元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="17aaf-102">View Element (Format)</span></span>

<span data-ttu-id="17aaf-103">定義顯示一或多個 .NET 物件的視圖。</span><span class="sxs-lookup"><span data-stu-id="17aaf-103">Defines a view that displays one or more .NET objects.</span></span> <span data-ttu-id="17aaf-104">可以在格式化檔案中定義的視圖數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="17aaf-104">There is no limit to the number of views that can be defined in a formatting file.</span></span>

<span data-ttu-id="17aaf-105">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="17aaf-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="17aaf-106">語法</span><span class="sxs-lookup"><span data-stu-id="17aaf-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="17aaf-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="17aaf-107">Attributes and Elements</span></span>

<span data-ttu-id="17aaf-108">下列各節說明屬性、子專案，以及 `View` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="17aaf-108">The following sections describe the attributes, child elements, and the parent element of the `View` element.</span></span> <span data-ttu-id="17aaf-109">您必須指定其中一個控制項子專案，而且您必須指定視圖的名稱和使用此視圖的物件。</span><span class="sxs-lookup"><span data-stu-id="17aaf-109">You must specify one and only one of the control child elements, and you must specify the name of the view and the objects that use the view.</span></span> <span data-ttu-id="17aaf-110">定義自訂控制項、如何將物件分組，以及指定此視圖是否超出範圍是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="17aaf-110">Defining custom controls, how to group objects, and specifying if the view is out-of-band are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="17aaf-111">屬性</span><span class="sxs-lookup"><span data-stu-id="17aaf-111">Attributes</span></span>

<span data-ttu-id="17aaf-112">無。</span><span class="sxs-lookup"><span data-stu-id="17aaf-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="17aaf-113">子元素</span><span class="sxs-lookup"><span data-stu-id="17aaf-113">Child Elements</span></span>

|<span data-ttu-id="17aaf-114">元素</span><span class="sxs-lookup"><span data-stu-id="17aaf-114">Element</span></span>|<span data-ttu-id="17aaf-115">描述</span><span class="sxs-lookup"><span data-stu-id="17aaf-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="17aaf-116">View 的 Controls 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="17aaf-116">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="17aaf-117">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="17aaf-117">Optional element.</span></span><br /><br /> <span data-ttu-id="17aaf-118">定義一組控制項，可由其在視圖內的名稱參考。</span><span class="sxs-lookup"><span data-stu-id="17aaf-118">Defines a set of controls that can be referenced by their name from within the view.</span></span>|
|[<span data-ttu-id="17aaf-119">CustomControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="17aaf-119">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="17aaf-120">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="17aaf-120">Optional element.</span></span><br /><br /> <span data-ttu-id="17aaf-121">定義視圖的自訂控制項格式。</span><span class="sxs-lookup"><span data-stu-id="17aaf-121">Defines a custom control format for the view.</span></span>|
|[<span data-ttu-id="17aaf-122">View 的 GroupBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="17aaf-122">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="17aaf-123">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="17aaf-123">Optional element.</span></span><br /><br /> <span data-ttu-id="17aaf-124">定義如何分組 .NET 物件的成員。</span><span class="sxs-lookup"><span data-stu-id="17aaf-124">Defines how the members of the .NET objects are grouped.</span></span>|
|[<span data-ttu-id="17aaf-125">ListControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="17aaf-125">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="17aaf-126">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="17aaf-126">Optional element.</span></span><br /><br /> <span data-ttu-id="17aaf-127">定義視圖的清單格式。</span><span class="sxs-lookup"><span data-stu-id="17aaf-127">Defines a list format for the view.</span></span>|
|[<span data-ttu-id="17aaf-128">View 的 Name 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="17aaf-128">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)|<span data-ttu-id="17aaf-129">必要項目。</span><span class="sxs-lookup"><span data-stu-id="17aaf-129">Required element.</span></span><br /><br /> <span data-ttu-id="17aaf-130">指定用來參考此視圖的名稱。</span><span class="sxs-lookup"><span data-stu-id="17aaf-130">Specifies the name used to reference the view.</span></span>|
|[<span data-ttu-id="17aaf-131">TableControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="17aaf-131">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="17aaf-132">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="17aaf-132">Optional element.</span></span><br /><br /> <span data-ttu-id="17aaf-133">定義視圖的資料表格式。</span><span class="sxs-lookup"><span data-stu-id="17aaf-133">Defines a table format for the view.</span></span>|
|[<span data-ttu-id="17aaf-134">View 的 ViewSelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="17aaf-134">ViewSelectedBy Element for View (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="17aaf-135">必要項目。</span><span class="sxs-lookup"><span data-stu-id="17aaf-135">Required element.</span></span><br /><br /> <span data-ttu-id="17aaf-136">定義此視圖顯示的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="17aaf-136">Defines the .NET objects that this view displays.</span></span>|
|[<span data-ttu-id="17aaf-137">WideControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="17aaf-137">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="17aaf-138">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="17aaf-138">Optional element.</span></span><br /><br /> <span data-ttu-id="17aaf-139">定義視圖的寬（單一值）清單格式。</span><span class="sxs-lookup"><span data-stu-id="17aaf-139">Defines a wide (single value) list format for the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="17aaf-140">父元素</span><span class="sxs-lookup"><span data-stu-id="17aaf-140">Parent Elements</span></span>

|<span data-ttu-id="17aaf-141">元素</span><span class="sxs-lookup"><span data-stu-id="17aaf-141">Element</span></span>|<span data-ttu-id="17aaf-142">描述</span><span class="sxs-lookup"><span data-stu-id="17aaf-142">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="17aaf-143">ViewDefinitions 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="17aaf-143">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="17aaf-144">定義用來顯示物件的視圖。</span><span class="sxs-lookup"><span data-stu-id="17aaf-144">Defines the views used to display objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="17aaf-145">備註</span><span class="sxs-lookup"><span data-stu-id="17aaf-145">Remarks</span></span>

<span data-ttu-id="17aaf-146">如需不同視圖和自訂控制項之元件的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="17aaf-146">For more information about the components of different views and custom controls, see the following topics:</span></span>

- [<span data-ttu-id="17aaf-147">資料表視圖元件</span><span class="sxs-lookup"><span data-stu-id="17aaf-147">Table View Components</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="17aaf-148">清單視圖元件</span><span class="sxs-lookup"><span data-stu-id="17aaf-148">List View Components</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="17aaf-149">寬視圖元件</span><span class="sxs-lookup"><span data-stu-id="17aaf-149">Wide View Components</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="17aaf-150">自訂控制項</span><span class="sxs-lookup"><span data-stu-id="17aaf-150">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="17aaf-151">範例</span><span class="sxs-lookup"><span data-stu-id="17aaf-151">Example</span></span>

<span data-ttu-id="17aaf-152">這個範例會顯示定義[system.serviceprocess.dll. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)物件之資料表視圖的 `View` 元素。</span><span class="sxs-lookup"><span data-stu-id="17aaf-152">This example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="17aaf-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17aaf-153">See Also</span></span>

[<span data-ttu-id="17aaf-154">ViewDefinitions 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="17aaf-154">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="17aaf-155">View 的 Name 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="17aaf-155">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)

[<span data-ttu-id="17aaf-156">ViewSelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="17aaf-156">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="17aaf-157">View 的 Controls 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="17aaf-157">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="17aaf-158">View 的 GroupBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="17aaf-158">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="17aaf-159">TableControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="17aaf-159">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="17aaf-160">ListControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="17aaf-160">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="17aaf-161">WideControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="17aaf-161">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="17aaf-162">CustomControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="17aaf-162">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="17aaf-163">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="17aaf-163">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
