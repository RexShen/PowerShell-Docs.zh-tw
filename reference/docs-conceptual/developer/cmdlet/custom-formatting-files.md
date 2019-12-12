---
title: 自訂格式檔案 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 85d27545-8097-4010-9947-6d8b3ce2eac0
caps.latest.revision: 15
ms.openlocfilehash: 71c1c181058c5646c817b90d9832976a78c6c7de
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369827"
---
# <a name="custom-formatting-files"></a><span data-ttu-id="5f57f-102">自訂格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="5f57f-102">Custom Formatting Files</span></span>

<span data-ttu-id="5f57f-103">Cmdlet、函式和腳本所傳回物件的顯示格式是使用格式檔案（types.ps1xml 檔案）所定義。</span><span class="sxs-lookup"><span data-stu-id="5f57f-103">The display format for the objects returned by cmdlets, functions, and scripts are defined using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="5f57f-104">Windows PowerShell 會提供這些檔案中的幾個，以定義 Windows PowerShell Cmdlet 所傳回之物件的預設顯示格式。</span><span class="sxs-lookup"><span data-stu-id="5f57f-104">Several of these files are provided by Windows PowerShell to define the default display format for those objects returned by Windows PowerShell cmdlets.</span></span> <span data-ttu-id="5f57f-105">不過，您也可以建立自己的自訂格式檔案，以覆寫預設的顯示格式，或定義您自己的命令所傳回的物件顯示。</span><span class="sxs-lookup"><span data-stu-id="5f57f-105">However, you can also create your own custom formatting files to overwrite the default display formats or to define the display of objects returned by your own commands.</span></span>

<span data-ttu-id="5f57f-106">Windows PowerShell 會使用這些格式檔案中的資料來判斷要顯示的內容，以及資料的格式化方式。</span><span class="sxs-lookup"><span data-stu-id="5f57f-106">Windows PowerShell uses the data in these formatting files to determine what is displayed and how the data is formatted.</span></span> <span data-ttu-id="5f57f-107">顯示的資料可以包含物件的屬性或腳本區塊的值。</span><span class="sxs-lookup"><span data-stu-id="5f57f-107">The displayed data can include the properties of an object or the value of a script block.</span></span>  <span data-ttu-id="5f57f-108">如果您想要顯示無法直接從物件的屬性取得的某個值，則會使用腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="5f57f-108">Script blocks are used if you want to display some value that is not available directly from the properties of an object.</span></span> <span data-ttu-id="5f57f-109">例如，您可能會想要新增物件的兩個屬性值，並將總和顯示為個別的資料片段。</span><span class="sxs-lookup"><span data-stu-id="5f57f-109">For example, you may want to add the value of two properties of an object and display the sum as a separate piece of data.</span></span> <span data-ttu-id="5f57f-110">當您撰寫自己的格式化檔案時，您必須定義要顯示之物件的*視圖*。</span><span class="sxs-lookup"><span data-stu-id="5f57f-110">When you write your own formatting file, you will need to define *views* for the objects that you want to display.</span></span> <span data-ttu-id="5f57f-111">您可以為每個物件定義單一視圖，您可以為多個物件定義單一視圖，也可以為相同的物件定義多個視圖。</span><span class="sxs-lookup"><span data-stu-id="5f57f-111">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="5f57f-112">您可以定義的視圖數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="5f57f-112">There is no limit to the number of views that you can define.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5f57f-113">格式化檔案不會判斷傳回給管線之物件的元素。</span><span class="sxs-lookup"><span data-stu-id="5f57f-113">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="5f57f-114">當物件傳回至管線時，可以使用該物件的所有成員。</span><span class="sxs-lookup"><span data-stu-id="5f57f-114">When an object is returned to the pipeline, all members of that object are available.</span></span>

## <a name="format-views"></a><span data-ttu-id="5f57f-115">格式化視圖</span><span class="sxs-lookup"><span data-stu-id="5f57f-115">Format Views</span></span>

<span data-ttu-id="5f57f-116">格式化視圖可以使用表格格式、清單格式、寬格式，以及自訂格式來顯示物件。</span><span class="sxs-lookup"><span data-stu-id="5f57f-116">Formatting views can display objects in a table format, a list format, a wide format, and a custom format.</span></span> <span data-ttu-id="5f57f-117">在大部分的情況下，每個格式定義都是由一組描述視圖的 XML 標記所描述。</span><span class="sxs-lookup"><span data-stu-id="5f57f-117">For the most part, each formatting definition is described by a set of XML tags that describe a view.</span></span> <span data-ttu-id="5f57f-118">每個視圖都會包含視圖的名稱、使用此視圖的物件，以及視圖的元素，例如資料表視圖的資料行和資料列資訊。</span><span class="sxs-lookup"><span data-stu-id="5f57f-118">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="5f57f-119">下列為可用的視圖。</span><span class="sxs-lookup"><span data-stu-id="5f57f-119">The following views are available.</span></span>

<span data-ttu-id="5f57f-120">資料表視圖會列出一個或多個資料行中物件或腳本區塊值的屬性。</span><span class="sxs-lookup"><span data-stu-id="5f57f-120">Table view Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="5f57f-121">每個資料行都代表物件或腳本區塊值的屬性。</span><span class="sxs-lookup"><span data-stu-id="5f57f-121">Each column represents a property of the object or a script block value.</span></span> <span data-ttu-id="5f57f-122">您可以定義資料表視圖，以顯示物件的所有屬性、物件屬性的子集，或是屬性和腳本區塊值的組合。</span><span class="sxs-lookup"><span data-stu-id="5f57f-122">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script block values.</span></span> <span data-ttu-id="5f57f-123">資料表的每個資料列都代表一個傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="5f57f-123">Each row of the table represents a returned object.</span></span> <span data-ttu-id="5f57f-124">如需此視圖的詳細資訊，請參閱[資料表視圖](../format/creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="5f57f-124">For more information about this view, see [Table View](../format/creating-a-table-view.md).</span></span>

<span data-ttu-id="5f57f-125">清單視圖會列出物件的屬性或單一資料行中的腳本區塊值。</span><span class="sxs-lookup"><span data-stu-id="5f57f-125">List view Lists the properties of an object or a script block value in a single column.</span></span> <span data-ttu-id="5f57f-126">清單的每個資料列都會顯示選擇性標籤或屬性名稱，後面接著屬性或腳本區塊的值。</span><span class="sxs-lookup"><span data-stu-id="5f57f-126">Each row of the list displays an optional label or the property name followed by the value of the property or script block.</span></span> <span data-ttu-id="5f57f-127">如需此視圖的詳細資訊，請參閱[清單視圖](../format/creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="5f57f-127">For more information about this view, see [List View](../format/creating-a-list-view.md).</span></span>

<span data-ttu-id="5f57f-128">寬型視圖會列出一個或多個資料行中物件或腳本區塊值的單一屬性。</span><span class="sxs-lookup"><span data-stu-id="5f57f-128">Wide view Lists a single property of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="5f57f-129">沒有此視圖的標籤或標頭。</span><span class="sxs-lookup"><span data-stu-id="5f57f-129">There is no label or header for this view.</span></span> <span data-ttu-id="5f57f-130">如需此視圖的詳細資訊，請參閱[Wide view](../format/creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="5f57f-130">For more information about this view, see [Wide View](../format/creating-a-wide-view.md).</span></span>

<span data-ttu-id="5f57f-131">[自訂視圖] 會顯示物件屬性或腳本區塊值的可自訂視圖，而不會遵守資料表視圖、清單視圖或寬視圖的嚴格結構。</span><span class="sxs-lookup"><span data-stu-id="5f57f-131">Custom view Displays a customizable view of object properties or script block values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="5f57f-132">您可以定義獨立的自訂視圖，也可以定義另一個視圖所使用的自訂視圖，例如資料表視圖或清單視圖。</span><span class="sxs-lookup"><span data-stu-id="5f57f-132">You can define a standalone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="5f57f-133">如需此視圖的詳細資訊，請參閱[自訂視圖](../format/creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="5f57f-133">For more information about this view, see [Custom View](../format/creating-custom-controls.md).</span></span>

## <a name="view-xml-elements"></a><span data-ttu-id="5f57f-134">View XML 元素</span><span class="sxs-lookup"><span data-stu-id="5f57f-134">View XML Elements</span></span>

<span data-ttu-id="5f57f-135">下列範例顯示用來定義包含兩個數據行之資料表視圖的 XML 標記。</span><span class="sxs-lookup"><span data-stu-id="5f57f-135">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="5f57f-136">[ViewDefinitions](../format/viewdefinitions-element-format.md)元素是格式檔案中定義之所有視圖的容器元素。</span><span class="sxs-lookup"><span data-stu-id="5f57f-136">The [ViewDefinitions](../format/viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="5f57f-137">[View](../format/view-element-format.md)元素會定義特定的資料表、清單、寬型或自訂視圖。</span><span class="sxs-lookup"><span data-stu-id="5f57f-137">The [View](../format/view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="5f57f-138">在每個視圖中， [name](../format/name-element-for-view-format.md)元素會指定視圖的名稱， [ViewSelectedBy](../format/viewselectedby-element-format.md)元素會定義使用此視圖的物件，而不同的控制項專案（例如 `TableControl` 專案）會定義視圖的格式。</span><span class="sxs-lookup"><span data-stu-id="5f57f-138">Within each view, the [Name](../format/name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](../format/viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element) define the format of the view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="5f57f-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f57f-139">See Also</span></span>

[<span data-ttu-id="5f57f-140">資料表視圖</span><span class="sxs-lookup"><span data-stu-id="5f57f-140">Table View</span></span>](../format/creating-a-table-view.md)

[<span data-ttu-id="5f57f-141">清單檢視</span><span class="sxs-lookup"><span data-stu-id="5f57f-141">List View</span></span>](../format/creating-a-list-view.md)

[<span data-ttu-id="5f57f-142">寬視圖</span><span class="sxs-lookup"><span data-stu-id="5f57f-142">Wide View</span></span>](../format/creating-a-wide-view.md)

[<span data-ttu-id="5f57f-143">自訂視圖</span><span class="sxs-lookup"><span data-stu-id="5f57f-143">Custom View</span></span>](../format/creating-custom-controls.md)

[<span data-ttu-id="5f57f-144">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5f57f-144">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
