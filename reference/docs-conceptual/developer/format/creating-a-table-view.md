---
title: 建立資料表視圖 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: cbe81962a0f68d64506062898a8f21a1596cc29a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786147"
---
# <a name="creating-a-table-view"></a><span data-ttu-id="a020f-102">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="a020f-102">Creating a Table View</span></span>

<span data-ttu-id="a020f-103">資料表視圖會在一或多個資料行中顯示資料。</span><span class="sxs-lookup"><span data-stu-id="a020f-103">A table view displays data in one or more columns.</span></span> <span data-ttu-id="a020f-104">資料表中的每個資料列都代表一個 .NET 物件，而資料表的每個資料行都代表物件的屬性或腳本值。</span><span class="sxs-lookup"><span data-stu-id="a020f-104">Each row in the table represents a .NET object, and each column of the table represents a property of the object or a script value.</span></span> <span data-ttu-id="a020f-105">您可以定義資料表視圖，以顯示物件的所有屬性或物件屬性的子集。</span><span class="sxs-lookup"><span data-stu-id="a020f-105">You can define a table view that displays all the properties of an object or a subset of the properties of an object.</span></span>

## <a name="a-table-view-display"></a><span data-ttu-id="a020f-106">資料表視圖顯示</span><span class="sxs-lookup"><span data-stu-id="a020f-106">A Table View Display</span></span>

<span data-ttu-id="a020f-107">下列範例示範 Windows PowerShell 如何顯示由[Get-服務](/powershell/module/microsoft.powershell.management/get-service)Cmdlet 傳回的[system.serviceprocess.dll. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)物件。</span><span class="sxs-lookup"><span data-stu-id="a020f-107">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="a020f-108">針對此物件，Windows PowerShell 定義了顯示內容的資料表視圖 `Status` ， `Name` (此屬性的屬性是 `ServiceName` 屬性) 和屬性的別名屬性 `DisplayName` 。</span><span class="sxs-lookup"><span data-stu-id="a020f-108">For this object, Windows PowerShell has defined a table view that displays the `Status` property, the `Name` property (this property is an alias property for the `ServiceName` property), and the `DisplayName` property.</span></span> <span data-ttu-id="a020f-109">資料表中的每個資料列都代表 Cmdlet 所傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="a020f-109">Each row in the table represents an object returned by the cmdlet.</span></span>

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a><span data-ttu-id="a020f-110">定義資料表視圖</span><span class="sxs-lookup"><span data-stu-id="a020f-110">Defining the Table View</span></span>

<span data-ttu-id="a020f-111">下列 XML 顯示用來顯示 System.serviceprocess.dll. Servicecontroller 的資料表視圖架構[？Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController)物件。</span><span class="sxs-lookup"><span data-stu-id="a020f-111">The following XML shows the table view schema for displaying the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="a020f-112">您必須指定要在資料表視圖中顯示的每個屬性。</span><span class="sxs-lookup"><span data-stu-id="a020f-112">You must specify each property that you want displayed in the table view.</span></span>

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

<span data-ttu-id="a020f-113">下列 XML 元素可用來定義清單視圖：</span><span class="sxs-lookup"><span data-stu-id="a020f-113">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="a020f-114">[View](./view-element-format.md)元素是資料表視圖的父元素。</span><span class="sxs-lookup"><span data-stu-id="a020f-114">The [View](./view-element-format.md) element is the parent element of the table view.</span></span> <span data-ttu-id="a020f-115"> (這是 [清單]、[寬] 和 [自訂] 控制項視圖的相同父元素。 ) </span><span class="sxs-lookup"><span data-stu-id="a020f-115">(This is the same parent element for the list, wide, and custom control views.)</span></span>

- <span data-ttu-id="a020f-116">[Name](./name-element-for-view-format.md)元素會指定視圖的名稱。</span><span class="sxs-lookup"><span data-stu-id="a020f-116">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="a020f-117">所有的視圖都需要此元素。</span><span class="sxs-lookup"><span data-stu-id="a020f-117">This element is required for all views.</span></span>

- <span data-ttu-id="a020f-118">[ViewSelectedBy](./viewselectedby-element-format.md)元素會定義使用此視圖的物件。</span><span class="sxs-lookup"><span data-stu-id="a020f-118">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="a020f-119">這個元素是必要的。</span><span class="sxs-lookup"><span data-stu-id="a020f-119">This element is required.</span></span>

- <span data-ttu-id="a020f-120">這個範例中未顯示[GroupBy](./groupby-element-for-view-format.md)元素 () 會定義何時顯示新的物件群組。</span><span class="sxs-lookup"><span data-stu-id="a020f-120">The [GroupBy](./groupby-element-for-view-format.md) element (not shown in this example) defines when a new group of objects is displayed.</span></span> <span data-ttu-id="a020f-121">每當特定屬性或腳本的值變更時，就會啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="a020f-121">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="a020f-122">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="a020f-122">This element is optional.</span></span>

- <span data-ttu-id="a020f-123">這個範例中不會顯示[Controls](./controls-element-for-view-format.md)元素 (，) 定義由資料表視圖所定義的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="a020f-123">The [Controls](./controls-element-for-view-format.md) element (not shown in this example) defines the custom controls that are defined by the table view.</span></span> <span data-ttu-id="a020f-124">控制項可讓您進一步指定資料的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="a020f-124">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="a020f-125">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="a020f-125">This element is optional.</span></span> <span data-ttu-id="a020f-126">View 可以定義自己的自訂控制項，也可以使用格式檔案中任何視圖可以使用的通用控制項。</span><span class="sxs-lookup"><span data-stu-id="a020f-126">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="a020f-127">如需自訂控制項的詳細資訊，請參閱[建立自訂控制項](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="a020f-127">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="a020f-128">在此範例中不會顯示[HideTableHeaders](./hidetableheaders-element-format.md)元素 () 指定資料表不會在資料表頂端顯示任何標籤。</span><span class="sxs-lookup"><span data-stu-id="a020f-128">The [HideTableHeaders](./hidetableheaders-element-format.md) element (not show in this example) specifies that the table will not show any labels at the top of the table.</span></span> <span data-ttu-id="a020f-129">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="a020f-129">This element is optional.</span></span>

- <span data-ttu-id="a020f-130">定義資料表之標頭和資料列資訊的[TableControl](./tablecontrol-element-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="a020f-130">The [TableControl](./tablecontrol-element-format.md) element that defines the header and row information of the table.</span></span> <span data-ttu-id="a020f-131">類似于所有其他的視圖，資料表視圖可以顯示物件屬性的值或腳本所產生的值。</span><span class="sxs-lookup"><span data-stu-id="a020f-131">Similar to all other views, a table view can display the values of object properties or values generated by scripts.</span></span>

## <a name="defining-column-headers"></a><span data-ttu-id="a020f-132">定義資料行標題</span><span class="sxs-lookup"><span data-stu-id="a020f-132">Defining Column Headers</span></span>

1. <span data-ttu-id="a020f-133">[TableHeaders](./tableheaders-element-format.md)元素及其子項目會定義在資料表頂端顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="a020f-133">The [TableHeaders](./tableheaders-element-format.md) element and its child elements define what is displayed at the top of the table.</span></span>

2. <span data-ttu-id="a020f-134">[之 tablecolumnheader](./tablecolumnheader-element-format.md)元素會定義在資料表的資料行頂端顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="a020f-134">The [TableColumnHeader](./tablecolumnheader-element-format.md) element defines what is displayed at the top of a column of the table.</span></span> <span data-ttu-id="a020f-135">以您想要顯示標頭的順序指定這些元素。</span><span class="sxs-lookup"><span data-stu-id="a020f-135">Specify these elements in the order that you want the headers displayed.</span></span>

   <span data-ttu-id="a020f-136">您可以使用的這些元素數目沒有限制，但資料表視圖中的[之 tablecolumnheader](./tablecolumnheader-element-format.md)元素數目必須等於您所使用的[TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)元素數目。</span><span class="sxs-lookup"><span data-stu-id="a020f-136">There is no limit to the number of these element that you can use, but the number of [TableColumnHeader](./tablecolumnheader-element-format.md) elements in your table view must equal the number of [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) elements that you use.</span></span>

3. <span data-ttu-id="a020f-137">[Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)元素會指定所顯示的文字。</span><span class="sxs-lookup"><span data-stu-id="a020f-137">The [Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the text that is displayed.</span></span> <span data-ttu-id="a020f-138">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="a020f-138">This element is optional.</span></span>

4. <span data-ttu-id="a020f-139">[Width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)元素會指定資料行的字元) 寬度 (。</span><span class="sxs-lookup"><span data-stu-id="a020f-139">The [Width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the width (in characters) of the column.</span></span> <span data-ttu-id="a020f-140">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="a020f-140">This element is optional.</span></span>

5. <span data-ttu-id="a020f-141">[對齊](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)元素會指定標籤的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="a020f-141">The [Alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies how the label is displayed.</span></span> <span data-ttu-id="a020f-142">標籤可以靠左、向右或置中對齊。</span><span class="sxs-lookup"><span data-stu-id="a020f-142">The label can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="a020f-143">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="a020f-143">This element is optional.</span></span>

## <a name="defining-the-table-rows"></a><span data-ttu-id="a020f-144">定義資料表資料列</span><span class="sxs-lookup"><span data-stu-id="a020f-144">Defining the Table Rows</span></span>

<span data-ttu-id="a020f-145">資料表視圖可以提供一或多個定義，以指定在資料表的資料列中，使用[TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md)元素的子項目來顯示哪些資料。</span><span class="sxs-lookup"><span data-stu-id="a020f-145">Table views can provide one or more definitions that specify what data is displayed in the rows of the table by using the child elements of the [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="a020f-146">請注意，您可以針對資料表的資料列指定多個定義，但是不論使用哪一個資料列定義，資料列的標頭都會維持不變。</span><span class="sxs-lookup"><span data-stu-id="a020f-146">Notice that you can specify multiple definitions for the rows of the table, but the headers for the rows remains the same, regardless of what row definition is used.</span></span> <span data-ttu-id="a020f-147">通常，資料表只會有一個定義。</span><span class="sxs-lookup"><span data-stu-id="a020f-147">Typically, a table will have only one definition.</span></span>

<span data-ttu-id="a020f-148">在下列範例中，此視圖會提供單一定義，顯示系統的數個屬性值。 [Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process)物件。</span><span class="sxs-lookup"><span data-stu-id="a020f-148">In the following example, the view provides a single definition that displays the values of several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="a020f-149">資料表視圖可以顯示內容的值或腳本的值 (不會顯示在其資料列的範例) 中。</span><span class="sxs-lookup"><span data-stu-id="a020f-149">A table view can display the value of a property or the value of a script (not shown in the example) in its rows.</span></span>

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

<span data-ttu-id="a020f-150">下列 XML 元素可以用來提供資料列的定義：</span><span class="sxs-lookup"><span data-stu-id="a020f-150">The following XML elements can be used to provide definitions for a row:</span></span>

- <span data-ttu-id="a020f-151">[TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md)元素及其子項目會定義要在資料表的資料列中顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="a020f-151">The [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element and its child elements define what is displayed in the rows of the table.</span></span>

- <span data-ttu-id="a020f-152">[TableRowEntry](./listentry-element-for-listcontrol-format.md)元素會提供資料列的定義。</span><span class="sxs-lookup"><span data-stu-id="a020f-152">The [TableRowEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the row.</span></span> <span data-ttu-id="a020f-153">至少需要一個[TableRowEntry](./listentry-element-for-listcontrol-format.md) ;不過，您可以新增的專案數沒有最大限制。</span><span class="sxs-lookup"><span data-stu-id="a020f-153">At least one [TableRowEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="a020f-154">在大部分的情況下，視圖只會有一個定義。</span><span class="sxs-lookup"><span data-stu-id="a020f-154">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="a020f-155">[之 entryselectedby](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)元素會指定特定定義所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="a020f-155">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="a020f-156">這個元素是選擇性的，只有當您定義多個[TableRowEntry](./listentry-element-for-listcontrol-format.md)專案來顯示不同的物件時，才需要此專案。</span><span class="sxs-lookup"><span data-stu-id="a020f-156">This element is optional and is needed only when you define multiple [TableRowEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="a020f-157">[Wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)元素會指定超過資料行寬度的文字會顯示在下一行。</span><span class="sxs-lookup"><span data-stu-id="a020f-157">The [Wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) element specifies that text that exceeds the column width is displayed on the next line.</span></span> <span data-ttu-id="a020f-158">根據預設，系統會截斷超過欄寬度的文字。</span><span class="sxs-lookup"><span data-stu-id="a020f-158">By default, text that exceeds the column width is truncated.</span></span>

- <span data-ttu-id="a020f-159">[TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)元素會定義其值會顯示在資料列中的屬性或腳本。</span><span class="sxs-lookup"><span data-stu-id="a020f-159">The [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) element defines the properties or scripts whose values are displayed in the row.</span></span>

- <span data-ttu-id="a020f-160">[之 tablecolumnitem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)元素會定義屬性或腳本，其值會顯示在資料列的資料行中。</span><span class="sxs-lookup"><span data-stu-id="a020f-160">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="a020f-161">資料列的每個資料行都需要[之 tablecolumnitem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="a020f-161">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="a020f-162">第一個專案會顯示在第一個資料行、第二個數據行中的第二個專案，依此類推。</span><span class="sxs-lookup"><span data-stu-id="a020f-162">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="a020f-163">[PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)元素會指定屬性，其值會顯示在資料列中。</span><span class="sxs-lookup"><span data-stu-id="a020f-163">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="a020f-164">您必須指定屬性或腳本，但不能同時指定這兩者。</span><span class="sxs-lookup"><span data-stu-id="a020f-164">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="a020f-165">[ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)元素會指定其值顯示在資料列中的腳本。</span><span class="sxs-lookup"><span data-stu-id="a020f-165">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="a020f-166">您必須指定腳本或屬性，但不能同時指定這兩者。</span><span class="sxs-lookup"><span data-stu-id="a020f-166">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="a020f-167">[[字串](./label-element-for-listitem-for-listcontrol-format.md)類型] 元素會指定定義屬性或腳本值顯示方式的格式模式。</span><span class="sxs-lookup"><span data-stu-id="a020f-167">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span> <span data-ttu-id="a020f-168">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="a020f-168">This element is optional.</span></span>

- <span data-ttu-id="a020f-169">[對齊](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)元素會指定如何顯示內容或腳本的值。</span><span class="sxs-lookup"><span data-stu-id="a020f-169">The [Alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies how the value of the property or script is displayed.</span></span> <span data-ttu-id="a020f-170">值可以靠左、靠右或置中對齊。</span><span class="sxs-lookup"><span data-stu-id="a020f-170">The value can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="a020f-171">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="a020f-171">This element is optional.</span></span>

## <a name="defining-the-objects-that-use-the-table-view"></a><span data-ttu-id="a020f-172">定義使用資料表視圖的物件</span><span class="sxs-lookup"><span data-stu-id="a020f-172">Defining the Objects That Use the Table View</span></span>

<span data-ttu-id="a020f-173">有兩種方式可定義哪些 .NET 物件使用資料表視圖。</span><span class="sxs-lookup"><span data-stu-id="a020f-173">There are two ways to define which .NET objects use the table view.</span></span> <span data-ttu-id="a020f-174">您可以使用[ViewSelectedBy](./viewselectedby-element-format.md)專案來定義可由視圖的所有定義顯示的物件，也可以使用[之 entryselectedby](./entryselectedby-element-for-listentry-for-listcontrol-format.md)專案來定義由視圖的特定定義所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="a020f-174">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="a020f-175">在大部分情況下，一個 view 只有一個定義，因此物件通常是由[ViewSelectedBy](./viewselectedby-element-format.md)元素所定義。</span><span class="sxs-lookup"><span data-stu-id="a020f-175">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="a020f-176">下列範例顯示如何使用[ViewSelectedBy](./viewselectedby-element-format.md)和[TypeName](./typename-element-for-viewselectedby-format.md)元素，定義資料表視圖所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="a020f-176">The following example shows how to define the objects that are displayed by the table view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="a020f-177">您可以指定的[TypeName](./typename-element-for-viewselectedby-format.md)元素數目沒有限制，而且其順序並不重要。</span><span class="sxs-lookup"><span data-stu-id="a020f-177">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="a020f-178">下列 XML 元素可以用來指定資料表視圖所使用的物件：</span><span class="sxs-lookup"><span data-stu-id="a020f-178">The following XML elements can be used to specify the objects that are used by the table view:</span></span>

- <span data-ttu-id="a020f-179">[ViewSelectedBy](./viewselectedby-element-format.md)元素會定義清單視圖所要顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="a020f-179">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="a020f-180">[TypeName](./typename-element-for-viewselectedby-format.md)元素會指定視圖所顯示的 .net 物件。</span><span class="sxs-lookup"><span data-stu-id="a020f-180">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="a020f-181">需要完整的 .NET 類型名稱。</span><span class="sxs-lookup"><span data-stu-id="a020f-181">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="a020f-182">您必須為此視圖指定至少一個類型或選取範圍，但不能指定的元素數目上限。</span><span class="sxs-lookup"><span data-stu-id="a020f-182">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="a020f-183">下列範例會使用[ViewSelectedBy](./viewselectedby-element-format.md)和[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="a020f-183">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="a020f-184">使用 [選取範圍]，您可以在其中擁有一組使用多個視圖顯示的相關物件，例如當您為相同的物件定義清單視圖和資料表視圖時。</span><span class="sxs-lookup"><span data-stu-id="a020f-184">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="a020f-185">如需有關如何建立選擇集的詳細資訊，請參閱[定義選取範圍集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="a020f-185">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="a020f-186">下列 XML 元素可以用來指定清單視圖所使用的物件：</span><span class="sxs-lookup"><span data-stu-id="a020f-186">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="a020f-187">[ViewSelectedBy](./viewselectedby-element-format.md)元素會定義清單視圖所要顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="a020f-187">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="a020f-188">[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素會指定一組可由視圖顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="a020f-188">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="a020f-189">您必須為此視圖指定至少一個選取範圍或類型，但不能指定的元素數目上限。</span><span class="sxs-lookup"><span data-stu-id="a020f-189">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="a020f-190">下列範例示範如何使用[之 entryselectedby](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)元素，定義由資料表視圖的特定定義所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="a020f-190">The following example shows how to define the objects displayed by a specific definition of the table view using the [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="a020f-191">使用這個專案，您可以指定物件的 .NET 型別名稱、物件的選擇集，或指定何時使用定義的選取條件。</span><span class="sxs-lookup"><span data-stu-id="a020f-191">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="a020f-192">如需如何建立選取條件的詳細資訊，請參閱[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="a020f-192">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

> [!NOTE]
> <span data-ttu-id="a020f-193">建立資料表視圖的多個定義時，您不能指定不同的資料行標題。</span><span class="sxs-lookup"><span data-stu-id="a020f-193">When creating multiple definitions of the table view you cannot specify different column headers.</span></span> <span data-ttu-id="a020f-194">您只能指定在資料表的資料列中顯示的內容，例如要顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="a020f-194">You can specify only what is displayed in the rows of the table, such as what objects are displayed.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

<span data-ttu-id="a020f-195">下列 XML 元素可以用來指定清單視圖的特定定義所使用的物件：</span><span class="sxs-lookup"><span data-stu-id="a020f-195">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="a020f-196">[之 entryselectedby](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)元素會定義定義要顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="a020f-196">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="a020f-197">[TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md)元素會指定定義所顯示的 .net 物件。</span><span class="sxs-lookup"><span data-stu-id="a020f-197">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="a020f-198">使用此元素時，需要完整的 .NET 類型名稱。</span><span class="sxs-lookup"><span data-stu-id="a020f-198">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="a020f-199">您必須為定義至少指定一個類型、選擇集或選取條件，但不能指定的元素數目上限。</span><span class="sxs-lookup"><span data-stu-id="a020f-199">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="a020f-200">[SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)元素 (不會顯示) 指定一組可由這個定義顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="a020f-200">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="a020f-201">您必須為定義至少指定一個類型、選擇集或選取條件，但不能指定的元素數目上限。</span><span class="sxs-lookup"><span data-stu-id="a020f-201">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="a020f-202">[SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)元素 (不會顯示) 指定必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="a020f-202">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="a020f-203">您必須為定義至少指定一個類型、選擇集或選取條件，但不能指定的元素數目上限。</span><span class="sxs-lookup"><span data-stu-id="a020f-203">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="a020f-204">如需定義選取條件的詳細資訊，請參閱[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="a020f-204">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="a020f-205">使用格式字串</span><span class="sxs-lookup"><span data-stu-id="a020f-205">Using Format Strings</span></span>

<span data-ttu-id="a020f-206">將字串格式化可以加入至視圖，以進一步定義資料的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="a020f-206">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="a020f-207">下列範例顯示如何為屬性的值定義格式化字串 `StartTime` 。</span><span class="sxs-lookup"><span data-stu-id="a020f-207">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

<span data-ttu-id="a020f-208">下列 XML 元素可以用來指定格式模式：</span><span class="sxs-lookup"><span data-stu-id="a020f-208">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="a020f-209">[之 tablecolumnitem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)元素會定義屬性或腳本，其值會顯示在資料列的資料行中。</span><span class="sxs-lookup"><span data-stu-id="a020f-209">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="a020f-210">資料列的每個資料行都需要[之 tablecolumnitem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="a020f-210">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="a020f-211">第一個專案會顯示在第一個資料行、第二個數據行中的第二個專案，依此類推。</span><span class="sxs-lookup"><span data-stu-id="a020f-211">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="a020f-212">[PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)元素會指定屬性，其值會顯示在資料列中。</span><span class="sxs-lookup"><span data-stu-id="a020f-212">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="a020f-213">您必須指定屬性或腳本，但不能同時指定這兩者。</span><span class="sxs-lookup"><span data-stu-id="a020f-213">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="a020f-214">[[字串](./label-element-for-listitem-for-listcontrol-format.md)類型] 元素會指定定義屬性或腳本值顯示方式的格式模式。</span><span class="sxs-lookup"><span data-stu-id="a020f-214">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="a020f-215">在下列範例中， `ToString` 會呼叫方法來格式化腳本的值。</span><span class="sxs-lookup"><span data-stu-id="a020f-215">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="a020f-216">腳本可以呼叫物件的任何方法。</span><span class="sxs-lookup"><span data-stu-id="a020f-216">Scripts can call any method of an object.</span></span> <span data-ttu-id="a020f-217">因此，如果物件具有具有格式化參數的方法（例如 `ToString` ），則腳本可以呼叫該方法來格式化腳本的輸出值。</span><span class="sxs-lookup"><span data-stu-id="a020f-217">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="a020f-218">下列 XML 元素可以用來呼叫 `ToString` 方法：</span><span class="sxs-lookup"><span data-stu-id="a020f-218">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="a020f-219">[之 tablecolumnitem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)元素會定義屬性或腳本，其值會顯示在資料列的資料行中。</span><span class="sxs-lookup"><span data-stu-id="a020f-219">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="a020f-220">資料列的每個資料行都需要[之 tablecolumnitem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="a020f-220">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="a020f-221">第一個專案會顯示在第一個資料行、第二個數據行中的第二個專案，依此類推。</span><span class="sxs-lookup"><span data-stu-id="a020f-221">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="a020f-222">[ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)元素會指定其值顯示在資料列中的腳本。</span><span class="sxs-lookup"><span data-stu-id="a020f-222">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="a020f-223">您必須指定腳本或屬性，但不能同時指定這兩者。</span><span class="sxs-lookup"><span data-stu-id="a020f-223">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="a020f-224">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a020f-224">See Also</span></span>

[<span data-ttu-id="a020f-225">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="a020f-225">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
