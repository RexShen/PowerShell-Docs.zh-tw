---
ms.date: 09/13/2016
ms.topic: reference
title: 建立寬型檢視
description: 建立寬型檢視
ms.openlocfilehash: 4230ef91a3612e962b2773b12e8016df6f760eae
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655604"
---
# <a name="creating-a-wide-view"></a><span data-ttu-id="1ee9f-103">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="1ee9f-103">Creating a Wide View</span></span>

<span data-ttu-id="1ee9f-104">寬型視圖會顯示每個顯示物件的單一值。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-104">A wide view displays a single value for each object that is displayed.</span></span> <span data-ttu-id="1ee9f-105">顯示的值可以是 .NET 物件屬性的值或腳本的值。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-105">The displayed value can be the value of a .NET object property or the value of a script.</span></span> <span data-ttu-id="1ee9f-106">根據預設，此視圖沒有標籤或標頭。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-106">By default, there is no label or header for this view.</span></span>

## <a name="a-wide-view-display"></a><span data-ttu-id="1ee9f-107">寬視圖顯示</span><span class="sxs-lookup"><span data-stu-id="1ee9f-107">A Wide View Display</span></span>

<span data-ttu-id="1ee9f-108">下列範例顯示 Windows PowerShell 如何顯示在將其輸出輸送至[全格式](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide)Cmdlet 時，由[取得](/powershell/module/Microsoft.PowerShell.Management/Get-Process)程式 Cmdlet 傳回的[system.object](/dotnet/api/System.Diagnostics.Process)物件。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-108">The following example shows how Windows PowerShell displays the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object that is returned by the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet when its output is piped to the [Format-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet.</span></span> <span data-ttu-id="1ee9f-109"> (根據預設， [取得程式](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Cmdlet 會傳回資料表視圖。在此範例中，) 這兩個數據行用來顯示每個傳回物件之進程的名稱。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-109">(By default, the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns a table view.) In this example, the two columns are used to display the name of the process for each returned object.</span></span> <span data-ttu-id="1ee9f-110">不會顯示物件屬性的名稱，只會顯示內容的值。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-110">The name of the object's property is not displayed, only the value of the property.</span></span>

```
Get-Process | format-wide
AEADISRV                     agrsmsvc
Ati2evxx                     Ati2evxx
audiodg                      CCC
CcmExec                      communicator
Crypserv                     csrss
csrss                        DevDtct2
DM1Service                   dpupdchk
dwm                          DxStudio
EXCEL                        explorer
GoogleToolbarNotifier        GrooveMonitor
hpqwmiex                     hpservice
Idle                         InoRpc
InoRT                        InoTask
ipoint                       lsass
lsm                          MOM
MSASCui                      notepad
...                          ...

```

## <a name="defining-the-wide-view"></a><span data-ttu-id="1ee9f-111">定義寬視圖</span><span class="sxs-lookup"><span data-stu-id="1ee9f-111">Defining the Wide View</span></span>

<span data-ttu-id="1ee9f-112">下列 XML 會顯示適用于 [system.object](/dotnet/api/System.Diagnostics.Process) 物件的廣泛視圖架構。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-112">The following XML shows the wide view schema for the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <GroupBy>...</GroupBy>
  <Controls>...</Controls>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

<span data-ttu-id="1ee9f-113">下列 XML 元素用來定義寬視圖：</span><span class="sxs-lookup"><span data-stu-id="1ee9f-113">The following XML elements are used to define a wide view:</span></span>

- <span data-ttu-id="1ee9f-114">[View](./view-element-format.md)元素是寬視圖的父元素。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-114">The [View](./view-element-format.md) element is the parent element of the wide view.</span></span> <span data-ttu-id="1ee9f-115"> (這是資料表、清單和自訂控制項視圖的相同父元素。 ) </span><span class="sxs-lookup"><span data-stu-id="1ee9f-115">(This is the same parent element for the table, list, and custom control views.)</span></span>

- <span data-ttu-id="1ee9f-116">[Name](./name-element-for-view-format.md)元素會指定視圖的名稱。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-116">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="1ee9f-117">所有視圖都需要這個元素。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-117">This element is required for all views.</span></span>

- <span data-ttu-id="1ee9f-118">[ViewSelectedBy](./viewselectedby-element-format.md)元素會定義使用 view 的物件。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-118">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="1ee9f-119">這個元素是必要的。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-119">This element is required.</span></span>

- <span data-ttu-id="1ee9f-120">[GroupBy](./groupby-element-for-view-format.md)元素會定義何時會顯示新的物件群組。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-120">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="1ee9f-121">每當特定屬性或腳本的值變更時，就會啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-121">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="1ee9f-122">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-122">This element is optional.</span></span>

- <span data-ttu-id="1ee9f-123">[Controls](./controls-element-for-view-format.md)元素定義由寬視圖定義的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-123">The [Controls](./controls-element-for-view-format.md) elements defines the custom controls that are defined by the wide view.</span></span> <span data-ttu-id="1ee9f-124">控制項可讓您進一步指定顯示資料的方式。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-124">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="1ee9f-125">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-125">This element is optional.</span></span> <span data-ttu-id="1ee9f-126">View 可以定義自己的自訂控制項，也可以使用格式檔案中任何視圖都可使用的通用控制項。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-126">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="1ee9f-127">如需自訂控制項的詳細資訊，請參閱 [建立自訂控制項](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-127">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="1ee9f-128">[WideControl](./widecontrol-element-format.md)元素和其子項目會定義要顯示在視圖中的內容。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-128">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span> <span data-ttu-id="1ee9f-129">在上述範例中，視圖是設計來顯示 [Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) 屬性。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-129">In the preceding example, the view is designed to display the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span>

<span data-ttu-id="1ee9f-130">如需完整格式化檔案的範例，以定義簡單的全視圖，請參閱 [wide (基本) ](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-130">For an example of a complete formatting file that defines a simple wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-wide-view"></a><span data-ttu-id="1ee9f-131">為您的寬視野提供定義</span><span class="sxs-lookup"><span data-stu-id="1ee9f-131">Providing Definitions for Your Wide View</span></span>

<span data-ttu-id="1ee9f-132">寬型視圖可以使用 [WideControl](./widecontrol-element-format.md) 元素的子項目來提供一或多個定義。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-132">Wide views can provide one or more definitions by using the child elements of the [WideControl](./widecontrol-element-format.md) element.</span></span> <span data-ttu-id="1ee9f-133">一般而言，視圖只會有一個定義。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-133">Typically, a view will have only one definition.</span></span> <span data-ttu-id="1ee9f-134">在下列範例中，視圖會提供單一定義，以顯示 [Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-134">In the following example, the view provides a single definition that displays the value of the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span> <span data-ttu-id="1ee9f-135">寬型視圖可以顯示內容的值或腳本的值 (未顯示在範例) 中。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-135">A wide view can display the value of a property or the value of a script (not shown in the example).</span></span>

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber></ColumnNumber>
  <WideEntries>
    <WideEntry>
      <WideItem>
        <PropertyName>ProcessName</PropertyName>
      </WideItem>
    </WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="1ee9f-136">下列 XML 元素可用來提供廣泛視圖的定義：</span><span class="sxs-lookup"><span data-stu-id="1ee9f-136">The following XML elements can be used to provide definitions for a wide view:</span></span>

- <span data-ttu-id="1ee9f-137">[WideControl](./widecontrol-element-format.md)元素和其子項目會定義要顯示在視圖中的內容。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-137">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="1ee9f-138">[AutoSize](./autosize-element-for-widecontrol-format.md)元素會指定資料行大小和資料行數目是否根據資料的大小進行調整。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-138">The [AutoSize](./autosize-element-for-widecontrol-format.md) element specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span> <span data-ttu-id="1ee9f-139">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-139">This element is optional.</span></span>

- <span data-ttu-id="1ee9f-140">[ColumnNumber](./columnnumber-element-for-widecontrol-format.md)元素會指定在寬視圖中顯示的資料行數目。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-140">The [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element specifies the number of columns displayed in the wide view.</span></span> <span data-ttu-id="1ee9f-141">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-141">This element is optional.</span></span>

- <span data-ttu-id="1ee9f-142">[WideEntries](./wideentries-element-for-widecontrol-format.md)元素會提供視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-142">The [WideEntries](./wideentries-element-for-widecontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="1ee9f-143">在大部分的情況下，view 只會有一個定義。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-143">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="1ee9f-144">這個元素是必要的。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-144">This element is required.</span></span>

- <span data-ttu-id="1ee9f-145">[WideEntry](./wideentry-element-for-widecontrol-format.md)元素會提供視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-145">The [WideEntry](./wideentry-element-for-widecontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="1ee9f-146">至少需要一個 [WideEntry](./wideentry-element-for-widecontrol-format.md) ;不過，您可以新增的元素數目沒有最大限制。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-146">At least one [WideEntry](./wideentry-element-for-widecontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="1ee9f-147">在大部分的情況下，view 只會有一個定義。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-147">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="1ee9f-148">[之 entryselectedby](./entryselectedby-element-for-wideentry-format.md)元素會指定特定定義所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-148">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="1ee9f-149">這個元素是選擇性的，只有當您定義多個顯示不同物件的 [WideEntry](./wideentry-element-for-widecontrol-format.md) 專案時，才需要此專案。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-149">This element is optional and is needed only when you define multiple [WideEntry](./wideentry-element-for-widecontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="1ee9f-150">[之 wideitem](./wideitem-element-for-widecontrol-format.md)元素會指定視圖所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-150">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span> <span data-ttu-id="1ee9f-151">相較于其他類型的視圖，寬控制項只能顯示一個專案。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-151">In contrast to other types of views, a wide control can display only one item.</span></span>

- <span data-ttu-id="1ee9f-152">[PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md)元素會指定屬性，其值會由視圖顯示。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-152">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="1ee9f-153">您必須指定屬性或腳本，但不能同時指定這兩種方法。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-153">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="1ee9f-154">[ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md)元素會指定由視圖顯示其值的腳本。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-154">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="1ee9f-155">您必須指定腳本或屬性，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-155">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="1ee9f-156">[格式格式](./formatstring-element-for-wideitem-for-widecontrol-format.md)元素會指定用來顯示資料的模式。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-156">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a pattern that is used to display the data.</span></span> <span data-ttu-id="1ee9f-157">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-157">This element is optional.</span></span>

<span data-ttu-id="1ee9f-158">如需定義寬視圖定義之完整格式化檔案的範例，請參閱 [wide (基本) ](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-158">For an example of a complete formatting file that defines a wide view definition, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-wide-view"></a><span data-ttu-id="1ee9f-159">定義使用廣泛視圖的物件</span><span class="sxs-lookup"><span data-stu-id="1ee9f-159">Defining the Objects That Use the Wide View</span></span>

<span data-ttu-id="1ee9f-160">有兩種方式可以定義使用寬視圖的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-160">There are two ways to define which .NET objects use the wide view.</span></span> <span data-ttu-id="1ee9f-161">您可以使用 [ViewSelectedBy](./viewselectedby-element-format.md) 專案來定義可由視圖的所有定義顯示的物件，或者，您可以使用 [之 entryselectedby](./entryselectedby-element-for-wideentry-format.md) 元素來定義由視圖的特定定義所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-161">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="1ee9f-162">在大部分的情況下，視圖只有一個定義，因此物件通常是由 [ViewSelectedBy](./viewselectedby-element-format.md) 元素定義。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-162">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="1ee9f-163">下列範例示範如何使用 [ViewSelectedBy](./viewselectedby-element-format.md) 和 [TypeName](./typename-element-for-viewselectedby-format.md) 元素，定義寬視圖所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-163">The following example shows how to define the objects that are displayed by the wide view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="1ee9f-164">您可以指定的 [TypeName](./typename-element-for-viewselectedby-format.md) 元素數目沒有任何限制，而且其順序並不重要。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-164">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="1ee9f-165">下列 XML 元素可用來指定寬視圖所使用的物件：</span><span class="sxs-lookup"><span data-stu-id="1ee9f-165">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="1ee9f-166">[ViewSelectedBy](./viewselectedby-element-format.md)元素會定義寬視圖所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-166">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="1ee9f-167">[TypeName](./typename-element-for-viewselectedby-format.md)元素會指定視圖所顯示的 .net。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-167">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the view.</span></span> <span data-ttu-id="1ee9f-168">需要完整的 .NET 型別名稱。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-168">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="1ee9f-169">您必須為此視圖指定至少一個類型或選取範圍，但無法指定的元素數目上限。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-169">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="1ee9f-170">如需完整格式化檔案的範例，請參閱 [Wide (基本) ](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-170">For an example of a complete formatting file, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

<span data-ttu-id="1ee9f-171">下列範例會使用 [ViewSelectedBy](./viewselectedby-element-format.md) 和 [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-171">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="1ee9f-172">如果您有一組相關的物件會使用多個視圖顯示，例如當您為相同的物件定義寬視圖和資料表視圖時，請使用選取集。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-172">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a wide view and a table view for the same objects.</span></span> <span data-ttu-id="1ee9f-173">如需有關如何建立選取範圍的詳細資訊，請參閱 [定義選取集合](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-173">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="1ee9f-174">下列 XML 元素可用來指定寬視圖所使用的物件：</span><span class="sxs-lookup"><span data-stu-id="1ee9f-174">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="1ee9f-175">[ViewSelectedBy](./viewselectedby-element-format.md)元素會定義寬視圖所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-175">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="1ee9f-176">[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素會指定可供視圖顯示的一組物件。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-176">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="1ee9f-177">您必須為此視圖指定至少一個選擇集或類型，但無法指定的元素數目上限。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-177">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="1ee9f-178">下列範例示範如何使用 [之 entryselectedby](./entryselectedby-element-for-wideentry-format.md) 元素，定義寬視圖的特定定義所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-178">The following example shows how to define the objects displayed by a specific definition of the wide view using the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element.</span></span> <span data-ttu-id="1ee9f-179">您可以使用這個專案，指定物件的 .NET 類型名稱、一組選取的物件，或指定使用定義時指定的選取條件。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-179">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="1ee9f-180">如需如何建立選取條件的詳細資訊，請參閱 [定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-180">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

<span data-ttu-id="1ee9f-181">下列 XML 元素可用來指定廣泛視圖的特定定義所使用的物件：</span><span class="sxs-lookup"><span data-stu-id="1ee9f-181">The following XML elements can be used to specify the objects that are used by a specific definition of the wide view:</span></span>

- <span data-ttu-id="1ee9f-182">[之 entryselectedby](./entryselectedby-element-for-wideentry-format.md)元素會定義定義所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-182">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="1ee9f-183">[TypeName](./typename-element-for-viewselectedby-format.md)元素會指定定義所顯示的 .net。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-183">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the definition.</span></span> <span data-ttu-id="1ee9f-184">使用這個專案時，需要完整的 .NET 型別名稱。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-184">When using this element the fully qualified .NET type name is required.</span></span> <span data-ttu-id="1ee9f-185">您必須為定義指定至少一個類型、選取集或選取條件，但無法指定的元素數目上限。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-185">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="1ee9f-186">[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素 (未顯示) 指定可由此定義顯示的一組物件。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-186">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="1ee9f-187">您必須為定義指定至少一個類型、選取集或選取條件，但無法指定的元素數目上限。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-187">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="1ee9f-188">[SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)元素 (未顯示) 指定必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-188">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="1ee9f-189">您必須為定義指定至少一個類型、選取集或選取條件，但無法指定的元素數目上限。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-189">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="1ee9f-190">如需定義選取條件的詳細資訊，請參閱 [定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-190">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-wide-view"></a><span data-ttu-id="1ee9f-191">在寬型視圖中顯示物件群組</span><span class="sxs-lookup"><span data-stu-id="1ee9f-191">Displaying Groups of objects in a Wide View</span></span>

<span data-ttu-id="1ee9f-192">您可以將寬視圖所顯示的物件分隔成群組。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-192">You can separate the objects that are displayed by the wide view into groups.</span></span> <span data-ttu-id="1ee9f-193">這並不表示您定義了群組，只有當特定屬性或腳本的值變更時，Windows PowerShell 才會啟動新群組。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-193">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="1ee9f-194">下列範例會在 [system.serviceprocess.dll. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) 屬性的值變更時，啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-194">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="1ee9f-195">下列 XML 元素可用來定義何時啟動群組：</span><span class="sxs-lookup"><span data-stu-id="1ee9f-195">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="1ee9f-196">[GroupBy](./groupby-element-for-view-format.md)元素會定義可啟動新群組的屬性或腳本，並定義如何顯示群組。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-196">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="1ee9f-197">[PropertyName](./propertyname-element-for-groupby-format.md)元素會指定在其值變更時啟動新群組的屬性。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-197">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="1ee9f-198">您必須指定屬性或腳本來啟動群組，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-198">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="1ee9f-199">[ScriptBlock](./scriptblock-element-for-groupby-format.md)元素會指定在其值變更時啟動新群組的腳本。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-199">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="1ee9f-200">您必須指定腳本或屬性來啟動群組，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-200">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="1ee9f-201">[Label](./label-element-for-groupby-format.md)元素會定義在每個群組的開頭顯示的標籤。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-201">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="1ee9f-202">除了這個專案所指定的文字之外，Windows PowerShell 會顯示觸發新群組的值，並在標籤前後加上空白行。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-202">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="1ee9f-203">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-203">This element is optional.</span></span>

- <span data-ttu-id="1ee9f-204">[CustomControl](./customcontrol-element-for-groupby-format.md)元素會定義用來顯示資料的控制項。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-204">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="1ee9f-205">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-205">This element is optional.</span></span>

- <span data-ttu-id="1ee9f-206">[CustomControlName](./customcontrolname-element-for-groupby-format.md)元素會指定用來顯示資料的通用或視圖控制項。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-206">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="1ee9f-207">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-207">This element is optional.</span></span>

<span data-ttu-id="1ee9f-208">如需定義群組之完整格式化檔案的範例，請參閱 [Wide View (GroupBy) ](./wide-view-groupby.md)。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-208">For an example of a complete formatting file that defines groups, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="1ee9f-209">使用格式字串</span><span class="sxs-lookup"><span data-stu-id="1ee9f-209">Using Format Strings</span></span>

<span data-ttu-id="1ee9f-210">您可以將格式化字串新增到廣泛的視圖，以進一步定義資料的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-210">Formatting strings can be added to a wide view to further define how the data is displayed.</span></span> <span data-ttu-id="1ee9f-211">下列範例顯示如何定義屬性值的格式化字串 `StartTime` 。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-211">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

<span data-ttu-id="1ee9f-212">下列 XML 元素可以用來指定格式模式：</span><span class="sxs-lookup"><span data-stu-id="1ee9f-212">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="1ee9f-213">[之 wideitem](./wideitem-element-for-widecontrol-format.md)元素會指定視圖所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-213">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="1ee9f-214">[PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md)元素會指定屬性，其值會由視圖顯示。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-214">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="1ee9f-215">您必須指定屬性或腳本，但不能同時指定這兩種方法。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-215">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="1ee9f-216">格式 [值元素指定](./formatstring-element-for-wideitem-for-widecontrol-format.md) 的格式模式定義屬性或腳本值在視圖中的顯示方式</span><span class="sxs-lookup"><span data-stu-id="1ee9f-216">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view</span></span>

- <span data-ttu-id="1ee9f-217"> (不會顯示 [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) 元素) 指定由視圖顯示其值的腳本。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-217">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="1ee9f-218">您必須指定腳本或屬性，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-218">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="1ee9f-219">在下列範例中， `ToString` 會呼叫方法來格式化腳本的值。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-219">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="1ee9f-220">腳本可以呼叫物件的任何方法。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-220">Scripts can call any method of an object.</span></span> <span data-ttu-id="1ee9f-221">因此，如果物件具有具有格式化參數的方法（例如 `ToString` ），則腳本可以呼叫該方法來格式化腳本的輸出值。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-221">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

<span data-ttu-id="1ee9f-222">下列 XML 元素可以用來呼叫 `ToString` 方法：</span><span class="sxs-lookup"><span data-stu-id="1ee9f-222">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="1ee9f-223">[之 wideitem](./wideitem-element-for-widecontrol-format.md)元素會指定視圖所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-223">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="1ee9f-224"> (不會顯示 [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) 元素) 指定由視圖顯示其值的腳本。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-224">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="1ee9f-225">您必須指定腳本或屬性，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="1ee9f-225">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="1ee9f-226">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ee9f-226">See Also</span></span>

[<span data-ttu-id="1ee9f-227">寬型檢視 (基本)</span><span class="sxs-lookup"><span data-stu-id="1ee9f-227">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="1ee9f-228">寬型檢視 (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="1ee9f-228">Wide View (GroupBy)</span></span>](./wide-view-groupby.md)

[<span data-ttu-id="1ee9f-229">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="1ee9f-229">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
