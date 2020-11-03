---
description: 從 PowerShell 6 開始，會在 PowerShell 原始程式碼中定義物件的預設視圖。  您可以建立自己的檔案 `Format.ps1xml` 來變更物件的顯示方式，或針對您在 PowerShell 中建立的新物件類型定義預設顯示。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_format.ps1xml?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Format.ps1xml
ms.openlocfilehash: ea7a5262be912750b2a4ff6ce72060b31ccdfb8a
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207443"
---
# <a name="about-formatps1xml"></a><span data-ttu-id="3b0fc-105">關於 Format.ps1xml</span><span class="sxs-lookup"><span data-stu-id="3b0fc-105">About Format.ps1xml</span></span>

## <a name="short-description"></a><span data-ttu-id="3b0fc-106">簡短描述</span><span class="sxs-lookup"><span data-stu-id="3b0fc-106">Short description</span></span>

<span data-ttu-id="3b0fc-107">從 PowerShell 6 開始，會在 PowerShell 原始程式碼中定義物件的預設視圖。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-107">Beginning in PowerShell 6, the default views for objects are defined in PowerShell source code.</span></span>

<span data-ttu-id="3b0fc-108">您可以建立自己的檔案 `Format.ps1xml` 來變更物件的顯示方式，或針對您在 PowerShell 中建立的新物件類型定義預設顯示。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-108">You can create your own `Format.ps1xml` files to change the display of objects or to define default displays for new object types that you create in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="3b0fc-109">完整描述</span><span class="sxs-lookup"><span data-stu-id="3b0fc-109">Long description</span></span>

<span data-ttu-id="3b0fc-110">從 PowerShell 6 開始，預設的視圖會定義于 PowerShell 原始程式碼中。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-110">Beginning in PowerShell 6, the default views are defined in PowerShell source code.</span></span> <span data-ttu-id="3b0fc-111">Powershell `Format.ps1xml` 5.1 與較舊版本中的檔案不存在於 powershell 6 和更新版本中。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-111">The `Format.ps1xml` files from PowerShell 5.1 and earlier versions don't exist in PowerShell 6 and later versions.</span></span>

<span data-ttu-id="3b0fc-112">PowerShell 原始程式碼會定義 PowerShell 主控台中物件的預設顯示。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-112">The PowerShell source code defines the default display of objects in the PowerShell console.</span></span> <span data-ttu-id="3b0fc-113">您可以建立自己的檔案 `Format.ps1xml` 來變更物件的顯示方式，或針對您在 PowerShell 中建立的新物件類型定義預設顯示。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-113">You can create your own `Format.ps1xml` files to change the display of objects or to define default displays for new object types that you create in PowerShell.</span></span>

<span data-ttu-id="3b0fc-114">當 PowerShell 顯示物件時，它會使用結構化格式設定檔案中的資料來判斷物件的預設顯示。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-114">When PowerShell displays an object, it uses the data in structured formatting files to determine the default display of the object.</span></span> <span data-ttu-id="3b0fc-115">格式檔案中的資料會決定物件是轉譯在資料表或清單中，而且會決定預設會顯示哪些屬性。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-115">The data in the formatting files determines whether the object is rendered in a table or in a list, and it determines which properties are displayed by default.</span></span>

<span data-ttu-id="3b0fc-116">格式只會影響顯示。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-116">The formatting affects the display only.</span></span> <span data-ttu-id="3b0fc-117">它不會影響在管線或傳遞的物件屬性。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-117">It doesn't affect which object properties are passed down the pipeline or how they're passed.</span></span> <span data-ttu-id="3b0fc-118">`Format.ps1xml` 檔案不能用來自訂雜湊表的輸出格式。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-118">`Format.ps1xml` files can't be used to customize the output format for hash tables.</span></span>

<span data-ttu-id="3b0fc-119">`.ps1xml`格式化檔案可以為每個物件定義四個不同的視圖：</span><span class="sxs-lookup"><span data-stu-id="3b0fc-119">A `.ps1xml` formatting file can define four different views of each object:</span></span>

- <span data-ttu-id="3b0fc-120">Table</span><span class="sxs-lookup"><span data-stu-id="3b0fc-120">Table</span></span>
- <span data-ttu-id="3b0fc-121">清單</span><span class="sxs-lookup"><span data-stu-id="3b0fc-121">List</span></span>
- <span data-ttu-id="3b0fc-122">寬</span><span class="sxs-lookup"><span data-stu-id="3b0fc-122">Wide</span></span>
- <span data-ttu-id="3b0fc-123">Custom</span><span class="sxs-lookup"><span data-stu-id="3b0fc-123">Custom</span></span>

<span data-ttu-id="3b0fc-124">例如，將命令的輸出 `Get-ChildItem` 輸送至 `Format-List` 命令時，會使用在 `Format-List` 原始程式碼中定義的清單視圖，以決定如何將檔案和資料夾物件顯示為清單。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-124">For example, when the output of a `Get-ChildItem` command is piped to a `Format-List` command, `Format-List` uses the list view defined in the source code to determine how to display the file and folder objects as a list.</span></span>

<span data-ttu-id="3b0fc-125">當格式化檔案包含一個以上的物件檢視時，PowerShell 會套用它所找到的第一個視圖。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-125">When a formatting file includes more than one view of an object, PowerShell applies the first view that it finds.</span></span>

<span data-ttu-id="3b0fc-126">在自訂檔案中 `Format.ps1xml` ，view 是由一組 XML 標記所定義，這些標籤會描述視圖的名稱、可套用它的物件類型、資料行標頭，以及顯示在視圖主體中的屬性。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-126">In a custom `Format.ps1xml` file, a view is defined by a set of XML tags that describe the name of the view, the type of object to which it can be applied, the column headers, and the properties that are displayed in the body of the view.</span></span> <span data-ttu-id="3b0fc-127">檔案中的格式 `Format.ps1xml` 會在將資料呈現給使用者之前套用。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-127">The format in `Format.ps1xml` files is applied just before the data is presented to the user.</span></span>

## <a name="creating-new-formatps1xml-files"></a><span data-ttu-id="3b0fc-128">建立新的 Format.ps1xml 檔案</span><span class="sxs-lookup"><span data-stu-id="3b0fc-128">Creating new Format.ps1xml files</span></span>

<span data-ttu-id="3b0fc-129">若要變更現有物件檢視的顯示格式，或加入新物件的視圖，請建立您自己的檔案 `Format.ps1xml` ，然後將它們新增至您的 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-129">To change the display format of an existing object view, or to add views for new objects, create your own `Format.ps1xml` files, and then add them to your PowerShell session.</span></span>

<span data-ttu-id="3b0fc-130">若要建立檔案 `Format.ps1xml` 來定義自訂視圖，請使用 [FormatData](xref:Microsoft.PowerShell.Utility.Get-FormatData) 和 [Export-FormatData](xref:Microsoft.PowerShell.Utility.Export-FormatData) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-130">To create a `Format.ps1xml` file to define a custom view, use the [Get-FormatData](xref:Microsoft.PowerShell.Utility.Get-FormatData) and [Export-FormatData](xref:Microsoft.PowerShell.Utility.Export-FormatData) cmdlets.</span></span> <span data-ttu-id="3b0fc-131">使用文字編輯器來編輯檔案。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-131">Use a text editor to edit the file.</span></span> <span data-ttu-id="3b0fc-132">檔案可以儲存至 PowerShell 可存取的任何目錄，例如的子目錄 `$HOME` 。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-132">The file can be saved to any directory that PowerShell can access, such as a subdirectory of `$HOME`.</span></span>

<span data-ttu-id="3b0fc-133">若要變更目前視圖的格式，請在格式化檔案中找出視圖，然後使用這些標記來變更視圖。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-133">To change the formatting of a current view, locate the view in the formatting file, and then use the tags to change the view.</span></span> <span data-ttu-id="3b0fc-134">若要建立新物件類型的視圖，請建立新的視圖，或使用現有的 view 做為模型。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-134">To create a view for a new object type, create a new view, or use an existing view as a model.</span></span> <span data-ttu-id="3b0fc-135">下一節將說明這些標記。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-135">The tags are described in the next section.</span></span> <span data-ttu-id="3b0fc-136">然後，您可以刪除檔案中的所有其他視圖，讓任何人都能清楚變更檢查檔案的方式。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-136">You can then delete all the other views in the file so that the changes are obvious to anyone examining the file.</span></span>

<span data-ttu-id="3b0fc-137">儲存變更之後，請使用 [FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData) 將新檔案新增至您的 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-137">After you save the changes, use the [Update-FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData) to add the new file to your PowerShell session.</span></span> <span data-ttu-id="3b0fc-138">如果您想要讓您的視圖優先于內建檔案中所定義的視圖，請使用 **PrependPath** 參數。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-138">If you want your view to take precedence over a view defined in the built-in files, use the **PrependPath** parameter.</span></span> <span data-ttu-id="3b0fc-139">`Update-FormatData` 只會影響目前的會話。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-139">`Update-FormatData` affects only the current session.</span></span> <span data-ttu-id="3b0fc-140">若要對所有未來的會話進行變更，請將 `Update-FormatData` 命令新增至您的 PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-140">To make the change to all future sessions, add the `Update-FormatData` command to your PowerShell profile.</span></span>

### <a name="example-add-calendar-data-to-culture-objects"></a><span data-ttu-id="3b0fc-141">範例：將行事歷數據加入至文化特性物件</span><span class="sxs-lookup"><span data-stu-id="3b0fc-141">Example: Add calendar data to culture objects</span></span>

<span data-ttu-id="3b0fc-142">此範例示範如何在目前的 PowerShell 會話中，變更 Cmdlet 所產生之文化特性物件的格式 **。** `Get-Culture`</span><span class="sxs-lookup"><span data-stu-id="3b0fc-142">This example shows how to change the formatting of the culture objects **System.Globalization.CultureInfo** generated by the `Get-Culture` cmdlet in the current PowerShell session.</span></span> <span data-ttu-id="3b0fc-143">範例中的命令會將行事 **曆** 屬性新增至文化特性物件的預設資料表視圖顯示。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-143">The commands in the example add the **Calendar** property to the default table view display of culture objects.</span></span>

<span data-ttu-id="3b0fc-144">首先，從原始程式碼檔取得格式資料，然後建立 `Format.ps1xml` 包含文化特性物件目前觀點的檔案。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-144">To begin, get the format data from the source code file and create a `Format.ps1xml` file that contains the current view of the culture objects.</span></span>

```powershell
Get-FormatData -TypeName System.Globalization.CultureInfo |
  Export-FormatData -Path $HOME\Format\CultureInfo.Format.ps1xml
```

<span data-ttu-id="3b0fc-145">`CultureInfo.Format.ps1xml`在任何 XML 或文字編輯器中開啟檔案，例如 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-145">Open the `CultureInfo.Format.ps1xml` file in any XML or text editor, such as Visual Studio Code.</span></span> <span data-ttu-id="3b0fc-146">下列 XML 會定義 **CultureInfo** 物件的視圖。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-146">The following XML defines the views of the **CultureInfo** object.</span></span>

<span data-ttu-id="3b0fc-147">檔案 `CultureInfo.Format.ps1xml` 看起來應該如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="3b0fc-147">The `CultureInfo.Format.ps1xml` file should look like the following sample:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<Configuration>
  <ViewDefinitions>
    <View>
      <Name>System.Globalization.CultureInfo</Name>
      <ViewSelectedBy>
        <TypeName>System.Globalization.CultureInfo</TypeName>
      </ViewSelectedBy>
      <TableControl>
        <TableHeaders>
          <TableColumnHeader>
            <Width>16</Width>
          </TableColumnHeader>
          <TableColumnHeader>
            <Width>16</Width>
          </TableColumnHeader>
          <TableColumnHeader />
        </TableHeaders>
        <TableRowEntries>
          <TableRowEntry>
            <TableColumnItems>
              <TableColumnItem>
                <PropertyName>LCID</PropertyName>
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
  </ViewDefinitions>
</Configuration>
```

<span data-ttu-id="3b0fc-148">藉由新增一組新的標記，為行事 **曆** 屬性建立新的資料行 `<TableColumnHeader>` 。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-148">Create a new column for the **Calendar** property by adding a new set of `<TableColumnHeader>` tags.</span></span> <span data-ttu-id="3b0fc-149">行事 **曆** 屬性的值可能很長，因此請將45個字元的值指定為 `<Width>` 。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-149">The value of the **Calendar** property can be long, so specify a value of 45 characters as the `<Width>`.</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>
    <Width>16</Width>
  </TableColumnHeader>
  <TableColumnHeader>
    <Width>16</Width>
  </TableColumnHeader>
  <TableColumnHeader>
    <Width>45</Width>
  </TableColumnHeader>
  <TableColumnHeader/>
</TableHeaders>
```

<span data-ttu-id="3b0fc-150">使用和標記，在資料表資料列中加入行事 **曆** 的新資料行專案 `<TableColumnItem>` `<PropertyName` ：</span><span class="sxs-lookup"><span data-stu-id="3b0fc-150">Add a new column item for **Calendar** in the table rows using the `<TableColumnItem>` and `<PropertyName` tags:</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>
    <TableColumnItems>
      <TableColumnItem>
        <PropertyName>LCID</PropertyName>
      </TableColumnItem>
      <TableColumnItem>
        <PropertyName>Name</PropertyName>
      </TableColumnItem>
      <TableColumnItem>
        <PropertyName>Calendar</PropertyName>
      </TableColumnItem>
      <TableColumnItem>
        <PropertyName>DisplayName</PropertyName>
      </TableColumnItem>
    </TableColumnItems>
  </TableRowEntry>
</TableRowEntries>
```

<span data-ttu-id="3b0fc-151">儲存並關閉檔案。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-151">Save and close the file.</span></span> <span data-ttu-id="3b0fc-152">使用將 `Update-FormatData` 新的格式檔案新增至目前的 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-152">Use `Update-FormatData` to add the new format file to the current PowerShell session.</span></span>

<span data-ttu-id="3b0fc-153">這個範例會使用 **PrependPath** 參數，將新的檔案以比原始檔案更高的優先順序來放置。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-153">This example uses the **PrependPath** parameter to place the new file in a higher precedence order than the original file.</span></span> <span data-ttu-id="3b0fc-154">如需詳細資訊，請參閱 [FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData)。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-154">For more information, see [Update-FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData).</span></span>

```powershell
Update-FormatData -PrependPath $HOME\Format\CultureInfo.Format.ps1xml
```

<span data-ttu-id="3b0fc-155">若要測試變更，請輸入 `Get-Culture` 並檢查包含行事 **曆** 屬性的輸出。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-155">To test the change, type `Get-Culture` and review the output that includes the **Calendar** property.</span></span>

```powershell
Get-Culture
```

```Output
LCID  Name   Calendar                                DisplayName
----  ----   --------                                -----------
1033  en-US  System.Globalization.GregorianCalendar  English (United States)
```

## <a name="the-xml-in-formatps1xml-files"></a><span data-ttu-id="3b0fc-156">Format.ps1xml 檔案中的 XML</span><span class="sxs-lookup"><span data-stu-id="3b0fc-156">The XML in Format.ps1xml files</span></span>

<span data-ttu-id="3b0fc-157">您可以在 GitHub 上的 PowerShell 原始程式碼存放庫中，以 [.Xsd 格式](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Format.xsd) 找到完整的架構定義。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-157">The full schema definition can be found in [Format.xsd](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Format.xsd) in the PowerShell source code repository on GitHub.</span></span>

<span data-ttu-id="3b0fc-158">每個檔案的 **ViewDefinitions** 區段 `Format.ps1xml` 包含 `<View>` 定義每個視圖的標記。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-158">The **ViewDefinitions** section of each `Format.ps1xml` file contains the `<View>` tags that define each view.</span></span> <span data-ttu-id="3b0fc-159">典型的 `<View>` 標記包含下列標記：</span><span class="sxs-lookup"><span data-stu-id="3b0fc-159">A typical `<View>` tag includes the following tags:</span></span>

- <span data-ttu-id="3b0fc-160">`<Name>` 識別視圖的名稱。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-160">`<Name>` identifies the name of the view.</span></span>
- <span data-ttu-id="3b0fc-161">`<ViewSelectedBy>` 指定要套用視圖的物件類型或類型。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-161">`<ViewSelectedBy>` specifies the object type or types to which the view applies.</span></span>
- <span data-ttu-id="3b0fc-162">`<GroupBy>` 指定如何將視圖中的專案結合在群組中。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-162">`<GroupBy>` specifies how items in the view will be combined in groups.</span></span>
- <span data-ttu-id="3b0fc-163">`<TableControl>`、 `<ListControl>` 、 `<WideControl>` 和 `<CustomControl>` 包含指定每個專案的顯示方式的標記。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-163">`<TableControl>`, `<ListControl>`, `<WideControl>`, and `<CustomControl>` contain the tags that specify how each item will be displayed.</span></span>

### <a name="viewselectedby-tag"></a><span data-ttu-id="3b0fc-164">ViewSelectedBy 標記</span><span class="sxs-lookup"><span data-stu-id="3b0fc-164">ViewSelectedBy tag</span></span>

<span data-ttu-id="3b0fc-165">`<ViewSelectedBy>`標記可包含 `<TypeName>` 適用于此視圖之每個物件類型的標記。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-165">The `<ViewSelectedBy>` tag can contain a `<TypeName>` tag for each object type to which the view applies.</span></span> <span data-ttu-id="3b0fc-166">或者，它可以包含一個 `<SelectionSetName>` 標記，參考使用標記在其他地方定義的選取集合 `<SelectionSet>` 。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-166">Or, it can contain a `<SelectionSetName>` tag that references a selection set that is defined elsewhere by using a `<SelectionSet>` tag.</span></span>

### <a name="groupby-tag"></a><span data-ttu-id="3b0fc-167">GroupBy 標記</span><span class="sxs-lookup"><span data-stu-id="3b0fc-167">GroupBy tag</span></span>

<span data-ttu-id="3b0fc-168">`<GroupBy>`標記包含一個 `<PropertyName>` 標記，可指定要用來分組專案的物件屬性。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-168">The `<GroupBy>` tag contains a `<PropertyName>` tag that specifies the object property by which items are to be grouped.</span></span> <span data-ttu-id="3b0fc-169">它也包含一個 `<Label>` 標記，可指定要當做每個群組的標籤使用的字串，或 `<CustomControlName>` 參考使用標記在其他位置定義的自訂控制項的標記 `<Control>` 。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-169">It also contains either a `<Label>` tag that specifies a string to be used as a label for each group or a `<CustomControlName>` tag that references a custom control defined elsewhere using a `<Control>` tag.</span></span> <span data-ttu-id="3b0fc-170">`<Control>`標記包含 `<Name>` 標記和 `<CustomControl>` 標記。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-170">The `<Control>` tag contains a `<Name>` tag and a `<CustomControl>` tag.</span></span>

### <a name="tablecontroltag"></a><span data-ttu-id="3b0fc-171">TableControlTag</span><span class="sxs-lookup"><span data-stu-id="3b0fc-171">TableControlTag</span></span>

<span data-ttu-id="3b0fc-172">`<TableControl>`標記通常包含 `<TableHeaders>` `<TableRowEntries>` 定義資料表標頭和資料列之格式的和標記。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-172">The `<TableControl>` tag typically contains `<TableHeaders>` and `<TableRowEntries>` tags that define the formatting for the table's heads and rows.</span></span> <span data-ttu-id="3b0fc-173">`<TableHeaders>`標記通常會包含 `<TableColumnHeader>` 包含 `<Label>` 、 `<Width>` 和標記的標記 `<Alignment>` 。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-173">The `<TableHeaders>` tag typically contains `<TableColumnHeader>` tags that contain `<Label>`, `<Width>`, and `<Alignment>` tags.</span></span> <span data-ttu-id="3b0fc-174">`<TableRowEntries>`標記包含 `<TableRowEntry>` 資料表中每個資料列的標記。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-174">The `<TableRowEntries>` tag contains `<TableRowEntry>` tags for each row in the table.</span></span> <span data-ttu-id="3b0fc-175">`<TableRowEntry>`標記包含一個 `<TableColumnItems>` 標記，其中包含資料 `<TableColumnItem>` 列中每個資料行的標記。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-175">The `<TableRowEntry>` tag contains a `<TableColumnItems>` tag that contains a `<TableColumnItem>` tag for each column in the row.</span></span> <span data-ttu-id="3b0fc-176">通常， `<TableColumnItem>` 標記包含的標記會 `<PropertyName>` 識別要顯示在定義位置中的物件屬性，或是包含 `<ScriptBlock>` 腳本的標記，此標記會計算要顯示在位置中的結果。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-176">Typically, the `<TableColumnItem>` tag contains either a `<PropertyName>` tag that identifies the object property to be displayed in the defined location, or a `<ScriptBlock>` tag that contains script code that calculates a result that is to be displayed in the location.</span></span>

> [!NOTE]
> <span data-ttu-id="3b0fc-177">您也可以在其他地方，將腳本區塊用於計算結果可能很有用的位置。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-177">Script blocks can also be used elsewhere in locations where calculated results can be useful.</span></span>

<span data-ttu-id="3b0fc-178">`<TableColumnItem>`標記也可以包含 `<FormatString>` 指定如何顯示內容或計算結果的標記。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-178">The `<TableColumnItem>` tag can also contain a `<FormatString>` tag that specifies how the property or the calculated results will be displayed.</span></span>

### <a name="listcontrol-tag"></a><span data-ttu-id="3b0fc-179">ListControl 標記</span><span class="sxs-lookup"><span data-stu-id="3b0fc-179">ListControl tag</span></span>

<span data-ttu-id="3b0fc-180">`<ListControl>`標記通常會包含 `<ListEntries>` 標記。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-180">The `<ListControl>` tag typically contains a `<ListEntries>` tag.</span></span> <span data-ttu-id="3b0fc-181">`<ListEntries>`標記包含 `<ListEntry>` 標記。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-181">The `<ListEntries>` tag contains a `<ListEntry>` tag.</span></span> <span data-ttu-id="3b0fc-182">`<ListEntry>`標記包含 `<ListItems>` 標記。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-182">The `<ListEntry>` tag contains a `<ListItems>` tag.</span></span> <span data-ttu-id="3b0fc-183">`<ListItems>`標記包含 `<ListItem>` 包含標記的標記 `<PropertyName>` 。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-183">The `<ListItems>` tag contains `<ListItem>` tags, which contain `<PropertyName>` tags.</span></span> <span data-ttu-id="3b0fc-184">`<PropertyName>`標記會指定要顯示在清單中指定位置的物件屬性。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-184">The `<PropertyName>` tags specify the object property to be displayed at the specified location in the list.</span></span> <span data-ttu-id="3b0fc-185">如果使用選取集來定義視圖選取範圍， `<ListControl>` 和 `<ListEntry>` 標記也可以包含 `<EntrySelectedBy>` 包含一或多個標記的標記 `<TypeName>` 。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-185">If the view selection is defined using a selection set, the `<ListControl>` and `<ListEntry>` tags can also contain an `<EntrySelectedBy>` tag that contains one or more `<TypeName>` tags.</span></span> <span data-ttu-id="3b0fc-186">這些 `<TypeName>` 標記 `<ListControl>` 會指定標記要顯示的物件類型。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-186">These `<TypeName>` tags specify the object type that the `<ListControl>` tag is intended to display.</span></span>

### <a name="widecontrol-tag"></a><span data-ttu-id="3b0fc-187">WideControl 標記</span><span class="sxs-lookup"><span data-stu-id="3b0fc-187">WideControl tag</span></span>

<span data-ttu-id="3b0fc-188">`<WideControl>`標記通常會包含 `<WideEntries>` 標記。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-188">The `<WideControl>` tag typically contains a `<WideEntries>` tag.</span></span> <span data-ttu-id="3b0fc-189">`<WideEntries>`標記包含一或多個 `<WideEntry>` 標記。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-189">The `<WideEntries>` tag contains one or more `<WideEntry>` tags.</span></span> <span data-ttu-id="3b0fc-190">`<WideEntry>`標記通常包含一個 `<PropertyName>` 標記，可指定要在視圖中指定位置顯示的屬性。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-190">A `<WideEntry>` tag typically contains a `<PropertyName>` tag that specifies the property to be displayed at the specified location in the view.</span></span> <span data-ttu-id="3b0fc-191">`<PropertyName>`標記可以包含 `<FormatString>` 指定如何顯示內容的標記。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-191">The `<PropertyName>` tag can contain a `<FormatString>` tag that specifies how the property is to be displayed.</span></span>

### <a name="customcontrol-tag"></a><span data-ttu-id="3b0fc-192">CustomControl 標記</span><span class="sxs-lookup"><span data-stu-id="3b0fc-192">CustomControl tag</span></span>

<span data-ttu-id="3b0fc-193">`<CustomControl>`標記可讓您使用腳本區塊來定義格式。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-193">The `<CustomControl>` tag lets you use a script block to define a format.</span></span> <span data-ttu-id="3b0fc-194">`<CustomControl>`標記通常包含一個 `<CustomEntries>` 包含多個標記的標記 `<CustomEntry>` 。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-194">A `<CustomControl>` tag typically contains a `<CustomEntries>` tag that contains multiple `<CustomEntry>` tags.</span></span> <span data-ttu-id="3b0fc-195">每個 `<CustomEntry>` 標記都包含一個 `<CustomItem>` 標記，其中可包含各種標記，以指定在視圖中指定位置的內容和格式，包括 `<Text>` 、 `<Indentation>` 、 `<ExpressionBinding>` 和 `<NewLine>` 標記。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-195">Each `<CustomEntry>` tag contains a `<CustomItem>` tag that can contain a variety of tags that specify contents and formatting of the specified location in the view, including `<Text>`, `<Indentation>`, `<ExpressionBinding>`, and `<NewLine>` tags.</span></span>

## <a name="tracing-formatps1xml-file-use"></a><span data-ttu-id="3b0fc-196">追蹤 Format.ps1xml 檔案使用</span><span class="sxs-lookup"><span data-stu-id="3b0fc-196">Tracing Format.ps1xml file use</span></span>

<span data-ttu-id="3b0fc-197">若要偵測檔案載入或應用程式中的錯誤 `Format.ps1xml` ，請使用 `Trace-Command` Cmdlet 搭配下列任何格式元件做為 **Name** 參數的值：</span><span class="sxs-lookup"><span data-stu-id="3b0fc-197">To detect errors in the loading or application of `Format.ps1xml` files, use the `Trace-Command` cmdlet with any of the following format components as the value of the **Name** parameter:</span></span>

- <span data-ttu-id="3b0fc-198">FormatFileLoading</span><span class="sxs-lookup"><span data-stu-id="3b0fc-198">FormatFileLoading</span></span>
- <span data-ttu-id="3b0fc-199">FormatViewBinding</span><span class="sxs-lookup"><span data-stu-id="3b0fc-199">FormatViewBinding</span></span>

<span data-ttu-id="3b0fc-200">如需詳細資訊，請參閱 [追蹤命令](xref:Microsoft.PowerShell.Utility.Trace-Command) 和 [TraceSource](xref:Microsoft.PowerShell.Utility.Get-TraceSource)。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-200">For more information, see [Trace-Command](xref:Microsoft.PowerShell.Utility.Trace-Command) and [Get-TraceSource](xref:Microsoft.PowerShell.Utility.Get-TraceSource).</span></span>

## <a name="signing-a-formatps1xml-file"></a><span data-ttu-id="3b0fc-201">簽署 Format.ps1xml 檔案</span><span class="sxs-lookup"><span data-stu-id="3b0fc-201">Signing a Format.ps1xml file</span></span>

<span data-ttu-id="3b0fc-202">若要保護檔案的使用者 `Format.ps1xml` ，請使用數位簽章來簽署檔案。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-202">To protect the users of your `Format.ps1xml` file, sign the file using a digital signature.</span></span> <span data-ttu-id="3b0fc-203">如需詳細資訊，請參閱 [about_Signing](about_Signing.md)。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-203">For more information, see [about_Signing](about_Signing.md).</span></span>

## <a name="sample-xml-for-a-format-table-custom-view"></a><span data-ttu-id="3b0fc-204">Format-Table 自訂視圖的範例 XML</span><span class="sxs-lookup"><span data-stu-id="3b0fc-204">Sample XML for a Format-Table custom view</span></span>

<span data-ttu-id="3b0fc-205">下列 XML 範例會 `Format-Table` 為所建立的 **DirectoryInfo** 和 **FileInfo** 物件建立自訂的視圖 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-205">The following XML sample creates a `Format-Table` custom view for the **System.IO.DirectoryInfo** and **System.IO.FileInfo** objects created by `Get-ChildItem`.</span></span> <span data-ttu-id="3b0fc-206">自訂視圖會命名為 **mygciview** ，並將 **CreationTime** 資料行加入至資料表。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-206">The custom view is named **mygciview** and adds the **CreationTime** column to the table.</span></span>

<span data-ttu-id="3b0fc-207">若要建立自訂視圖，請使用 `Get-FormatData` 和 `Export-FormatData` Cmdlet 來產生檔案 `.ps1xml` 。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-207">To create the custom view, use the `Get-FormatData` and `Export-FormatData` cmdlets to generate a `.ps1xml` file.</span></span> <span data-ttu-id="3b0fc-208">然後，編輯您的檔案， `.ps1xml` 以建立自訂視圖的程式碼。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-208">Then, edit your `.ps1xml` file to create the code for your custom view.</span></span> <span data-ttu-id="3b0fc-209">檔案 `.ps1xml` 可以儲存在任何 PowerShell 可以存取的目錄中。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-209">The `.ps1xml` file can be stored in any directory that PowerShell can access.</span></span> <span data-ttu-id="3b0fc-210">例如，的子目錄 `$HOME` 。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-210">For example, a subdirectory of `$HOME`.</span></span>

<span data-ttu-id="3b0fc-211">建立檔案之後 `.ps1xml` ，請使用 Cmdlet 將 `Update-FormatData` 視圖包含在目前的 PowerShell 會話中。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-211">After the `.ps1xml` file is created, use the `Update-FormatData` cmdlet to include the view in the current PowerShell session.</span></span> <span data-ttu-id="3b0fc-212">或者，如果您需要所有 PowerShell 會話都有可用的 view，請將 update 命令新增至您的 PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-212">Or, add the update command to your PowerShell profile if you need the view available in all PowerShell sessions.</span></span>

<span data-ttu-id="3b0fc-213">在此範例中，自訂視圖必須使用表格格式，否則 `Format-Table` 會失敗。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-213">For this example, the custom view must use the table format, otherwise, `Format-Table` fails.</span></span>

<span data-ttu-id="3b0fc-214">使用 `Format-Table` **View** 參數可指定自訂視圖的名稱、 **Mygciview** ，以及使用 **CreationTime** 資料行來格式化資料表的輸出。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-214">Use `Format-Table` with the **View** parameter to specify the custom view's name, **mygciview** , and format the table's output with the **CreationTime** column.</span></span> <span data-ttu-id="3b0fc-215">如需如何執行命令的範例，請參閱 [格式化資料表](xref:Microsoft.PowerShell.Utility.Format-Table)。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-215">For an example of how the command is run, see [Format-Table](xref:Microsoft.PowerShell.Utility.Format-Table).</span></span>

> [!NOTE]
> <span data-ttu-id="3b0fc-216">雖然您可以從原始程式碼取得格式化 XML 來建立自訂視圖，但可能需要進行更多的開發以取得所需的結果。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-216">Although you can get the formatting XML from the source code to create a custom view, more development might be needed to get the desired result.</span></span>

<span data-ttu-id="3b0fc-217">在下列 `Get-FormatData` 命令中，有一個 **PowerShellVersion** 參數的替代方法，以確保傳回所有的本機格式化資訊。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-217">In the following `Get-FormatData` command, there's an alternative for the **PowerShellVersion** parameter to ensure that all local formatting information is returned.</span></span> <span data-ttu-id="3b0fc-218">使用 `-PowerShellVersion $PSVersionTable.PSVersion` 而不是特定的 PowerShell 版本。</span><span class="sxs-lookup"><span data-stu-id="3b0fc-218">Use `-PowerShellVersion $PSVersionTable.PSVersion` rather than a specific PowerShell version.</span></span>

```powershell
Get-FormatData -PowerShellVersion 5.1 -TypeName System.IO.DirectoryInfo |
   Export-FormatData -Path ./Mygciview.Format.ps1xml
Update-FormatData -AppendPath ./Mygciview.Format.ps1xml
```

```xml
<?xml version="1.0" encoding="utf-8"?>
<Configuration>
  <ViewDefinitions>
    <View>
      <Name>mygciview</Name>
      <ViewSelectedBy>
        <TypeName>System.IO.DirectoryInfo</TypeName>
        <TypeName>System.IO.FileInfo</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <PropertyName>PSParentPath</PropertyName>
      </GroupBy>
      <TableControl>
        <TableHeaders>
          <TableColumnHeader>
            <Label>Mode</Label>
            <Width>7</Width>
            <Alignment>Left</Alignment>
          </TableColumnHeader>
          <TableColumnHeader>
            <Label>LastWriteTime</Label>
            <Width>26</Width>
            <Alignment>Right</Alignment>
          </TableColumnHeader>
          <TableColumnHeader>
            <Label>CreationTime</Label>
            <Width>26</Width>
            <Alignment>Right</Alignment>
          </TableColumnHeader>
          <TableColumnHeader>
            <Label>Length</Label>
            <Width>14</Width>
            <Alignment>Right</Alignment>
          </TableColumnHeader>
          <TableColumnHeader>
            <Label>Name</Label>
            <Alignment>Left</Alignment>
          </TableColumnHeader>
        </TableHeaders>
        <TableRowEntries>
          <TableRowEntry>
            <Wrap />
            <TableColumnItems>
              <TableColumnItem>
                <PropertyName>ModeWithoutHardLink</PropertyName>
              </TableColumnItem>
              <TableColumnItem>
                <PropertyName>LastWriteTime</PropertyName>
              </TableColumnItem>
              <TableColumnItem>
                <PropertyName>CreationTime</PropertyName>
              </TableColumnItem>
              <TableColumnItem>
                <PropertyName>Length</PropertyName>
              </TableColumnItem>
              <TableColumnItem>
                <PropertyName>Name</PropertyName>
              </TableColumnItem>
            </TableColumnItems>
          </TableRowEntry>
        </TableRowEntries>
      </TableControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

## <a name="see-also"></a><span data-ttu-id="3b0fc-219">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b0fc-219">See also</span></span>

[<span data-ttu-id="3b0fc-220">Export-FormatData</span><span class="sxs-lookup"><span data-stu-id="3b0fc-220">Export-FormatData</span></span>](xref:Microsoft.PowerShell.Utility.Export-FormatData)

[<span data-ttu-id="3b0fc-221">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="3b0fc-221">Get-FormatData</span></span>](xref:Microsoft.PowerShell.Utility.Get-FormatData)

[<span data-ttu-id="3b0fc-222">Get-TraceSource</span><span class="sxs-lookup"><span data-stu-id="3b0fc-222">Get-TraceSource</span></span>](xref:Microsoft.PowerShell.Utility.Get-TraceSource)

[<span data-ttu-id="3b0fc-223">格式結構描述 XML 參考</span><span class="sxs-lookup"><span data-stu-id="3b0fc-223">Format Schema XML Reference</span></span>](/powershell/scripting/developer/format/format-schema-xml-reference)

[<span data-ttu-id="3b0fc-224">Trace-Command</span><span class="sxs-lookup"><span data-stu-id="3b0fc-224">Trace-Command</span></span>](xref:Microsoft.PowerShell.Utility.Trace-Command)

[<span data-ttu-id="3b0fc-225">Update-FormatData</span><span class="sxs-lookup"><span data-stu-id="3b0fc-225">Update-FormatData</span></span>](xref:Microsoft.PowerShell.Utility.Update-FormatData)

[<span data-ttu-id="3b0fc-226">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="3b0fc-226">Writing a PowerShell Formatting File</span></span>](/powershell/scripting/developer/format/writing-a-powershell-formatting-file)
