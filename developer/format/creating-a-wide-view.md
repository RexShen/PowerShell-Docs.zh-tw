---
title: 建立寬型檢視 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d4303c5-b451-4ccb-9831-b17a17ceac20
caps.latest.revision: 16
ms.openlocfilehash: 651de5d3bc2619f20438f3951ac5a8c4b0bf46d4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858494"
---
# <a name="creating-a-wide-view"></a><span data-ttu-id="b04cf-102">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="b04cf-102">Creating a Wide View</span></span>

<span data-ttu-id="b04cf-103">寬型檢視會顯示每個物件，會顯示單一值。</span><span class="sxs-lookup"><span data-stu-id="b04cf-103">A wide view displays a single value for each object that is displayed.</span></span> <span data-ttu-id="b04cf-104">顯示的值可以是.NET 物件屬性的值或值的指令碼。</span><span class="sxs-lookup"><span data-stu-id="b04cf-104">The displayed value can be the value of a .NET object property or the value of a script.</span></span> <span data-ttu-id="b04cf-105">根據預設，沒有任何標籤或標頭，此檢視。</span><span class="sxs-lookup"><span data-stu-id="b04cf-105">By default, there is no label or header for this view.</span></span>

## <a name="a-wide-view-display"></a><span data-ttu-id="b04cf-106">寬型檢視顯示</span><span class="sxs-lookup"><span data-stu-id="b04cf-106">A Wide View Display</span></span>

<span data-ttu-id="b04cf-107">下列範例會示範 Windows PowerShell 的會顯示[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)所傳回的物件[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet 時其輸出輸送到[Format-wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b04cf-107">The following example shows how Windows PowerShell displays the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object that is returned by the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet when its output is piped to the [Format-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet.</span></span> <span data-ttu-id="b04cf-108">(根據預設， [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)指令程式可傳回資料表的檢視。)在此範例中，兩個資料行用來顯示每個傳回的物件的程序的名稱。</span><span class="sxs-lookup"><span data-stu-id="b04cf-108">(By default, the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns a table view.) In this example, the two columns are used to display the name of the process for each returned object.</span></span> <span data-ttu-id="b04cf-109">未顯示物件的屬性名稱，屬性的值。</span><span class="sxs-lookup"><span data-stu-id="b04cf-109">The name of the object's property is not displayed, only the value of the property.</span></span>

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

## <a name="defining-the-wide-view"></a><span data-ttu-id="b04cf-110">定義的寬型檢視</span><span class="sxs-lookup"><span data-stu-id="b04cf-110">Defining the Wide View</span></span>

<span data-ttu-id="b04cf-111">下列 XML 顯示的寬型檢視結構描述[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)物件。</span><span class="sxs-lookup"><span data-stu-id="b04cf-111">The following XML shows the wide view schema for the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

<span data-ttu-id="b04cf-112">下列 XML 元素用來定義的寬型檢視中：</span><span class="sxs-lookup"><span data-stu-id="b04cf-112">The following XML elements are used to define a wide view:</span></span>

- <span data-ttu-id="b04cf-113">[檢視](./view-element-format.md)項目是寬型檢視的父項目。</span><span class="sxs-lookup"><span data-stu-id="b04cf-113">The [View](./view-element-format.md) element is the parent element of the wide view.</span></span> <span data-ttu-id="b04cf-114">（這是資料表、 清單和自訂的控制項檢視的相同父項目）。</span><span class="sxs-lookup"><span data-stu-id="b04cf-114">(This is the same parent element for the table, list, and custom control views.)</span></span>

- <span data-ttu-id="b04cf-115">[名稱](./name-element-for-view-format.md)項目會指定檢視的名稱。</span><span class="sxs-lookup"><span data-stu-id="b04cf-115">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="b04cf-116">所有檢視需要此項目。</span><span class="sxs-lookup"><span data-stu-id="b04cf-116">This element is required for all views.</span></span>

- <span data-ttu-id="b04cf-117">[ViewSelectedBy](./viewselectedby-element-format.md)項目會定義使用檢視的物件。</span><span class="sxs-lookup"><span data-stu-id="b04cf-117">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="b04cf-118">需要此項目。</span><span class="sxs-lookup"><span data-stu-id="b04cf-118">This element is required.</span></span>

- <span data-ttu-id="b04cf-119">[GroupBy](./groupby-element-for-view-format.md)項目會定義當物件的新群組就會顯示。</span><span class="sxs-lookup"><span data-stu-id="b04cf-119">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="b04cf-120">每次特定的屬性或指令碼的值變更時，會啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="b04cf-120">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="b04cf-121">這是選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="b04cf-121">This element is optional.</span></span>

- <span data-ttu-id="b04cf-122">[控制項](./controls-element-for-view-format.md)項目定義的寬型檢視所定義的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="b04cf-122">The [Controls](./controls-element-for-view-format.md) elements defines the custom controls that are defined by the wide view.</span></span> <span data-ttu-id="b04cf-123">控制項可讓您進一步指定 顯示資料的方式。</span><span class="sxs-lookup"><span data-stu-id="b04cf-123">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="b04cf-124">這是選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="b04cf-124">This element is optional.</span></span> <span data-ttu-id="b04cf-125">檢視可以定義自己的自訂控制項，或可以使用通用控制項，可供任何檢視中的格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="b04cf-125">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="b04cf-126">如需有關自訂控制項的詳細資訊，請參閱 <<c0> [ 建立自訂控制項](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="b04cf-126">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="b04cf-127">[WideControl](./widecontrol-element-format.md)元素和其子項目會定義在檢視中顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="b04cf-127">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span> <span data-ttu-id="b04cf-128">在上述範例中，檢視設計來顯示[System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName)屬性。</span><span class="sxs-lookup"><span data-stu-id="b04cf-128">In the preceding example, the view is designed to display the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span>

<span data-ttu-id="b04cf-129">如需完整的格式化檔案，定義簡單的寬型檢視的範例，請參閱 < [（基本） 的寬型檢視](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="b04cf-129">For an example of a complete formatting file that defines a simple wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-wide-view"></a><span data-ttu-id="b04cf-130">提供您的寬型檢視的定義</span><span class="sxs-lookup"><span data-stu-id="b04cf-130">Providing Definitions for Your Wide View</span></span>

<span data-ttu-id="b04cf-131">寬型檢視可以使用的子元素，提供一個或多個定義[WideControl](./widecontrol-element-format.md)項目。</span><span class="sxs-lookup"><span data-stu-id="b04cf-131">Wide views can provide one or more definitions by using the child elements of the [WideControl](./widecontrol-element-format.md) element.</span></span> <span data-ttu-id="b04cf-132">通常，檢視必須只有一個定義。</span><span class="sxs-lookup"><span data-stu-id="b04cf-132">Typically, a view will have only one definition.</span></span> <span data-ttu-id="b04cf-133">在下列範例中，此檢視會提供顯示的值的單一定義[System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName)屬性。</span><span class="sxs-lookup"><span data-stu-id="b04cf-133">In the following example, the view provides a single definition that displays the value of the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span> <span data-ttu-id="b04cf-134">寬型檢視可以顯示屬性的值或 （在範例中未顯示） 的指令碼的值。</span><span class="sxs-lookup"><span data-stu-id="b04cf-134">A wide view can display the value of a property or the value of a script (not shown in the example).</span></span>

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

<span data-ttu-id="b04cf-135">下列的 XML 項目可以用來提供的寬型檢視定義中：</span><span class="sxs-lookup"><span data-stu-id="b04cf-135">The following XML elements can be used to provide definitions for a wide view:</span></span>

- <span data-ttu-id="b04cf-136">[WideControl](./widecontrol-element-format.md)元素和其子項目會定義在檢視中顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="b04cf-136">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="b04cf-137">[AutoSize](./autosize-element-for-widecontrol-format.md)項目會指定是否資料行大小和資料行數目根據調整大小的資料大小。</span><span class="sxs-lookup"><span data-stu-id="b04cf-137">The [AutoSize](./autosize-element-for-widecontrol-format.md) element specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span> <span data-ttu-id="b04cf-138">這是選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="b04cf-138">This element is optional.</span></span>

- <span data-ttu-id="b04cf-139">[ColumnNumber](./columnnumber-element-for-widecontrol-format.md)項目會指定寬型檢視中顯示的資料行數目。</span><span class="sxs-lookup"><span data-stu-id="b04cf-139">The [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element specifies the number of columns displayed in the wide view.</span></span> <span data-ttu-id="b04cf-140">這是選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="b04cf-140">This element is optional.</span></span>

- <span data-ttu-id="b04cf-141">[WideEntries](./wideentries-element-for-widecontrol-format.md)項目會提供檢視的定義。</span><span class="sxs-lookup"><span data-stu-id="b04cf-141">The [WideEntries](./wideentries-element-for-widecontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="b04cf-142">在大部分情況下，檢視必須只有一個定義。</span><span class="sxs-lookup"><span data-stu-id="b04cf-142">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="b04cf-143">需要此項目。</span><span class="sxs-lookup"><span data-stu-id="b04cf-143">This element is required.</span></span>

- <span data-ttu-id="b04cf-144">[WideEntry](./wideentry-element-for-widecontrol-format.md)項目會提供檢視的定義。</span><span class="sxs-lookup"><span data-stu-id="b04cf-144">The [WideEntry](./wideentry-element-for-widecontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="b04cf-145">至少一個[WideEntry](./wideentry-element-for-widecontrol-format.md)是必要項; 不過，還有您可以新增的項目數沒有上限限制。</span><span class="sxs-lookup"><span data-stu-id="b04cf-145">At least one [WideEntry](./wideentry-element-for-widecontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="b04cf-146">在大部分情況下，檢視必須只有一個定義。</span><span class="sxs-lookup"><span data-stu-id="b04cf-146">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="b04cf-147">[EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md)項目會指定特定的定義所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="b04cf-147">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="b04cf-148">這個項目是選擇性的只有在您定義多個時，才需要[WideEntry](./wideentry-element-for-widecontrol-format.md)顯示不同的物件項目。</span><span class="sxs-lookup"><span data-stu-id="b04cf-148">This element is optional and is needed only when you define multiple [WideEntry](./wideentry-element-for-widecontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="b04cf-149">[WideItem](./wideitem-element-for-widecontrol-format.md)項目會指定檢視所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="b04cf-149">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span> <span data-ttu-id="b04cf-150">相較於其他類型的檢視，廣泛的控制項可以顯示一個項目。</span><span class="sxs-lookup"><span data-stu-id="b04cf-150">In contrast to other types of views, a wide control can display only one item.</span></span>

- <span data-ttu-id="b04cf-151">[PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md)項目會指定其值會顯示由檢視的屬性。</span><span class="sxs-lookup"><span data-stu-id="b04cf-151">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="b04cf-152">您必須指定屬性或指令碼，但您無法同時指定。</span><span class="sxs-lookup"><span data-stu-id="b04cf-152">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="b04cf-153">[ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md)項目會指定其值會顯示檢視指令碼。</span><span class="sxs-lookup"><span data-stu-id="b04cf-153">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="b04cf-154">您必須指定指令碼或屬性，但您無法同時指定。</span><span class="sxs-lookup"><span data-stu-id="b04cf-154">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="b04cf-155">[FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md)項目會指定用來顯示資料的模式。</span><span class="sxs-lookup"><span data-stu-id="b04cf-155">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a pattern that is used to display the data.</span></span> <span data-ttu-id="b04cf-156">這是選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="b04cf-156">This element is optional.</span></span>

<span data-ttu-id="b04cf-157">如需完整的格式化檔案定義的寬型檢視定義的範例，請參閱 < [（基本） 的寬型檢視](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="b04cf-157">For an example of a complete formatting file that defines a wide view definition, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-wide-view"></a><span data-ttu-id="b04cf-158">定義使用寬型檢視的物件</span><span class="sxs-lookup"><span data-stu-id="b04cf-158">Defining the Objects That Use the Wide View</span></span>

<span data-ttu-id="b04cf-159">有兩種方式可定義的.NET 物件使用寬型檢視。</span><span class="sxs-lookup"><span data-stu-id="b04cf-159">There are two ways to define which .NET objects use the wide view.</span></span> <span data-ttu-id="b04cf-160">您可以使用[ViewSelectedBy](./viewselectedby-element-format.md)項目來定義可顯示的檢視，或您的所有定義的物件可以使用[EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md)項目來定義會顯示哪些物件特定檢視的定義。</span><span class="sxs-lookup"><span data-stu-id="b04cf-160">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="b04cf-161">在大部分情況下，檢視有只有一個定義，因此物件通常會定義所[ViewSelectedBy](./viewselectedby-element-format.md)項目。</span><span class="sxs-lookup"><span data-stu-id="b04cf-161">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="b04cf-162">下列範例示範如何定義會顯示寬型檢視使用的物件[ViewSelectedBy](./viewselectedby-element-format.md)並[TypeName](./typename-element-for-viewselectedby-format.md)項目。</span><span class="sxs-lookup"><span data-stu-id="b04cf-162">The following example shows how to define the objects that are displayed by the wide view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="b04cf-163">沒有任何限制的數目[TypeName](./typename-element-for-viewselectedby-format.md) ，您可以指定，且其順序並不重要的項目。</span><span class="sxs-lookup"><span data-stu-id="b04cf-163">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="b04cf-164">下列的 XML 項目可以用來指定物件所使用的寬型檢視中：</span><span class="sxs-lookup"><span data-stu-id="b04cf-164">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="b04cf-165">[ViewSelectedBy](./viewselectedby-element-format.md)項目可讓您定義的寬型檢視會顯示哪些物件。</span><span class="sxs-lookup"><span data-stu-id="b04cf-165">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="b04cf-166">[TypeName](./typename-element-for-viewselectedby-format.md)項目會指定.NET 所顯示的檢視。</span><span class="sxs-lookup"><span data-stu-id="b04cf-166">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the view.</span></span> <span data-ttu-id="b04cf-167">需要完整的.NET 型別名稱。</span><span class="sxs-lookup"><span data-stu-id="b04cf-167">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="b04cf-168">您必須指定至少一個型別或設定檢視中，選取項目，但可以指定的項目沒有最大數目。</span><span class="sxs-lookup"><span data-stu-id="b04cf-168">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="b04cf-169">如需完整的格式化檔案的範例，請參閱 < [（基本） 的寬型檢視](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="b04cf-169">For an example of a complete formatting file, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

<span data-ttu-id="b04cf-170">下列範例會使用[ViewSelectedBy](./viewselectedby-element-format.md)並[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)項目。</span><span class="sxs-lookup"><span data-stu-id="b04cf-170">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="b04cf-171">使用選取項目集都有一組相關的物件，會顯示使用多個檢視，例如當您定義的寬型檢視和資料表檢視表相同的物件的位置。</span><span class="sxs-lookup"><span data-stu-id="b04cf-171">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a wide view and a table view for the same objects.</span></span> <span data-ttu-id="b04cf-172">如需如何建立選取項目集的詳細資訊，請參閱[定義的選取項目集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="b04cf-172">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="b04cf-173">下列的 XML 項目可以用來指定物件所使用的寬型檢視中：</span><span class="sxs-lookup"><span data-stu-id="b04cf-173">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="b04cf-174">[ViewSelectedBy](./viewselectedby-element-format.md)項目可讓您定義的寬型檢視會顯示哪些物件。</span><span class="sxs-lookup"><span data-stu-id="b04cf-174">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="b04cf-175">[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)項目會指定一組可以檢視所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="b04cf-175">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="b04cf-176">您必須指定至少一個選取項目集或類型檢視中，但您可以指定的項目沒有最大數目。</span><span class="sxs-lookup"><span data-stu-id="b04cf-176">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="b04cf-177">下列範例示範如何定義的寬型檢視使用特定定義所顯示的物件[EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md)項目。</span><span class="sxs-lookup"><span data-stu-id="b04cf-177">The following example shows how to define the objects displayed by a specific definition of the wide view using the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element.</span></span> <span data-ttu-id="b04cf-178">您可以使用這個項目，來指定物件、 選取項目集的物件或選取條件，指定當使用定義的.NET 型別名稱。</span><span class="sxs-lookup"><span data-stu-id="b04cf-178">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="b04cf-179">如需如何建立選取項目條件的詳細資訊，請參閱[定義的條件，顯示資料](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="b04cf-179">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

<span data-ttu-id="b04cf-180">下列的 XML 項目可用來指定特定的寬型檢視定義所使用的物件：</span><span class="sxs-lookup"><span data-stu-id="b04cf-180">The following XML elements can be used to specify the objects that are used by a specific definition of the wide view:</span></span>

- <span data-ttu-id="b04cf-181">[EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md)項目會定義哪些物件會定義所顯示。</span><span class="sxs-lookup"><span data-stu-id="b04cf-181">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="b04cf-182">[TypeName](./typename-element-for-viewselectedby-format.md)項目會指定.NET 所定義顯示。</span><span class="sxs-lookup"><span data-stu-id="b04cf-182">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the definition.</span></span> <span data-ttu-id="b04cf-183">使用此項目的完整的.NET 型別名稱時需要。</span><span class="sxs-lookup"><span data-stu-id="b04cf-183">When using this element the fully qualified .NET type name is required.</span></span> <span data-ttu-id="b04cf-184">您必須指定至少一個型別、 選取項目集或選擇條件的定義，但您可以指定的項目沒有最大數目。</span><span class="sxs-lookup"><span data-stu-id="b04cf-184">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="b04cf-185">[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) （未顯示） 的項目會指定一組可顯示的這個定義的物件。</span><span class="sxs-lookup"><span data-stu-id="b04cf-185">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="b04cf-186">您必須指定至少一個型別、 選取項目集或選擇條件的定義，但您可以指定的項目沒有最大數目。</span><span class="sxs-lookup"><span data-stu-id="b04cf-186">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="b04cf-187">[SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) （未顯示） 的項目會指定要使用此定義必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="b04cf-187">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="b04cf-188">您必須指定至少一個型別、 選取項目集或選擇條件的定義，但您可以指定的項目沒有最大數目。</span><span class="sxs-lookup"><span data-stu-id="b04cf-188">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="b04cf-189">如需定義選擇條件的詳細資訊，請參閱 <<c0> [ 定義的條件，顯示資料](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="b04cf-189">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-wide-view"></a><span data-ttu-id="b04cf-190">在寬型檢視中顯示物件的群組</span><span class="sxs-lookup"><span data-stu-id="b04cf-190">Displaying Groups of objects in a Wide View</span></span>

<span data-ttu-id="b04cf-191">您可以分隔成群組寬型檢視所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="b04cf-191">You can separate the objects that are displayed by the wide view into groups.</span></span> <span data-ttu-id="b04cf-192">這不表示您定義一個群組，只有特定的屬性或指令碼的值變更時，Windows PowerShell 會啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="b04cf-192">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="b04cf-193">在下列範例中，啟動新的群組時的值[System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType)屬性變更。</span><span class="sxs-lookup"><span data-stu-id="b04cf-193">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="b04cf-194">下列 XML 元素用來定義一組啟動時：</span><span class="sxs-lookup"><span data-stu-id="b04cf-194">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="b04cf-195">[GroupBy](./groupby-element-for-view-format.md)項目定義之屬性或啟動新的群組，並定義群組的顯示方式的指令碼。</span><span class="sxs-lookup"><span data-stu-id="b04cf-195">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="b04cf-196">[PropertyName](./propertyname-element-for-groupby-format.md)項目會指定開始新的群組，其值變更時的屬性。</span><span class="sxs-lookup"><span data-stu-id="b04cf-196">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="b04cf-197">您必須指定屬性或指令碼，以啟動群組中，但您無法同時指定。</span><span class="sxs-lookup"><span data-stu-id="b04cf-197">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="b04cf-198">[ScriptBlock](./scriptblock-element-for-groupby-format.md)項目會指定指令碼，其值變更時，會啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="b04cf-198">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="b04cf-199">您必須指定指令碼或屬性，以啟動群組中，但您無法同時指定。</span><span class="sxs-lookup"><span data-stu-id="b04cf-199">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="b04cf-200">[標籤](./label-element-for-groupby-format.md)項目會定義每個群組的開頭所顯示的標籤。</span><span class="sxs-lookup"><span data-stu-id="b04cf-200">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="b04cf-201">除了這個項目所指定的文字，Windows PowerShell 會顯示觸發新的群組，並新增一個空白行，標籤前後的值。</span><span class="sxs-lookup"><span data-stu-id="b04cf-201">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="b04cf-202">這是選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="b04cf-202">This element is optional.</span></span>

- <span data-ttu-id="b04cf-203">[CustomControl](./customcontrol-element-for-groupby-format.md)項目會定義用來顯示資料的控制項。</span><span class="sxs-lookup"><span data-stu-id="b04cf-203">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="b04cf-204">這是選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="b04cf-204">This element is optional.</span></span>

- <span data-ttu-id="b04cf-205">[CustomControlName](./customcontrolname-element-for-groupby-format.md)項目會指定一般或檢視來顯示資料的控制項。</span><span class="sxs-lookup"><span data-stu-id="b04cf-205">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="b04cf-206">這是選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="b04cf-206">This element is optional.</span></span>

<span data-ttu-id="b04cf-207">如需完整的格式化檔案，定義群組的範例，請參閱 <<c0> [ 寬型檢視 (GroupBy)](./wide-view-groupby.md)。</span><span class="sxs-lookup"><span data-stu-id="b04cf-207">For an example of a complete formatting file that defines groups, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="b04cf-208">使用格式字串</span><span class="sxs-lookup"><span data-stu-id="b04cf-208">Using Format Strings</span></span>

<span data-ttu-id="b04cf-209">格式字串可以加入成寬型檢視，以進一步定義資料的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="b04cf-209">Formatting strings can be added to a wide view to further define how the data is displayed.</span></span> <span data-ttu-id="b04cf-210">下列範例示範如何定義的格式化字串的值，`StartTime`屬性。</span><span class="sxs-lookup"><span data-stu-id="b04cf-210">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

<span data-ttu-id="b04cf-211">下列的 XML 項目可以用來指定之格式模式中：</span><span class="sxs-lookup"><span data-stu-id="b04cf-211">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="b04cf-212">[WideItem](./wideitem-element-for-widecontrol-format.md)項目會指定檢視所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="b04cf-212">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="b04cf-213">[PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md)項目會指定其值會顯示由檢視的屬性。</span><span class="sxs-lookup"><span data-stu-id="b04cf-213">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="b04cf-214">您必須指定屬性或指令碼，但您無法同時指定。</span><span class="sxs-lookup"><span data-stu-id="b04cf-214">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="b04cf-215">[FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md)項目會指定之格式模式所定義的屬性或指令碼的值在檢視中的顯示方式</span><span class="sxs-lookup"><span data-stu-id="b04cf-215">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view</span></span>

- <span data-ttu-id="b04cf-216">[ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) （未顯示） 的項目會指定其值會顯示檢視指令碼。</span><span class="sxs-lookup"><span data-stu-id="b04cf-216">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="b04cf-217">您必須指定指令碼或屬性，但您無法同時指定。</span><span class="sxs-lookup"><span data-stu-id="b04cf-217">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="b04cf-218">在下列範例中，`ToString`來格式化值的指令碼會呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="b04cf-218">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="b04cf-219">指令碼可以呼叫任何方法的物件。</span><span class="sxs-lookup"><span data-stu-id="b04cf-219">Scripts can call any method of an object.</span></span> <span data-ttu-id="b04cf-220">因此，如果物件有一個方法，例如`ToString`具有格式設定的參數，指令碼可以呼叫該方法，來設定指令碼的輸出值的格式。</span><span class="sxs-lookup"><span data-stu-id="b04cf-220">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

<span data-ttu-id="b04cf-221">下列的 XML 項目可以用來呼叫`ToString`方法：</span><span class="sxs-lookup"><span data-stu-id="b04cf-221">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="b04cf-222">[WideItem](./wideitem-element-for-widecontrol-format.md)項目會指定檢視所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="b04cf-222">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="b04cf-223">[ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) （未顯示） 的項目會指定其值會顯示檢視指令碼。</span><span class="sxs-lookup"><span data-stu-id="b04cf-223">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="b04cf-224">您必須指定指令碼或屬性，但您無法同時指定。</span><span class="sxs-lookup"><span data-stu-id="b04cf-224">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="b04cf-225">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b04cf-225">See Also</span></span>

[<span data-ttu-id="b04cf-226">寬型檢視 （基本）</span><span class="sxs-lookup"><span data-stu-id="b04cf-226">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="b04cf-227">寬型檢視 (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="b04cf-227">Wide View (GroupBy)</span></span>](./wide-view-groupby.md)

[<span data-ttu-id="b04cf-228">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="b04cf-228">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
