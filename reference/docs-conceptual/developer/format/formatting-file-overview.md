---
ms.date: 09/13/2016
ms.topic: reference
title: 格式設定檔案概觀
description: 格式設定檔案概觀
ms.openlocfilehash: b86119c304c895ec08ac67de693b3a052bc7a2a0
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667822"
---
# <a name="formatting-file-overview"></a><span data-ttu-id="e967b-103">格式設定檔案概觀</span><span class="sxs-lookup"><span data-stu-id="e967b-103">Formatting File Overview</span></span>

<span data-ttu-id="e967b-104">命令所傳回之物件的顯示格式 (Cmdlet、函式和腳本) 是使用 ( # B0 xml 檔案) 的格式檔案來定義。</span><span class="sxs-lookup"><span data-stu-id="e967b-104">The display format for the objects that are returned by commands (cmdlets, functions, and scripts) are defined by using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="e967b-105">PowerShell 會提供這些檔案中的數個，以定義由 PowerShell 所提供命令所傳回之物件的顯示格式，例如 Cmdlet 所傳回的[system.object （Process](/dotnet/api/System.Diagnostics.Process) ）物件。 `Get-Process`</span><span class="sxs-lookup"><span data-stu-id="e967b-105">Several of these files are provided by PowerShell to define the display format for those objects returned by PowerShell-provided commands, such as the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object returned by the `Get-Process` cmdlet.</span></span> <span data-ttu-id="e967b-106">不過，您也可以建立自己的自訂格式檔案來覆寫預設顯示格式，也可以撰寫自訂格式檔案來定義您自己的命令所傳回的物件顯示。</span><span class="sxs-lookup"><span data-stu-id="e967b-106">However, you can also create your own custom formatting files to overwrite the default display formats or you can write a custom formatting file to define the display of objects returned by your own commands.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e967b-107">格式化檔案不會決定傳回至管線的物件元素。</span><span class="sxs-lookup"><span data-stu-id="e967b-107">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="e967b-108">當物件傳回至管線時，該物件的所有成員即使沒有顯示，也可以使用。</span><span class="sxs-lookup"><span data-stu-id="e967b-108">When an object is returned to the pipeline, all members of that object are available even if some are not displayed.</span></span>

<span data-ttu-id="e967b-109">PowerShell 會使用這些格式設定檔案中的資料來判斷所顯示的內容，以及如何格式化顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="e967b-109">PowerShell uses the data in these formatting files to determine what is displayed and how the displayed data is formatted.</span></span> <span data-ttu-id="e967b-110">顯示的資料可以包含物件的屬性或腳本的值。</span><span class="sxs-lookup"><span data-stu-id="e967b-110">The displayed data can include the properties of an object or the value of a script.</span></span> <span data-ttu-id="e967b-111">如果您想要顯示一些無法直接從物件的屬性中使用的值，例如加入物件的兩個屬性值，然後將總和顯示為數據片段，則會使用腳本。</span><span class="sxs-lookup"><span data-stu-id="e967b-111">Scripts are used if you want to display some value that is not available directly from the properties of an object, such as adding the value of two properties of an object and then displaying the sum as a piece of data.</span></span> <span data-ttu-id="e967b-112">您可以藉由定義要顯示之物件的視圖，來格式化顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="e967b-112">Formatting of the displayed data is done by defining views for the objects that you want to display.</span></span> <span data-ttu-id="e967b-113">您可以為每個物件定義單一視圖，您可以為多個物件定義單一視圖，也可以為相同的物件定義多個視圖。</span><span class="sxs-lookup"><span data-stu-id="e967b-113">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="e967b-114">您可以定義的視圖數目沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="e967b-114">There is no limit to the number of views that you can define.</span></span>

## <a name="common-features-of-formatting-files"></a><span data-ttu-id="e967b-115">格式化檔案的一般功能</span><span class="sxs-lookup"><span data-stu-id="e967b-115">Common Features of Formatting Files</span></span>

<span data-ttu-id="e967b-116">每個格式化檔案都可以定義下列元件，這些元件可以跨檔案定義的所有視圖共用：</span><span class="sxs-lookup"><span data-stu-id="e967b-116">Each formatting file can define the following components that can be shared across all the views defined by the file:</span></span>

- <span data-ttu-id="e967b-117">預設設定，例如，如果資料的長度超過資料行的寬度，則資料列中顯示的資料是否會顯示在下一行。</span><span class="sxs-lookup"><span data-stu-id="e967b-117">Default configuration setting, such as whether the data displayed in the rows of tables will be displayed on the next line if the data is longer than the width of the column.</span></span> <span data-ttu-id="e967b-118">如需這些設定的詳細資訊，請參閱 [定義一般設定](./defining-common-configuration-features.md)。</span><span class="sxs-lookup"><span data-stu-id="e967b-118">For more information about these settings, see [Defining Common Configuration Settings](./defining-common-configuration-features.md).</span></span>

- <span data-ttu-id="e967b-119">物件的集合，可由格式化檔案的任何視圖顯示。</span><span class="sxs-lookup"><span data-stu-id="e967b-119">Sets of objects that can be displayed by any of the views of the formatting file.</span></span> <span data-ttu-id="e967b-120">如需這些集合的詳細資訊 (稱為 *選取範圍*) ，請參閱 [定義物件集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="e967b-120">For more information about these sets (referred to as *selection sets*), see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

- <span data-ttu-id="e967b-121">格式化檔案的所有視圖都可使用的通用控制項。</span><span class="sxs-lookup"><span data-stu-id="e967b-121">Common controls that can be used by all the views of the formatting file.</span></span> <span data-ttu-id="e967b-122">控制項可讓您更精確地控制資料的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="e967b-122">Controls give you finer control on how data is displayed.</span></span> <span data-ttu-id="e967b-123">如需控制項的詳細資訊，請參閱 [定義自訂控制項](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="e967b-123">For more information about controls, see [Defining Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="formatting-views"></a><span data-ttu-id="e967b-124">格式化視圖</span><span class="sxs-lookup"><span data-stu-id="e967b-124">Formatting Views</span></span>

<span data-ttu-id="e967b-125">格式化視圖可以用表格格式、清單格式、寬格式和自訂格式來顯示物件。</span><span class="sxs-lookup"><span data-stu-id="e967b-125">Formatting views can display objects in a table format, list format, wide format, and custom format.</span></span> <span data-ttu-id="e967b-126">在大部分的情況下，每個格式化定義都是由一組描述視圖的 XML 標記所描述。</span><span class="sxs-lookup"><span data-stu-id="e967b-126">For the most part, each formatting definition is described by a set of XML tags that describe the view.</span></span> <span data-ttu-id="e967b-127">每個視圖都包含視圖的名稱、使用視圖的物件以及視圖的元素，例如資料表視圖的資料行和資料列資訊。</span><span class="sxs-lookup"><span data-stu-id="e967b-127">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="e967b-128">資料表視圖會列出一或多個資料行中物件或腳本區塊值的屬性。</span><span class="sxs-lookup"><span data-stu-id="e967b-128">Table View Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="e967b-129">每個資料行都代表物件或腳本值的單一屬性。</span><span class="sxs-lookup"><span data-stu-id="e967b-129">Each column represents a single property of the object or a script value.</span></span> <span data-ttu-id="e967b-130">您可以定義資料表視圖，以顯示物件的所有屬性、物件的屬性子集，或屬性和腳本值的組合。</span><span class="sxs-lookup"><span data-stu-id="e967b-130">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script values.</span></span> <span data-ttu-id="e967b-131">資料表的每個資料列都代表一個傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="e967b-131">Each row of the table represents a returned object.</span></span> <span data-ttu-id="e967b-132">建立資料表視圖非常類似于當您使用管線將物件傳送至 `Format-Table` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e967b-132">Creating a table view is very similar to when you pipe an object to the `Format-Table` cmdlet.</span></span> <span data-ttu-id="e967b-133">如需此視圖的詳細資訊，請參閱 [表格視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="e967b-133">For more information about this view, see [Table View](./creating-a-table-view.md).</span></span>

<span data-ttu-id="e967b-134">清單視圖會列出物件的屬性，或是單一資料行中的腳本值。</span><span class="sxs-lookup"><span data-stu-id="e967b-134">List View Lists the properties of an object or a script value in a single column.</span></span> <span data-ttu-id="e967b-135">清單中的每個資料列都會顯示選用的標籤，或屬性名稱後面接著屬性或腳本的值。</span><span class="sxs-lookup"><span data-stu-id="e967b-135">Each row of the list displays an optional label or the property name followed by the value of the property or script.</span></span> <span data-ttu-id="e967b-136">建立清單視圖非常類似于使用管線將物件傳送至 `Format-List` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e967b-136">Creating a list view is very similar to piping an object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="e967b-137">如需此視圖的詳細資訊，請參閱 [清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="e967b-137">For more information about this view, see [List View](./creating-a-list-view.md).</span></span>

<span data-ttu-id="e967b-138">寬型視圖會列出一個或多個資料行中物件或腳本值的單一屬性。</span><span class="sxs-lookup"><span data-stu-id="e967b-138">Wide View Lists a single property of an object or a script value in one or more columns.</span></span> <span data-ttu-id="e967b-139">此視圖沒有標籤或標頭。</span><span class="sxs-lookup"><span data-stu-id="e967b-139">There is no label or header for this view.</span></span> <span data-ttu-id="e967b-140">建立廣泛的視圖非常類似于將物件輸送至 `Format-Wide` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e967b-140">Creating a wide view is very similar to piping an object to the `Format-Wide` cmdlet.</span></span> <span data-ttu-id="e967b-141">如需此視圖的詳細資訊，請參閱 [Wide view](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="e967b-141">For more information about this view, see [Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="e967b-142">自訂視圖會顯示物件屬性或腳本值的可自訂視圖，這些值不會遵守資料表視圖、清單視圖或寬視圖的固定結構。</span><span class="sxs-lookup"><span data-stu-id="e967b-142">Custom View Displays a customizable view of object properties or script values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="e967b-143">您可以定義獨立的自訂視圖，也可以定義另一個視圖所使用的自訂視圖，例如資料表視圖或清單視圖。</span><span class="sxs-lookup"><span data-stu-id="e967b-143">You can define a stand-alone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="e967b-144">建立自訂的視圖非常類似于使用管線將物件傳送至 `Format-Custom` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e967b-144">Creating a custom view is very similar to piping an object to the `Format-Custom` cmdlet.</span></span> <span data-ttu-id="e967b-145">如需此視圖的詳細資訊，請參閱 [自訂視圖](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="e967b-145">For more information about this view, see [Custom View](./creating-custom-controls.md).</span></span>

## <a name="components-of-a-view"></a><span data-ttu-id="e967b-146">視圖的元件</span><span class="sxs-lookup"><span data-stu-id="e967b-146">Components of a View</span></span>

<span data-ttu-id="e967b-147">下列 XML 範例顯示視圖的基本 XML 元件。</span><span class="sxs-lookup"><span data-stu-id="e967b-147">The following XML examples show the basic XML components of a view.</span></span> <span data-ttu-id="e967b-148">個別的 XML 元素會根據您想要建立的視圖而有所不同，但視圖的基本元件全都相同。</span><span class="sxs-lookup"><span data-stu-id="e967b-148">The individual XML elements vary depending on which view you want to create, but the basic components of the views are all the same.</span></span>

<span data-ttu-id="e967b-149">首先，每個視圖都有一個專案 `Name` ，可指定用來參考視圖的使用者易記名稱。</span><span class="sxs-lookup"><span data-stu-id="e967b-149">To start with, each view has a `Name` element that specifies a user friendly name that is used to reference the view.</span></span> <span data-ttu-id="e967b-150">專案， `ViewSelectedBy` 定義要由視圖顯示的 .net 物件，以及定義此視圖的 *控制項* 元素。</span><span class="sxs-lookup"><span data-stu-id="e967b-150">a `ViewSelectedBy` element that defines which .NET objects are displayed by the view, and a *control* element that defines the view.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <ListControl>...</ListControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <WideControl>...</WideControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <CustomControl>...</CustomControl>
  </View>
</ViewDefinitions>

```

<span data-ttu-id="e967b-151">在控制項專案中，您可以定義一個或多個 *entry 專案* 。</span><span class="sxs-lookup"><span data-stu-id="e967b-151">Within the control element, you can define one or more *entry* elements.</span></span> <span data-ttu-id="e967b-152">如果您使用多個定義，您必須指定要使用每個定義的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="e967b-152">If you use multiple definitions, you must specify which .NET objects use each definition.</span></span> <span data-ttu-id="e967b-153">每個控制項通常都只需要一個專案，只有一個定義。</span><span class="sxs-lookup"><span data-stu-id="e967b-153">Typically only one entry, with only one definition, is needed for each control.</span></span>

```xml
<ListControl>
  <ListEntries>
    <ListEntry>
      <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
  </ListEntries>
</ListControl>

```

<span data-ttu-id="e967b-154">在視圖的每個專案專案內，您可以指定 *專案專案* ，以定義該視圖所顯示的 .net 屬性或腳本。</span><span class="sxs-lookup"><span data-stu-id="e967b-154">Within each entry element of a view, you specify the *item* elements that define the .NET properties or scripts that are displayed by that view.</span></span>

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

<span data-ttu-id="e967b-155">如先前的範例所示，格式化檔案可以包含多個視圖、一個 view 可以包含多個定義，而且每個定義都可以包含多個專案。</span><span class="sxs-lookup"><span data-stu-id="e967b-155">As shown in the preceding examples, the formatting file can contain multiple views, a view can contain multiple definitions, and each definition can contain multiple items.</span></span>

## <a name="example-of-a-table-view"></a><span data-ttu-id="e967b-156">資料表視圖的範例</span><span class="sxs-lookup"><span data-stu-id="e967b-156">Example of a Table View</span></span>

<span data-ttu-id="e967b-157">下列範例顯示用來定義資料表視圖的 XML 標記，其中包含兩個數據行。</span><span class="sxs-lookup"><span data-stu-id="e967b-157">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="e967b-158">[ViewDefinitions](./viewdefinitions-element-format.md)元素是格式化檔案中定義之所有視圖的容器元素。</span><span class="sxs-lookup"><span data-stu-id="e967b-158">The [ViewDefinitions](./viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="e967b-159">[View](./view-element-format.md)元素會定義特定的資料表、清單、寬或自訂視圖。</span><span class="sxs-lookup"><span data-stu-id="e967b-159">The [View](./view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="e967b-160">在每個 [view](./view-element-format.md) 專案中， [Name](./name-element-for-view-format.md) 元素會指定視圖的名稱、 [ViewSelectedBy](./viewselectedby-element-format.md) 元素會定義使用 view 的物件，而不同的控制項元素 (例如 `TableControl` 下列範例中所示的元素) 定義視圖的型別。</span><span class="sxs-lookup"><span data-stu-id="e967b-160">Within each [View](./view-element-format.md) element, the [Name](./name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element shown in the following example) define the type of the view.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>Name of View</Name>
    <ViewSelectedBy>
      <TypeName>Object to display using this view</TypeName>
      <TypeName>Object to display using this view</TypeName>
    </ViewSelectedBy>
    <TableControl>
      <TableHeaders>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
      </TableHeaders>
      <TableRowEntries>
        <TableRowEntry>
          <TableColumnItems>
            <TableColumnItem>
              <PropertyName>Header for column 1</PropertyName>
            </TableColumnItem>
            <TableColumnItem>
              <PropertyName>Header for column 2</PropertyName>
            </TableColumnItem>
          </TableColumnItems>
        </TableRowEntry>
      </TableRowEntries>
    </TableControl)
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a><span data-ttu-id="e967b-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e967b-161">See Also</span></span>

[<span data-ttu-id="e967b-162">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="e967b-162">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="e967b-163">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="e967b-163">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="e967b-164">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="e967b-164">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="e967b-165">建立自訂控制項</span><span class="sxs-lookup"><span data-stu-id="e967b-165">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="e967b-166">撰寫 PowerShell 格式化和類型檔案</span><span class="sxs-lookup"><span data-stu-id="e967b-166">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
