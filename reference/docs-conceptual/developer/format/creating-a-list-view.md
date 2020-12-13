---
ms.date: 09/13/2016
ms.topic: reference
title: 建立清單檢視
description: 建立清單檢視
ms.openlocfilehash: c34c4fddc27d4fd016fba37fc465924d693756a5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655637"
---
# <a name="creating-a-list-view"></a><span data-ttu-id="922f4-103">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="922f4-103">Creating a List View</span></span>

<span data-ttu-id="922f4-104">清單視圖會依序顯示單一資料行中的資料 (順序) 。</span><span class="sxs-lookup"><span data-stu-id="922f4-104">A list view displays data in a single column (in sequential order).</span></span> <span data-ttu-id="922f4-105">清單中顯示的資料可以是 .NET 屬性的值或腳本的值。</span><span class="sxs-lookup"><span data-stu-id="922f4-105">The data displayed in the list can be the value of a .NET property or the value of a script.</span></span>

## <a name="a-list-view-display"></a><span data-ttu-id="922f4-106">清單視圖顯示</span><span class="sxs-lookup"><span data-stu-id="922f4-106">A List View Display</span></span>

<span data-ttu-id="922f4-107">下列輸出顯示 Windows PowerShell 如何顯示 [system.serviceprocess.dll. Servicecontroller 的屬性？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController) [取得服務](/powershell/module/microsoft.powershell.management/get-service) Cmdlet 所傳回的 Fullname 物件。</span><span class="sxs-lookup"><span data-stu-id="922f4-107">The following output shows how Windows PowerShell displays the properties of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects that are returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="922f4-108">在此範例中，傳回了三個物件，每個物件都以空白行分隔。</span><span class="sxs-lookup"><span data-stu-id="922f4-108">In this example, three objects were returned, with each object separated from the preceding object by a blank line.</span></span>

```powershell
Get-Service | format-list
```

```output
Name                : AEADIFilters
DisplayName         : Andrea ADI Filters Service
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess

Name                : AeLookupSvc
DisplayName         : Application Experience
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32ShareProcess

Name                : AgereModemAudio
DisplayName         : Agere Modem Call Progress Audio
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess
...
```

## <a name="defining-the-list-view"></a><span data-ttu-id="922f4-109">定義清單視圖</span><span class="sxs-lookup"><span data-stu-id="922f4-109">Defining the List View</span></span>

<span data-ttu-id="922f4-110">下列 XML 會顯示清單視圖架構，以顯示 System.serviceprocess.dll Servicecontroller 的數個屬性。 [Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) 物件。</span><span class="sxs-lookup"><span data-stu-id="922f4-110">The following XML shows the list view schema for displaying several properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="922f4-111">您必須指定要顯示在清單視圖中的每個屬性。</span><span class="sxs-lookup"><span data-stu-id="922f4-111">You must specify each property that you want displayed in the list view.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

<span data-ttu-id="922f4-112">下列 XML 元素用來定義清單視圖：</span><span class="sxs-lookup"><span data-stu-id="922f4-112">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="922f4-113">[View](./view-element-format.md)元素是清單視圖的父元素。</span><span class="sxs-lookup"><span data-stu-id="922f4-113">The [View](./view-element-format.md) element is the parent element of the list view.</span></span> <span data-ttu-id="922f4-114"> (此為數據表、寬和自訂控制項視圖的相同父元素。 ) </span><span class="sxs-lookup"><span data-stu-id="922f4-114">(This is the same parent element for the table, wide, and custom control views.)</span></span>

- <span data-ttu-id="922f4-115">[Name](./name-element-for-view-format.md)元素會指定視圖的名稱。</span><span class="sxs-lookup"><span data-stu-id="922f4-115">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="922f4-116">所有視圖都需要這個元素。</span><span class="sxs-lookup"><span data-stu-id="922f4-116">This element is required for all views.</span></span>

- <span data-ttu-id="922f4-117">[ViewSelectedBy](./viewselectedby-element-format.md)元素會定義使用 view 的物件。</span><span class="sxs-lookup"><span data-stu-id="922f4-117">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="922f4-118">這個元素是必要的。</span><span class="sxs-lookup"><span data-stu-id="922f4-118">This element is required.</span></span>

- <span data-ttu-id="922f4-119">[GroupBy](./groupby-element-for-view-format.md)元素會定義何時會顯示新的物件群組。</span><span class="sxs-lookup"><span data-stu-id="922f4-119">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="922f4-120">每當特定屬性或腳本的值變更時，就會啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="922f4-120">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="922f4-121">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="922f4-121">This element is optional.</span></span>

- <span data-ttu-id="922f4-122">[Controls](./controls-element-for-view-format.md)元素會定義清單視圖所定義的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="922f4-122">The [Controls](./controls-element-for-view-format.md) element defines the custom controls that are defined by the list view.</span></span> <span data-ttu-id="922f4-123">控制項可讓您進一步指定顯示資料的方式。</span><span class="sxs-lookup"><span data-stu-id="922f4-123">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="922f4-124">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="922f4-124">This element is optional.</span></span> <span data-ttu-id="922f4-125">View 可以定義自己的自訂控制項，也可以使用格式檔案中任何視圖都可使用的通用控制項。</span><span class="sxs-lookup"><span data-stu-id="922f4-125">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="922f4-126">如需自訂控制項的詳細資訊，請參閱 [建立自訂控制項](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="922f4-126">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="922f4-127">[ListControl](./listcontrol-element-format.md)元素會定義要顯示在視圖中的內容，以及其格式化方式。</span><span class="sxs-lookup"><span data-stu-id="922f4-127">The [ListControl](./listcontrol-element-format.md) element defines what is displayed in the view and how it is formatted.</span></span> <span data-ttu-id="922f4-128">清單視圖類似于所有其他的視圖，可顯示物件屬性的值或腳本所產生的值。</span><span class="sxs-lookup"><span data-stu-id="922f4-128">Similar to all other views, a list view can display the values of object properties or values generated by script.</span></span>

<span data-ttu-id="922f4-129">如需定義簡單列表視圖的完整格式化檔案範例，請參閱 [清單視圖 (基本) ](./list-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="922f4-129">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-list-view"></a><span data-ttu-id="922f4-130">提供清單視圖的定義</span><span class="sxs-lookup"><span data-stu-id="922f4-130">Providing Definitions for Your List View</span></span>

<span data-ttu-id="922f4-131">清單視圖可以使用 [ListControl](./listcontrol-element-format.md) 元素的子項目來提供一或多個定義。</span><span class="sxs-lookup"><span data-stu-id="922f4-131">List views can provide one or more definitions by using the child elements of the [ListControl](./listcontrol-element-format.md) element.</span></span> <span data-ttu-id="922f4-132">一般而言，視圖只會有一個定義。</span><span class="sxs-lookup"><span data-stu-id="922f4-132">Typically, a view will have only one definition.</span></span> <span data-ttu-id="922f4-133">在下列範例中，此視圖會提供單一定義，以顯示系統的數個屬性 [。Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process) 物件。</span><span class="sxs-lookup"><span data-stu-id="922f4-133">In the following example, the view provides a single definition that displays several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="922f4-134">清單視圖可以顯示內容的值或腳本的值 (未顯示在範例) 中。</span><span class="sxs-lookup"><span data-stu-id="922f4-134">A list view can display the value of a property or the value of a script (not shown in the example).</span></span>

```xml
<ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>

```

<span data-ttu-id="922f4-135">下列 XML 元素可用來提供清單視圖的定義：</span><span class="sxs-lookup"><span data-stu-id="922f4-135">The following XML elements can be used to provide definitions for a list view:</span></span>

- <span data-ttu-id="922f4-136">[ListControl](./listcontrol-element-format.md)元素和其子項目會定義要顯示在視圖中的內容。</span><span class="sxs-lookup"><span data-stu-id="922f4-136">The [ListControl](./listcontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="922f4-137">[ListEntries](./listentries-element-for-listcontrol-format.md)元素會提供視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="922f4-137">The [ListEntries](./listentries-element-for-listcontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="922f4-138">在大部分的情況下，view 只會有一個定義。</span><span class="sxs-lookup"><span data-stu-id="922f4-138">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="922f4-139">這個元素是必要的。</span><span class="sxs-lookup"><span data-stu-id="922f4-139">This element is required.</span></span>

- <span data-ttu-id="922f4-140">[ListEntry](./listentry-element-for-listcontrol-format.md)元素會提供視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="922f4-140">The [ListEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="922f4-141">至少需要一個 [ListEntry](./listentry-element-for-listcontrol-format.md) ;不過，您可以新增的元素數目沒有最大限制。</span><span class="sxs-lookup"><span data-stu-id="922f4-141">At least one [ListEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="922f4-142">在大部分的情況下，view 只會有一個定義。</span><span class="sxs-lookup"><span data-stu-id="922f4-142">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="922f4-143">[之 entryselectedby](./entryselectedby-element-for-listentry-for-listcontrol-format.md)元素會指定特定定義所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="922f4-143">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="922f4-144">這個元素是選擇性的，只有當您定義多個顯示不同物件的 [ListEntry](./listentry-element-for-listcontrol-format.md) 專案時，才需要此專案。</span><span class="sxs-lookup"><span data-stu-id="922f4-144">This element is optional and is needed only when you define multiple [ListEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="922f4-145">[ListItems](./listitems-element-for-listentry-for-listcontrol-format.md)元素會指定屬性和腳本，其值會顯示在清單視圖的資料列中。</span><span class="sxs-lookup"><span data-stu-id="922f4-145">The [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies the properties and scripts whose values are displayed in the rows of the list view.</span></span>

- <span data-ttu-id="922f4-146">專案 [清單元素會](./listitems-element-for-listentry-for-listcontrol-format.md) 指定屬性或腳本，其值會顯示在清單視圖的資料列中。</span><span class="sxs-lookup"><span data-stu-id="922f4-146">The [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies a property or script whose value is displayed in a row of the list view.</span></span> <span data-ttu-id="922f4-147">清單視圖必須指定至少一個屬性或腳本。</span><span class="sxs-lookup"><span data-stu-id="922f4-147">A list view must specify at least one property or script.</span></span> <span data-ttu-id="922f4-148">可指定的資料列數目沒有最大限制。</span><span class="sxs-lookup"><span data-stu-id="922f4-148">There is no maximum limit to the number of rows that can be specified.</span></span>

- <span data-ttu-id="922f4-149">[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)元素會指定屬性，其值會顯示在資料列中。</span><span class="sxs-lookup"><span data-stu-id="922f4-149">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="922f4-150">您必須指定屬性或腳本，但不能同時指定這兩種方法。</span><span class="sxs-lookup"><span data-stu-id="922f4-150">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="922f4-151">[ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md)元素會指定其值會顯示在資料列中的腳本。</span><span class="sxs-lookup"><span data-stu-id="922f4-151">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="922f4-152">您必須指定腳本或屬性，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="922f4-152">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="922f4-153">[Label](./label-element-for-listitem-for-listcontrol-format.md)元素會指定在資料列中屬性或腳本值的左邊顯示的標籤。</span><span class="sxs-lookup"><span data-stu-id="922f4-153">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element specifies the label that is displayed to the left of the property or script value in the row.</span></span> <span data-ttu-id="922f4-154">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="922f4-154">This element is optional.</span></span> <span data-ttu-id="922f4-155">如果未指定標籤，則會顯示內容或腳本的名稱。</span><span class="sxs-lookup"><span data-stu-id="922f4-155">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="922f4-156">如需完整範例，請參閱 [清單視圖 (標籤) ](./list-view-labels.md)。</span><span class="sxs-lookup"><span data-stu-id="922f4-156">For a complete example, see [List View (Labels)](./list-view-labels.md).</span></span>

- <span data-ttu-id="922f4-157">[ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)元素會指定必須存在才能顯示資料列的條件。</span><span class="sxs-lookup"><span data-stu-id="922f4-157">The [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) element specifies a condition that must exist for the row to be displayed.</span></span> <span data-ttu-id="922f4-158">如需有關在清單視圖中加入條件的詳細資訊，請參閱 [定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="922f4-158">For more information about adding conditions to the list view, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span> <span data-ttu-id="922f4-159">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="922f4-159">This element is optional.</span></span>

- <span data-ttu-id="922f4-160">[格式](./formatstring-element-for-listitem-for-listcontrol-format.md)值元素會指定用來顯示內容或腳本值的模式。</span><span class="sxs-lookup"><span data-stu-id="922f4-160">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a pattern that is used to display the value of the property or script.</span></span> <span data-ttu-id="922f4-161">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="922f4-161">This element is optional.</span></span>

<span data-ttu-id="922f4-162">如需定義簡單列表視圖的完整格式化檔案範例，請參閱 [清單視圖 (基本) ](./list-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="922f4-162">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-list-view"></a><span data-ttu-id="922f4-163">定義使用清單視圖的物件</span><span class="sxs-lookup"><span data-stu-id="922f4-163">Defining the Objects That Use the List View</span></span>

<span data-ttu-id="922f4-164">有兩種方式可以定義使用清單視圖的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="922f4-164">There are two ways to define which .NET objects use the list view.</span></span> <span data-ttu-id="922f4-165">您可以使用 [ViewSelectedBy](./viewselectedby-element-format.md) 專案來定義可由視圖的所有定義顯示的物件，或者，您可以使用 [之 entryselectedby](./entryselectedby-element-for-listentry-for-listcontrol-format.md) 元素來定義由視圖的特定定義所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="922f4-165">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="922f4-166">在大部分的情況下，視圖只有一個定義，因此物件通常是由 [ViewSelectedBy](./viewselectedby-element-format.md) 元素定義。</span><span class="sxs-lookup"><span data-stu-id="922f4-166">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="922f4-167">下列範例示範如何使用 [ViewSelectedBy](./viewselectedby-element-format.md) 和 [TypeName](./typename-element-for-viewselectedby-format.md) 元素，定義清單視圖所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="922f4-167">The following example shows how to define the objects that are displayed by the list view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="922f4-168">您可以指定的 [TypeName](./typename-element-for-viewselectedby-format.md) 元素數目沒有任何限制，而且其順序並不重要。</span><span class="sxs-lookup"><span data-stu-id="922f4-168">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="922f4-169">下列 XML 元素可以用來指定清單視圖所使用的物件：</span><span class="sxs-lookup"><span data-stu-id="922f4-169">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="922f4-170">[ViewSelectedBy](./viewselectedby-element-format.md)元素會定義清單視圖要顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="922f4-170">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="922f4-171">[TypeName](./typename-element-for-viewselectedby-format.md)元素會指定視圖所顯示的 .net 物件。</span><span class="sxs-lookup"><span data-stu-id="922f4-171">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="922f4-172">需要完整的 .NET 型別名稱。</span><span class="sxs-lookup"><span data-stu-id="922f4-172">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="922f4-173">您必須為此視圖指定至少一個類型或選取範圍，但無法指定的元素數目上限。</span><span class="sxs-lookup"><span data-stu-id="922f4-173">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="922f4-174">如需完整格式化檔案的範例，請參閱 [清單視圖 (基本) ](./list-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="922f4-174">For an example of a complete formatting file, see [List View (Basic)](./list-view-basic.md).</span></span>

<span data-ttu-id="922f4-175">下列範例會使用 [ViewSelectedBy](./viewselectedby-element-format.md) 和 [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="922f4-175">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="922f4-176">如果您有一組相關的物件會使用多個視圖顯示，例如當您針對相同物件定義清單視圖和資料表視圖時，請使用選取集。</span><span class="sxs-lookup"><span data-stu-id="922f4-176">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="922f4-177">如需有關如何建立選取範圍的詳細資訊，請參閱 [定義選取集合](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="922f4-177">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="922f4-178">下列 XML 元素可以用來指定清單視圖所使用的物件：</span><span class="sxs-lookup"><span data-stu-id="922f4-178">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="922f4-179">[ViewSelectedBy](./viewselectedby-element-format.md)元素會定義清單視圖要顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="922f4-179">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="922f4-180">[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素會指定可供視圖顯示的一組物件。</span><span class="sxs-lookup"><span data-stu-id="922f4-180">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="922f4-181">您必須為此視圖指定至少一個選擇集或類型，但無法指定的元素數目上限。</span><span class="sxs-lookup"><span data-stu-id="922f4-181">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="922f4-182">下列範例示範如何使用 [之 entryselectedby](./entryselectedby-element-for-listentry-for-listcontrol-format.md) 元素定義清單視圖的特定定義所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="922f4-182">The following example shows how to define the objects displayed by a specific definition of the list view using the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element.</span></span> <span data-ttu-id="922f4-183">您可以使用這個專案，指定物件的 .NET 類型名稱、一組選取的物件，或指定使用定義時指定的選取條件。</span><span class="sxs-lookup"><span data-stu-id="922f4-183">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="922f4-184">如需如何建立選取條件的詳細資訊，請參閱 [定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="922f4-184">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

<span data-ttu-id="922f4-185">下列 XML 專案可以用來指定清單視圖的特定定義所使用的物件：</span><span class="sxs-lookup"><span data-stu-id="922f4-185">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="922f4-186">[之 entryselectedby](./entryselectedby-element-for-listentry-for-listcontrol-format.md)元素會定義定義所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="922f4-186">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="922f4-187">[TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md)元素會指定定義所顯示的 .net 物件。</span><span class="sxs-lookup"><span data-stu-id="922f4-187">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="922f4-188">使用這個專案時，需要完整的 .NET 型別名稱。</span><span class="sxs-lookup"><span data-stu-id="922f4-188">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="922f4-189">您必須為定義指定至少一個類型、選取集或選取條件，但無法指定的元素數目上限。</span><span class="sxs-lookup"><span data-stu-id="922f4-189">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="922f4-190">[SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)元素 (未顯示) 指定可由此定義顯示的一組物件。</span><span class="sxs-lookup"><span data-stu-id="922f4-190">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="922f4-191">您必須為定義指定至少一個類型、選取集或選取條件，但無法指定的元素數目上限。</span><span class="sxs-lookup"><span data-stu-id="922f4-191">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="922f4-192">[SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)元素 (未顯示) 指定必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="922f4-192">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="922f4-193">您必須為定義指定至少一個類型、選取集或選取條件，但無法指定的元素數目上限。</span><span class="sxs-lookup"><span data-stu-id="922f4-193">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="922f4-194">如需定義選取條件的詳細資訊，請參閱 [定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="922f4-194">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-list-view"></a><span data-ttu-id="922f4-195">在清單視圖中顯示物件群組</span><span class="sxs-lookup"><span data-stu-id="922f4-195">Displaying Groups of Objects in a List View</span></span>

<span data-ttu-id="922f4-196">您可以將清單視圖所顯示的物件分隔成群組。</span><span class="sxs-lookup"><span data-stu-id="922f4-196">You can separate the objects that are displayed by the list view into groups.</span></span> <span data-ttu-id="922f4-197">這並不表示您定義了群組，只有當特定屬性或腳本的值變更時，Windows PowerShell 才會啟動新群組。</span><span class="sxs-lookup"><span data-stu-id="922f4-197">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="922f4-198">下列範例會在 [system.serviceprocess.dll. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) 屬性的值變更時，啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="922f4-198">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="922f4-199">下列 XML 元素可用來定義何時啟動群組：</span><span class="sxs-lookup"><span data-stu-id="922f4-199">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="922f4-200">[GroupBy](./groupby-element-for-view-format.md)元素會定義可啟動新群組的屬性或腳本，並定義如何顯示群組。</span><span class="sxs-lookup"><span data-stu-id="922f4-200">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="922f4-201">[PropertyName](./propertyname-element-for-groupby-format.md)元素會指定在其值變更時啟動新群組的屬性。</span><span class="sxs-lookup"><span data-stu-id="922f4-201">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="922f4-202">您必須指定屬性或腳本來啟動群組，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="922f4-202">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="922f4-203">[ScriptBlock](./scriptblock-element-for-groupby-format.md)元素會指定在其值變更時啟動新群組的腳本。</span><span class="sxs-lookup"><span data-stu-id="922f4-203">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="922f4-204">您必須指定腳本或屬性來啟動群組，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="922f4-204">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="922f4-205">[Label](./label-element-for-groupby-format.md)元素會定義在每個群組的開頭顯示的標籤。</span><span class="sxs-lookup"><span data-stu-id="922f4-205">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="922f4-206">除了這個專案所指定的文字之外，Windows PowerShell 會顯示觸發新群組的值，並在標籤前後加上空白行。</span><span class="sxs-lookup"><span data-stu-id="922f4-206">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="922f4-207">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="922f4-207">This element is optional.</span></span>

- <span data-ttu-id="922f4-208">[CustomControl](./customcontrol-element-for-groupby-format.md)元素會定義用來顯示資料的控制項。</span><span class="sxs-lookup"><span data-stu-id="922f4-208">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="922f4-209">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="922f4-209">This element is optional.</span></span>

- <span data-ttu-id="922f4-210">[CustomControlName](./customcontrolname-element-for-groupby-format.md)元素會指定用來顯示資料的通用或視圖控制項。</span><span class="sxs-lookup"><span data-stu-id="922f4-210">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="922f4-211">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="922f4-211">This element is optional.</span></span>

<span data-ttu-id="922f4-212">如需定義群組之完整格式化檔案的範例，請參閱 [清單視圖 (GroupBy) ](./list-view-groupby.md)。</span><span class="sxs-lookup"><span data-stu-id="922f4-212">For an example of a complete formatting file that defines groups, see [List View (GroupBy)](./list-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="922f4-213">使用格式字串</span><span class="sxs-lookup"><span data-stu-id="922f4-213">Using Format Strings</span></span>

<span data-ttu-id="922f4-214">您可以將字串格式設定加入至視圖，以進一步定義資料的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="922f4-214">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="922f4-215">下列範例顯示如何定義屬性值的格式化字串 `StartTime` 。</span><span class="sxs-lookup"><span data-stu-id="922f4-215">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

<span data-ttu-id="922f4-216">下列 XML 元素可以用來指定格式模式：</span><span class="sxs-lookup"><span data-stu-id="922f4-216">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="922f4-217">[專案 [] 元素會](./listitem-element-for-listitems-for-listcontrol-format.md) 指定視圖所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="922f4-217">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="922f4-218">[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)元素會指定屬性，其值會由視圖顯示。</span><span class="sxs-lookup"><span data-stu-id="922f4-218">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="922f4-219">您必須指定屬性或腳本，但不能同時指定這兩種方法。</span><span class="sxs-lookup"><span data-stu-id="922f4-219">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="922f4-220">格式 [值元素會](./formatstring-element-for-listitem-for-listcontrol-format.md) 指定格式模式，以定義屬性或腳本值在視圖中的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="922f4-220">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

- <span data-ttu-id="922f4-221"> (不會顯示 [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) 元素) 指定由視圖顯示其值的腳本。</span><span class="sxs-lookup"><span data-stu-id="922f4-221">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="922f4-222">您必須指定腳本或屬性，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="922f4-222">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="922f4-223">在下列範例中， `ToString` 會呼叫方法來格式化腳本的值。</span><span class="sxs-lookup"><span data-stu-id="922f4-223">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="922f4-224">腳本可以呼叫物件的任何方法。</span><span class="sxs-lookup"><span data-stu-id="922f4-224">Scripts can call any method of an object.</span></span> <span data-ttu-id="922f4-225">因此，如果物件具有具有格式化參數的方法（例如 `ToString` ），則腳本可以呼叫該方法來格式化腳本的輸出值。</span><span class="sxs-lookup"><span data-stu-id="922f4-225">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="922f4-226">下列 XML 元素可以用來呼叫 `ToString` 方法：</span><span class="sxs-lookup"><span data-stu-id="922f4-226">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="922f4-227">[專案 [] 元素會](./listitem-element-for-listitems-for-listcontrol-format.md) 指定視圖所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="922f4-227">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="922f4-228"> (不會顯示 [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) 元素) 指定由視圖顯示其值的腳本。</span><span class="sxs-lookup"><span data-stu-id="922f4-228">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="922f4-229">您必須指定腳本或屬性，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="922f4-229">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="922f4-230">另請參閱</span><span class="sxs-lookup"><span data-stu-id="922f4-230">See Also</span></span>

[<span data-ttu-id="922f4-231">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="922f4-231">Writing a Windows PowerShell Cmdlet</span></span>](../cmdlet/writing-a-windows-powershell-cmdlet.md)
