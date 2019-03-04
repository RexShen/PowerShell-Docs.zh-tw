---
title: 建立清單檢視 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c7a40ca-1786-46f0-bab5-6ce229daa7ee
caps.latest.revision: 14
ms.openlocfilehash: 25d24063501196d44e0f806a55bb699c82f771ce
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861574"
---
# <a name="creating-a-list-view"></a><span data-ttu-id="84b9e-102">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="84b9e-102">Creating a List View</span></span>

<span data-ttu-id="84b9e-103">清單檢視會顯示資料 （在循序順序） 的單一資料行中。</span><span class="sxs-lookup"><span data-stu-id="84b9e-103">A list view displays data in a single column (in sequential order).</span></span> <span data-ttu-id="84b9e-104">顯示在清單中的資料可以是.NET 屬性的值或值的指令碼。</span><span class="sxs-lookup"><span data-stu-id="84b9e-104">The data displayed in the list can be the value of a .NET property or the value of a script.</span></span>

## <a name="a-list-view-display"></a><span data-ttu-id="84b9e-105">以清單檢視顯示</span><span class="sxs-lookup"><span data-stu-id="84b9e-105">A List View Display</span></span>

<span data-ttu-id="84b9e-106">下列輸出顯示 Windows PowerShell 如何顯示的屬性[System.Serviceprocess.Servicecontroller 嗎？Displayproperty = Fullname>](/dotnet/api/System.ServiceProcess.ServiceController)所傳回的物件[Get-service](/powershell/module/microsoft.powershell.management/get-service) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="84b9e-106">The following output shows how Windows PowerShell displays the properties of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects that are returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="84b9e-107">在此範例中，已傳回三個物件，與上述物件使用空白行來分隔每個物件。</span><span class="sxs-lookup"><span data-stu-id="84b9e-107">In this example, three objects were returned, with each object separated from the preceding object by a blank line.</span></span>

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

## <a name="defining-the-list-view"></a><span data-ttu-id="84b9e-108">定義清單檢視</span><span class="sxs-lookup"><span data-stu-id="84b9e-108">Defining the List View</span></span>

<span data-ttu-id="84b9e-109">下列 XML 說明顯示的數個屬性的清單檢視結構描述[System.Serviceprocess.Servicecontroller 嗎？Displayproperty = Fullname>](/dotnet/api/System.ServiceProcess.ServiceController)物件。</span><span class="sxs-lookup"><span data-stu-id="84b9e-109">The following XML shows the list view schema for displaying several properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="84b9e-110">您必須指定您想要顯示在清單檢視中的每一個屬性。</span><span class="sxs-lookup"><span data-stu-id="84b9e-110">You must specify each property that you want displayed in the list view.</span></span>

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

<span data-ttu-id="84b9e-111">下列 XML 元素用來定義清單檢視：</span><span class="sxs-lookup"><span data-stu-id="84b9e-111">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="84b9e-112">[檢視](./view-element-format.md)項目是清單檢視中的父項目。</span><span class="sxs-lookup"><span data-stu-id="84b9e-112">The [View](./view-element-format.md) element is the parent element of the list view.</span></span> <span data-ttu-id="84b9e-113">（這是資料表，和自訂的控制項檢視相同的父項目）。</span><span class="sxs-lookup"><span data-stu-id="84b9e-113">(This is the same parent element for the table, wide, and custom control views.)</span></span>

- <span data-ttu-id="84b9e-114">[名稱](./name-element-for-view-format.md)項目會指定檢視的名稱。</span><span class="sxs-lookup"><span data-stu-id="84b9e-114">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="84b9e-115">所有檢視需要此項目。</span><span class="sxs-lookup"><span data-stu-id="84b9e-115">This element is required for all views.</span></span>

- <span data-ttu-id="84b9e-116">[ViewSelectedBy](./viewselectedby-element-format.md)項目會定義使用檢視的物件。</span><span class="sxs-lookup"><span data-stu-id="84b9e-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="84b9e-117">需要此項目。</span><span class="sxs-lookup"><span data-stu-id="84b9e-117">This element is required.</span></span>

- <span data-ttu-id="84b9e-118">[GroupBy](./groupby-element-for-view-format.md)項目會定義當物件的新群組就會顯示。</span><span class="sxs-lookup"><span data-stu-id="84b9e-118">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="84b9e-119">每次特定的屬性或指令碼的值變更時，會啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="84b9e-119">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="84b9e-120">這是選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="84b9e-120">This element is optional.</span></span>

- <span data-ttu-id="84b9e-121">[控制項](./controls-element-for-view-format.md)項目會定義 [清單] 檢視所定義的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="84b9e-121">The [Controls](./controls-element-for-view-format.md) element defines the custom controls that are defined by the list view.</span></span> <span data-ttu-id="84b9e-122">控制項可讓您進一步指定 顯示資料的方式。</span><span class="sxs-lookup"><span data-stu-id="84b9e-122">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="84b9e-123">這是選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="84b9e-123">This element is optional.</span></span> <span data-ttu-id="84b9e-124">檢視可以定義自己的自訂控制項，或可以使用通用控制項，可供任何檢視中的格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="84b9e-124">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="84b9e-125">如需有關自訂控制項的詳細資訊，請參閱 <<c0> [ 建立自訂控制項](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="84b9e-125">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="84b9e-126">[ListControl](./listcontrol-element-format.md)項目會定義在檢視中顯示的內容和格式的方式。</span><span class="sxs-lookup"><span data-stu-id="84b9e-126">The [ListControl](./listcontrol-element-format.md) element defines what is displayed in the view and how it is formatted.</span></span> <span data-ttu-id="84b9e-127">類似於其他所有的檢視，清單檢視可以顯示指令碼所產生的值或物件屬性的值。</span><span class="sxs-lookup"><span data-stu-id="84b9e-127">Similar to all other views, a list view can display the values of object properties or values generated by script.</span></span>

<span data-ttu-id="84b9e-128">如需完整的格式化檔案，定義簡單的清單檢視的範例，請參閱 <<c0> [ 清單檢視 （基本）](./list-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="84b9e-128">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-list-view"></a><span data-ttu-id="84b9e-129">提供您的清單檢視的定義</span><span class="sxs-lookup"><span data-stu-id="84b9e-129">Providing Definitions for Your List View</span></span>

<span data-ttu-id="84b9e-130">清單檢視可提供一個或多個定義所使用之子項目的[ListControl](./listcontrol-element-format.md)項目。</span><span class="sxs-lookup"><span data-stu-id="84b9e-130">List views can provide one or more definitions by using the child elements of the [ListControl](./listcontrol-element-format.md) element.</span></span> <span data-ttu-id="84b9e-131">通常，檢視必須只有一個定義。</span><span class="sxs-lookup"><span data-stu-id="84b9e-131">Typically, a view will have only one definition.</span></span> <span data-ttu-id="84b9e-132">在下列範例中，此檢視會提供顯示的數個屬性的單一定義[System.Diagnostics.Process 嗎？Displayproperty = Fullname>](/dotnet/api/System.Diagnostics.Process)物件。</span><span class="sxs-lookup"><span data-stu-id="84b9e-132">In the following example, the view provides a single definition that displays several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="84b9e-133">清單檢視可以顯示屬性的值或 （在範例中未顯示） 的指令碼的值。</span><span class="sxs-lookup"><span data-stu-id="84b9e-133">A list view can display the value of a property or the value of a script (not shown in the example).</span></span>

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

<span data-ttu-id="84b9e-134">下列的 XML 項目可以用來提供針對清單檢視的定義中：</span><span class="sxs-lookup"><span data-stu-id="84b9e-134">The following XML elements can be used to provide definitions for a list view:</span></span>

- <span data-ttu-id="84b9e-135">[ListControl](./listcontrol-element-format.md)元素和其子項目會定義在檢視中顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="84b9e-135">The [ListControl](./listcontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="84b9e-136">[ListEntries](./listentries-element-for-listcontrol-format.md)項目會提供檢視的定義。</span><span class="sxs-lookup"><span data-stu-id="84b9e-136">The [ListEntries](./listentries-element-for-listcontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="84b9e-137">在大部分情況下，檢視必須只有一個定義。</span><span class="sxs-lookup"><span data-stu-id="84b9e-137">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="84b9e-138">需要此項目。</span><span class="sxs-lookup"><span data-stu-id="84b9e-138">This element is required.</span></span>

- <span data-ttu-id="84b9e-139">[ListEntry](./listentry-element-for-listcontrol-format.md)項目會提供檢視的定義。</span><span class="sxs-lookup"><span data-stu-id="84b9e-139">The [ListEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="84b9e-140">至少一個[ListEntry](./listentry-element-for-listcontrol-format.md)是必要項; 不過，還有您可以新增的項目數沒有上限限制。</span><span class="sxs-lookup"><span data-stu-id="84b9e-140">At least one [ListEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="84b9e-141">在大部分情況下，檢視必須只有一個定義。</span><span class="sxs-lookup"><span data-stu-id="84b9e-141">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="84b9e-142">[EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md)項目會指定特定的定義所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="84b9e-142">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="84b9e-143">這個項目是選擇性的只有在您定義多個時，才需要[ListEntry](./listentry-element-for-listcontrol-format.md)顯示不同的物件項目。</span><span class="sxs-lookup"><span data-stu-id="84b9e-143">This element is optional and is needed only when you define multiple [ListEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="84b9e-144">[ListItems](./listitems-element-for-listentry-for-listcontrol-format.md)項目指定的屬性和其值會顯示在清單檢視的資料列中的指令碼。</span><span class="sxs-lookup"><span data-stu-id="84b9e-144">The [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies the properties and scripts whose values are displayed in the rows of the list view.</span></span>

- <span data-ttu-id="84b9e-145">[ListItem](./listitems-element-for-listentry-for-listcontrol-format.md)元素會指定屬性或其值會顯示 [清單] 檢視的資料列中的指令碼。</span><span class="sxs-lookup"><span data-stu-id="84b9e-145">The [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies a property or script whose value is displayed in a row of the list view.</span></span> <span data-ttu-id="84b9e-146">至少一個屬性或指令碼，必須指定清單檢視。</span><span class="sxs-lookup"><span data-stu-id="84b9e-146">A list view must specify at least one property or script.</span></span> <span data-ttu-id="84b9e-147">沒有任何最大的限制，您可以指定的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="84b9e-147">There is no maximum limit to the number of rows that can be specified.</span></span>

- <span data-ttu-id="84b9e-148">[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)項目會指定資料列中顯示其值的屬性。</span><span class="sxs-lookup"><span data-stu-id="84b9e-148">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="84b9e-149">您必須指定屬性或指令碼，但您無法同時指定。</span><span class="sxs-lookup"><span data-stu-id="84b9e-149">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="84b9e-150">[ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md)項目會指定其值會顯示資料列中的指令碼。</span><span class="sxs-lookup"><span data-stu-id="84b9e-150">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="84b9e-151">您必須指定指令碼或屬性，但您無法同時指定。</span><span class="sxs-lookup"><span data-stu-id="84b9e-151">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="84b9e-152">[標籤](./label-element-for-listitem-for-listcontrol-format.md)項目會指定顯示屬性或指令碼中值的資料列左邊的標籤。</span><span class="sxs-lookup"><span data-stu-id="84b9e-152">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element specifies the label that is displayed to the left of the property or script value in the row.</span></span> <span data-ttu-id="84b9e-153">這是選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="84b9e-153">This element is optional.</span></span> <span data-ttu-id="84b9e-154">如果未指定標籤，則會顯示屬性或指令碼的名稱。</span><span class="sxs-lookup"><span data-stu-id="84b9e-154">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="84b9e-155">如需完整範例，請參閱 <<c0> [ 清單檢視 （標籤）](./list-view-labels.md)。</span><span class="sxs-lookup"><span data-stu-id="84b9e-155">For a complete example, see [List View (Labels)](./list-view-labels.md).</span></span>

- <span data-ttu-id="84b9e-156">[ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)項目會指定要顯示的資料列必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="84b9e-156">The [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) element specifies a condition that must exist for the row to be displayed.</span></span> <span data-ttu-id="84b9e-157">如需有關如何將條件新增至 [清單] 檢視的詳細資訊，請參閱[定義的條件，顯示資料](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="84b9e-157">For more information about adding conditions to the list view, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span> <span data-ttu-id="84b9e-158">這是選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="84b9e-158">This element is optional.</span></span>

- <span data-ttu-id="84b9e-159">[FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md)項目會指定用來顯示屬性或指令碼的值的模式。</span><span class="sxs-lookup"><span data-stu-id="84b9e-159">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a pattern that is used to display the value of the property or script.</span></span> <span data-ttu-id="84b9e-160">這是選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="84b9e-160">This element is optional.</span></span>

<span data-ttu-id="84b9e-161">如需完整的格式化檔案，定義簡單的清單檢視的範例，請參閱 <<c0> [ 清單檢視 （基本）](./list-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="84b9e-161">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-list-view"></a><span data-ttu-id="84b9e-162">定義使用清單檢視的物件</span><span class="sxs-lookup"><span data-stu-id="84b9e-162">Defining the Objects That Use the List View</span></span>

<span data-ttu-id="84b9e-163">有兩種方式可定義的.NET 物件會使用清單檢視。</span><span class="sxs-lookup"><span data-stu-id="84b9e-163">There are two ways to define which .NET objects use the list view.</span></span> <span data-ttu-id="84b9e-164">您可以使用[ViewSelectedBy](./viewselectedby-element-format.md)項目來定義可顯示的檢視，或您的所有定義的物件可以使用[EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md)項目來定義會顯示哪些物件特定檢視的定義。</span><span class="sxs-lookup"><span data-stu-id="84b9e-164">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="84b9e-165">在大部分情況下，檢視有只有一個定義，因此物件通常會定義所[ViewSelectedBy](./viewselectedby-element-format.md)項目。</span><span class="sxs-lookup"><span data-stu-id="84b9e-165">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="84b9e-166">下列範例示範如何定義會顯示清單檢視使用的物件[ViewSelectedBy](./viewselectedby-element-format.md)並[TypeName](./typename-element-for-viewselectedby-format.md)項目。</span><span class="sxs-lookup"><span data-stu-id="84b9e-166">The following example shows how to define the objects that are displayed by the list view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="84b9e-167">沒有任何限制的數目[TypeName](./typename-element-for-viewselectedby-format.md) ，您可以指定，且其順序並不重要的項目。</span><span class="sxs-lookup"><span data-stu-id="84b9e-167">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="84b9e-168">下列的 XML 項目可以用來指定物件所使用的清單檢視中：</span><span class="sxs-lookup"><span data-stu-id="84b9e-168">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="84b9e-169">[ViewSelectedBy](./viewselectedby-element-format.md)項目會定義 [清單] 檢視會顯示哪些物件。</span><span class="sxs-lookup"><span data-stu-id="84b9e-169">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="84b9e-170">[TypeName](./typename-element-for-viewselectedby-format.md)項目會指定檢視所顯示的.NET 物件。</span><span class="sxs-lookup"><span data-stu-id="84b9e-170">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="84b9e-171">需要完整的.NET 型別名稱。</span><span class="sxs-lookup"><span data-stu-id="84b9e-171">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="84b9e-172">您必須指定至少一個型別或設定檢視中，選取項目，但可以指定的項目沒有最大數目。</span><span class="sxs-lookup"><span data-stu-id="84b9e-172">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="84b9e-173">如需完整的格式化檔案的範例，請參閱 <<c0> [ 清單檢視 （基本）](./list-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="84b9e-173">For an example of a complete formatting file, see [List View (Basic)](./list-view-basic.md).</span></span>

<span data-ttu-id="84b9e-174">下列範例會使用[ViewSelectedBy](./viewselectedby-element-format.md)並[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)項目。</span><span class="sxs-lookup"><span data-stu-id="84b9e-174">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="84b9e-175">使用選取項目集都有一組相關的物件，會顯示使用多個檢視，例如當您定義清單檢視和資料表檢視表相同的物件的位置。</span><span class="sxs-lookup"><span data-stu-id="84b9e-175">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="84b9e-176">如需如何建立選取項目集的詳細資訊，請參閱[定義的選取項目集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="84b9e-176">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="84b9e-177">下列的 XML 項目可以用來指定物件所使用的清單檢視中：</span><span class="sxs-lookup"><span data-stu-id="84b9e-177">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="84b9e-178">[ViewSelectedBy](./viewselectedby-element-format.md)項目會定義 [清單] 檢視會顯示哪些物件。</span><span class="sxs-lookup"><span data-stu-id="84b9e-178">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="84b9e-179">[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)項目會指定一組可以檢視所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="84b9e-179">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="84b9e-180">您必須指定至少一個選取項目集或類型檢視中，但您可以指定的項目沒有最大數目。</span><span class="sxs-lookup"><span data-stu-id="84b9e-180">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="84b9e-181">下列範例示範如何定義顯示清單檢視使用特定定義的物件[EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md)項目。</span><span class="sxs-lookup"><span data-stu-id="84b9e-181">The following example shows how to define the objects displayed by a specific definition of the list view using the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element.</span></span> <span data-ttu-id="84b9e-182">您可以使用這個項目，來指定物件、 選取項目集的物件或選取條件，指定當使用定義的.NET 型別名稱。</span><span class="sxs-lookup"><span data-stu-id="84b9e-182">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="84b9e-183">如需如何建立選取項目條件的詳細資訊，請參閱[定義的條件，顯示資料](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="84b9e-183">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

<span data-ttu-id="84b9e-184">下列的 XML 項目可以用來指定物件所使用的特定檢視的定義清單中：</span><span class="sxs-lookup"><span data-stu-id="84b9e-184">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="84b9e-185">[EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md)項目會定義哪些物件會定義所顯示。</span><span class="sxs-lookup"><span data-stu-id="84b9e-185">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="84b9e-186">[TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md)項目會指定定義所顯示的.NET 物件。</span><span class="sxs-lookup"><span data-stu-id="84b9e-186">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="84b9e-187">使用這個項目，完整的.NET 型別名稱時需要。</span><span class="sxs-lookup"><span data-stu-id="84b9e-187">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="84b9e-188">您必須指定至少一個型別、 選取項目集或選擇條件的定義，但您可以指定的項目沒有最大數目。</span><span class="sxs-lookup"><span data-stu-id="84b9e-188">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="84b9e-189">[SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) （未顯示） 的項目會指定一組可顯示的這個定義的物件。</span><span class="sxs-lookup"><span data-stu-id="84b9e-189">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="84b9e-190">您必須指定至少一個型別、 選取項目集或選擇條件的定義，但您可以指定的項目沒有最大數目。</span><span class="sxs-lookup"><span data-stu-id="84b9e-190">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="84b9e-191">[SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) （未顯示） 的項目會指定要使用此定義必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="84b9e-191">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="84b9e-192">您必須指定至少一個型別、 選取項目集或選擇條件的定義，但您可以指定的項目沒有最大數目。</span><span class="sxs-lookup"><span data-stu-id="84b9e-192">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="84b9e-193">如需定義選擇條件的詳細資訊，請參閱 <<c0> [ 定義的條件，顯示資料](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="84b9e-193">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-list-view"></a><span data-ttu-id="84b9e-194">在 清單檢視中顯示之物件的群組</span><span class="sxs-lookup"><span data-stu-id="84b9e-194">Displaying Groups of Objects in a List View</span></span>

<span data-ttu-id="84b9e-195">您可以分隔成群組的 [清單] 檢視所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="84b9e-195">You can separate the objects that are displayed by the list view into groups.</span></span> <span data-ttu-id="84b9e-196">這不表示您定義一個群組，只有特定的屬性或指令碼的值變更時，Windows PowerShell 會啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="84b9e-196">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="84b9e-197">在下列範例中，啟動新的群組時的值[System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType)屬性變更。</span><span class="sxs-lookup"><span data-stu-id="84b9e-197">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="84b9e-198">下列 XML 元素用來定義一組啟動時：</span><span class="sxs-lookup"><span data-stu-id="84b9e-198">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="84b9e-199">[GroupBy](./groupby-element-for-view-format.md)項目定義之屬性或啟動新的群組，並定義群組的顯示方式的指令碼。</span><span class="sxs-lookup"><span data-stu-id="84b9e-199">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="84b9e-200">[PropertyName](./propertyname-element-for-groupby-format.md)項目會指定開始新的群組，其值變更時的屬性。</span><span class="sxs-lookup"><span data-stu-id="84b9e-200">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="84b9e-201">您必須指定屬性或指令碼，以啟動群組中，但您無法同時指定。</span><span class="sxs-lookup"><span data-stu-id="84b9e-201">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="84b9e-202">[ScriptBlock](./scriptblock-element-for-groupby-format.md)項目會指定指令碼，其值變更時，會啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="84b9e-202">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="84b9e-203">您必須指定指令碼或屬性，以啟動群組中，但您無法同時指定。</span><span class="sxs-lookup"><span data-stu-id="84b9e-203">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="84b9e-204">[標籤](./label-element-for-groupby-format.md)項目會定義每個群組的開頭所顯示的標籤。</span><span class="sxs-lookup"><span data-stu-id="84b9e-204">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="84b9e-205">除了這個項目所指定的文字，Windows PowerShell 會顯示觸發新的群組，並新增一個空白行，標籤前後的值。</span><span class="sxs-lookup"><span data-stu-id="84b9e-205">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="84b9e-206">這是選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="84b9e-206">This element is optional.</span></span>

- <span data-ttu-id="84b9e-207">[CustomControl](./customcontrol-element-for-groupby-format.md)項目會定義用來顯示資料的控制項。</span><span class="sxs-lookup"><span data-stu-id="84b9e-207">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="84b9e-208">這是選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="84b9e-208">This element is optional.</span></span>

- <span data-ttu-id="84b9e-209">[CustomControlName](./customcontrolname-element-for-groupby-format.md)項目會指定一般或檢視來顯示資料的控制項。</span><span class="sxs-lookup"><span data-stu-id="84b9e-209">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="84b9e-210">這是選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="84b9e-210">This element is optional.</span></span>

<span data-ttu-id="84b9e-211">如需完整的格式化檔案，定義群組的範例，請參閱 <<c0> [ 清單檢視 (GroupBy)](./list-view-groupby.md)。</span><span class="sxs-lookup"><span data-stu-id="84b9e-211">For an example of a complete formatting file that defines groups, see [List View (GroupBy)](./list-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="84b9e-212">使用格式字串</span><span class="sxs-lookup"><span data-stu-id="84b9e-212">Using Format Strings</span></span>

<span data-ttu-id="84b9e-213">格式字串可以加入檢視，以進一步定義資料的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="84b9e-213">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="84b9e-214">下列範例示範如何定義的格式化字串的值，`StartTime`屬性。</span><span class="sxs-lookup"><span data-stu-id="84b9e-214">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

<span data-ttu-id="84b9e-215">下列的 XML 項目可以用來指定之格式模式中：</span><span class="sxs-lookup"><span data-stu-id="84b9e-215">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="84b9e-216">[ListItem](./listitem-element-for-listitems-for-listcontrol-format.md)項目會指定檢視所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="84b9e-216">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="84b9e-217">[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)項目會指定其值會顯示由檢視的屬性。</span><span class="sxs-lookup"><span data-stu-id="84b9e-217">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="84b9e-218">您必須指定屬性或指令碼，但您無法同時指定。</span><span class="sxs-lookup"><span data-stu-id="84b9e-218">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="84b9e-219">[FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md)項目會指定定義的屬性或指令碼的值在檢視中的顯示方式的格式模式。</span><span class="sxs-lookup"><span data-stu-id="84b9e-219">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

- <span data-ttu-id="84b9e-220">[ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) （未顯示） 的項目會指定其值會顯示檢視指令碼。</span><span class="sxs-lookup"><span data-stu-id="84b9e-220">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="84b9e-221">您必須指定指令碼或屬性，但您無法同時指定。</span><span class="sxs-lookup"><span data-stu-id="84b9e-221">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="84b9e-222">在下列範例中，`ToString`來格式化值的指令碼會呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="84b9e-222">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="84b9e-223">指令碼可以呼叫任何方法的物件。</span><span class="sxs-lookup"><span data-stu-id="84b9e-223">Scripts can call any method of an object.</span></span> <span data-ttu-id="84b9e-224">因此，如果物件有一個方法，例如`ToString`具有格式設定的參數，指令碼可以呼叫該方法，來設定指令碼的輸出值的格式。</span><span class="sxs-lookup"><span data-stu-id="84b9e-224">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="84b9e-225">下列的 XML 項目可以用來呼叫`ToString`方法：</span><span class="sxs-lookup"><span data-stu-id="84b9e-225">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="84b9e-226">[ListItem](./listitem-element-for-listitems-for-listcontrol-format.md)項目會指定檢視所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="84b9e-226">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="84b9e-227">[ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) （未顯示） 的項目會指定其值會顯示檢視指令碼。</span><span class="sxs-lookup"><span data-stu-id="84b9e-227">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="84b9e-228">您必須指定指令碼或屬性，但您無法同時指定。</span><span class="sxs-lookup"><span data-stu-id="84b9e-228">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="84b9e-229">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84b9e-229">See Also</span></span>

[<span data-ttu-id="84b9e-230">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="84b9e-230">Writing a Windows PowerShell Cmdlet</span></span>](../cmdlet/writing-a-windows-powershell-cmdlet.md)
