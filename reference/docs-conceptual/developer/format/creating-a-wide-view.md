---
title: 建立寬視圖 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0cf6a35201c47e4b12dd160191570eccec3427ef
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786130"
---
# <a name="creating-a-wide-view"></a><span data-ttu-id="87f26-102">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="87f26-102">Creating a Wide View</span></span>

<span data-ttu-id="87f26-103">寬型視圖會針對每個顯示的物件顯示單一值。</span><span class="sxs-lookup"><span data-stu-id="87f26-103">A wide view displays a single value for each object that is displayed.</span></span> <span data-ttu-id="87f26-104">顯示的值可以是 .NET 物件屬性的值或腳本的值。</span><span class="sxs-lookup"><span data-stu-id="87f26-104">The displayed value can be the value of a .NET object property or the value of a script.</span></span> <span data-ttu-id="87f26-105">根據預設，沒有此視圖的標籤或標頭。</span><span class="sxs-lookup"><span data-stu-id="87f26-105">By default, there is no label or header for this view.</span></span>

## <a name="a-wide-view-display"></a><span data-ttu-id="87f26-106">寬視圖顯示</span><span class="sxs-lookup"><span data-stu-id="87f26-106">A Wide View Display</span></span>

<span data-ttu-id="87f26-107">下列範例示範 Windows PowerShell 如何顯示由[取得處理](/powershell/module/Microsoft.PowerShell.Management/Get-Process)程式 Cmdlet 將其輸出輸送至[全格式](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide)的 Cmdlet 時，所傳回的[system.servicemodel 物件。](/dotnet/api/System.Diagnostics.Process)</span><span class="sxs-lookup"><span data-stu-id="87f26-107">The following example shows how Windows PowerShell displays the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object that is returned by the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet when its output is piped to the [Format-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet.</span></span> <span data-ttu-id="87f26-108"> (預設會傳回資料表視圖[。在此](/powershell/module/Microsoft.PowerShell.Management/Get-Process)範例中 ) ，這兩個數據行是用來顯示每個傳回物件的進程名稱。</span><span class="sxs-lookup"><span data-stu-id="87f26-108">(By default, the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns a table view.) In this example, the two columns are used to display the name of the process for each returned object.</span></span> <span data-ttu-id="87f26-109">物件的屬性名稱不會顯示，只有屬性的值。</span><span class="sxs-lookup"><span data-stu-id="87f26-109">The name of the object's property is not displayed, only the value of the property.</span></span>

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

## <a name="defining-the-wide-view"></a><span data-ttu-id="87f26-110">定義全形視圖</span><span class="sxs-lookup"><span data-stu-id="87f26-110">Defining the Wide View</span></span>

<span data-ttu-id="87f26-111">下列 XML 顯示[system.object](/dotnet/api/System.Diagnostics.Process)物件的寬視圖架構。</span><span class="sxs-lookup"><span data-stu-id="87f26-111">The following XML shows the wide view schema for the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

<span data-ttu-id="87f26-112">下列 XML 元素可用來定義寬視圖：</span><span class="sxs-lookup"><span data-stu-id="87f26-112">The following XML elements are used to define a wide view:</span></span>

- <span data-ttu-id="87f26-113">[View](./view-element-format.md)元素是寬視圖的父元素。</span><span class="sxs-lookup"><span data-stu-id="87f26-113">The [View](./view-element-format.md) element is the parent element of the wide view.</span></span> <span data-ttu-id="87f26-114"> (這是資料表、清單和自訂控制項視圖的相同父元素。 ) </span><span class="sxs-lookup"><span data-stu-id="87f26-114">(This is the same parent element for the table, list, and custom control views.)</span></span>

- <span data-ttu-id="87f26-115">[Name](./name-element-for-view-format.md)元素會指定視圖的名稱。</span><span class="sxs-lookup"><span data-stu-id="87f26-115">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="87f26-116">所有的視圖都需要此元素。</span><span class="sxs-lookup"><span data-stu-id="87f26-116">This element is required for all views.</span></span>

- <span data-ttu-id="87f26-117">[ViewSelectedBy](./viewselectedby-element-format.md)元素會定義使用此視圖的物件。</span><span class="sxs-lookup"><span data-stu-id="87f26-117">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="87f26-118">這個元素是必要的。</span><span class="sxs-lookup"><span data-stu-id="87f26-118">This element is required.</span></span>

- <span data-ttu-id="87f26-119">[GroupBy](./groupby-element-for-view-format.md)元素會定義何時顯示新的物件群組。</span><span class="sxs-lookup"><span data-stu-id="87f26-119">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="87f26-120">每當特定屬性或腳本的值變更時，就會啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="87f26-120">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="87f26-121">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="87f26-121">This element is optional.</span></span>

- <span data-ttu-id="87f26-122">[Controls](./controls-element-for-view-format.md)元素會定義寬視圖所定義的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="87f26-122">The [Controls](./controls-element-for-view-format.md) elements defines the custom controls that are defined by the wide view.</span></span> <span data-ttu-id="87f26-123">控制項可讓您進一步指定資料的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="87f26-123">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="87f26-124">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="87f26-124">This element is optional.</span></span> <span data-ttu-id="87f26-125">View 可以定義自己的自訂控制項，也可以使用格式檔案中任何視圖可以使用的通用控制項。</span><span class="sxs-lookup"><span data-stu-id="87f26-125">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="87f26-126">如需自訂控制項的詳細資訊，請參閱[建立自訂控制項](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="87f26-126">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="87f26-127">[WideControl](./widecontrol-element-format.md)元素及其子項目會定義要在視圖中顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="87f26-127">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span> <span data-ttu-id="87f26-128">在上述範例中，此視圖設計為顯示[Processname](/dotnet/api/System.Diagnostics.Process.ProcessName)屬性。</span><span class="sxs-lookup"><span data-stu-id="87f26-128">In the preceding example, the view is designed to display the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span>

<span data-ttu-id="87f26-129">如需定義簡單寬視圖的完整格式檔案範例，請參閱[Wide view (基本) ](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="87f26-129">For an example of a complete formatting file that defines a simple wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-wide-view"></a><span data-ttu-id="87f26-130">提供全形視圖的定義</span><span class="sxs-lookup"><span data-stu-id="87f26-130">Providing Definitions for Your Wide View</span></span>

<span data-ttu-id="87f26-131">寬視圖可以使用[WideControl](./widecontrol-element-format.md)專案的子專案來提供一或多個定義。</span><span class="sxs-lookup"><span data-stu-id="87f26-131">Wide views can provide one or more definitions by using the child elements of the [WideControl](./widecontrol-element-format.md) element.</span></span> <span data-ttu-id="87f26-132">一般而言，視圖只會有一個定義。</span><span class="sxs-lookup"><span data-stu-id="87f26-132">Typically, a view will have only one definition.</span></span> <span data-ttu-id="87f26-133">在下列範例中，此視圖提供單一定義來顯示[Processname](/dotnet/api/System.Diagnostics.Process.ProcessName)屬性的值。</span><span class="sxs-lookup"><span data-stu-id="87f26-133">In the following example, the view provides a single definition that displays the value of the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span> <span data-ttu-id="87f26-134">寬視圖可以顯示內容的值或腳本的值 (不會顯示在範例) 中。</span><span class="sxs-lookup"><span data-stu-id="87f26-134">A wide view can display the value of a property or the value of a script (not shown in the example).</span></span>

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

<span data-ttu-id="87f26-135">下列 XML 元素可以用來提供寬視圖的定義：</span><span class="sxs-lookup"><span data-stu-id="87f26-135">The following XML elements can be used to provide definitions for a wide view:</span></span>

- <span data-ttu-id="87f26-136">[WideControl](./widecontrol-element-format.md)元素及其子項目會定義要在視圖中顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="87f26-136">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="87f26-137">[AutoSize](./autosize-element-for-widecontrol-format.md)元素會指定資料行大小和資料行數目是否根據資料的大小來調整。</span><span class="sxs-lookup"><span data-stu-id="87f26-137">The [AutoSize](./autosize-element-for-widecontrol-format.md) element specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span> <span data-ttu-id="87f26-138">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="87f26-138">This element is optional.</span></span>

- <span data-ttu-id="87f26-139">[ColumnNumber](./columnnumber-element-for-widecontrol-format.md)元素會指定在寬視圖中顯示的資料行數目。</span><span class="sxs-lookup"><span data-stu-id="87f26-139">The [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element specifies the number of columns displayed in the wide view.</span></span> <span data-ttu-id="87f26-140">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="87f26-140">This element is optional.</span></span>

- <span data-ttu-id="87f26-141">[WideEntries](./wideentries-element-for-widecontrol-format.md)元素會提供視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="87f26-141">The [WideEntries](./wideentries-element-for-widecontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="87f26-142">在大部分的情況下，視圖只會有一個定義。</span><span class="sxs-lookup"><span data-stu-id="87f26-142">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="87f26-143">這個元素是必要的。</span><span class="sxs-lookup"><span data-stu-id="87f26-143">This element is required.</span></span>

- <span data-ttu-id="87f26-144">[WideEntry](./wideentry-element-for-widecontrol-format.md)元素會提供 view 的定義。</span><span class="sxs-lookup"><span data-stu-id="87f26-144">The [WideEntry](./wideentry-element-for-widecontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="87f26-145">至少需要一個[WideEntry](./wideentry-element-for-widecontrol-format.md) ;不過，您可以新增的專案數沒有最大限制。</span><span class="sxs-lookup"><span data-stu-id="87f26-145">At least one [WideEntry](./wideentry-element-for-widecontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="87f26-146">在大部分的情況下，視圖只會有一個定義。</span><span class="sxs-lookup"><span data-stu-id="87f26-146">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="87f26-147">[之 entryselectedby](./entryselectedby-element-for-wideentry-format.md)元素會指定特定定義所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="87f26-147">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="87f26-148">這個元素是選擇性的，只有當您定義多個[WideEntry](./wideentry-element-for-widecontrol-format.md)專案來顯示不同的物件時，才需要此專案。</span><span class="sxs-lookup"><span data-stu-id="87f26-148">This element is optional and is needed only when you define multiple [WideEntry](./wideentry-element-for-widecontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="87f26-149">[之 wideitem](./wideitem-element-for-widecontrol-format.md)元素會指定視圖所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="87f26-149">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span> <span data-ttu-id="87f26-150">相較于其他類型的視圖，寬型控制項只能顯示一個專案。</span><span class="sxs-lookup"><span data-stu-id="87f26-150">In contrast to other types of views, a wide control can display only one item.</span></span>

- <span data-ttu-id="87f26-151">[PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md)元素會指定屬性，其值會由視圖顯示。</span><span class="sxs-lookup"><span data-stu-id="87f26-151">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="87f26-152">您必須指定屬性或腳本，但不能同時指定這兩者。</span><span class="sxs-lookup"><span data-stu-id="87f26-152">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="87f26-153">[ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md)元素會指定由視圖顯示其值的腳本。</span><span class="sxs-lookup"><span data-stu-id="87f26-153">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="87f26-154">您必須指定腳本或屬性，但不能同時指定這兩者。</span><span class="sxs-lookup"><span data-stu-id="87f26-154">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="87f26-155">[[字串](./formatstring-element-for-wideitem-for-widecontrol-format.md)類型] 元素會指定用來顯示資料的模式。</span><span class="sxs-lookup"><span data-stu-id="87f26-155">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a pattern that is used to display the data.</span></span> <span data-ttu-id="87f26-156">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="87f26-156">This element is optional.</span></span>

<span data-ttu-id="87f26-157">如需定義寬視圖定義的完整格式檔案範例，請參閱[Wide view (基本) ](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="87f26-157">For an example of a complete formatting file that defines a wide view definition, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-wide-view"></a><span data-ttu-id="87f26-158">定義使用寬視圖的物件</span><span class="sxs-lookup"><span data-stu-id="87f26-158">Defining the Objects That Use the Wide View</span></span>

<span data-ttu-id="87f26-159">有兩種方式可定義哪些 .NET 物件使用寬視圖。</span><span class="sxs-lookup"><span data-stu-id="87f26-159">There are two ways to define which .NET objects use the wide view.</span></span> <span data-ttu-id="87f26-160">您可以使用[ViewSelectedBy](./viewselectedby-element-format.md)專案來定義可由視圖的所有定義顯示的物件，也可以使用[之 entryselectedby](./entryselectedby-element-for-wideentry-format.md)專案來定義由視圖的特定定義所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="87f26-160">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="87f26-161">在大部分情況下，一個 view 只有一個定義，因此物件通常是由[ViewSelectedBy](./viewselectedby-element-format.md)元素所定義。</span><span class="sxs-lookup"><span data-stu-id="87f26-161">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="87f26-162">下列範例示範如何使用[ViewSelectedBy](./viewselectedby-element-format.md)和[TypeName](./typename-element-for-viewselectedby-format.md)元素定義寬視圖所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="87f26-162">The following example shows how to define the objects that are displayed by the wide view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="87f26-163">您可以指定的[TypeName](./typename-element-for-viewselectedby-format.md)元素數目沒有限制，而且其順序並不重要。</span><span class="sxs-lookup"><span data-stu-id="87f26-163">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="87f26-164">下列 XML 元素可以用來指定寬視圖所使用的物件：</span><span class="sxs-lookup"><span data-stu-id="87f26-164">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="87f26-165">[ViewSelectedBy](./viewselectedby-element-format.md)元素會定義寬視圖所要顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="87f26-165">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="87f26-166">[TypeName](./typename-element-for-viewselectedby-format.md)元素會指定視圖所顯示的 .net。</span><span class="sxs-lookup"><span data-stu-id="87f26-166">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the view.</span></span> <span data-ttu-id="87f26-167">需要完整的 .NET 類型名稱。</span><span class="sxs-lookup"><span data-stu-id="87f26-167">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="87f26-168">您必須為此視圖指定至少一個類型或選取範圍，但不能指定的元素數目上限。</span><span class="sxs-lookup"><span data-stu-id="87f26-168">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="87f26-169">如需完整格式檔案的範例，請參閱[Wide View (Basic) ](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="87f26-169">For an example of a complete formatting file, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

<span data-ttu-id="87f26-170">下列範例會使用[ViewSelectedBy](./viewselectedby-element-format.md)和[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="87f26-170">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="87f26-171">使用 [選取專案集]，您可以在其中擁有一組使用多個視圖顯示的相關物件，例如當您為相同的物件定義寬視圖和資料表視圖時。</span><span class="sxs-lookup"><span data-stu-id="87f26-171">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a wide view and a table view for the same objects.</span></span> <span data-ttu-id="87f26-172">如需有關如何建立選擇集的詳細資訊，請參閱[定義選取範圍集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="87f26-172">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="87f26-173">下列 XML 元素可以用來指定寬視圖所使用的物件：</span><span class="sxs-lookup"><span data-stu-id="87f26-173">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="87f26-174">[ViewSelectedBy](./viewselectedby-element-format.md)元素會定義寬視圖所要顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="87f26-174">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="87f26-175">[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素會指定一組可由視圖顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="87f26-175">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="87f26-176">您必須為此視圖指定至少一個選取範圍或類型，但不能指定的元素數目上限。</span><span class="sxs-lookup"><span data-stu-id="87f26-176">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="87f26-177">下列範例示範如何使用[之 entryselectedby](./entryselectedby-element-for-wideentry-format.md)專案，定義以寬視圖的特定定義所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="87f26-177">The following example shows how to define the objects displayed by a specific definition of the wide view using the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element.</span></span> <span data-ttu-id="87f26-178">使用這個專案，您可以指定物件的 .NET 型別名稱、物件的選擇集，或指定何時使用定義的選取條件。</span><span class="sxs-lookup"><span data-stu-id="87f26-178">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="87f26-179">如需如何建立選取條件的詳細資訊，請參閱[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="87f26-179">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

<span data-ttu-id="87f26-180">下列 XML 元素可以用來指定寬視圖的特定定義所使用的物件：</span><span class="sxs-lookup"><span data-stu-id="87f26-180">The following XML elements can be used to specify the objects that are used by a specific definition of the wide view:</span></span>

- <span data-ttu-id="87f26-181">[之 entryselectedby](./entryselectedby-element-for-wideentry-format.md)元素會定義定義要顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="87f26-181">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="87f26-182">[TypeName](./typename-element-for-viewselectedby-format.md)元素會指定定義所顯示的 .net。</span><span class="sxs-lookup"><span data-stu-id="87f26-182">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the definition.</span></span> <span data-ttu-id="87f26-183">使用此元素時，需要完整的 .NET 類型名稱。</span><span class="sxs-lookup"><span data-stu-id="87f26-183">When using this element the fully qualified .NET type name is required.</span></span> <span data-ttu-id="87f26-184">您必須為定義至少指定一個類型、選擇集或選取條件，但不能指定的元素數目上限。</span><span class="sxs-lookup"><span data-stu-id="87f26-184">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="87f26-185">[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素 (不會顯示) 指定一組可由這個定義顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="87f26-185">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="87f26-186">您必須為定義至少指定一個類型、選擇集或選取條件，但不能指定的元素數目上限。</span><span class="sxs-lookup"><span data-stu-id="87f26-186">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="87f26-187">[SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)元素 (不會顯示) 指定必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="87f26-187">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="87f26-188">您必須為定義至少指定一個類型、選擇集或選取條件，但不能指定的元素數目上限。</span><span class="sxs-lookup"><span data-stu-id="87f26-188">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="87f26-189">如需定義選取條件的詳細資訊，請參閱[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="87f26-189">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-wide-view"></a><span data-ttu-id="87f26-190">以寬視圖顯示物件群組</span><span class="sxs-lookup"><span data-stu-id="87f26-190">Displaying Groups of objects in a Wide View</span></span>

<span data-ttu-id="87f26-191">您可以將寬視圖所顯示的物件分隔成群組。</span><span class="sxs-lookup"><span data-stu-id="87f26-191">You can separate the objects that are displayed by the wide view into groups.</span></span> <span data-ttu-id="87f26-192">這並不表示您定義群組，只有當特定屬性或腳本的值變更時，Windows PowerShell 才會啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="87f26-192">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="87f26-193">在下列範例中，每當 [ [system.serviceprocess.dll. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) ] 屬性的值變更時，就會啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="87f26-193">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="87f26-194">下列 XML 元素可用來定義何時啟動群組：</span><span class="sxs-lookup"><span data-stu-id="87f26-194">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="87f26-195">[GroupBy](./groupby-element-for-view-format.md)元素會定義啟動新群組的屬性或腳本，並定義群組的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="87f26-195">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="87f26-196">[PropertyName](./propertyname-element-for-groupby-format.md)元素會指定在每次其值變更時啟動新群組的屬性。</span><span class="sxs-lookup"><span data-stu-id="87f26-196">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="87f26-197">您必須指定要啟動群組的屬性或腳本，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="87f26-197">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="87f26-198">[ScriptBlock](./scriptblock-element-for-groupby-format.md)元素會指定在每次其值變更時啟動新群組的腳本。</span><span class="sxs-lookup"><span data-stu-id="87f26-198">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="87f26-199">您必須指定腳本或屬性來啟動群組，但不能同時指定這兩者。</span><span class="sxs-lookup"><span data-stu-id="87f26-199">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="87f26-200">[Label](./label-element-for-groupby-format.md)元素會定義在每個群組的開頭顯示的標籤。</span><span class="sxs-lookup"><span data-stu-id="87f26-200">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="87f26-201">除了此元素所指定的文字之外，Windows PowerShell 還會顯示觸發新群組的值，並在標籤前後加上空白行。</span><span class="sxs-lookup"><span data-stu-id="87f26-201">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="87f26-202">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="87f26-202">This element is optional.</span></span>

- <span data-ttu-id="87f26-203">[CustomControl](./customcontrol-element-for-groupby-format.md)元素會定義用來顯示資料的控制項。</span><span class="sxs-lookup"><span data-stu-id="87f26-203">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="87f26-204">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="87f26-204">This element is optional.</span></span>

- <span data-ttu-id="87f26-205">[CustomControlName](./customcontrolname-element-for-groupby-format.md)元素會指定用來顯示資料的通用或 view 控制項。</span><span class="sxs-lookup"><span data-stu-id="87f26-205">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="87f26-206">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="87f26-206">This element is optional.</span></span>

<span data-ttu-id="87f26-207">如需定義群組之完整格式檔案的範例，請參閱[Wide View (GroupBy) ](./wide-view-groupby.md)。</span><span class="sxs-lookup"><span data-stu-id="87f26-207">For an example of a complete formatting file that defines groups, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="87f26-208">使用格式字串</span><span class="sxs-lookup"><span data-stu-id="87f26-208">Using Format Strings</span></span>

<span data-ttu-id="87f26-209">將字串格式化可以加入至寬視圖，以進一步定義資料的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="87f26-209">Formatting strings can be added to a wide view to further define how the data is displayed.</span></span> <span data-ttu-id="87f26-210">下列範例顯示如何為屬性的值定義格式化字串 `StartTime` 。</span><span class="sxs-lookup"><span data-stu-id="87f26-210">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

<span data-ttu-id="87f26-211">下列 XML 元素可以用來指定格式模式：</span><span class="sxs-lookup"><span data-stu-id="87f26-211">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="87f26-212">[之 wideitem](./wideitem-element-for-widecontrol-format.md)元素會指定視圖所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="87f26-212">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="87f26-213">[PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md)元素會指定屬性，其值會由視圖顯示。</span><span class="sxs-lookup"><span data-stu-id="87f26-213">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="87f26-214">您必須指定屬性或腳本，但不能同時指定這兩者。</span><span class="sxs-lookup"><span data-stu-id="87f26-214">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="87f26-215">[[字串](./formatstring-element-for-wideitem-for-widecontrol-format.md)類型] 元素會指定格式模式，以定義屬性或腳本值在視圖中的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="87f26-215">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view</span></span>

- <span data-ttu-id="87f26-216">[ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md)元素 (不會顯示) 指定由視圖顯示其值的腳本。</span><span class="sxs-lookup"><span data-stu-id="87f26-216">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="87f26-217">您必須指定腳本或屬性，但不能同時指定這兩者。</span><span class="sxs-lookup"><span data-stu-id="87f26-217">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="87f26-218">在下列範例中， `ToString` 會呼叫方法來格式化腳本的值。</span><span class="sxs-lookup"><span data-stu-id="87f26-218">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="87f26-219">腳本可以呼叫物件的任何方法。</span><span class="sxs-lookup"><span data-stu-id="87f26-219">Scripts can call any method of an object.</span></span> <span data-ttu-id="87f26-220">因此，如果物件具有具有格式化參數的方法（例如 `ToString` ），則腳本可以呼叫該方法來格式化腳本的輸出值。</span><span class="sxs-lookup"><span data-stu-id="87f26-220">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

<span data-ttu-id="87f26-221">下列 XML 元素可以用來呼叫 `ToString` 方法：</span><span class="sxs-lookup"><span data-stu-id="87f26-221">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="87f26-222">[之 wideitem](./wideitem-element-for-widecontrol-format.md)元素會指定視圖所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="87f26-222">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="87f26-223">[ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md)元素 (不會顯示) 指定由視圖顯示其值的腳本。</span><span class="sxs-lookup"><span data-stu-id="87f26-223">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="87f26-224">您必須指定腳本或屬性，但不能同時指定這兩者。</span><span class="sxs-lookup"><span data-stu-id="87f26-224">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="87f26-225">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87f26-225">See Also</span></span>

[<span data-ttu-id="87f26-226">寬型檢視 (基本)</span><span class="sxs-lookup"><span data-stu-id="87f26-226">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="87f26-227">寬型檢視 (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="87f26-227">Wide View (GroupBy)</span></span>](./wide-view-groupby.md)

[<span data-ttu-id="87f26-228">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="87f26-228">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
