---
ms.date: 09/13/2016
ms.topic: reference
title: 建立表格檢視
description: 建立表格檢視
ms.openlocfilehash: 035d42f7968a9e8babec692a7a5873e24b36cd97
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660297"
---
# <a name="creating-a-table-view"></a><span data-ttu-id="0eec6-103">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="0eec6-103">Creating a Table View</span></span>

<span data-ttu-id="0eec6-104">資料表視圖會顯示一個或多個資料行中的資料。</span><span class="sxs-lookup"><span data-stu-id="0eec6-104">A table view displays data in one or more columns.</span></span> <span data-ttu-id="0eec6-105">資料表中的每個資料列都代表一個 .NET 物件，而資料表的每個資料行都代表物件或腳本值的屬性。</span><span class="sxs-lookup"><span data-stu-id="0eec6-105">Each row in the table represents a .NET object, and each column of the table represents a property of the object or a script value.</span></span> <span data-ttu-id="0eec6-106">您可以定義資料表視圖，以顯示物件的所有屬性或物件的屬性子集。</span><span class="sxs-lookup"><span data-stu-id="0eec6-106">You can define a table view that displays all the properties of an object or a subset of the properties of an object.</span></span>

## <a name="a-table-view-display"></a><span data-ttu-id="0eec6-107">資料表視圖顯示</span><span class="sxs-lookup"><span data-stu-id="0eec6-107">A Table View Display</span></span>

<span data-ttu-id="0eec6-108">下列範例顯示 Windows PowerShell 如何顯示由[get-help](/powershell/module/microsoft.powershell.management/get-service) Cmdlet 所傳回的[system.serviceprocess.dll Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)物件。</span><span class="sxs-lookup"><span data-stu-id="0eec6-108">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="0eec6-109">對於此物件，Windows PowerShell 已定義顯示內容的資料表視圖 `Status` 、 `Name` 屬性 (這個屬性是屬性) 的別名屬性 `ServiceName` 和 `DisplayName` 屬性。</span><span class="sxs-lookup"><span data-stu-id="0eec6-109">For this object, Windows PowerShell has defined a table view that displays the `Status` property, the `Name` property (this property is an alias property for the `ServiceName` property), and the `DisplayName` property.</span></span> <span data-ttu-id="0eec6-110">資料表中的每個資料列都代表 Cmdlet 所傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="0eec6-110">Each row in the table represents an object returned by the cmdlet.</span></span>

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a><span data-ttu-id="0eec6-111">定義資料表視圖</span><span class="sxs-lookup"><span data-stu-id="0eec6-111">Defining the Table View</span></span>

<span data-ttu-id="0eec6-112">下列 XML 會顯示用來顯示 System.serviceprocess.dll. Servicecontroller 的表格視圖架構 [？Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) 物件。</span><span class="sxs-lookup"><span data-stu-id="0eec6-112">The following XML shows the table view schema for displaying the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="0eec6-113">您必須指定要顯示在資料表視圖中的每個屬性。</span><span class="sxs-lookup"><span data-stu-id="0eec6-113">You must specify each property that you want displayed in the table view.</span></span>

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

<span data-ttu-id="0eec6-114">下列 XML 元素用來定義清單視圖：</span><span class="sxs-lookup"><span data-stu-id="0eec6-114">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="0eec6-115">[View](./view-element-format.md)元素是資料表視圖的父元素。</span><span class="sxs-lookup"><span data-stu-id="0eec6-115">The [View](./view-element-format.md) element is the parent element of the table view.</span></span> <span data-ttu-id="0eec6-116"> (這是清單、寬和自訂控制項視圖的相同父元素。 ) </span><span class="sxs-lookup"><span data-stu-id="0eec6-116">(This is the same parent element for the list, wide, and custom control views.)</span></span>

- <span data-ttu-id="0eec6-117">[Name](./name-element-for-view-format.md)元素會指定視圖的名稱。</span><span class="sxs-lookup"><span data-stu-id="0eec6-117">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="0eec6-118">所有視圖都需要這個元素。</span><span class="sxs-lookup"><span data-stu-id="0eec6-118">This element is required for all views.</span></span>

- <span data-ttu-id="0eec6-119">[ViewSelectedBy](./viewselectedby-element-format.md)元素會定義使用 view 的物件。</span><span class="sxs-lookup"><span data-stu-id="0eec6-119">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="0eec6-120">這個元素是必要的。</span><span class="sxs-lookup"><span data-stu-id="0eec6-120">This element is required.</span></span>

- <span data-ttu-id="0eec6-121">這個範例中未顯示的 [GroupBy](./groupby-element-for-view-format.md) 元素 () 會定義何時會顯示新的物件群組。</span><span class="sxs-lookup"><span data-stu-id="0eec6-121">The [GroupBy](./groupby-element-for-view-format.md) element (not shown in this example) defines when a new group of objects is displayed.</span></span> <span data-ttu-id="0eec6-122">每當特定屬性或腳本的值變更時，就會啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="0eec6-122">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="0eec6-123">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="0eec6-123">This element is optional.</span></span>

- <span data-ttu-id="0eec6-124"> (不會在此範例中顯示 [Controls](./controls-element-for-view-format.md) 元素) 定義資料表視圖所定義的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="0eec6-124">The [Controls](./controls-element-for-view-format.md) element (not shown in this example) defines the custom controls that are defined by the table view.</span></span> <span data-ttu-id="0eec6-125">控制項可讓您進一步指定顯示資料的方式。</span><span class="sxs-lookup"><span data-stu-id="0eec6-125">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="0eec6-126">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="0eec6-126">This element is optional.</span></span> <span data-ttu-id="0eec6-127">View 可以定義自己的自訂控制項，也可以使用格式檔案中任何視圖都可使用的通用控制項。</span><span class="sxs-lookup"><span data-stu-id="0eec6-127">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="0eec6-128">如需自訂控制項的詳細資訊，請參閱 [建立自訂控制項](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="0eec6-128">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="0eec6-129">[HideTableHeaders](./hidetableheaders-element-format.md)元素 (不會顯示在此範例中) 指定資料表不會在資料表頂端顯示任何標籤。</span><span class="sxs-lookup"><span data-stu-id="0eec6-129">The [HideTableHeaders](./hidetableheaders-element-format.md) element (not show in this example) specifies that the table will not show any labels at the top of the table.</span></span> <span data-ttu-id="0eec6-130">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="0eec6-130">This element is optional.</span></span>

- <span data-ttu-id="0eec6-131">[TableControl](./tablecontrol-element-format.md)元素，定義資料表的標頭和資料列資訊。</span><span class="sxs-lookup"><span data-stu-id="0eec6-131">The [TableControl](./tablecontrol-element-format.md) element that defines the header and row information of the table.</span></span> <span data-ttu-id="0eec6-132">資料表視圖類似于所有其他的視圖，可顯示物件屬性的值或腳本所產生的值。</span><span class="sxs-lookup"><span data-stu-id="0eec6-132">Similar to all other views, a table view can display the values of object properties or values generated by scripts.</span></span>

## <a name="defining-column-headers"></a><span data-ttu-id="0eec6-133">定義欄標題</span><span class="sxs-lookup"><span data-stu-id="0eec6-133">Defining Column Headers</span></span>

1. <span data-ttu-id="0eec6-134">[TableHeaders](./tableheaders-element-format.md)元素和其子項目會定義在資料表頂端顯示的專案。</span><span class="sxs-lookup"><span data-stu-id="0eec6-134">The [TableHeaders](./tableheaders-element-format.md) element and its child elements define what is displayed at the top of the table.</span></span>

2. <span data-ttu-id="0eec6-135">[之 tablecolumnheader](./tablecolumnheader-element-format.md)元素會定義在資料表資料行頂端顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="0eec6-135">The [TableColumnHeader](./tablecolumnheader-element-format.md) element defines what is displayed at the top of a column of the table.</span></span> <span data-ttu-id="0eec6-136">依您想要顯示標頭的順序指定這些元素。</span><span class="sxs-lookup"><span data-stu-id="0eec6-136">Specify these elements in the order that you want the headers displayed.</span></span>

   <span data-ttu-id="0eec6-137">您可以使用的元素數目沒有限制，但資料表視圖中的 [之 tablecolumnheader](./tablecolumnheader-element-format.md) 元素數目必須等於您所使用的 [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) 元素數目。</span><span class="sxs-lookup"><span data-stu-id="0eec6-137">There is no limit to the number of these element that you can use, but the number of [TableColumnHeader](./tablecolumnheader-element-format.md) elements in your table view must equal the number of [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) elements that you use.</span></span>

3. <span data-ttu-id="0eec6-138">[Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)元素會指定所顯示的文字。</span><span class="sxs-lookup"><span data-stu-id="0eec6-138">The [Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the text that is displayed.</span></span> <span data-ttu-id="0eec6-139">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="0eec6-139">This element is optional.</span></span>

4. <span data-ttu-id="0eec6-140">[Width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)元素會指定資料行的寬度 (字元) 。</span><span class="sxs-lookup"><span data-stu-id="0eec6-140">The [Width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the width (in characters) of the column.</span></span> <span data-ttu-id="0eec6-141">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="0eec6-141">This element is optional.</span></span>

5. <span data-ttu-id="0eec6-142">[對齊](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)元素會指定標籤的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="0eec6-142">The [Alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies how the label is displayed.</span></span> <span data-ttu-id="0eec6-143">標籤可以靠左、靠右或置中對齊。</span><span class="sxs-lookup"><span data-stu-id="0eec6-143">The label can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="0eec6-144">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="0eec6-144">This element is optional.</span></span>

## <a name="defining-the-table-rows"></a><span data-ttu-id="0eec6-145">定義資料表資料列</span><span class="sxs-lookup"><span data-stu-id="0eec6-145">Defining the Table Rows</span></span>

<span data-ttu-id="0eec6-146">資料表視圖可以提供一或多個定義，以使用 [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) 元素的子項目來指定要在資料表的資料列中顯示哪些資料。</span><span class="sxs-lookup"><span data-stu-id="0eec6-146">Table views can provide one or more definitions that specify what data is displayed in the rows of the table by using the child elements of the [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="0eec6-147">請注意，您可以為資料表的資料列指定多個定義，但是資料列的標頭會維持不變，不論使用哪一種資料列定義。</span><span class="sxs-lookup"><span data-stu-id="0eec6-147">Notice that you can specify multiple definitions for the rows of the table, but the headers for the rows remains the same, regardless of what row definition is used.</span></span> <span data-ttu-id="0eec6-148">通常，資料表只會有一個定義。</span><span class="sxs-lookup"><span data-stu-id="0eec6-148">Typically, a table will have only one definition.</span></span>

<span data-ttu-id="0eec6-149">在下列範例中，視圖會提供單一定義，以顯示 [...] 的數個屬性值 [？Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process) 物件。</span><span class="sxs-lookup"><span data-stu-id="0eec6-149">In the following example, the view provides a single definition that displays the values of several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="0eec6-150">資料表視圖可以顯示內容的值或腳本的值 (不會顯示在其資料列中的範例) 。</span><span class="sxs-lookup"><span data-stu-id="0eec6-150">A table view can display the value of a property or the value of a script (not shown in the example) in its rows.</span></span>

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

<span data-ttu-id="0eec6-151">下列 XML 元素可以用來提供資料列的定義：</span><span class="sxs-lookup"><span data-stu-id="0eec6-151">The following XML elements can be used to provide definitions for a row:</span></span>

- <span data-ttu-id="0eec6-152">[TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md)元素和其子項目會定義資料表的資料列中所顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="0eec6-152">The [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element and its child elements define what is displayed in the rows of the table.</span></span>

- <span data-ttu-id="0eec6-153">[TableRowEntry](./listentry-element-for-listcontrol-format.md)元素提供資料列的定義。</span><span class="sxs-lookup"><span data-stu-id="0eec6-153">The [TableRowEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the row.</span></span> <span data-ttu-id="0eec6-154">至少需要一個 [TableRowEntry](./listentry-element-for-listcontrol-format.md) ;不過，您可以新增的元素數目沒有最大限制。</span><span class="sxs-lookup"><span data-stu-id="0eec6-154">At least one [TableRowEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="0eec6-155">在大部分的情況下，view 只會有一個定義。</span><span class="sxs-lookup"><span data-stu-id="0eec6-155">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="0eec6-156">[之 entryselectedby](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)元素會指定特定定義所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="0eec6-156">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="0eec6-157">這個元素是選擇性的，只有當您定義多個顯示不同物件的 [TableRowEntry](./listentry-element-for-listcontrol-format.md) 專案時，才需要此專案。</span><span class="sxs-lookup"><span data-stu-id="0eec6-157">This element is optional and is needed only when you define multiple [TableRowEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="0eec6-158">[Wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)元素會指定超出資料行寬度的文字會顯示在下一行。</span><span class="sxs-lookup"><span data-stu-id="0eec6-158">The [Wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) element specifies that text that exceeds the column width is displayed on the next line.</span></span> <span data-ttu-id="0eec6-159">根據預設，系統會截斷超過欄寬度的文字。</span><span class="sxs-lookup"><span data-stu-id="0eec6-159">By default, text that exceeds the column width is truncated.</span></span>

- <span data-ttu-id="0eec6-160">[TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)元素會定義其值會顯示在資料列中的屬性或腳本。</span><span class="sxs-lookup"><span data-stu-id="0eec6-160">The [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) element defines the properties or scripts whose values are displayed in the row.</span></span>

- <span data-ttu-id="0eec6-161">[之 tablecolumnitem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)元素會定義其值會顯示在資料列的資料行中的屬性或腳本。</span><span class="sxs-lookup"><span data-stu-id="0eec6-161">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="0eec6-162">資料列的每個資料行都需要 [之 tablecolumnitem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="0eec6-162">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="0eec6-163">第一個專案會顯示在第一個資料行中，第二個數據行中的第二個專案，依此類推。</span><span class="sxs-lookup"><span data-stu-id="0eec6-163">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="0eec6-164">[PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)元素會指定屬性，其值會顯示在資料列中。</span><span class="sxs-lookup"><span data-stu-id="0eec6-164">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="0eec6-165">您必須指定屬性或腳本，但不能同時指定這兩種方法。</span><span class="sxs-lookup"><span data-stu-id="0eec6-165">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="0eec6-166">[ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)元素會指定其值會顯示在資料列中的腳本。</span><span class="sxs-lookup"><span data-stu-id="0eec6-166">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="0eec6-167">您必須指定腳本或屬性，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="0eec6-167">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="0eec6-168">格式 [值元素會](./label-element-for-listitem-for-listcontrol-format.md) 指定定義屬性或腳本值顯示方式的格式模式。</span><span class="sxs-lookup"><span data-stu-id="0eec6-168">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span> <span data-ttu-id="0eec6-169">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="0eec6-169">This element is optional.</span></span>

- <span data-ttu-id="0eec6-170">[對齊](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)元素會指定屬性或腳本的值的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="0eec6-170">The [Alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies how the value of the property or script is displayed.</span></span> <span data-ttu-id="0eec6-171">值可以靠左、靠右或置中對齊。</span><span class="sxs-lookup"><span data-stu-id="0eec6-171">The value can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="0eec6-172">這是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="0eec6-172">This element is optional.</span></span>

## <a name="defining-the-objects-that-use-the-table-view"></a><span data-ttu-id="0eec6-173">定義使用資料表視圖的物件</span><span class="sxs-lookup"><span data-stu-id="0eec6-173">Defining the Objects That Use the Table View</span></span>

<span data-ttu-id="0eec6-174">有兩種方式可以定義要使用資料表視圖的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="0eec6-174">There are two ways to define which .NET objects use the table view.</span></span> <span data-ttu-id="0eec6-175">您可以使用 [ViewSelectedBy](./viewselectedby-element-format.md) 專案來定義可由視圖的所有定義顯示的物件，或者，您可以使用 [之 entryselectedby](./entryselectedby-element-for-listentry-for-listcontrol-format.md) 元素來定義由視圖的特定定義所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="0eec6-175">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="0eec6-176">在大部分的情況下，視圖只有一個定義，因此物件通常是由 [ViewSelectedBy](./viewselectedby-element-format.md) 元素定義。</span><span class="sxs-lookup"><span data-stu-id="0eec6-176">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="0eec6-177">下列範例示範如何使用 [ViewSelectedBy](./viewselectedby-element-format.md) 和 [TypeName](./typename-element-for-viewselectedby-format.md) 元素，定義資料表視圖所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="0eec6-177">The following example shows how to define the objects that are displayed by the table view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="0eec6-178">您可以指定的 [TypeName](./typename-element-for-viewselectedby-format.md) 元素數目沒有任何限制，而且其順序並不重要。</span><span class="sxs-lookup"><span data-stu-id="0eec6-178">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="0eec6-179">下列 XML 元素可以用來指定資料表視圖所使用的物件：</span><span class="sxs-lookup"><span data-stu-id="0eec6-179">The following XML elements can be used to specify the objects that are used by the table view:</span></span>

- <span data-ttu-id="0eec6-180">[ViewSelectedBy](./viewselectedby-element-format.md)元素會定義清單視圖要顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="0eec6-180">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="0eec6-181">[TypeName](./typename-element-for-viewselectedby-format.md)元素會指定視圖所顯示的 .net 物件。</span><span class="sxs-lookup"><span data-stu-id="0eec6-181">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="0eec6-182">需要完整的 .NET 型別名稱。</span><span class="sxs-lookup"><span data-stu-id="0eec6-182">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="0eec6-183">您必須為此視圖指定至少一個類型或選取範圍，但無法指定的元素數目上限。</span><span class="sxs-lookup"><span data-stu-id="0eec6-183">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="0eec6-184">下列範例會使用 [ViewSelectedBy](./viewselectedby-element-format.md) 和 [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="0eec6-184">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="0eec6-185">如果您有一組相關的物件會使用多個視圖顯示，例如當您針對相同物件定義清單視圖和資料表視圖時，請使用選取集。</span><span class="sxs-lookup"><span data-stu-id="0eec6-185">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="0eec6-186">如需有關如何建立選取範圍的詳細資訊，請參閱 [定義選取集合](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="0eec6-186">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="0eec6-187">下列 XML 元素可以用來指定清單視圖所使用的物件：</span><span class="sxs-lookup"><span data-stu-id="0eec6-187">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="0eec6-188">[ViewSelectedBy](./viewselectedby-element-format.md)元素會定義清單視圖要顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="0eec6-188">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="0eec6-189">[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素會指定可供視圖顯示的一組物件。</span><span class="sxs-lookup"><span data-stu-id="0eec6-189">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="0eec6-190">您必須為此視圖指定至少一個選擇集或類型，但無法指定的元素數目上限。</span><span class="sxs-lookup"><span data-stu-id="0eec6-190">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="0eec6-191">下列範例示範如何使用 [之 entryselectedby](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) 元素定義資料表視圖的特定定義所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="0eec6-191">The following example shows how to define the objects displayed by a specific definition of the table view using the [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="0eec6-192">您可以使用這個專案，指定物件的 .NET 類型名稱、一組選取的物件，或指定使用定義時指定的選取條件。</span><span class="sxs-lookup"><span data-stu-id="0eec6-192">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="0eec6-193">如需如何建立選取條件的詳細資訊，請參閱 [定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="0eec6-193">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

> [!NOTE]
> <span data-ttu-id="0eec6-194">當您建立資料表視圖的多個定義時，不能指定不同的資料行標題。</span><span class="sxs-lookup"><span data-stu-id="0eec6-194">When creating multiple definitions of the table view you cannot specify different column headers.</span></span> <span data-ttu-id="0eec6-195">您只能指定顯示在資料表資料列中的內容，例如要顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="0eec6-195">You can specify only what is displayed in the rows of the table, such as what objects are displayed.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

<span data-ttu-id="0eec6-196">下列 XML 專案可以用來指定清單視圖的特定定義所使用的物件：</span><span class="sxs-lookup"><span data-stu-id="0eec6-196">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="0eec6-197">[之 entryselectedby](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)元素會定義定義所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="0eec6-197">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="0eec6-198">[TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md)元素會指定定義所顯示的 .net 物件。</span><span class="sxs-lookup"><span data-stu-id="0eec6-198">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="0eec6-199">使用這個專案時，需要完整的 .NET 型別名稱。</span><span class="sxs-lookup"><span data-stu-id="0eec6-199">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="0eec6-200">您必須為定義指定至少一個類型、選取集或選取條件，但無法指定的元素數目上限。</span><span class="sxs-lookup"><span data-stu-id="0eec6-200">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="0eec6-201">[SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)元素 (未顯示) 指定可由此定義顯示的一組物件。</span><span class="sxs-lookup"><span data-stu-id="0eec6-201">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="0eec6-202">您必須為定義指定至少一個類型、選取集或選取條件，但無法指定的元素數目上限。</span><span class="sxs-lookup"><span data-stu-id="0eec6-202">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="0eec6-203">[SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)元素 (未顯示) 指定必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="0eec6-203">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="0eec6-204">您必須為定義指定至少一個類型、選取集或選取條件，但無法指定的元素數目上限。</span><span class="sxs-lookup"><span data-stu-id="0eec6-204">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="0eec6-205">如需定義選取條件的詳細資訊，請參閱 [定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="0eec6-205">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="0eec6-206">使用格式字串</span><span class="sxs-lookup"><span data-stu-id="0eec6-206">Using Format Strings</span></span>

<span data-ttu-id="0eec6-207">您可以將字串格式設定加入至視圖，以進一步定義資料的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="0eec6-207">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="0eec6-208">下列範例顯示如何定義屬性值的格式化字串 `StartTime` 。</span><span class="sxs-lookup"><span data-stu-id="0eec6-208">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

<span data-ttu-id="0eec6-209">下列 XML 元素可以用來指定格式模式：</span><span class="sxs-lookup"><span data-stu-id="0eec6-209">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="0eec6-210">[之 tablecolumnitem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)元素會定義其值會顯示在資料列的資料行中的屬性或腳本。</span><span class="sxs-lookup"><span data-stu-id="0eec6-210">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="0eec6-211">資料列的每個資料行都需要 [之 tablecolumnitem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="0eec6-211">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="0eec6-212">第一個專案會顯示在第一個資料行中，第二個數據行中的第二個專案，依此類推。</span><span class="sxs-lookup"><span data-stu-id="0eec6-212">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="0eec6-213">[PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)元素會指定屬性，其值會顯示在資料列中。</span><span class="sxs-lookup"><span data-stu-id="0eec6-213">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="0eec6-214">您必須指定屬性或腳本，但不能同時指定這兩種方法。</span><span class="sxs-lookup"><span data-stu-id="0eec6-214">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="0eec6-215">格式 [值元素會](./label-element-for-listitem-for-listcontrol-format.md) 指定定義屬性或腳本值顯示方式的格式模式。</span><span class="sxs-lookup"><span data-stu-id="0eec6-215">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="0eec6-216">在下列範例中， `ToString` 會呼叫方法來格式化腳本的值。</span><span class="sxs-lookup"><span data-stu-id="0eec6-216">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="0eec6-217">腳本可以呼叫物件的任何方法。</span><span class="sxs-lookup"><span data-stu-id="0eec6-217">Scripts can call any method of an object.</span></span> <span data-ttu-id="0eec6-218">因此，如果物件具有具有格式化參數的方法（例如 `ToString` ），則腳本可以呼叫該方法來格式化腳本的輸出值。</span><span class="sxs-lookup"><span data-stu-id="0eec6-218">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="0eec6-219">下列 XML 元素可以用來呼叫 `ToString` 方法：</span><span class="sxs-lookup"><span data-stu-id="0eec6-219">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="0eec6-220">[之 tablecolumnitem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)元素會定義其值會顯示在資料列的資料行中的屬性或腳本。</span><span class="sxs-lookup"><span data-stu-id="0eec6-220">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="0eec6-221">資料列的每個資料行都需要 [之 tablecolumnitem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="0eec6-221">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="0eec6-222">第一個專案會顯示在第一個資料行中，第二個數據行中的第二個專案，依此類推。</span><span class="sxs-lookup"><span data-stu-id="0eec6-222">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="0eec6-223">[ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)元素會指定其值會顯示在資料列中的腳本。</span><span class="sxs-lookup"><span data-stu-id="0eec6-223">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="0eec6-224">您必須指定腳本或屬性，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="0eec6-224">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="0eec6-225">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0eec6-225">See Also</span></span>

[<span data-ttu-id="0eec6-226">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="0eec6-226">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
