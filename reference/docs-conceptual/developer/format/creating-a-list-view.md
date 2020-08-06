---
title: 建立清單視圖 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 24eb673e0db011a1439fa5ba1f2966fcc3bdc338
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783767"
---
# <a name="creating-a-list-view"></a><span data-ttu-id="7ef54-102">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="7ef54-102">Creating a List View</span></span>

<span data-ttu-id="7ef54-103">清單視圖會依序)  (顯示單一資料行中的資料。</span><span class="sxs-lookup"><span data-stu-id="7ef54-103">A list view displays data in a single column (in sequential order).</span></span> <span data-ttu-id="7ef54-104">清單中顯示的資料可以是 .NET 屬性的值或腳本的值。</span><span class="sxs-lookup"><span data-stu-id="7ef54-104">The data displayed in the list can be the value of a .NET property or the value of a script.</span></span>

## <a name="a-list-view-display"></a><span data-ttu-id="7ef54-105">清單視圖顯示</span><span class="sxs-lookup"><span data-stu-id="7ef54-105">A List View Display</span></span>

<span data-ttu-id="7ef54-106">下列輸出顯示 Windows PowerShell 如何顯示[system.serviceprocess.dll. Servicecontroller 的屬性？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)由[Get-服務](/powershell/module/microsoft.powershell.management/get-service)Cmdlet 傳回的 Fullname 物件。</span><span class="sxs-lookup"><span data-stu-id="7ef54-106">The following output shows how Windows PowerShell displays the properties of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects that are returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="7ef54-107">在此範例中，傳回了三個物件，其中每個物件都是以空白行隔開。</span><span class="sxs-lookup"><span data-stu-id="7ef54-107">In this example, three objects were returned, with each object separated from the preceding object by a blank line.</span></span>

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

## <a name="defining-the-list-view"></a><span data-ttu-id="7ef54-108">定義清單視圖</span><span class="sxs-lookup"><span data-stu-id="7ef54-108">Defining the List View</span></span>

<span data-ttu-id="7ef54-109">下列 XML 顯示用來顯示 System.serviceprocess.dll Servicecontroller 之數個屬性的清單視圖架構。 [Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController)物件。</span><span class="sxs-lookup"><span data-stu-id="7ef54-109">The following XML shows the list view schema for displaying several properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="7ef54-110">您必須指定要顯示在清單視圖中的每個屬性。</span><span class="sxs-lookup"><span data-stu-id="7ef54-110">You must specify each property that you want displayed in the list view.</span></span>

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

<span data-ttu-id="7ef54-111">下列 XML 元素可用來定義清單視圖：</span><span class="sxs-lookup"><span data-stu-id="7ef54-111">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="7ef54-112">[View](./view-element-format.md)元素是清單視圖的父元素。</span><span class="sxs-lookup"><span data-stu-id="7ef54-112">The [View](./view-element-format.md) element is the parent element of the list view.</span></span> <span data-ttu-id="7ef54-113"> (這是資料表、寬和自訂控制項視圖的相同父元素。 ) </span><span class="sxs-lookup"><span data-stu-id="7ef54-113">(This is the same parent element for the table, wide, and custom control views.)</span></span>

- <span data-ttu-id="7ef54-114">[Name](./name-element-for-view-format.md)元素會指定視圖的名稱。</span><span class="sxs-lookup"><span data-stu-id="7ef54-114">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="7ef54-115">所有的視圖都需要此元素。</span><span class="sxs-lookup"><span data-stu-id="7ef54-115">This element is required for all views.</span></span>

- <span data-ttu-id="7ef54-116">[ViewSelectedBy](./viewselectedby-element-format.md)元素會定義使用此視圖的物件。</span><span class="sxs-lookup"><span data-stu-id="7ef54-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="7ef54-117">這個元素是必要的。</span><span class="sxs-lookup"><span data-stu-id="7ef54-117">This element is required.</span></span>

- <span data-ttu-id="7ef54-118">[GroupBy](./groupby-element-for-view-format.md)元素會定義何時顯示新的物件群組。</span><span class="sxs-lookup"><span data-stu-id="7ef54-118">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="7ef54-119">每當特定屬性或腳本的值變更時，就會啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="7ef54-119">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="7ef54-120">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="7ef54-120">This element is optional.</span></span>

- <span data-ttu-id="7ef54-121">[Controls](./controls-element-for-view-format.md)元素會定義清單視圖所定義的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="7ef54-121">The [Controls](./controls-element-for-view-format.md) element defines the custom controls that are defined by the list view.</span></span> <span data-ttu-id="7ef54-122">控制項可讓您進一步指定資料的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="7ef54-122">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="7ef54-123">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="7ef54-123">This element is optional.</span></span> <span data-ttu-id="7ef54-124">View 可以定義自己的自訂控制項，也可以使用格式檔案中任何視圖可以使用的通用控制項。</span><span class="sxs-lookup"><span data-stu-id="7ef54-124">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="7ef54-125">如需自訂控制項的詳細資訊，請參閱[建立自訂控制項](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="7ef54-125">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="7ef54-126">[ListControl](./listcontrol-element-format.md)元素會定義要在視圖中顯示的內容，以及其格式化方式。</span><span class="sxs-lookup"><span data-stu-id="7ef54-126">The [ListControl](./listcontrol-element-format.md) element defines what is displayed in the view and how it is formatted.</span></span> <span data-ttu-id="7ef54-127">清單視圖類似于所有其他的視圖，可以顯示物件屬性的值或腳本所產生的值。</span><span class="sxs-lookup"><span data-stu-id="7ef54-127">Similar to all other views, a list view can display the values of object properties or values generated by script.</span></span>

<span data-ttu-id="7ef54-128">如需定義簡單列表視圖的完整格式檔案範例，請參閱[ (基本) 的清單視圖](./list-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="7ef54-128">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-list-view"></a><span data-ttu-id="7ef54-129">提供清單視圖的定義</span><span class="sxs-lookup"><span data-stu-id="7ef54-129">Providing Definitions for Your List View</span></span>

<span data-ttu-id="7ef54-130">清單視圖可以藉由使用[ListControl](./listcontrol-element-format.md)專案的子項目，提供一或多個定義。</span><span class="sxs-lookup"><span data-stu-id="7ef54-130">List views can provide one or more definitions by using the child elements of the [ListControl](./listcontrol-element-format.md) element.</span></span> <span data-ttu-id="7ef54-131">一般而言，視圖只會有一個定義。</span><span class="sxs-lookup"><span data-stu-id="7ef54-131">Typically, a view will have only one definition.</span></span> <span data-ttu-id="7ef54-132">在下列範例中，此視圖會提供單一定義來顯示系統的數個屬性。 [Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process)物件。</span><span class="sxs-lookup"><span data-stu-id="7ef54-132">In the following example, the view provides a single definition that displays several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="7ef54-133">清單視圖可以顯示內容的值或腳本的值 (不會顯示在範例) 中。</span><span class="sxs-lookup"><span data-stu-id="7ef54-133">A list view can display the value of a property or the value of a script (not shown in the example).</span></span>

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

<span data-ttu-id="7ef54-134">下列 XML 元素可以用來提供清單視圖的定義：</span><span class="sxs-lookup"><span data-stu-id="7ef54-134">The following XML elements can be used to provide definitions for a list view:</span></span>

- <span data-ttu-id="7ef54-135">[ListControl](./listcontrol-element-format.md)元素及其子項目會定義要在視圖中顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="7ef54-135">The [ListControl](./listcontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="7ef54-136">[ListEntries](./listentries-element-for-listcontrol-format.md)元素會提供視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="7ef54-136">The [ListEntries](./listentries-element-for-listcontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="7ef54-137">在大部分的情況下，視圖只會有一個定義。</span><span class="sxs-lookup"><span data-stu-id="7ef54-137">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="7ef54-138">這個元素是必要的。</span><span class="sxs-lookup"><span data-stu-id="7ef54-138">This element is required.</span></span>

- <span data-ttu-id="7ef54-139">[ListEntry](./listentry-element-for-listcontrol-format.md)元素會提供 view 的定義。</span><span class="sxs-lookup"><span data-stu-id="7ef54-139">The [ListEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="7ef54-140">至少需要一個[ListEntry](./listentry-element-for-listcontrol-format.md) ;不過，您可以新增的專案數沒有最大限制。</span><span class="sxs-lookup"><span data-stu-id="7ef54-140">At least one [ListEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="7ef54-141">在大部分的情況下，視圖只會有一個定義。</span><span class="sxs-lookup"><span data-stu-id="7ef54-141">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="7ef54-142">[之 entryselectedby](./entryselectedby-element-for-listentry-for-listcontrol-format.md)元素會指定特定定義所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="7ef54-142">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="7ef54-143">這個元素是選擇性的，只有當您定義多個[ListEntry](./listentry-element-for-listcontrol-format.md)專案來顯示不同的物件時，才需要此專案。</span><span class="sxs-lookup"><span data-stu-id="7ef54-143">This element is optional and is needed only when you define multiple [ListEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="7ef54-144">[ListItems](./listitems-element-for-listentry-for-listcontrol-format.md)元素會指定屬性和腳本，其值會顯示在清單視圖的資料列中。</span><span class="sxs-lookup"><span data-stu-id="7ef54-144">The [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies the properties and scripts whose values are displayed in the rows of the list view.</span></span>

- <span data-ttu-id="7ef54-145">[專案清單[] 元素會](./listitems-element-for-listentry-for-listcontrol-format.md)指定屬性或腳本，其值會顯示在清單視圖的資料列中。</span><span class="sxs-lookup"><span data-stu-id="7ef54-145">The [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies a property or script whose value is displayed in a row of the list view.</span></span> <span data-ttu-id="7ef54-146">清單視圖必須指定至少一個屬性或腳本。</span><span class="sxs-lookup"><span data-stu-id="7ef54-146">A list view must specify at least one property or script.</span></span> <span data-ttu-id="7ef54-147">可以指定的資料列數目沒有上限。</span><span class="sxs-lookup"><span data-stu-id="7ef54-147">There is no maximum limit to the number of rows that can be specified.</span></span>

- <span data-ttu-id="7ef54-148">[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)元素會指定屬性，其值會顯示在資料列中。</span><span class="sxs-lookup"><span data-stu-id="7ef54-148">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="7ef54-149">您必須指定屬性或腳本，但不能同時指定這兩者。</span><span class="sxs-lookup"><span data-stu-id="7ef54-149">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="7ef54-150">[ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md)元素會指定其值顯示在資料列中的腳本。</span><span class="sxs-lookup"><span data-stu-id="7ef54-150">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="7ef54-151">您必須指定腳本或屬性，但不能同時指定這兩者。</span><span class="sxs-lookup"><span data-stu-id="7ef54-151">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="7ef54-152">[Label](./label-element-for-listitem-for-listcontrol-format.md)元素會指定顯示在資料列中屬性或腳本值左邊的標籤。</span><span class="sxs-lookup"><span data-stu-id="7ef54-152">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element specifies the label that is displayed to the left of the property or script value in the row.</span></span> <span data-ttu-id="7ef54-153">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="7ef54-153">This element is optional.</span></span> <span data-ttu-id="7ef54-154">如果未指定標籤，則會顯示內容或腳本的名稱。</span><span class="sxs-lookup"><span data-stu-id="7ef54-154">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="7ef54-155">如需完整範例，請參閱[清單視圖 (標籤) ](./list-view-labels.md)。</span><span class="sxs-lookup"><span data-stu-id="7ef54-155">For a complete example, see [List View (Labels)](./list-view-labels.md).</span></span>

- <span data-ttu-id="7ef54-156">[ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)元素會指定必須存在的條件，才能顯示資料列。</span><span class="sxs-lookup"><span data-stu-id="7ef54-156">The [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) element specifies a condition that must exist for the row to be displayed.</span></span> <span data-ttu-id="7ef54-157">如需將條件新增至清單視圖的詳細資訊，請參閱[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="7ef54-157">For more information about adding conditions to the list view, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span> <span data-ttu-id="7ef54-158">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="7ef54-158">This element is optional.</span></span>

- <span data-ttu-id="7ef54-159">[[字串](./formatstring-element-for-listitem-for-listcontrol-format.md)類型] 元素會指定用來顯示內容或腳本值的模式。</span><span class="sxs-lookup"><span data-stu-id="7ef54-159">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a pattern that is used to display the value of the property or script.</span></span> <span data-ttu-id="7ef54-160">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="7ef54-160">This element is optional.</span></span>

<span data-ttu-id="7ef54-161">如需定義簡單列表視圖的完整格式檔案範例，請參閱[ (基本) 的清單視圖](./list-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="7ef54-161">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-list-view"></a><span data-ttu-id="7ef54-162">定義使用清單視圖的物件</span><span class="sxs-lookup"><span data-stu-id="7ef54-162">Defining the Objects That Use the List View</span></span>

<span data-ttu-id="7ef54-163">有兩種方式可定義要使用清單視圖的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="7ef54-163">There are two ways to define which .NET objects use the list view.</span></span> <span data-ttu-id="7ef54-164">您可以使用[ViewSelectedBy](./viewselectedby-element-format.md)專案來定義可由視圖的所有定義顯示的物件，也可以使用[之 entryselectedby](./entryselectedby-element-for-listentry-for-listcontrol-format.md)專案來定義由視圖的特定定義所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="7ef54-164">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="7ef54-165">在大部分情況下，一個 view 只有一個定義，因此物件通常是由[ViewSelectedBy](./viewselectedby-element-format.md)元素所定義。</span><span class="sxs-lookup"><span data-stu-id="7ef54-165">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="7ef54-166">下列範例顯示如何使用[ViewSelectedBy](./viewselectedby-element-format.md)和[TypeName](./typename-element-for-viewselectedby-format.md)元素定義清單視圖所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="7ef54-166">The following example shows how to define the objects that are displayed by the list view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="7ef54-167">您可以指定的[TypeName](./typename-element-for-viewselectedby-format.md)元素數目沒有限制，而且其順序並不重要。</span><span class="sxs-lookup"><span data-stu-id="7ef54-167">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="7ef54-168">下列 XML 元素可以用來指定清單視圖所使用的物件：</span><span class="sxs-lookup"><span data-stu-id="7ef54-168">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="7ef54-169">[ViewSelectedBy](./viewselectedby-element-format.md)元素會定義清單視圖所要顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="7ef54-169">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="7ef54-170">[TypeName](./typename-element-for-viewselectedby-format.md)元素會指定視圖所顯示的 .net 物件。</span><span class="sxs-lookup"><span data-stu-id="7ef54-170">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="7ef54-171">需要完整的 .NET 類型名稱。</span><span class="sxs-lookup"><span data-stu-id="7ef54-171">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="7ef54-172">您必須為此視圖指定至少一個類型或選取範圍，但不能指定的元素數目上限。</span><span class="sxs-lookup"><span data-stu-id="7ef54-172">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="7ef54-173">如需完整格式檔案的範例，請參閱[ (基本) 的清單視圖](./list-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="7ef54-173">For an example of a complete formatting file, see [List View (Basic)](./list-view-basic.md).</span></span>

<span data-ttu-id="7ef54-174">下列範例會使用[ViewSelectedBy](./viewselectedby-element-format.md)和[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="7ef54-174">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="7ef54-175">使用 [選取範圍]，您可以在其中擁有一組使用多個視圖顯示的相關物件，例如當您為相同的物件定義清單視圖和資料表視圖時。</span><span class="sxs-lookup"><span data-stu-id="7ef54-175">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="7ef54-176">如需有關如何建立選擇集的詳細資訊，請參閱[定義選取範圍集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="7ef54-176">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="7ef54-177">下列 XML 元素可以用來指定清單視圖所使用的物件：</span><span class="sxs-lookup"><span data-stu-id="7ef54-177">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="7ef54-178">[ViewSelectedBy](./viewselectedby-element-format.md)元素會定義清單視圖所要顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="7ef54-178">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="7ef54-179">[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素會指定一組可由視圖顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="7ef54-179">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="7ef54-180">您必須為此視圖指定至少一個選取範圍或類型，但不能指定的元素數目上限。</span><span class="sxs-lookup"><span data-stu-id="7ef54-180">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="7ef54-181">下列範例示範如何使用[之 entryselectedby](./entryselectedby-element-for-listentry-for-listcontrol-format.md)元素，定義清單視圖的特定定義所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="7ef54-181">The following example shows how to define the objects displayed by a specific definition of the list view using the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element.</span></span> <span data-ttu-id="7ef54-182">使用這個專案，您可以指定物件的 .NET 型別名稱、物件的選擇集，或指定何時使用定義的選取條件。</span><span class="sxs-lookup"><span data-stu-id="7ef54-182">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="7ef54-183">如需如何建立選取條件的詳細資訊，請參閱[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="7ef54-183">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

<span data-ttu-id="7ef54-184">下列 XML 元素可以用來指定清單視圖的特定定義所使用的物件：</span><span class="sxs-lookup"><span data-stu-id="7ef54-184">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="7ef54-185">[之 entryselectedby](./entryselectedby-element-for-listentry-for-listcontrol-format.md)元素會定義定義要顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="7ef54-185">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="7ef54-186">[TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md)元素會指定定義所顯示的 .net 物件。</span><span class="sxs-lookup"><span data-stu-id="7ef54-186">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="7ef54-187">使用此元素時，需要完整的 .NET 類型名稱。</span><span class="sxs-lookup"><span data-stu-id="7ef54-187">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="7ef54-188">您必須為定義至少指定一個類型、選擇集或選取條件，但不能指定的元素數目上限。</span><span class="sxs-lookup"><span data-stu-id="7ef54-188">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="7ef54-189">[SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)元素 (不會顯示) 指定一組可由這個定義顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="7ef54-189">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="7ef54-190">您必須為定義至少指定一個類型、選擇集或選取條件，但不能指定的元素數目上限。</span><span class="sxs-lookup"><span data-stu-id="7ef54-190">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="7ef54-191">[SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)元素 (不會顯示) 指定必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="7ef54-191">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="7ef54-192">您必須為定義至少指定一個類型、選擇集或選取條件，但不能指定的元素數目上限。</span><span class="sxs-lookup"><span data-stu-id="7ef54-192">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="7ef54-193">如需定義選取條件的詳細資訊，請參閱[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="7ef54-193">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-list-view"></a><span data-ttu-id="7ef54-194">在清單視圖中顯示物件群組</span><span class="sxs-lookup"><span data-stu-id="7ef54-194">Displaying Groups of Objects in a List View</span></span>

<span data-ttu-id="7ef54-195">您可以將清單視圖所顯示的物件分隔成群組。</span><span class="sxs-lookup"><span data-stu-id="7ef54-195">You can separate the objects that are displayed by the list view into groups.</span></span> <span data-ttu-id="7ef54-196">這並不表示您定義群組，只有當特定屬性或腳本的值變更時，Windows PowerShell 才會啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="7ef54-196">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="7ef54-197">在下列範例中，每當 [ [system.serviceprocess.dll. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) ] 屬性的值變更時，就會啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="7ef54-197">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="7ef54-198">下列 XML 元素可用來定義何時啟動群組：</span><span class="sxs-lookup"><span data-stu-id="7ef54-198">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="7ef54-199">[GroupBy](./groupby-element-for-view-format.md)元素會定義啟動新群組的屬性或腳本，並定義群組的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="7ef54-199">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="7ef54-200">[PropertyName](./propertyname-element-for-groupby-format.md)元素會指定在每次其值變更時啟動新群組的屬性。</span><span class="sxs-lookup"><span data-stu-id="7ef54-200">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="7ef54-201">您必須指定要啟動群組的屬性或腳本，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="7ef54-201">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="7ef54-202">[ScriptBlock](./scriptblock-element-for-groupby-format.md)元素會指定在每次其值變更時啟動新群組的腳本。</span><span class="sxs-lookup"><span data-stu-id="7ef54-202">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="7ef54-203">您必須指定腳本或屬性來啟動群組，但不能同時指定這兩者。</span><span class="sxs-lookup"><span data-stu-id="7ef54-203">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="7ef54-204">[Label](./label-element-for-groupby-format.md)元素會定義在每個群組的開頭顯示的標籤。</span><span class="sxs-lookup"><span data-stu-id="7ef54-204">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="7ef54-205">除了此元素所指定的文字之外，Windows PowerShell 還會顯示觸發新群組的值，並在標籤前後加上空白行。</span><span class="sxs-lookup"><span data-stu-id="7ef54-205">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="7ef54-206">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="7ef54-206">This element is optional.</span></span>

- <span data-ttu-id="7ef54-207">[CustomControl](./customcontrol-element-for-groupby-format.md)元素會定義用來顯示資料的控制項。</span><span class="sxs-lookup"><span data-stu-id="7ef54-207">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="7ef54-208">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="7ef54-208">This element is optional.</span></span>

- <span data-ttu-id="7ef54-209">[CustomControlName](./customcontrolname-element-for-groupby-format.md)元素會指定用來顯示資料的通用或 view 控制項。</span><span class="sxs-lookup"><span data-stu-id="7ef54-209">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="7ef54-210">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="7ef54-210">This element is optional.</span></span>

<span data-ttu-id="7ef54-211">如需定義群組之完整格式檔案的範例，請參閱[清單視圖 (GroupBy) ](./list-view-groupby.md)。</span><span class="sxs-lookup"><span data-stu-id="7ef54-211">For an example of a complete formatting file that defines groups, see [List View (GroupBy)](./list-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="7ef54-212">使用格式字串</span><span class="sxs-lookup"><span data-stu-id="7ef54-212">Using Format Strings</span></span>

<span data-ttu-id="7ef54-213">將字串格式化可以加入至視圖，以進一步定義資料的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="7ef54-213">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="7ef54-214">下列範例顯示如何為屬性的值定義格式化字串 `StartTime` 。</span><span class="sxs-lookup"><span data-stu-id="7ef54-214">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

<span data-ttu-id="7ef54-215">下列 XML 元素可以用來指定格式模式：</span><span class="sxs-lookup"><span data-stu-id="7ef54-215">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="7ef54-216">[專案類型[] 元素會](./listitem-element-for-listitems-for-listcontrol-format.md)指定視圖所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="7ef54-216">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="7ef54-217">[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)元素會指定屬性，其值會由視圖顯示。</span><span class="sxs-lookup"><span data-stu-id="7ef54-217">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="7ef54-218">您必須指定屬性或腳本，但不能同時指定這兩者。</span><span class="sxs-lookup"><span data-stu-id="7ef54-218">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="7ef54-219">[[字串](./formatstring-element-for-listitem-for-listcontrol-format.md)類型] 元素會指定格式模式，以定義屬性或腳本值在視圖中的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="7ef54-219">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

- <span data-ttu-id="7ef54-220">[ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md)元素 (不會顯示) 指定由視圖顯示其值的腳本。</span><span class="sxs-lookup"><span data-stu-id="7ef54-220">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="7ef54-221">您必須指定腳本或屬性，但不能同時指定這兩者。</span><span class="sxs-lookup"><span data-stu-id="7ef54-221">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="7ef54-222">在下列範例中， `ToString` 會呼叫方法來格式化腳本的值。</span><span class="sxs-lookup"><span data-stu-id="7ef54-222">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="7ef54-223">腳本可以呼叫物件的任何方法。</span><span class="sxs-lookup"><span data-stu-id="7ef54-223">Scripts can call any method of an object.</span></span> <span data-ttu-id="7ef54-224">因此，如果物件具有具有格式化參數的方法（例如 `ToString` ），則腳本可以呼叫該方法來格式化腳本的輸出值。</span><span class="sxs-lookup"><span data-stu-id="7ef54-224">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="7ef54-225">下列 XML 元素可以用來呼叫 `ToString` 方法：</span><span class="sxs-lookup"><span data-stu-id="7ef54-225">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="7ef54-226">[專案類型[] 元素會](./listitem-element-for-listitems-for-listcontrol-format.md)指定視圖所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="7ef54-226">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="7ef54-227">[ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md)元素 (不會顯示) 指定由視圖顯示其值的腳本。</span><span class="sxs-lookup"><span data-stu-id="7ef54-227">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="7ef54-228">您必須指定腳本或屬性，但不能同時指定這兩者。</span><span class="sxs-lookup"><span data-stu-id="7ef54-228">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ef54-229">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ef54-229">See Also</span></span>

[<span data-ttu-id="7ef54-230">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7ef54-230">Writing a Windows PowerShell Cmdlet</span></span>](../cmdlet/writing-a-windows-powershell-cmdlet.md)
