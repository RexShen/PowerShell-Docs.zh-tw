---
ms.date: 09/13/2016
ms.topic: reference
title: 自訂格式設定檔案
description: 自訂格式設定檔案
ms.openlocfilehash: 16e1c1046e25b35ff346585a5fd930c449c04bf8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653248"
---
# <a name="custom-formatting-files"></a><span data-ttu-id="52dd9-103">自訂格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="52dd9-103">Custom Formatting Files</span></span>

<span data-ttu-id="52dd9-104">Cmdlet、函式和腳本所傳回之物件的顯示格式，是使用 ( # B0 xml 檔案) 的格式化檔案來定義。</span><span class="sxs-lookup"><span data-stu-id="52dd9-104">The display format for the objects returned by cmdlets, functions, and scripts are defined using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="52dd9-105">其中有幾個檔案是由 Windows PowerShell 提供，以定義 Windows PowerShell Cmdlet 所傳回之物件的預設顯示格式。</span><span class="sxs-lookup"><span data-stu-id="52dd9-105">Several of these files are provided by Windows PowerShell to define the default display format for those objects returned by Windows PowerShell cmdlets.</span></span> <span data-ttu-id="52dd9-106">不過，您也可以建立自己的自訂格式檔案來覆寫預設顯示格式，或定義您自己的命令所傳回的物件顯示。</span><span class="sxs-lookup"><span data-stu-id="52dd9-106">However, you can also create your own custom formatting files to overwrite the default display formats or to define the display of objects returned by your own commands.</span></span>

<span data-ttu-id="52dd9-107">Windows PowerShell 使用這些格式設定檔案中的資料來判斷所顯示的內容，以及資料的格式化方式。</span><span class="sxs-lookup"><span data-stu-id="52dd9-107">Windows PowerShell uses the data in these formatting files to determine what is displayed and how the data is formatted.</span></span> <span data-ttu-id="52dd9-108">顯示的資料可以包含物件的屬性或腳本區塊的值。</span><span class="sxs-lookup"><span data-stu-id="52dd9-108">The displayed data can include the properties of an object or the value of a script block.</span></span>  <span data-ttu-id="52dd9-109">如果您想要顯示一些無法直接從物件的屬性中使用的值，則會使用腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="52dd9-109">Script blocks are used if you want to display some value that is not available directly from the properties of an object.</span></span> <span data-ttu-id="52dd9-110">例如，您可能會想要加入物件的兩個屬性值，並將總和顯示為個別的資料片段。</span><span class="sxs-lookup"><span data-stu-id="52dd9-110">For example, you may want to add the value of two properties of an object and display the sum as a separate piece of data.</span></span> <span data-ttu-id="52dd9-111">當您撰寫自己的格式化檔案時，您需要定義要顯示之物件的 *視圖* 。</span><span class="sxs-lookup"><span data-stu-id="52dd9-111">When you write your own formatting file, you will need to define *views* for the objects that you want to display.</span></span> <span data-ttu-id="52dd9-112">您可以為每個物件定義單一視圖，您可以為多個物件定義單一視圖，也可以為相同的物件定義多個視圖。</span><span class="sxs-lookup"><span data-stu-id="52dd9-112">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="52dd9-113">您可以定義的視圖數目沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="52dd9-113">There is no limit to the number of views that you can define.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="52dd9-114">格式化檔案不會決定傳回至管線的物件元素。</span><span class="sxs-lookup"><span data-stu-id="52dd9-114">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="52dd9-115">當物件傳回至管線時，該物件的所有成員都可以使用。</span><span class="sxs-lookup"><span data-stu-id="52dd9-115">When an object is returned to the pipeline, all members of that object are available.</span></span>

## <a name="format-views"></a><span data-ttu-id="52dd9-116">格式化視圖</span><span class="sxs-lookup"><span data-stu-id="52dd9-116">Format Views</span></span>

<span data-ttu-id="52dd9-117">格式化視圖可以以表格格式顯示物件、清單格式、寬格式和自訂格式。</span><span class="sxs-lookup"><span data-stu-id="52dd9-117">Formatting views can display objects in a table format, a list format, a wide format, and a custom format.</span></span> <span data-ttu-id="52dd9-118">在大部分的情況下，每個格式化定義都是由一組描述視圖的 XML 標記所描述。</span><span class="sxs-lookup"><span data-stu-id="52dd9-118">For the most part, each formatting definition is described by a set of XML tags that describe a view.</span></span> <span data-ttu-id="52dd9-119">每個視圖都包含視圖的名稱、使用視圖的物件以及視圖的元素，例如資料表視圖的資料行和資料列資訊。</span><span class="sxs-lookup"><span data-stu-id="52dd9-119">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="52dd9-120">下列為可用的視圖。</span><span class="sxs-lookup"><span data-stu-id="52dd9-120">The following views are available.</span></span>

<span data-ttu-id="52dd9-121">資料表視圖會列出一或多個資料行中物件或腳本區塊值的屬性。</span><span class="sxs-lookup"><span data-stu-id="52dd9-121">Table view Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="52dd9-122">每個資料行都代表物件或腳本區塊值的屬性。</span><span class="sxs-lookup"><span data-stu-id="52dd9-122">Each column represents a property of the object or a script block value.</span></span> <span data-ttu-id="52dd9-123">您可以定義資料表視圖，以顯示物件的所有屬性、物件的屬性子集，或屬性和腳本區塊值的組合。</span><span class="sxs-lookup"><span data-stu-id="52dd9-123">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script block values.</span></span> <span data-ttu-id="52dd9-124">資料表的每個資料列都代表一個傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="52dd9-124">Each row of the table represents a returned object.</span></span> <span data-ttu-id="52dd9-125">如需此視圖的詳細資訊，請參閱 [表格視圖](../format/creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="52dd9-125">For more information about this view, see [Table View](../format/creating-a-table-view.md).</span></span>

<span data-ttu-id="52dd9-126">清單視圖會列出物件的屬性，或是單一資料行中的腳本區塊值。</span><span class="sxs-lookup"><span data-stu-id="52dd9-126">List view Lists the properties of an object or a script block value in a single column.</span></span> <span data-ttu-id="52dd9-127">清單中的每個資料列都會顯示選用的標籤，或屬性名稱後面接著屬性或腳本區塊的值。</span><span class="sxs-lookup"><span data-stu-id="52dd9-127">Each row of the list displays an optional label or the property name followed by the value of the property or script block.</span></span> <span data-ttu-id="52dd9-128">如需此視圖的詳細資訊，請參閱 [清單視圖](../format/creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="52dd9-128">For more information about this view, see [List View](../format/creating-a-list-view.md).</span></span>

<span data-ttu-id="52dd9-129">寬型視圖會列出一或多個資料行中物件或腳本區塊值的單一屬性。</span><span class="sxs-lookup"><span data-stu-id="52dd9-129">Wide view Lists a single property of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="52dd9-130">此視圖沒有標籤或標頭。</span><span class="sxs-lookup"><span data-stu-id="52dd9-130">There is no label or header for this view.</span></span> <span data-ttu-id="52dd9-131">如需此視圖的詳細資訊，請參閱 [Wide view](../format/creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="52dd9-131">For more information about this view, see [Wide View](../format/creating-a-wide-view.md).</span></span>

<span data-ttu-id="52dd9-132">自訂視圖會顯示物件屬性或腳本區塊值的可自訂視圖，這些值不會遵守資料表視圖、清單視圖或寬視圖的固定結構。</span><span class="sxs-lookup"><span data-stu-id="52dd9-132">Custom view Displays a customizable view of object properties or script block values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="52dd9-133">您可以定義獨立的自訂視圖，也可以定義另一個視圖所使用的自訂視圖，例如資料表視圖或清單視圖。</span><span class="sxs-lookup"><span data-stu-id="52dd9-133">You can define a standalone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="52dd9-134">如需此視圖的詳細資訊，請參閱 [自訂視圖](../format/creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="52dd9-134">For more information about this view, see [Custom View](../format/creating-custom-controls.md).</span></span>

## <a name="view-xml-elements"></a><span data-ttu-id="52dd9-135">View XML 元素</span><span class="sxs-lookup"><span data-stu-id="52dd9-135">View XML Elements</span></span>

<span data-ttu-id="52dd9-136">下列範例顯示用來定義資料表視圖的 XML 標記，其中包含兩個數據行。</span><span class="sxs-lookup"><span data-stu-id="52dd9-136">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="52dd9-137">[ViewDefinitions](../format/viewdefinitions-element-format.md)元素是格式化檔案中定義之所有視圖的容器元素。</span><span class="sxs-lookup"><span data-stu-id="52dd9-137">The [ViewDefinitions](../format/viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="52dd9-138">[View](../format/view-element-format.md)元素會定義特定的資料表、清單、寬或自訂視圖。</span><span class="sxs-lookup"><span data-stu-id="52dd9-138">The [View](../format/view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="52dd9-139">在每個視圖內， [Name](../format/name-element-for-view-format.md) 元素會指定視圖的名稱、 [ViewSelectedBy](../format/viewselectedby-element-format.md) 元素會定義使用視圖的物件，而不同的控制項元素 (例如 `TableControl` 元素) 定義視圖的格式。</span><span class="sxs-lookup"><span data-stu-id="52dd9-139">Within each view, the [Name](../format/name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](../format/viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element) define the format of the view.</span></span>

```xml
ViewDefinitions
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

## <a name="see-also"></a><span data-ttu-id="52dd9-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52dd9-140">See Also</span></span>

[<span data-ttu-id="52dd9-141">資料表視圖</span><span class="sxs-lookup"><span data-stu-id="52dd9-141">Table View</span></span>](../format/creating-a-table-view.md)

[<span data-ttu-id="52dd9-142">清單視圖</span><span class="sxs-lookup"><span data-stu-id="52dd9-142">List View</span></span>](../format/creating-a-list-view.md)

[<span data-ttu-id="52dd9-143">寬視圖</span><span class="sxs-lookup"><span data-stu-id="52dd9-143">Wide View</span></span>](../format/creating-a-wide-view.md)

[<span data-ttu-id="52dd9-144">自訂視圖</span><span class="sxs-lookup"><span data-stu-id="52dd9-144">Custom View</span></span>](../format/creating-custom-controls.md)

[<span data-ttu-id="52dd9-145">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="52dd9-145">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
