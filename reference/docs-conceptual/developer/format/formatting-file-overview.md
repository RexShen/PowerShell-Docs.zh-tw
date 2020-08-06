---
title: 格式化檔案總覽 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: efdd3eed15c5f3c88636fcbe7a39f6c6cfb20ced
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773499"
---
# <a name="formatting-file-overview"></a><span data-ttu-id="2b8f4-102">格式設定檔案概觀</span><span class="sxs-lookup"><span data-stu-id="2b8f4-102">Formatting File Overview</span></span>

<span data-ttu-id="2b8f4-103">命令所傳回之物件的顯示格式 (Cmdlet、函式和腳本) 是使用格式檔案 ( # B0 xml 檔案) 來定義。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-103">The display format for the objects that are returned by commands (cmdlets, functions, and scripts) are defined by using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="2b8f4-104">PowerShell 會提供其中幾個檔案，以定義 PowerShell 提供的命令所傳回之物件的顯示格式，例如 Cmdlet 所傳回的[system.object](/dotnet/api/System.Diagnostics.Process)物件。 `Get-Process`</span><span class="sxs-lookup"><span data-stu-id="2b8f4-104">Several of these files are provided by PowerShell to define the display format for those objects returned by PowerShell-provided commands, such as the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object returned by the `Get-Process` cmdlet.</span></span> <span data-ttu-id="2b8f4-105">不過，您也可以建立自己的自訂格式檔案來覆寫預設的顯示格式，或者您也可以撰寫自訂格式檔案，以定義您自己的命令所傳回的物件顯示。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-105">However, you can also create your own custom formatting files to overwrite the default display formats or you can write a custom formatting file to define the display of objects returned by your own commands.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2b8f4-106">格式化檔案不會判斷傳回給管線之物件的元素。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-106">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="2b8f4-107">當物件傳回至管線時，即使部分不會顯示，該物件的所有成員都可供使用。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-107">When an object is returned to the pipeline, all members of that object are available even if some are not displayed.</span></span>

<span data-ttu-id="2b8f4-108">PowerShell 會使用這些格式檔案中的資料來決定要顯示的內容，以及如何格式化顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-108">PowerShell uses the data in these formatting files to determine what is displayed and how the displayed data is formatted.</span></span> <span data-ttu-id="2b8f4-109">顯示的資料可以包含物件的屬性或腳本的值。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-109">The displayed data can include the properties of an object or the value of a script.</span></span> <span data-ttu-id="2b8f4-110">如果您想要顯示無法直接從物件的屬性取得的某個值，例如加入物件的兩個屬性值，然後將總和顯示為數據片段，則會使用腳本。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-110">Scripts are used if you want to display some value that is not available directly from the properties of an object, such as adding the value of two properties of an object and then displaying the sum as a piece of data.</span></span> <span data-ttu-id="2b8f4-111">藉由定義要顯示之物件的視圖，即可完成所顯示資料的格式設定。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-111">Formatting of the displayed data is done by defining views for the objects that you want to display.</span></span> <span data-ttu-id="2b8f4-112">您可以為每個物件定義單一視圖，您可以為多個物件定義單一視圖，也可以為相同的物件定義多個視圖。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-112">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="2b8f4-113">您可以定義的視圖數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-113">There is no limit to the number of views that you can define.</span></span>

## <a name="common-features-of-formatting-files"></a><span data-ttu-id="2b8f4-114">格式化檔案的一般功能</span><span class="sxs-lookup"><span data-stu-id="2b8f4-114">Common Features of Formatting Files</span></span>

<span data-ttu-id="2b8f4-115">每個格式化檔案都可以定義下列元件，這些元件可以在檔案所定義的所有視圖之間共用：</span><span class="sxs-lookup"><span data-stu-id="2b8f4-115">Each formatting file can define the following components that can be shared across all the views defined by the file:</span></span>

- <span data-ttu-id="2b8f4-116">預設設定，例如，資料表資料列中所顯示的資料是否會顯示在下一行（如果資料長度超過資料行的寬度）。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-116">Default configuration setting, such as whether the data displayed in the rows of tables will be displayed on the next line if the data is longer than the width of the column.</span></span> <span data-ttu-id="2b8f4-117">如需這些設定的詳細資訊，請參閱[定義一般設定](./defining-common-configuration-features.md)。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-117">For more information about these settings, see [Defining Common Configuration Settings](./defining-common-configuration-features.md).</span></span>

- <span data-ttu-id="2b8f4-118">一組物件，可由格式化檔案的任何一種視圖顯示。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-118">Sets of objects that can be displayed by any of the views of the formatting file.</span></span> <span data-ttu-id="2b8f4-119">如需這些集合的詳細資訊 (稱為*選取集*) ，請參閱[定義物件的集合](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-119">For more information about these sets (referred to as *selection sets*), see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

- <span data-ttu-id="2b8f4-120">可供格式檔案的所有視圖使用的通用控制項。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-120">Common controls that can be used by all the views of the formatting file.</span></span> <span data-ttu-id="2b8f4-121">控制項可讓您更精確地控制資料的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-121">Controls give you finer control on how data is displayed.</span></span> <span data-ttu-id="2b8f4-122">如需控制項的詳細資訊，請參閱[定義自訂控制項](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-122">For more information about controls, see [Defining Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="formatting-views"></a><span data-ttu-id="2b8f4-123">格式化視圖</span><span class="sxs-lookup"><span data-stu-id="2b8f4-123">Formatting Views</span></span>

<span data-ttu-id="2b8f4-124">格式化視圖可以使用表格格式、清單格式、寬格式和自訂格式來顯示物件。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-124">Formatting views can display objects in a table format, list format, wide format, and custom format.</span></span> <span data-ttu-id="2b8f4-125">在大部分的情況下，每個格式定義都是由一組描述此視圖的 XML 標記所描述。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-125">For the most part, each formatting definition is described by a set of XML tags that describe the view.</span></span> <span data-ttu-id="2b8f4-126">每個視圖都會包含視圖的名稱、使用此視圖的物件，以及視圖的元素，例如資料表視圖的資料行和資料列資訊。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-126">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="2b8f4-127">資料表視圖會列出一個或多個資料行中物件或腳本區塊值的屬性。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-127">Table View Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="2b8f4-128">每個資料行都代表物件的單一屬性或腳本值。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-128">Each column represents a single property of the object or a script value.</span></span> <span data-ttu-id="2b8f4-129">您可以定義資料表視圖，以顯示物件的所有屬性、物件屬性的子集，或是屬性和腳本值的組合。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-129">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script values.</span></span> <span data-ttu-id="2b8f4-130">資料表的每個資料列都代表一個傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-130">Each row of the table represents a returned object.</span></span> <span data-ttu-id="2b8f4-131">當您使用管線將物件傳送至 Cmdlet 時，建立資料表視圖非常類似 `Format-Table` 。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-131">Creating a table view is very similar to when you pipe an object to the `Format-Table` cmdlet.</span></span> <span data-ttu-id="2b8f4-132">如需此視圖的詳細資訊，請參閱[資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-132">For more information about this view, see [Table View](./creating-a-table-view.md).</span></span>

<span data-ttu-id="2b8f4-133">清單視圖會列出物件的屬性或單一資料行中的腳本值。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-133">List View Lists the properties of an object or a script value in a single column.</span></span> <span data-ttu-id="2b8f4-134">清單的每個資料列都會顯示選擇性標籤或屬性名稱，後面接著屬性或腳本的值。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-134">Each row of the list displays an optional label or the property name followed by the value of the property or script.</span></span> <span data-ttu-id="2b8f4-135">建立清單視圖非常類似于使用管線將物件傳送至 `Format-List` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-135">Creating a list view is very similar to piping an object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="2b8f4-136">如需此視圖的詳細資訊，請參閱[清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-136">For more information about this view, see [List View](./creating-a-list-view.md).</span></span>

<span data-ttu-id="2b8f4-137">寬型視圖會列出物件的單一屬性或一或多個資料行中的腳本值。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-137">Wide View Lists a single property of an object or a script value in one or more columns.</span></span> <span data-ttu-id="2b8f4-138">沒有此視圖的標籤或標頭。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-138">There is no label or header for this view.</span></span> <span data-ttu-id="2b8f4-139">建立寬視圖非常類似于使用管線將物件傳送至 `Format-Wide` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-139">Creating a wide view is very similar to piping an object to the `Format-Wide` cmdlet.</span></span> <span data-ttu-id="2b8f4-140">如需此視圖的詳細資訊，請參閱[Wide view](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-140">For more information about this view, see [Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="2b8f4-141">[自訂視圖] 會顯示物件屬性或腳本值的可自訂視圖，而不會遵守資料表視圖、清單視圖或寬視圖的嚴格結構。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-141">Custom View Displays a customizable view of object properties or script values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="2b8f4-142">您可以定義獨立的自訂視圖，也可以定義另一個視圖所使用的自訂視圖，例如資料表視圖或清單視圖。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-142">You can define a stand-alone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="2b8f4-143">建立自訂視圖非常類似于使用管線將物件傳送至 `Format-Custom` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-143">Creating a custom view is very similar to piping an object to the `Format-Custom` cmdlet.</span></span> <span data-ttu-id="2b8f4-144">如需此視圖的詳細資訊，請參閱[自訂視圖](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-144">For more information about this view, see [Custom View](./creating-custom-controls.md).</span></span>

## <a name="components-of-a-view"></a><span data-ttu-id="2b8f4-145">視圖的元件</span><span class="sxs-lookup"><span data-stu-id="2b8f4-145">Components of a View</span></span>

<span data-ttu-id="2b8f4-146">下列 XML 範例顯示視圖的基本 XML 元件。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-146">The following XML examples show the basic XML components of a view.</span></span> <span data-ttu-id="2b8f4-147">個別的 XML 元素會根據您要建立的視圖而有所不同，但 views 的基本元件全都相同。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-147">The individual XML elements vary depending on which view you want to create, but the basic components of the views are all the same.</span></span>

<span data-ttu-id="2b8f4-148">一開始，每個 view 都有一個 `Name` 元素，指定用來參考此視圖的使用者易記名稱。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-148">To start with, each view has a `Name` element that specifies a user friendly name that is used to reference the view.</span></span> <span data-ttu-id="2b8f4-149">`ViewSelectedBy`定義視圖所要顯示之 .net 物件的專案，以及定義視圖的*控制項*元素。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-149">a `ViewSelectedBy` element that defines which .NET objects are displayed by the view, and a *control* element that defines the view.</span></span>

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

<span data-ttu-id="2b8f4-150">在 control 元素內，您可以定義一個或多個*entry*元素。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-150">Within the control element, you can define one or more *entry* elements.</span></span> <span data-ttu-id="2b8f4-151">如果您使用多個定義，則必須指定要使用每個定義的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-151">If you use multiple definitions, you must specify which .NET objects use each definition.</span></span> <span data-ttu-id="2b8f4-152">每個控制項通常只需要一個只有一個定義的專案。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-152">Typically only one entry, with only one definition, is needed for each control.</span></span>

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

<span data-ttu-id="2b8f4-153">在 view 的每個 entry 元素內，您可以指定*專案*元素，以定義該視圖所顯示的 .net 屬性或腳本。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-153">Within each entry element of a view, you specify the *item* elements that define the .NET properties or scripts that are displayed by that view.</span></span>

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

<span data-ttu-id="2b8f4-154">如先前範例所示，格式檔案可以包含多個視圖、一個 view 可以包含多個定義，而且每個定義都可以包含多個專案。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-154">As shown in the preceding examples, the formatting file can contain multiple views, a view can contain multiple definitions, and each definition can contain multiple items.</span></span>

## <a name="example-of-a-table-view"></a><span data-ttu-id="2b8f4-155">資料表視圖的範例</span><span class="sxs-lookup"><span data-stu-id="2b8f4-155">Example of a Table View</span></span>

<span data-ttu-id="2b8f4-156">下列範例顯示用來定義包含兩個數據行之資料表視圖的 XML 標記。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-156">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="2b8f4-157">[ViewDefinitions](./viewdefinitions-element-format.md)元素是格式檔案中定義之所有視圖的容器元素。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-157">The [ViewDefinitions](./viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="2b8f4-158">[View](./view-element-format.md)元素會定義特定的資料表、清單、寬型或自訂視圖。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-158">The [View](./view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="2b8f4-159">在每個[view](./view-element-format.md)專案中， [name](./name-element-for-view-format.md)元素會指定視圖的名稱， [ViewSelectedBy](./viewselectedby-element-format.md)元素會定義使用此視圖的物件，而不同的控制項元素 (例如 `TableControl` 下列範例中所示的專案) 定義視圖的類型。</span><span class="sxs-lookup"><span data-stu-id="2b8f4-159">Within each [View](./view-element-format.md) element, the [Name](./name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element shown in the following example) define the type of the view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2b8f4-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b8f4-160">See Also</span></span>

[<span data-ttu-id="2b8f4-161">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="2b8f4-161">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="2b8f4-162">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="2b8f4-162">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="2b8f4-163">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="2b8f4-163">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="2b8f4-164">建立自訂控制項</span><span class="sxs-lookup"><span data-stu-id="2b8f4-164">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="2b8f4-165">撰寫 PowerShell 格式化和類型檔案</span><span class="sxs-lookup"><span data-stu-id="2b8f4-165">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
