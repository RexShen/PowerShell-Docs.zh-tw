---
title: 格式檔案概觀 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe888fee-1fe9-459f-9d62-35732c19a7f8
caps.latest.revision: 13
ms.openlocfilehash: d418cff70c1197aa3c331eed909f49198da139e9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863294"
---
# <a name="formatting-file-overview"></a><span data-ttu-id="371f4-102">格式設定檔案概觀</span><span class="sxs-lookup"><span data-stu-id="371f4-102">Formatting File Overview</span></span>

<span data-ttu-id="371f4-103">使用格式化檔案 （format.ps1xml 檔案中） 所定義的命令 （cmdlet、 函數和指令碼） 所傳回的物件的顯示格式。</span><span class="sxs-lookup"><span data-stu-id="371f4-103">The display format for the objects that are returned by commands (cmdlets, functions, and scripts) are defined by using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="371f4-104">這些檔案的數個所提供的 PowerShell，來定義所提供 PowerShell 命令，例如傳回這些物件的顯示格式[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)所傳回的物件`Get-Process`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="371f4-104">Several of these files are provided by PowerShell to define the display format for those objects returned by PowerShell-provided commands, such as the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object returned by the `Get-Process` cmdlet.</span></span> <span data-ttu-id="371f4-105">不過，您也可以建立您自己自訂的格式化檔案，以覆寫預設顯示格式，或者您可以撰寫自訂的格式檔案，以定義您自己的命令所傳回的物件的顯示。</span><span class="sxs-lookup"><span data-stu-id="371f4-105">However, you can also create your own custom formatting files to overwrite the default display formats or you can write a custom formatting file to define the display of objects returned by your own commands.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="371f4-106">格式化檔案並判斷會傳回至管線的物件項目。</span><span class="sxs-lookup"><span data-stu-id="371f4-106">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="371f4-107">當物件傳回至管線時，該物件的所有成員都是可用，即使有些無法顯示。</span><span class="sxs-lookup"><span data-stu-id="371f4-107">When an object is returned to the pipeline, all members of that object are available even if some are not displayed.</span></span>

<span data-ttu-id="371f4-108">PowerShell 會使用這些格式的檔案中的資料，來決定所顯示的內容，以及如何格式化顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="371f4-108">PowerShell uses the data in these formatting files to determine what is displayed and how the displayed data is formatted.</span></span> <span data-ttu-id="371f4-109">顯示的資料可以包含物件的屬性或指令碼的值。</span><span class="sxs-lookup"><span data-stu-id="371f4-109">The displayed data can include the properties of an object or the value of a script.</span></span> <span data-ttu-id="371f4-110">如果您想要顯示某些值不可以直接從物件，例如新增的兩個物件的屬性值，並顯示總和為某份資料的屬性，則會使用指令碼。</span><span class="sxs-lookup"><span data-stu-id="371f4-110">Scripts are used if you want to display some value that is not available directly from the properties of an object, such as adding the value of two properties of an object and then displaying the sum as a piece of data.</span></span> <span data-ttu-id="371f4-111">顯示資料的格式是由定義您想要顯示物件的檢視。</span><span class="sxs-lookup"><span data-stu-id="371f4-111">Formatting of the displayed data is done by defining views for the objects that you want to display.</span></span> <span data-ttu-id="371f4-112">您可以定義每個物件的單一檢視，您可以定義多個物件的單一檢視，或您可以定義多個檢視，針對相同的物件。</span><span class="sxs-lookup"><span data-stu-id="371f4-112">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="371f4-113">沒有任何限制，您可以定義的檢視數目。</span><span class="sxs-lookup"><span data-stu-id="371f4-113">There is no limit to the number of views that you can define.</span></span>

## <a name="common-features-of-formatting-files"></a><span data-ttu-id="371f4-114">格式化檔案的通用功能</span><span class="sxs-lookup"><span data-stu-id="371f4-114">Common Features of Formatting Files</span></span>

<span data-ttu-id="371f4-115">每個格式檔案可以定義可由檔案所定義的所有檢視之間共用的下列元件：</span><span class="sxs-lookup"><span data-stu-id="371f4-115">Each formatting file can define the following components that can be shared across all the views defined by the file:</span></span>

- <span data-ttu-id="371f4-116">預設的組態設定，例如是否只要資料長度超過資料行的寬度，資料表的資料列中顯示的資料就會顯示在下一行。</span><span class="sxs-lookup"><span data-stu-id="371f4-116">Default configuration setting, such as whether the data displayed in the rows of tables will be displayed on the next line if the data is longer than the width of the column.</span></span> <span data-ttu-id="371f4-117">如需有關這些設定的詳細資訊，請參閱 <<c0> [ 定義通用的組態設定](./defining-common-configuration-features.md)。</span><span class="sxs-lookup"><span data-stu-id="371f4-117">For more information about these settings, see [Defining Common Configuration Settings](./defining-common-configuration-features.md).</span></span>

- <span data-ttu-id="371f4-118">可以由任何格式化檔案的檢視所顯示的物件集。</span><span class="sxs-lookup"><span data-stu-id="371f4-118">Sets of objects that can be displayed by any of the views of the formatting file.</span></span> <span data-ttu-id="371f4-119">如需有關這些集合 (稱為*選取項目集*)，請參閱[定義設定的物件](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="371f4-119">For more information about these sets (referred to as *selection sets*), see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

- <span data-ttu-id="371f4-120">可用的格式化檔案的所有檢視通用控制項。</span><span class="sxs-lookup"><span data-stu-id="371f4-120">Common controls that can be used by all the views of the formatting file.</span></span> <span data-ttu-id="371f4-121">控制項可讓您更細微的控制，在資料顯示方式。</span><span class="sxs-lookup"><span data-stu-id="371f4-121">Controls give you finer control on how data is displayed.</span></span> <span data-ttu-id="371f4-122">如需控制項的詳細資訊，請參閱[定義的自訂控制項](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="371f4-122">For more information about controls, see [Defining Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="formatting-views"></a><span data-ttu-id="371f4-123">格式化檢視</span><span class="sxs-lookup"><span data-stu-id="371f4-123">Formatting Views</span></span>

<span data-ttu-id="371f4-124">格式化檢視可以表格格式，清單格式、 寬的格式和自訂格式中顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="371f4-124">Formatting views can display objects in a table format, list format, wide format, and custom format.</span></span> <span data-ttu-id="371f4-125">大部分的情況下，每個格式定義一組描述檢視的 XML 標記所描述。</span><span class="sxs-lookup"><span data-stu-id="371f4-125">For the most part, each formatting definition is described by a set of XML tags that describe the view.</span></span> <span data-ttu-id="371f4-126">每個檢視包含的檢視名稱使用檢視和檢視，例如表格檢視的資料行和資料列資訊的元件的物件。</span><span class="sxs-lookup"><span data-stu-id="371f4-126">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="371f4-127">資料表檢視清單物件或一或多個資料行中的指令碼區塊值的屬性。</span><span class="sxs-lookup"><span data-stu-id="371f4-127">Table View Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="371f4-128">每個資料行表示的物件或指令碼值的單一屬性。</span><span class="sxs-lookup"><span data-stu-id="371f4-128">Each column represents a single property of the object or a script value.</span></span> <span data-ttu-id="371f4-129">您可以定義顯示的物件，物件或屬性和指令碼值的組合的屬性子集的所有屬性的資料表檢視。</span><span class="sxs-lookup"><span data-stu-id="371f4-129">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script values.</span></span> <span data-ttu-id="371f4-130">資料表的每個資料列都代表傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="371f4-130">Each row of the table represents a returned object.</span></span> <span data-ttu-id="371f4-131">建立資料表檢視，是非常類似於當您使用管線傳送物件`Format-Table`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="371f4-131">Creating a table view is very similar to when you pipe an object to the `Format-Table` cmdlet.</span></span> <span data-ttu-id="371f4-132">如需有關此檢視的詳細資訊，請參閱[資料表檢視](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="371f4-132">For more information about this view, see [Table View](./creating-a-table-view.md).</span></span>

<span data-ttu-id="371f4-133">清單檢視會列出物件或單一資料行中的指令碼值的屬性。</span><span class="sxs-lookup"><span data-stu-id="371f4-133">List View Lists the properties of an object or a script value in a single column.</span></span> <span data-ttu-id="371f4-134">選擇性的標籤或屬性名稱後面的屬性或指令碼的值，則會顯示清單的每個資料列。</span><span class="sxs-lookup"><span data-stu-id="371f4-134">Each row of the list displays an optional label or the property name followed by the value of the property or script.</span></span> <span data-ttu-id="371f4-135">建立清單檢視是非常類似於使用管線傳送物件`Format-List`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="371f4-135">Creating a list view is very similar to piping an object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="371f4-136">如需有關此檢視的詳細資訊，請參閱[清單檢視](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="371f4-136">For more information about this view, see [List View](./creating-a-list-view.md).</span></span>

<span data-ttu-id="371f4-137">寬型檢視會列出物件或指令碼中的值一或多個資料行的單一屬性。</span><span class="sxs-lookup"><span data-stu-id="371f4-137">Wide View Lists a single property of an object or a script value in one or more columns.</span></span> <span data-ttu-id="371f4-138">沒有任何標籤或標頭，此檢視。</span><span class="sxs-lookup"><span data-stu-id="371f4-138">There is no label or header for this view.</span></span> <span data-ttu-id="371f4-139">建立寬型檢視是非常類似於使用管線傳送物件`Format-Wide`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="371f4-139">Creating a wide view is very similar to piping an object to the `Format-Wide` cmdlet.</span></span> <span data-ttu-id="371f4-140">如需有關此檢視的詳細資訊，請參閱[寬型檢視](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="371f4-140">For more information about this view, see [Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="371f4-141">自訂檢視會顯示物件屬性的指令碼的值不會遵守固定的結構的資料表檢視、 清單檢視或寬幅檢視的自訂檢視。</span><span class="sxs-lookup"><span data-stu-id="371f4-141">Custom View Displays a customizable view of object properties or script values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="371f4-142">您可以定義獨立的自訂檢視，或您可以定義自訂的檢視，可由另一個檢視，例如以資料表或清單檢視。</span><span class="sxs-lookup"><span data-stu-id="371f4-142">You can define a stand-alone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="371f4-143">建立自訂檢視是非常類似於使用管線傳送物件`Format-Custom`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="371f4-143">Creating a custom view is very similar to piping an object to the `Format-Custom` cmdlet.</span></span> <span data-ttu-id="371f4-144">如需有關此檢視的詳細資訊，請參閱[的自訂檢視](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="371f4-144">For more information about this view, see [Custom View](./creating-custom-controls.md).</span></span>

## <a name="components-of-a-view"></a><span data-ttu-id="371f4-145">檢視元件</span><span class="sxs-lookup"><span data-stu-id="371f4-145">Components of a View</span></span>

<span data-ttu-id="371f4-146">在下列 XML 中，示範了檢視表的基本 XML 元件。</span><span class="sxs-lookup"><span data-stu-id="371f4-146">The following XML examples show the basic XML components of a view.</span></span> <span data-ttu-id="371f4-147">個別的 XML 項目而異的檢視根據您想要建立，但基本的檢視元件全都相同。</span><span class="sxs-lookup"><span data-stu-id="371f4-147">The individual XML elements vary depending on which view you want to create, but the basic components of the views are all the same.</span></span>

<span data-ttu-id="371f4-148">若要開始，每個檢視有`Name`項目，指定用來參考檢視的使用者易記名稱。</span><span class="sxs-lookup"><span data-stu-id="371f4-148">To start with, each view has a `Name` element that specifies a user friendly name that is used to reference the view.</span></span> <span data-ttu-id="371f4-149">`ViewSelectedBy`定義的.NET 物件的檢視，所顯示的項目和*控制*定義檢視的項目。</span><span class="sxs-lookup"><span data-stu-id="371f4-149">a `ViewSelectedBy` element that defines which .NET objects are displayed by the view, and a *control* element that defines the view.</span></span>

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

<span data-ttu-id="371f4-150">在控制項項目，您可以定義一或多個*項目*項目。</span><span class="sxs-lookup"><span data-stu-id="371f4-150">Within the control element, you can define one or more *entry* elements.</span></span> <span data-ttu-id="371f4-151">如果您使用多個定義，您必須指定哪個.NET 物件會使用每個定義。</span><span class="sxs-lookup"><span data-stu-id="371f4-151">If you use multiple definitions, you must specify which .NET objects use each definition.</span></span> <span data-ttu-id="371f4-152">通常只有一個項目，只有一個定義，使用所需的每個控制項。</span><span class="sxs-lookup"><span data-stu-id="371f4-152">Typically only one entry, with only one definition, is needed for each control.</span></span>

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

<span data-ttu-id="371f4-153">您在檢視的每個輸入元素，指定*項目*定義該檢視所顯示的指令碼的.NET 屬性的項目。</span><span class="sxs-lookup"><span data-stu-id="371f4-153">Within each entry element of a view, you specify the *item* elements that define the .NET properties or scripts that are displayed by that view.</span></span>

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

<span data-ttu-id="371f4-154">上述範例所示，此格式的檔案可以包含多個檢視、 檢視表可以包含多個定義，和每個定義可以包含多個項目。</span><span class="sxs-lookup"><span data-stu-id="371f4-154">As shown in the preceding examples, the formatting file can contain multiple views, a view can contain multiple definitions, and each definition can contain multiple items.</span></span>

## <a name="example-of-a-table-view"></a><span data-ttu-id="371f4-155">資料表檢視的範例</span><span class="sxs-lookup"><span data-stu-id="371f4-155">Example of a Table View</span></span>

<span data-ttu-id="371f4-156">下列範例示範用來定義包含兩個資料行的資料表檢視的 XML 標記。</span><span class="sxs-lookup"><span data-stu-id="371f4-156">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="371f4-157">[ViewDefinitions](./viewdefinitions-element-format.md)項目是在格式檔案中定義的所有檢視的容器項目。</span><span class="sxs-lookup"><span data-stu-id="371f4-157">The [ViewDefinitions](./viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="371f4-158">[檢視](./view-element-format.md)項目會定義特定資料表、 清單、 寬，或自訂的檢視。</span><span class="sxs-lookup"><span data-stu-id="371f4-158">The [View](./view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="371f4-159">在每個[檢視](./view-element-format.md)項目[名稱](./name-element-for-view-format.md)項目指定的檢視名稱[ViewSelectedBy](./viewselectedby-element-format.md)項目會定義使用檢視和不同的物件控制項目 (例如`TableControl`下列範例所示的項目) 定義檢視的類型。</span><span class="sxs-lookup"><span data-stu-id="371f4-159">Within each [View](./view-element-format.md) element, the [Name](./name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element shown in the following example) define the type of the view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="371f4-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="371f4-160">See Also</span></span>

[<span data-ttu-id="371f4-161">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="371f4-161">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="371f4-162">建立資料表檢視</span><span class="sxs-lookup"><span data-stu-id="371f4-162">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="371f4-163">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="371f4-163">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="371f4-164">建立自訂控制項</span><span class="sxs-lookup"><span data-stu-id="371f4-164">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="371f4-165">撰寫 PowerShell 格式和類型的檔案</span><span class="sxs-lookup"><span data-stu-id="371f4-165">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
