---
title: 自訂格式的檔案 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 85d27545-8097-4010-9947-6d8b3ce2eac0
caps.latest.revision: 15
ms.openlocfilehash: 71c1c181058c5646c817b90d9832976a78c6c7de
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068295"
---
# <a name="custom-formatting-files"></a><span data-ttu-id="40cb9-102">自訂格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="40cb9-102">Custom Formatting Files</span></span>

<span data-ttu-id="40cb9-103">Cmdlet、 函數和指令碼所傳回的物件的顯示格式會定義使用格式檔案 （format.ps1xml 檔案）。</span><span class="sxs-lookup"><span data-stu-id="40cb9-103">The display format for the objects returned by cmdlets, functions, and scripts are defined using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="40cb9-104">這些檔案的數個會提供定義 Windows PowerShell cmdlet 所傳回的物件的預設顯示格式的 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="40cb9-104">Several of these files are provided by Windows PowerShell to define the default display format for those objects returned by Windows PowerShell cmdlets.</span></span> <span data-ttu-id="40cb9-105">不過，您也可以建立您自己自訂的格式化檔案，覆寫預設顯示格式，或定義您自己的命令所傳回的物件的顯示。</span><span class="sxs-lookup"><span data-stu-id="40cb9-105">However, you can also create your own custom formatting files to overwrite the default display formats or to define the display of objects returned by your own commands.</span></span>

<span data-ttu-id="40cb9-106">Windows PowerShell 會使用這些格式的檔案中的資料，來決定所顯示的內容，以及如何格式化資料。</span><span class="sxs-lookup"><span data-stu-id="40cb9-106">Windows PowerShell uses the data in these formatting files to determine what is displayed and how the data is formatted.</span></span> <span data-ttu-id="40cb9-107">顯示的資料可以包含物件的屬性或值的指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="40cb9-107">The displayed data can include the properties of an object or the value of a script block.</span></span>  <span data-ttu-id="40cb9-108">如果您想要顯示某些值不可以直接從物件的屬性，則會使用指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="40cb9-108">Script blocks are used if you want to display some value that is not available directly from the properties of an object.</span></span> <span data-ttu-id="40cb9-109">例如，您可能要新增的兩個物件的屬性值，並顯示為個別的一種資料的總和。</span><span class="sxs-lookup"><span data-stu-id="40cb9-109">For example, you may want to add the value of two properties of an object and display the sum as a separate piece of data.</span></span> <span data-ttu-id="40cb9-110">當您撰寫自己的格式化檔案時，您必須定義*檢視*您想要顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="40cb9-110">When you write your own formatting file, you will need to define *views* for the objects that you want to display.</span></span> <span data-ttu-id="40cb9-111">您可以定義每個物件的單一檢視，您可以定義多個物件的單一檢視，或您可以定義多個檢視，針對相同的物件。</span><span class="sxs-lookup"><span data-stu-id="40cb9-111">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="40cb9-112">沒有任何限制，您可以定義的檢視數目。</span><span class="sxs-lookup"><span data-stu-id="40cb9-112">There is no limit to the number of views that you can define.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="40cb9-113">格式化檔案並判斷會傳回至管線的物件項目。</span><span class="sxs-lookup"><span data-stu-id="40cb9-113">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="40cb9-114">當物件傳回至管線時，該物件的所有成員都都可用。</span><span class="sxs-lookup"><span data-stu-id="40cb9-114">When an object is returned to the pipeline, all members of that object are available.</span></span>

## <a name="format-views"></a><span data-ttu-id="40cb9-115">格式檢視</span><span class="sxs-lookup"><span data-stu-id="40cb9-115">Format Views</span></span>

<span data-ttu-id="40cb9-116">格式化檢視可以顯示的物件中以資料表格式、 以清單格式、 寬的格式和自訂的格式。</span><span class="sxs-lookup"><span data-stu-id="40cb9-116">Formatting views can display objects in a table format, a list format, a wide format, and a custom format.</span></span> <span data-ttu-id="40cb9-117">大部分的情況下，每個格式定義一組描述檢視的 XML 標記所描述。</span><span class="sxs-lookup"><span data-stu-id="40cb9-117">For the most part, each formatting definition is described by a set of XML tags that describe a view.</span></span> <span data-ttu-id="40cb9-118">每個檢視包含的檢視名稱使用檢視和檢視，例如表格檢視的資料行和資料列資訊的元件的物件。</span><span class="sxs-lookup"><span data-stu-id="40cb9-118">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="40cb9-119">提供下列檢視。</span><span class="sxs-lookup"><span data-stu-id="40cb9-119">The following views are available.</span></span>

<span data-ttu-id="40cb9-120">資料表檢視會列出物件或一或多個資料行中的指令碼區塊值的屬性。</span><span class="sxs-lookup"><span data-stu-id="40cb9-120">Table view Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="40cb9-121">每個資料行表示的物件或指令碼區塊值的屬性。</span><span class="sxs-lookup"><span data-stu-id="40cb9-121">Each column represents a property of the object or a script block value.</span></span> <span data-ttu-id="40cb9-122">您可以定義顯示的物件，物件或屬性和值的組合指令碼區塊的屬性子集的所有屬性的資料表檢視。</span><span class="sxs-lookup"><span data-stu-id="40cb9-122">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script block values.</span></span> <span data-ttu-id="40cb9-123">資料表的每個資料列都代表傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="40cb9-123">Each row of the table represents a returned object.</span></span> <span data-ttu-id="40cb9-124">如需有關此檢視的詳細資訊，請參閱[資料表檢視](../format/creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="40cb9-124">For more information about this view, see [Table View](../format/creating-a-table-view.md).</span></span>

<span data-ttu-id="40cb9-125">清單檢視會列出物件或單一資料行中的指令碼區塊值的屬性。</span><span class="sxs-lookup"><span data-stu-id="40cb9-125">List view Lists the properties of an object or a script block value in a single column.</span></span> <span data-ttu-id="40cb9-126">選擇性的標籤或屬性名稱後面的屬性或指令碼區塊的值，則會顯示清單的每個資料列。</span><span class="sxs-lookup"><span data-stu-id="40cb9-126">Each row of the list displays an optional label or the property name followed by the value of the property or script block.</span></span> <span data-ttu-id="40cb9-127">如需有關此檢視的詳細資訊，請參閱[清單檢視](../format/creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="40cb9-127">For more information about this view, see [List View](../format/creating-a-list-view.md).</span></span>

<span data-ttu-id="40cb9-128">寬型檢視會列出物件或指令碼區塊中的值一或多個資料行的單一屬性。</span><span class="sxs-lookup"><span data-stu-id="40cb9-128">Wide view Lists a single property of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="40cb9-129">沒有任何標籤或標頭，此檢視。</span><span class="sxs-lookup"><span data-stu-id="40cb9-129">There is no label or header for this view.</span></span> <span data-ttu-id="40cb9-130">如需有關此檢視的詳細資訊，請參閱[寬型檢視](../format/creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="40cb9-130">For more information about this view, see [Wide View](../format/creating-a-wide-view.md).</span></span>

<span data-ttu-id="40cb9-131">自訂檢視會顯示物件屬性的指令碼區塊值不會遵守固定的結構的資料表檢視、 清單檢視或寬幅檢視的自訂檢視。</span><span class="sxs-lookup"><span data-stu-id="40cb9-131">Custom view Displays a customizable view of object properties or script block values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="40cb9-132">您可以定義獨立自訂檢視，或您可以定義自訂的檢視，可由另一個檢視，例如以資料表或清單檢視。</span><span class="sxs-lookup"><span data-stu-id="40cb9-132">You can define a standalone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="40cb9-133">如需有關此檢視的詳細資訊，請參閱[的自訂檢視](../format/creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="40cb9-133">For more information about this view, see [Custom View](../format/creating-custom-controls.md).</span></span>

## <a name="view-xml-elements"></a><span data-ttu-id="40cb9-134">檢視 XML 項目</span><span class="sxs-lookup"><span data-stu-id="40cb9-134">View XML Elements</span></span>

<span data-ttu-id="40cb9-135">下列範例示範用來定義包含兩個資料行的資料表檢視的 XML 標記。</span><span class="sxs-lookup"><span data-stu-id="40cb9-135">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="40cb9-136">[ViewDefinitions](../format/viewdefinitions-element-format.md)項目是在格式檔案中定義的所有檢視的容器項目。</span><span class="sxs-lookup"><span data-stu-id="40cb9-136">The [ViewDefinitions](../format/viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="40cb9-137">[檢視](../format/view-element-format.md)項目會定義特定資料表、 清單、 寬，或自訂的檢視。</span><span class="sxs-lookup"><span data-stu-id="40cb9-137">The [View](../format/view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="40cb9-138">在每個檢視中，[名稱](../format/name-element-for-view-format.md)項目指定的檢視名稱[ViewSelectedBy](../format/viewselectedby-element-format.md)項目會定義檢視和不同的控制項項目所使用的物件 (例如`TableControl`項目） 定義的檢視格式。</span><span class="sxs-lookup"><span data-stu-id="40cb9-138">Within each view, the [Name](../format/name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](../format/viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element) define the format of the view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="40cb9-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40cb9-139">See Also</span></span>

[<span data-ttu-id="40cb9-140">資料表檢視</span><span class="sxs-lookup"><span data-stu-id="40cb9-140">Table View</span></span>](../format/creating-a-table-view.md)

[<span data-ttu-id="40cb9-141">清單檢視</span><span class="sxs-lookup"><span data-stu-id="40cb9-141">List View</span></span>](../format/creating-a-list-view.md)

[<span data-ttu-id="40cb9-142">寬型檢視</span><span class="sxs-lookup"><span data-stu-id="40cb9-142">Wide View</span></span>](../format/creating-a-wide-view.md)

[<span data-ttu-id="40cb9-143">自訂檢視</span><span class="sxs-lookup"><span data-stu-id="40cb9-143">Custom View</span></span>](../format/creating-custom-controls.md)

[<span data-ttu-id="40cb9-144">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="40cb9-144">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
