---
title: 建立資料表檢視 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1f405afb-70b5-4fe0-9986-bc07401d93fd
caps.latest.revision: 23
ms.openlocfilehash: 832527ea4b042812c39934cd7e124201c6dc2ea4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861494"
---
# <a name="creating-a-table-view"></a><span data-ttu-id="f08b2-102">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="f08b2-102">Creating a Table View</span></span>

<span data-ttu-id="f08b2-103">資料表檢視中一或多個資料行中顯示資料。</span><span class="sxs-lookup"><span data-stu-id="f08b2-103">A table view displays data in one or more columns.</span></span> <span data-ttu-id="f08b2-104">在資料表中的每個資料列代表.NET 物件，而資料表的每個資料行表示的物件或指令碼值的屬性。</span><span class="sxs-lookup"><span data-stu-id="f08b2-104">Each row in the table represents a .NET object, and each column of the table represents a property of the object or a script value.</span></span> <span data-ttu-id="f08b2-105">您可以定義會顯示物件的所有屬性或物件的屬性子集的資料表檢視。</span><span class="sxs-lookup"><span data-stu-id="f08b2-105">You can define a table view that displays all the properties of an object or a subset of the properties of an object.</span></span>

## <a name="a-table-view-display"></a><span data-ttu-id="f08b2-106">資料表檢視顯示</span><span class="sxs-lookup"><span data-stu-id="f08b2-106">A Table View Display</span></span>

<span data-ttu-id="f08b2-107">下列範例會示範 Windows PowerShell 的會顯示[System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)所傳回的物件[Get-service](/powershell/module/microsoft.powershell.management/get-service) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f08b2-107">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="f08b2-108">此物件中，Windows PowerShell 已定義顯示的資料表檢視`Status`屬性，`Name`屬性 (此屬性是別名屬性`ServiceName`屬性)，和`DisplayName`屬性。</span><span class="sxs-lookup"><span data-stu-id="f08b2-108">For this object, Windows PowerShell has defined a table view that displays the `Status` property, the `Name` property (this property is an alias property for the `ServiceName` property), and the `DisplayName` property.</span></span> <span data-ttu-id="f08b2-109">在資料表中的每個資料列代表 cmdlet 傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="f08b2-109">Each row in the table represents an object returned by the cmdlet.</span></span>

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a><span data-ttu-id="f08b2-110">定義資料表檢視</span><span class="sxs-lookup"><span data-stu-id="f08b2-110">Defining the Table View</span></span>

<span data-ttu-id="f08b2-111">下列 XML 顯示的資料表檢視結構描述顯示[System.Serviceprocess.Servicecontroller 嗎？Displayproperty = Fullname>](/dotnet/api/System.ServiceProcess.ServiceController)物件。</span><span class="sxs-lookup"><span data-stu-id="f08b2-111">The following XML shows the table view schema for displaying the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="f08b2-112">您必須指定您想要在資料表檢視中顯示每個屬性。</span><span class="sxs-lookup"><span data-stu-id="f08b2-112">You must specify each property that you want displayed in the table view.</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>
      <TableColumnHeader>
        <Width>8</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>18</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>38</Width>
      </TableColumnHeader>
    </TableHeaders>
    <TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
           <PropertyName>Status</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>
  </TableControl>
</View>
```

<span data-ttu-id="f08b2-113">下列 XML 元素用來定義清單檢視：</span><span class="sxs-lookup"><span data-stu-id="f08b2-113">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="f08b2-114">[檢視](./view-element-format.md)項目是 [資料表] 檢視的父項目。</span><span class="sxs-lookup"><span data-stu-id="f08b2-114">The [View](./view-element-format.md) element is the parent element of the table view.</span></span> <span data-ttu-id="f08b2-115">（這是針對清單中，，和自訂的控制項檢視相同的父項目）。</span><span class="sxs-lookup"><span data-stu-id="f08b2-115">(This is the same parent element for the list, wide, and custom control views.)</span></span>

- <span data-ttu-id="f08b2-116">[名稱](./name-element-for-view-format.md)項目會指定檢視的名稱。</span><span class="sxs-lookup"><span data-stu-id="f08b2-116">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="f08b2-117">所有檢視需要此項目。</span><span class="sxs-lookup"><span data-stu-id="f08b2-117">This element is required for all views.</span></span>

- <span data-ttu-id="f08b2-118">[ViewSelectedBy](./viewselectedby-element-format.md)項目會定義使用檢視的物件。</span><span class="sxs-lookup"><span data-stu-id="f08b2-118">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="f08b2-119">需要此項目。</span><span class="sxs-lookup"><span data-stu-id="f08b2-119">This element is required.</span></span>

- <span data-ttu-id="f08b2-120">[GroupBy](./groupby-element-for-view-format.md) （未顯示在此範例中） 的項目會定義當物件的新群組就會顯示。</span><span class="sxs-lookup"><span data-stu-id="f08b2-120">The [GroupBy](./groupby-element-for-view-format.md) element (not shown in this example) defines when a new group of objects is displayed.</span></span> <span data-ttu-id="f08b2-121">每次特定的屬性或指令碼的值變更時，會啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="f08b2-121">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="f08b2-122">這是選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="f08b2-122">This element is optional.</span></span>

- <span data-ttu-id="f08b2-123">[控制項](./controls-element-for-view-format.md)（未顯示在此範例中） 的項目會定義由 [資料表] 檢視所定義的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="f08b2-123">The [Controls](./controls-element-for-view-format.md) element (not shown in this example) defines the custom controls that are defined by the table view.</span></span> <span data-ttu-id="f08b2-124">控制項可讓您進一步指定 顯示資料的方式。</span><span class="sxs-lookup"><span data-stu-id="f08b2-124">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="f08b2-125">這是選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="f08b2-125">This element is optional.</span></span> <span data-ttu-id="f08b2-126">檢視可以定義自己的自訂控制項，或可以使用通用控制項，可供任何檢視中的格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="f08b2-126">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="f08b2-127">如需有關自訂控制項的詳細資訊，請參閱 <<c0> [ 建立自訂控制項](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="f08b2-127">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="f08b2-128">[HideTableHeaders](./hidetableheaders-element-format.md)項目 （不在此範例中顯示） 可讓您指定的資料表不會顯示在資料表頂端的任何標籤。</span><span class="sxs-lookup"><span data-stu-id="f08b2-128">The [HideTableHeaders](./hidetableheaders-element-format.md) element (not show in this example) specifies that the table will not show any labels at the top of the table.</span></span> <span data-ttu-id="f08b2-129">這是選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="f08b2-129">This element is optional.</span></span>

- <span data-ttu-id="f08b2-130">[TableControl](./tablecontrol-element-format.md)項目，定義的標頭和資料列資訊的資料表。</span><span class="sxs-lookup"><span data-stu-id="f08b2-130">The [TableControl](./tablecontrol-element-format.md) element that defines the header and row information of the table.</span></span> <span data-ttu-id="f08b2-131">類似於其他所有的檢視，[資料表] 檢視可以顯示指令碼所產生的值或物件屬性的值。</span><span class="sxs-lookup"><span data-stu-id="f08b2-131">Similar to all other views, a table view can display the values of object properties or values generated by scripts.</span></span>

## <a name="defining-column-headers"></a><span data-ttu-id="f08b2-132">定義資料行標頭</span><span class="sxs-lookup"><span data-stu-id="f08b2-132">Defining Column Headers</span></span>

1. <span data-ttu-id="f08b2-133">[TableHeaders](./tableheaders-element-format.md)項目和其子項目會定義在資料表頂端顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="f08b2-133">The [TableHeaders](./tableheaders-element-format.md) element and its child elements define what is displayed at the top of the table.</span></span>

2. <span data-ttu-id="f08b2-134">[TableColumnHeader](./tablecolumnheader-element-format.md)項目會定義在資料表資料行的頂端顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="f08b2-134">The [TableColumnHeader](./tablecolumnheader-element-format.md) element defines what is displayed at the top of a column of the table.</span></span> <span data-ttu-id="f08b2-135">您想要顯示的標頭的順序指定這些項目。</span><span class="sxs-lookup"><span data-stu-id="f08b2-135">Specify these elements in the order that you want the headers displayed.</span></span>

   <span data-ttu-id="f08b2-136">您可以使用，這些項目數目，但數目沒有限制[TableColumnHeader](./tablecolumnheader-element-format.md)在資料表檢視中的項目必須等於數目[TableRowEntry](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)您所使用的項目。</span><span class="sxs-lookup"><span data-stu-id="f08b2-136">There is no limit to the number of these element that you can use, but the number of [TableColumnHeader](./tablecolumnheader-element-format.md) elements in your table view must equal the number of [TableRowEntry](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md) elements that you use.</span></span>

3. <span data-ttu-id="f08b2-137">[標籤](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)項目會指定所顯示的文字。</span><span class="sxs-lookup"><span data-stu-id="f08b2-137">The [Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the text that is displayed.</span></span> <span data-ttu-id="f08b2-138">這是選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="f08b2-138">This element is optional.</span></span>

4. <span data-ttu-id="f08b2-139">[寬度](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)項目會指定資料行的寬度 （以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="f08b2-139">The [Width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the width (in characters) of the column.</span></span> <span data-ttu-id="f08b2-140">這是選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="f08b2-140">This element is optional.</span></span>

5. <span data-ttu-id="f08b2-141">[對齊](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)項目可讓您指定標籤的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="f08b2-141">The [Alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies how the label is displayed.</span></span> <span data-ttu-id="f08b2-142">標籤可以是靠左、 右邊，對齊或置中對齊。</span><span class="sxs-lookup"><span data-stu-id="f08b2-142">The label can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="f08b2-143">這是選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="f08b2-143">This element is optional.</span></span>

## <a name="defining-the-table-rows"></a><span data-ttu-id="f08b2-144">定義資料表的資料列</span><span class="sxs-lookup"><span data-stu-id="f08b2-144">Defining the Table Rows</span></span>

<span data-ttu-id="f08b2-145">資料表檢視可以提供一或多個指定哪些資料時，會顯示在資料表的資料列上，使用的子元素的定義[TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md)項目。</span><span class="sxs-lookup"><span data-stu-id="f08b2-145">Table views can provide one or more definitions that specify what data is displayed in the rows of the table by using the child elements of the [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="f08b2-146">請注意，您可以指定多個定義的資料列的資料表，但標頭資料列維持不變，不論使用何種資料列定義。</span><span class="sxs-lookup"><span data-stu-id="f08b2-146">Notice that you can specify multiple definitions for the rows of the table, but the headers for the rows remains the same, regardless of what row definition is used.</span></span> <span data-ttu-id="f08b2-147">一般而言，資料表必須只有一個定義。</span><span class="sxs-lookup"><span data-stu-id="f08b2-147">Typically, a table will have only one definition.</span></span>

<span data-ttu-id="f08b2-148">在下列範例中，此檢視會提供顯示的數個屬性的值的單一定義[System.Diagnostics.Process 嗎？Displayproperty = Fullname>](/dotnet/api/System.Diagnostics.Process)物件。</span><span class="sxs-lookup"><span data-stu-id="f08b2-148">In the following example, the view provides a single definition that displays the values of several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="f08b2-149">資料表檢視，可以顯示屬性的值或指令碼 （未顯示在範例中） 的值，其資料列中。</span><span class="sxs-lookup"><span data-stu-id="f08b2-149">A table view can display the value of a property or the value of a script (not shown in the example) in its rows.</span></span>

```xml
<TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
           <PropertyName>Status</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>

```

<span data-ttu-id="f08b2-150">下列的 XML 項目可以用來提供資料列的定義中：</span><span class="sxs-lookup"><span data-stu-id="f08b2-150">The following XML elements can be used to provide definitions for a row:</span></span>

- <span data-ttu-id="f08b2-151">[TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md)元素和其子項目會定義資料表的資料列中顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="f08b2-151">The [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element and its child elements define what is displayed in the rows of the table.</span></span>

- <span data-ttu-id="f08b2-152">[TableRowEntry](./listentry-element-for-listcontrol-format.md)項目提供的資料列的定義。</span><span class="sxs-lookup"><span data-stu-id="f08b2-152">The [TableRowEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the row.</span></span> <span data-ttu-id="f08b2-153">至少一個[TableRowEntry](./listentry-element-for-listcontrol-format.md)是必要項; 不過，還有您可以新增的項目數沒有上限限制。</span><span class="sxs-lookup"><span data-stu-id="f08b2-153">At least one [TableRowEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="f08b2-154">在大部分情況下，檢視必須只有一個定義。</span><span class="sxs-lookup"><span data-stu-id="f08b2-154">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="f08b2-155">[EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)項目會指定特定的定義所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="f08b2-155">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="f08b2-156">這個項目是選擇性的只有在您定義多個時，才需要[TableRowEntry](./listentry-element-for-listcontrol-format.md)顯示不同的物件項目。</span><span class="sxs-lookup"><span data-stu-id="f08b2-156">This element is optional and is needed only when you define multiple [TableRowEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="f08b2-157">[包裝](./wrap-element-for-tablerowentry-for-tablecontrl-format.md)項目會指定超過欄寬度的文字會顯示在下一行。</span><span class="sxs-lookup"><span data-stu-id="f08b2-157">The [Wrap](./wrap-element-for-tablerowentry-for-tablecontrl-format.md) element specifies that text that exceeds the column width is displayed on the next line.</span></span> <span data-ttu-id="f08b2-158">根據預設，系統會截斷超過欄寬度的文字。</span><span class="sxs-lookup"><span data-stu-id="f08b2-158">By default, text that exceeds the column width is truncated.</span></span>

- <span data-ttu-id="f08b2-159">[TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)項目定義的屬性或其值會顯示資料列中的指令碼。</span><span class="sxs-lookup"><span data-stu-id="f08b2-159">The [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) element defines the properties or scripts whose values are displayed in the row.</span></span>

- <span data-ttu-id="f08b2-160">[TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)項目定義之屬性或其值會顯示在資料列的資料行的指令碼。</span><span class="sxs-lookup"><span data-stu-id="f08b2-160">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="f08b2-161">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) ，則需要每個資料行的資料列元素。</span><span class="sxs-lookup"><span data-stu-id="f08b2-161">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="f08b2-162">第一個項目會顯示在第一個資料行，第二個項目，在第二個資料行，依此類推。</span><span class="sxs-lookup"><span data-stu-id="f08b2-162">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="f08b2-163">[PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)項目會指定資料列中顯示其值的屬性。</span><span class="sxs-lookup"><span data-stu-id="f08b2-163">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="f08b2-164">您必須指定屬性或指令碼，但您無法同時指定。</span><span class="sxs-lookup"><span data-stu-id="f08b2-164">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="f08b2-165">[ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)項目會指定其值會顯示資料列中的指令碼。</span><span class="sxs-lookup"><span data-stu-id="f08b2-165">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="f08b2-166">您必須指定指令碼或屬性，但您無法同時指定。</span><span class="sxs-lookup"><span data-stu-id="f08b2-166">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="f08b2-167">[FormatString](./label-element-for-listitem-for-listcontrol-format.md)項目會指定定義的屬性或指令碼的值的顯示方式的格式模式。</span><span class="sxs-lookup"><span data-stu-id="f08b2-167">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span> <span data-ttu-id="f08b2-168">這是選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="f08b2-168">This element is optional.</span></span>

- <span data-ttu-id="f08b2-169">[對齊](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)項目可讓您指定的指令碼的屬性值的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="f08b2-169">The [Alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies how the value of the property or script is displayed.</span></span> <span data-ttu-id="f08b2-170">值可以靠左，向右對齊或置中對齊。</span><span class="sxs-lookup"><span data-stu-id="f08b2-170">The value can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="f08b2-171">這是選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="f08b2-171">This element is optional.</span></span>

## <a name="defining-the-objects-that-use-the-table-view"></a><span data-ttu-id="f08b2-172">定義使用 [資料表] 檢視的物件</span><span class="sxs-lookup"><span data-stu-id="f08b2-172">Defining the Objects That Use the Table View</span></span>

<span data-ttu-id="f08b2-173">有兩種方式可定義的.NET 物件會使用 [資料表] 檢視。</span><span class="sxs-lookup"><span data-stu-id="f08b2-173">There are two ways to define which .NET objects use the table view.</span></span> <span data-ttu-id="f08b2-174">您可以使用[ViewSelectedBy](./viewselectedby-element-format.md)項目來定義可顯示的檢視，或您的所有定義的物件可以使用[EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md)項目來定義會顯示哪些物件特定檢視的定義。</span><span class="sxs-lookup"><span data-stu-id="f08b2-174">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="f08b2-175">在大部分情況下，檢視有只有一個定義，因此物件通常會定義所[ViewSelectedBy](./viewselectedby-element-format.md)項目。</span><span class="sxs-lookup"><span data-stu-id="f08b2-175">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="f08b2-176">下列範例示範如何定義會顯示資料表 檢視使用的物件[ViewSelectedBy](./viewselectedby-element-format.md)並[TypeName](./typename-element-for-viewselectedby-format.md)項目。</span><span class="sxs-lookup"><span data-stu-id="f08b2-176">The following example shows how to define the objects that are displayed by the table view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="f08b2-177">沒有任何限制的數目[TypeName](./typename-element-for-viewselectedby-format.md) ，您可以指定，且其順序並不重要的項目。</span><span class="sxs-lookup"><span data-stu-id="f08b2-177">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="f08b2-178">下列的 XML 項目可以用來指定物件所使用的資料表檢視中：</span><span class="sxs-lookup"><span data-stu-id="f08b2-178">The following XML elements can be used to specify the objects that are used by the table view:</span></span>

- <span data-ttu-id="f08b2-179">[ViewSelectedBy](./viewselectedby-element-format.md)項目會定義 [清單] 檢視會顯示哪些物件。</span><span class="sxs-lookup"><span data-stu-id="f08b2-179">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="f08b2-180">[TypeName](./typename-element-for-viewselectedby-format.md)項目會指定檢視所顯示的.NET 物件。</span><span class="sxs-lookup"><span data-stu-id="f08b2-180">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="f08b2-181">需要完整的.NET 型別名稱。</span><span class="sxs-lookup"><span data-stu-id="f08b2-181">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="f08b2-182">您必須指定至少一個型別或設定檢視中，選取項目，但可以指定的項目沒有最大數目。</span><span class="sxs-lookup"><span data-stu-id="f08b2-182">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="f08b2-183">下列範例會使用[ViewSelectedBy](./viewselectedby-element-format.md)並[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)項目。</span><span class="sxs-lookup"><span data-stu-id="f08b2-183">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="f08b2-184">使用選取項目集都有一組相關的物件，會顯示使用多個檢視，例如當您定義清單檢視和資料表檢視表相同的物件的位置。</span><span class="sxs-lookup"><span data-stu-id="f08b2-184">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="f08b2-185">如需如何建立選取項目集的詳細資訊，請參閱[定義的選取項目集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="f08b2-185">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="f08b2-186">下列的 XML 項目可以用來指定物件所使用的清單檢視中：</span><span class="sxs-lookup"><span data-stu-id="f08b2-186">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="f08b2-187">[ViewSelectedBy](./viewselectedby-element-format.md)項目會定義 [清單] 檢視會顯示哪些物件。</span><span class="sxs-lookup"><span data-stu-id="f08b2-187">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="f08b2-188">[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)項目會指定一組可以檢視所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="f08b2-188">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="f08b2-189">您必須指定至少一個選取項目集或類型檢視中，但您可以指定的項目沒有最大數目。</span><span class="sxs-lookup"><span data-stu-id="f08b2-189">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="f08b2-190">下列範例示範如何定義顯示由特定的資料表檢視使用定義的物件[EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)項目。</span><span class="sxs-lookup"><span data-stu-id="f08b2-190">The following example shows how to define the objects displayed by a specific definition of the table view using the [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="f08b2-191">您可以使用這個項目，來指定物件、 選取項目集的物件或選取條件，指定當使用定義的.NET 型別名稱。</span><span class="sxs-lookup"><span data-stu-id="f08b2-191">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="f08b2-192">如需如何建立選取項目條件的詳細資訊，請參閱[定義的條件，顯示資料](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="f08b2-192">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

> [!NOTE]
> <span data-ttu-id="f08b2-193">建立多個資料表的檢視定義時，您無法指定不同的資料行標頭。</span><span class="sxs-lookup"><span data-stu-id="f08b2-193">When creating multiple definitions of the table view you cannot specify different column headers.</span></span> <span data-ttu-id="f08b2-194">您可以指定只顯示之內容的資料表，例如哪些物件會顯示資料列。</span><span class="sxs-lookup"><span data-stu-id="f08b2-194">You can specify only what is displayed in the rows of the table, such as what objects are displayed.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

<span data-ttu-id="f08b2-195">下列的 XML 項目可以用來指定物件所使用的特定檢視的定義清單中：</span><span class="sxs-lookup"><span data-stu-id="f08b2-195">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="f08b2-196">[EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)項目會定義哪些物件會定義所顯示。</span><span class="sxs-lookup"><span data-stu-id="f08b2-196">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="f08b2-197">[TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md)項目會指定定義所顯示的.NET 物件。</span><span class="sxs-lookup"><span data-stu-id="f08b2-197">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="f08b2-198">使用這個項目，完整的.NET 型別名稱時需要。</span><span class="sxs-lookup"><span data-stu-id="f08b2-198">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="f08b2-199">您必須指定至少一個型別、 選取項目集或選擇條件的定義，但您可以指定的項目沒有最大數目。</span><span class="sxs-lookup"><span data-stu-id="f08b2-199">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="f08b2-200">[SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) （未顯示） 的項目會指定一組可顯示的這個定義的物件。</span><span class="sxs-lookup"><span data-stu-id="f08b2-200">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="f08b2-201">您必須指定至少一個型別、 選取項目集或選擇條件的定義，但您可以指定的項目沒有最大數目。</span><span class="sxs-lookup"><span data-stu-id="f08b2-201">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="f08b2-202">[SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) （未顯示） 的項目會指定要使用此定義必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="f08b2-202">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="f08b2-203">您必須指定至少一個型別、 選取項目集或選擇條件的定義，但您可以指定的項目沒有最大數目。</span><span class="sxs-lookup"><span data-stu-id="f08b2-203">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="f08b2-204">如需定義選擇條件的詳細資訊，請參閱 <<c0> [ 定義的條件，顯示資料](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="f08b2-204">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="f08b2-205">使用格式字串</span><span class="sxs-lookup"><span data-stu-id="f08b2-205">Using Format Strings</span></span>

<span data-ttu-id="f08b2-206">格式字串可以加入檢視，以進一步定義資料的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="f08b2-206">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="f08b2-207">下列範例示範如何定義的格式化字串的值，`StartTime`屬性。</span><span class="sxs-lookup"><span data-stu-id="f08b2-207">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

<span data-ttu-id="f08b2-208">下列的 XML 項目可以用來指定之格式模式中：</span><span class="sxs-lookup"><span data-stu-id="f08b2-208">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="f08b2-209">[TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)項目定義之屬性或其值會顯示在資料列的資料行的指令碼。</span><span class="sxs-lookup"><span data-stu-id="f08b2-209">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="f08b2-210">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) ，則需要每個資料行的資料列元素。</span><span class="sxs-lookup"><span data-stu-id="f08b2-210">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="f08b2-211">第一個項目會顯示在第一個資料行，第二個項目，在第二個資料行，依此類推。</span><span class="sxs-lookup"><span data-stu-id="f08b2-211">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="f08b2-212">[PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)項目會指定資料列中顯示其值的屬性。</span><span class="sxs-lookup"><span data-stu-id="f08b2-212">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="f08b2-213">您必須指定屬性或指令碼，但您無法同時指定。</span><span class="sxs-lookup"><span data-stu-id="f08b2-213">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="f08b2-214">[FormatString](./label-element-for-listitem-for-listcontrol-format.md)項目會指定定義的屬性或指令碼的值的顯示方式的格式模式。</span><span class="sxs-lookup"><span data-stu-id="f08b2-214">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="f08b2-215">在下列範例中，`ToString`來格式化值的指令碼會呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="f08b2-215">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="f08b2-216">指令碼可以呼叫任何方法的物件。</span><span class="sxs-lookup"><span data-stu-id="f08b2-216">Scripts can call any method of an object.</span></span> <span data-ttu-id="f08b2-217">因此，如果物件有一個方法，例如`ToString`具有格式設定的參數，指令碼可以呼叫該方法，來設定指令碼的輸出值的格式。</span><span class="sxs-lookup"><span data-stu-id="f08b2-217">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="f08b2-218">下列的 XML 項目可以用來呼叫`ToString`方法：</span><span class="sxs-lookup"><span data-stu-id="f08b2-218">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="f08b2-219">[TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)項目定義之屬性或其值會顯示在資料列的資料行的指令碼。</span><span class="sxs-lookup"><span data-stu-id="f08b2-219">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="f08b2-220">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) ，則需要每個資料行的資料列元素。</span><span class="sxs-lookup"><span data-stu-id="f08b2-220">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="f08b2-221">第一個項目會顯示在第一個資料行，第二個項目，在第二個資料行，依此類推。</span><span class="sxs-lookup"><span data-stu-id="f08b2-221">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="f08b2-222">[ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)項目會指定其值會顯示資料列中的指令碼。</span><span class="sxs-lookup"><span data-stu-id="f08b2-222">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="f08b2-223">您必須指定指令碼或屬性，但您無法同時指定。</span><span class="sxs-lookup"><span data-stu-id="f08b2-223">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="f08b2-224">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f08b2-224">See Also</span></span>

[<span data-ttu-id="f08b2-225">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="f08b2-225">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
