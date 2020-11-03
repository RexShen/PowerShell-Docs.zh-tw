---
description: PowerShell 中的檔案會在 `Format.ps1xml` powershell 主控台中定義物件的預設顯示。 您可以建立自己的檔案 `Format.ps1xml` 來變更物件的顯示方式，或針對您在 PowerShell 中建立的新物件類型定義預設顯示。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_format.ps1xml?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Format.ps1xml
ms.openlocfilehash: be88007d23ab98b9c2f707b77f9c43578ba9887b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207667"
---
# <a name="about-formatps1xml"></a><span data-ttu-id="7d451-105">關於 Format.ps1xml</span><span class="sxs-lookup"><span data-stu-id="7d451-105">About Format.ps1xml</span></span>

## <a name="short-description"></a><span data-ttu-id="7d451-106">簡短描述</span><span class="sxs-lookup"><span data-stu-id="7d451-106">Short description</span></span>

<span data-ttu-id="7d451-107">PowerShell 中的檔案會在 `Format.ps1xml` powershell 主控台中定義物件的預設顯示。</span><span class="sxs-lookup"><span data-stu-id="7d451-107">The `Format.ps1xml` files in PowerShell define the default display of objects in the PowerShell console.</span></span> <span data-ttu-id="7d451-108">您可以建立自己的檔案 `Format.ps1xml` 來變更物件的顯示方式，或針對您在 PowerShell 中建立的新物件類型定義預設顯示。</span><span class="sxs-lookup"><span data-stu-id="7d451-108">You can create your own `Format.ps1xml` files to change the display of objects or to define default displays for new object types that you create in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="7d451-109">完整描述</span><span class="sxs-lookup"><span data-stu-id="7d451-109">Long description</span></span>

<span data-ttu-id="7d451-110">PowerShell 中的檔案會在 `Format.ps1xml` powershell 中定義物件的預設顯示。</span><span class="sxs-lookup"><span data-stu-id="7d451-110">The `Format.ps1xml` files in PowerShell define the default display of objects in PowerShell.</span></span> <span data-ttu-id="7d451-111">您可以建立自己的檔案 `Format.ps1xml` 來變更物件的顯示方式，或針對您在 PowerShell 中建立的新物件類型定義預設顯示。</span><span class="sxs-lookup"><span data-stu-id="7d451-111">You can create your own `Format.ps1xml` files to change the display of objects or to define default displays for new object types that you create in PowerShell.</span></span>

<span data-ttu-id="7d451-112">當 PowerShell 顯示物件時，它會使用結構化格式設定檔案中的資料來判斷物件的預設顯示。</span><span class="sxs-lookup"><span data-stu-id="7d451-112">When PowerShell displays an object, it uses the data in structured formatting files to determine the default display of the object.</span></span> <span data-ttu-id="7d451-113">格式檔案中的資料會決定物件是轉譯在資料表或清單中，而且會決定預設會顯示哪些屬性。</span><span class="sxs-lookup"><span data-stu-id="7d451-113">The data in the formatting files determines whether the object is rendered in a table or in a list, and it determines which properties are displayed by default.</span></span>

<span data-ttu-id="7d451-114">格式只會影響顯示。</span><span class="sxs-lookup"><span data-stu-id="7d451-114">The formatting affects the display only.</span></span> <span data-ttu-id="7d451-115">它不會影響在管線或傳遞的物件屬性。</span><span class="sxs-lookup"><span data-stu-id="7d451-115">It doesn't affect which object properties are passed down the pipeline or how they're passed.</span></span> <span data-ttu-id="7d451-116">`Format.ps1xml` 檔案不能用來自訂雜湊表的輸出格式。</span><span class="sxs-lookup"><span data-stu-id="7d451-116">`Format.ps1xml` files can't be used to customize the output format for hash tables.</span></span>

<span data-ttu-id="7d451-117">PowerShell 包含七個格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="7d451-117">PowerShell includes seven formatting files.</span></span> <span data-ttu-id="7d451-118">這些檔案位於安裝目錄 (`$PSHOME`) 。</span><span class="sxs-lookup"><span data-stu-id="7d451-118">These files are located in the installation directory (`$PSHOME`).</span></span> <span data-ttu-id="7d451-119">每個檔案會定義一組 Microsoft .NET Framework 物件的顯示：</span><span class="sxs-lookup"><span data-stu-id="7d451-119">Each file defines the display of a group of Microsoft .NET Framework objects:</span></span>

1. `Certificate.Format.ps1xml`

   <span data-ttu-id="7d451-120">憑證存放區中的物件，例如 x.509 憑證和憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="7d451-120">Objects in the Certificate store, such as X.509 certificates and certificate stores.</span></span>

1. `DotNetTypes.Format.ps1xml`

   <span data-ttu-id="7d451-121">其他 .NET Framework 類型，例如 CultureInfo、FileVersionInfo 和 EventLogEntry 物件。</span><span class="sxs-lookup"><span data-stu-id="7d451-121">Other .NET Framework types, such as CultureInfo, FileVersionInfo, and EventLogEntry objects.</span></span>

1. `FileSystem.Format.ps1xml`

   <span data-ttu-id="7d451-122">檔案系統物件，例如檔案和目錄。</span><span class="sxs-lookup"><span data-stu-id="7d451-122">File system objects, such as files and directories.</span></span>

1. `Help.Format.ps1xml`

   <span data-ttu-id="7d451-123">說明視圖，例如詳細的和完整的視圖、參數和範例。</span><span class="sxs-lookup"><span data-stu-id="7d451-123">Help views, such as detailed and full views, parameters, and examples.</span></span>

1. `PowerShellCore.Format.ps1xml`

   <span data-ttu-id="7d451-124">PowerShell 核心 Cmdlet 所產生的物件，例如 `Get-Member` 和 `Get-History` 。</span><span class="sxs-lookup"><span data-stu-id="7d451-124">Objects generated by PowerShell core cmdlets, such as `Get-Member` and `Get-History`.</span></span>

1. `PowerShellTrace.Format.ps1xml`

   <span data-ttu-id="7d451-125">追蹤物件，例如 Cmdlet 所產生的物件 `Trace-Command` 。</span><span class="sxs-lookup"><span data-stu-id="7d451-125">Trace objects, such as those generated by the `Trace-Command` cmdlet.</span></span>

1. `Registry.Format.ps1xml`

   <span data-ttu-id="7d451-126">登錄物件，例如金鑰和專案。</span><span class="sxs-lookup"><span data-stu-id="7d451-126">Registry objects, such as keys and entries.</span></span>

<span data-ttu-id="7d451-127">格式化檔案可以為每個物件定義四個不同的視圖：</span><span class="sxs-lookup"><span data-stu-id="7d451-127">A formatting file can define four different views of each object:</span></span>

- <span data-ttu-id="7d451-128">Table</span><span class="sxs-lookup"><span data-stu-id="7d451-128">Table</span></span>
- <span data-ttu-id="7d451-129">清單</span><span class="sxs-lookup"><span data-stu-id="7d451-129">List</span></span>
- <span data-ttu-id="7d451-130">寬</span><span class="sxs-lookup"><span data-stu-id="7d451-130">Wide</span></span>
- <span data-ttu-id="7d451-131">Custom</span><span class="sxs-lookup"><span data-stu-id="7d451-131">Custom</span></span>

<span data-ttu-id="7d451-132">例如，將命令的輸出傳送 `Get-ChildItem` 至 `Format-List` 命令時，會使用檔案 `Format-List` 中的 view `FileSystem.Format.ps1xml` 來決定如何將檔案和資料夾物件顯示為清單。</span><span class="sxs-lookup"><span data-stu-id="7d451-132">For example, when the output of a `Get-ChildItem` command is piped to a `Format-List` command, `Format-List` uses the view in the `FileSystem.Format.ps1xml` file to determine how to display the file and folder objects as a list.</span></span>

<span data-ttu-id="7d451-133">當格式化檔案包含一個以上的物件檢視時，PowerShell 會套用它所找到的第一個視圖。</span><span class="sxs-lookup"><span data-stu-id="7d451-133">When a formatting file includes more than one view of an object, PowerShell applies the first view that it finds.</span></span>

<span data-ttu-id="7d451-134">在檔案中 `Format.ps1xml` ，view 是由一組 XML 標記所定義，這些標記描述視圖的名稱、可以套用的物件類型、資料行標頭，以及顯示在視圖主體中的屬性。</span><span class="sxs-lookup"><span data-stu-id="7d451-134">In a `Format.ps1xml` file, a view is defined by a set of XML tags that describe the name of the view, the type of object to which it can be applied, the column headers, and the properties that are displayed in the body of the view.</span></span> <span data-ttu-id="7d451-135">檔案中的格式 `Format.ps1xml` 會在將資料呈現給使用者之前套用。</span><span class="sxs-lookup"><span data-stu-id="7d451-135">The format in `Format.ps1xml` files is applied just before the data is presented to the user.</span></span>

## <a name="creating-new-formatps1xml-files"></a><span data-ttu-id="7d451-136">建立新的 Format.ps1xml 檔案</span><span class="sxs-lookup"><span data-stu-id="7d451-136">Creating new Format.ps1xml files</span></span>

<span data-ttu-id="7d451-137">`.ps1xml`隨 PowerShell 安裝的檔案會經過數位簽署，以防止篡改，因為格式化可能包含腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="7d451-137">The `.ps1xml` files that are installed with PowerShell are digitally signed to prevent tampering because the formatting can include script blocks.</span></span> <span data-ttu-id="7d451-138">若要變更現有物件檢視的顯示格式，或加入新物件的視圖，請建立您自己的檔案 `Format.ps1xml` ，然後將它們新增至您的 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="7d451-138">To change the display format of an existing object view, or to add views for new objects, create your own `Format.ps1xml` files, and then add them to your PowerShell session.</span></span>

<span data-ttu-id="7d451-139">若要建立新的檔案，請複製現有的檔案 `Format.ps1xml` 。</span><span class="sxs-lookup"><span data-stu-id="7d451-139">To create a new file, copy an existing `Format.ps1xml` file.</span></span> <span data-ttu-id="7d451-140">新檔案可以有任何名稱，但它必須有 `.ps1xml` 副檔名。</span><span class="sxs-lookup"><span data-stu-id="7d451-140">The new file can have any name, but it must have a `.ps1xml` file name extension.</span></span> <span data-ttu-id="7d451-141">您可以將新檔案放在 PowerShell 可存取的任何目錄中，但是將檔案放在 PowerShell 安裝目錄 (`$PSHOME`) 或安裝目錄的子目錄中會很有用。</span><span class="sxs-lookup"><span data-stu-id="7d451-141">You can place the new file in any directory that is accessible to PowerShell, but it's useful to place the files in the PowerShell installation directory (`$PSHOME`) or in a subdirectory of the installation directory.</span></span>

<span data-ttu-id="7d451-142">若要變更目前視圖的格式，請在格式化檔案中找出視圖，然後使用這些標記來變更視圖。</span><span class="sxs-lookup"><span data-stu-id="7d451-142">To change the formatting of a current view, locate the view in the formatting file, and then use the tags to change the view.</span></span> <span data-ttu-id="7d451-143">若要建立新物件類型的視圖，請建立新的視圖，或使用現有的 view 做為模型。</span><span class="sxs-lookup"><span data-stu-id="7d451-143">To create a view for a new object type, create a new view, or use an existing view as a model.</span></span> <span data-ttu-id="7d451-144">下一節將說明這些標記。</span><span class="sxs-lookup"><span data-stu-id="7d451-144">The tags are described in the next section.</span></span> <span data-ttu-id="7d451-145">然後，您可以刪除檔案中的所有其他視圖，讓任何人都能清楚變更檢查檔案的方式。</span><span class="sxs-lookup"><span data-stu-id="7d451-145">You can then delete all the other views in the file so that the changes are obvious to anyone examining the file.</span></span>

<span data-ttu-id="7d451-146">儲存變更之後，請使用 `Update-FormatData` Cmdlet 將新檔案新增至您的 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="7d451-146">After you save the changes, use the `Update-FormatData` cmdlet to add the new file to your PowerShell session.</span></span> <span data-ttu-id="7d451-147">如果您想要讓您的視圖優先于內建檔案中所定義的視圖，請使用 **PrependPath** 參數。</span><span class="sxs-lookup"><span data-stu-id="7d451-147">If you want your view to take precedence over a view defined in the built-in files, use the **PrependPath** parameter.</span></span>
<span data-ttu-id="7d451-148">`Update-FormatData` 只會影響目前的會話。</span><span class="sxs-lookup"><span data-stu-id="7d451-148">`Update-FormatData` affects only the current session.</span></span> <span data-ttu-id="7d451-149">若要對所有未來的會話進行變更，請將 `Update-FormatData` 命令新增至您的 PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="7d451-149">To make the change to all future sessions, add the `Update-FormatData` command to your PowerShell profile.</span></span>

### <a name="example-adding-calendar-data-to-culture-objects"></a><span data-ttu-id="7d451-150">範例：將行事歷數據加入至文化特性物件</span><span class="sxs-lookup"><span data-stu-id="7d451-150">Example: Adding calendar data to culture objects</span></span>

<span data-ttu-id="7d451-151">此範例示範如何在目前的 PowerShell 會話中，變更 Cmdlet 所產生之文化特性物件的格式 **。** `Get-Culture`</span><span class="sxs-lookup"><span data-stu-id="7d451-151">This example shows how to change the formatting of the culture objects **System.Globalization.CultureInfo** generated by the `Get-Culture` cmdlet in the current PowerShell session.</span></span> <span data-ttu-id="7d451-152">範例中的命令會將行事 **曆** 屬性新增至文化特性物件的預設資料表視圖顯示。</span><span class="sxs-lookup"><span data-stu-id="7d451-152">The commands in the example add the **Calendar** property to the default table view display of culture objects.</span></span>

<span data-ttu-id="7d451-153">第一個步驟是尋找 `Format.ps1xml` 包含文化特性物件目前觀點的檔案。</span><span class="sxs-lookup"><span data-stu-id="7d451-153">The first step is to find the `Format.ps1xml` file that contains the current view of the culture objects.</span></span> <span data-ttu-id="7d451-154">下列 `Select-String` 命令會尋找檔案：</span><span class="sxs-lookup"><span data-stu-id="7d451-154">The following `Select-String` command finds the file:</span></span>

```powershell
$Parms = @{
  Path = "$PSHOME\*Format.ps1xml"
  Pattern = "System.Globalization.CultureInfo"
}

Select-String @Parms
```

```Output
C:\Windows\System32\WindowsPowerShell\v1.0\DotNetTypes.format.ps1xml:113:
     <Name>System.Globalization.CultureInfo</Name>
C:\Windows\System32\WindowsPowerShell\v1.0\DotNetTypes.format.ps1xml:115:
<TypeName>System.Globalization.CultureInfo</TypeName>
```

<span data-ttu-id="7d451-155">此命令會顯示定義在檔案中 `DotNetTypes.Format.ps1xml` 。</span><span class="sxs-lookup"><span data-stu-id="7d451-155">This command reveals that the definition is in the `DotNetTypes.Format.ps1xml` file.</span></span>

<span data-ttu-id="7d451-156">下一個命令會將檔案內容複寫到新的檔案 `MyDotNetTypes.Format.ps1xml` 。</span><span class="sxs-lookup"><span data-stu-id="7d451-156">The next command copies the file contents to a new file, `MyDotNetTypes.Format.ps1xml`.</span></span>

```powershell
Copy-Item $PSHome\DotNetTypes.format.ps1xml MyDotNetTypes.Format.ps1xml
```

<span data-ttu-id="7d451-157">`MyDotNetTypes.Format.ps1xml`在任何 XML 或文字編輯器中開啟檔案，例如 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="7d451-157">Open the `MyDotNetTypes.Format.ps1xml` file in any XML or text editor, such as Visual Studio Code.</span></span> <span data-ttu-id="7d451-158">尋找 [ **system.object** 物件] 區段。</span><span class="sxs-lookup"><span data-stu-id="7d451-158">Find the **System.Globalization.CultureInfo** object section.</span></span> <span data-ttu-id="7d451-159">下列 XML 會定義 **CultureInfo** 物件的視圖。</span><span class="sxs-lookup"><span data-stu-id="7d451-159">The following XML defines the views of the **CultureInfo** object.</span></span> <span data-ttu-id="7d451-160">物件只有 **TableControl** 的視圖。</span><span class="sxs-lookup"><span data-stu-id="7d451-160">The object has only a **TableControl** view.</span></span>

```xml
<View>
  <Name>System.Globalization.CultureInfo</Name>
  <ViewSelectedBy>
    <TypeName>Deserialized.System.Globalization.CultureInfo</TypeName>
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
```

<span data-ttu-id="7d451-161">刪除檔案的其餘部分，除了開啟 `<?xml>` 、 `<Configuration>` 和 `<ViewDefinitions>` 標記，以及關閉 `<ViewDefinitions>` 和標記之外 `<Configuration>` 。</span><span class="sxs-lookup"><span data-stu-id="7d451-161">Delete the remainder of the file, except for the opening `<?xml>`, `<Configuration>`, and `<ViewDefinitions>` tags and the closing `<ViewDefinitions>` and `<Configuration>` tags.</span></span> <span data-ttu-id="7d451-162">如果有數位簽章，請將它從您的自訂檔案中刪除 `Format.ps1xml` 。</span><span class="sxs-lookup"><span data-stu-id="7d451-162">If there is a digital signature, delete it from your custom `Format.ps1xml`file.</span></span>

<span data-ttu-id="7d451-163">檔案 `MyDotNetTypes.Format.ps1xml` 現在看起來應該如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="7d451-163">The `MyDotNetTypes.Format.ps1xml` file should now look like the following sample:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Configuration>
<ViewDefinitions>
<View>
  <Name>System.Globalization.CultureInfo</Name>
  <ViewSelectedBy>
    <TypeName>Deserialized.System.Globalization.CultureInfo</TypeName>
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
      <TableColumnHeader/>
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

<span data-ttu-id="7d451-164">藉由新增一組新的標記，為行事 **曆** 屬性建立新的資料行 `<TableColumnHeader>` 。</span><span class="sxs-lookup"><span data-stu-id="7d451-164">Create a new column for the **Calendar** property by adding a new set of `<TableColumnHeader>` tags.</span></span> <span data-ttu-id="7d451-165">行事 **曆** 屬性的值可能很長，因此請將45個字元的值指定為 `<Width>` 。</span><span class="sxs-lookup"><span data-stu-id="7d451-165">The value of the **Calendar** property can be long, so specify a value of 45 characters as the `<Width>`.</span></span>

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

<span data-ttu-id="7d451-166">使用和標記，在資料表資料列中加入行事 **曆** 的新資料行專案 `<TableColumnItem>` `<PropertyName` ：</span><span class="sxs-lookup"><span data-stu-id="7d451-166">Add a new column item for **Calendar** in the table rows using the `<TableColumnItem>` and `<PropertyName` tags:</span></span>

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

<span data-ttu-id="7d451-167">儲存並關閉檔案。</span><span class="sxs-lookup"><span data-stu-id="7d451-167">Save and close the file.</span></span> <span data-ttu-id="7d451-168">使用將 `Update-FormatData` 新的格式檔案新增至目前的 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="7d451-168">Use `Update-FormatData` to add the new format file to the current PowerShell session.</span></span>

<span data-ttu-id="7d451-169">這個範例會使用 **PrependPath** 參數，將新的檔案以比原始檔案更高的優先順序來放置。</span><span class="sxs-lookup"><span data-stu-id="7d451-169">This example uses the **PrependPath** parameter to place the new file in a higher precedence order than the original file.</span></span> <span data-ttu-id="7d451-170">如需詳細資訊，請參閱 [FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData)。</span><span class="sxs-lookup"><span data-stu-id="7d451-170">For more information, see [Update-FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData).</span></span>

```powershell
Update-FormatData -PrependPath $PSHOME\MyDotNetTypes.Format.ps1xml
```

<span data-ttu-id="7d451-171">若要測試變更，請輸入 `Get-Culture` 並檢查包含行事 **曆** 屬性的輸出。</span><span class="sxs-lookup"><span data-stu-id="7d451-171">To test the change, type `Get-Culture` and review the output that includes the **Calendar** property.</span></span>

```powershell
Get-Culture
```

```Output
LCID Name  Calendar                               DisplayName
---- ----  --------                               -----------
1033 en-US System.Globalization.GregorianCalendar English (United States)
```

## <a name="the-xml-in-formatps1xml-files"></a><span data-ttu-id="7d451-172">Format.ps1xml 檔案中的 XML</span><span class="sxs-lookup"><span data-stu-id="7d451-172">The XML in Format.ps1xml files</span></span>

<span data-ttu-id="7d451-173">您可以在 GitHub 上的 PowerShell 原始程式碼存放庫中，以 [.Xsd 格式](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Format.xsd) 找到完整的架構定義。</span><span class="sxs-lookup"><span data-stu-id="7d451-173">The full schema definition can be found in [Format.xsd](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Format.xsd) in the PowerShell source code repository on GitHub.</span></span>

<span data-ttu-id="7d451-174">每個檔案的 **ViewDefinitions** 區段 `Format.ps1xml` 包含 `<View>` 定義每個視圖的標記。</span><span class="sxs-lookup"><span data-stu-id="7d451-174">The **ViewDefinitions** section of each `Format.ps1xml` file contains the `<View>` tags that define each view.</span></span> <span data-ttu-id="7d451-175">典型的 `<View>` 標記包含下列標記：</span><span class="sxs-lookup"><span data-stu-id="7d451-175">A typical `<View>` tag includes the following tags:</span></span>

- <span data-ttu-id="7d451-176">`<Name>` 識別視圖的名稱。</span><span class="sxs-lookup"><span data-stu-id="7d451-176">`<Name>` identifies the name of the view.</span></span>
- <span data-ttu-id="7d451-177">`<ViewSelectedBy>` 指定要套用視圖的物件類型或類型。</span><span class="sxs-lookup"><span data-stu-id="7d451-177">`<ViewSelectedBy>` specifies the object type or types to which the view applies.</span></span>
- <span data-ttu-id="7d451-178">`<GroupBy>` 指定如何將視圖中的專案結合在群組中。</span><span class="sxs-lookup"><span data-stu-id="7d451-178">`<GroupBy>` specifies how items in the view will be combined in groups.</span></span>
- <span data-ttu-id="7d451-179">`<TableControl>`、 `<ListControl>` 、 `<WideControl>` 和 `<CustomControl>` 包含指定每個專案的顯示方式的標記。</span><span class="sxs-lookup"><span data-stu-id="7d451-179">`<TableControl>`, `<ListControl>`, `<WideControl>`, and `<CustomControl>` contain the tags that specify how each item will be displayed.</span></span>

### <a name="viewselectedby-tag"></a><span data-ttu-id="7d451-180">ViewSelectedBy 標記</span><span class="sxs-lookup"><span data-stu-id="7d451-180">ViewSelectedBy tag</span></span>

<span data-ttu-id="7d451-181">`<ViewSelectedBy>`標記可包含 `<TypeName>` 適用于此視圖之每個物件類型的標記。</span><span class="sxs-lookup"><span data-stu-id="7d451-181">The `<ViewSelectedBy>` tag can contain a `<TypeName>` tag for each object type to which the view applies.</span></span> <span data-ttu-id="7d451-182">或者，它可以包含一個 `<SelectionSetName>` 標記，參考使用標記在其他地方定義的選取集合 `<SelectionSet>` 。</span><span class="sxs-lookup"><span data-stu-id="7d451-182">Or, it can contain a `<SelectionSetName>` tag that references a selection set that is defined elsewhere by using a `<SelectionSet>` tag.</span></span>

### <a name="groupby-tag"></a><span data-ttu-id="7d451-183">GroupBy 標記</span><span class="sxs-lookup"><span data-stu-id="7d451-183">GroupBy tag</span></span>

<span data-ttu-id="7d451-184">`<GroupBy>`標記包含一個 `<PropertyName>` 標記，可指定要用來分組專案的物件屬性。</span><span class="sxs-lookup"><span data-stu-id="7d451-184">The `<GroupBy>` tag contains a `<PropertyName>` tag that specifies the object property by which items are to be grouped.</span></span> <span data-ttu-id="7d451-185">它也包含一個 `<Label>` 標記，可指定要當做每個群組的標籤使用的字串，或 `<CustomControlName>` 參考使用標記在其他位置定義的自訂控制項的標記 `<Control>` 。</span><span class="sxs-lookup"><span data-stu-id="7d451-185">It also contains either a `<Label>` tag that specifies a string to be used as a label for each group or a `<CustomControlName>` tag that references a custom control defined elsewhere using a `<Control>` tag.</span></span> <span data-ttu-id="7d451-186">`<Control>`標記包含 `<Name>` 標記和 `<CustomControl>` 標記。</span><span class="sxs-lookup"><span data-stu-id="7d451-186">The `<Control>` tag contains a `<Name>` tag and a `<CustomControl>` tag.</span></span>

### <a name="tablecontroltag"></a><span data-ttu-id="7d451-187">TableControlTag</span><span class="sxs-lookup"><span data-stu-id="7d451-187">TableControlTag</span></span>

<span data-ttu-id="7d451-188">`<TableControl>`標記通常包含 `<TableHeaders>` `<TableRowEntries>` 定義資料表標頭和資料列之格式的和標記。</span><span class="sxs-lookup"><span data-stu-id="7d451-188">The `<TableControl>` tag typically contains `<TableHeaders>` and `<TableRowEntries>` tags that define the formatting for the table's heads and rows.</span></span> <span data-ttu-id="7d451-189">`<TableHeaders>`標記通常會包含 `<TableColumnHeader>` 包含 `<Label>` 、 `<Width>` 和標記的標記 `<Alignment>` 。</span><span class="sxs-lookup"><span data-stu-id="7d451-189">The `<TableHeaders>` tag typically contains `<TableColumnHeader>` tags that contain `<Label>`, `<Width>`, and `<Alignment>` tags.</span></span> <span data-ttu-id="7d451-190">`<TableRowEntries>`標記包含 `<TableRowEntry>` 資料表中每個資料列的標記。</span><span class="sxs-lookup"><span data-stu-id="7d451-190">The `<TableRowEntries>` tag contains `<TableRowEntry>` tags for each row in the table.</span></span> <span data-ttu-id="7d451-191">`<TableRowEntry>`標記包含一個 `<TableColumnItems>` 標記，其中包含資料 `<TableColumnItem>` 列中每個資料行的標記。</span><span class="sxs-lookup"><span data-stu-id="7d451-191">The `<TableRowEntry>` tag contains a `<TableColumnItems>` tag that contains a `<TableColumnItem>` tag for each column in the row.</span></span> <span data-ttu-id="7d451-192">通常， `<TableColumnItem>` 標記包含的標記會 `<PropertyName>` 識別要顯示在定義位置中的物件屬性，或是包含 `<ScriptBlock>` 腳本的標記，此標記會計算要顯示在位置中的結果。</span><span class="sxs-lookup"><span data-stu-id="7d451-192">Typically, the `<TableColumnItem>` tag contains either a `<PropertyName>` tag that identifies the object property to be displayed in the defined location, or a `<ScriptBlock>` tag that contains script code that calculates a result that is to be displayed in the location.</span></span>

> [!NOTE]
> <span data-ttu-id="7d451-193">您也可以在其他地方，將腳本區塊用於計算結果可能很有用的位置。</span><span class="sxs-lookup"><span data-stu-id="7d451-193">Script blocks can also be used elsewhere in locations where calculated results can be useful.</span></span>

<span data-ttu-id="7d451-194">`<TableColumnItem>`標記也可以包含 `<FormatString>` 指定如何顯示內容或計算結果的標記。</span><span class="sxs-lookup"><span data-stu-id="7d451-194">The `<TableColumnItem>` tag can also contain a `<FormatString>` tag that specifies how the property or the calculated results will be displayed.</span></span>

### <a name="listcontrol-tag"></a><span data-ttu-id="7d451-195">ListControl 標記</span><span class="sxs-lookup"><span data-stu-id="7d451-195">ListControl tag</span></span>

<span data-ttu-id="7d451-196">`<ListControl>`標記通常會包含 `<ListEntries>` 標記。</span><span class="sxs-lookup"><span data-stu-id="7d451-196">The `<ListControl>` tag typically contains a `<ListEntries>` tag.</span></span> <span data-ttu-id="7d451-197">`<ListEntries>`標記包含 `<ListEntry>` 標記。</span><span class="sxs-lookup"><span data-stu-id="7d451-197">The `<ListEntries>` tag contains a `<ListEntry>` tag.</span></span> <span data-ttu-id="7d451-198">`<ListEntry>`標記包含 `<ListItems>` 標記。</span><span class="sxs-lookup"><span data-stu-id="7d451-198">The `<ListEntry>` tag contains a `<ListItems>` tag.</span></span> <span data-ttu-id="7d451-199">`<ListItems>`標記包含 `<ListItem>` 包含標記的標記 `<PropertyName>` 。</span><span class="sxs-lookup"><span data-stu-id="7d451-199">The `<ListItems>` tag contains `<ListItem>` tags, which contain `<PropertyName>` tags.</span></span> <span data-ttu-id="7d451-200">`<PropertyName>`標記會指定要顯示在清單中指定位置的物件屬性。</span><span class="sxs-lookup"><span data-stu-id="7d451-200">The `<PropertyName>` tags specify the object property to be displayed at the specified location in the list.</span></span> <span data-ttu-id="7d451-201">如果使用選取集來定義視圖選取範圍， `<ListControl>` 和 `<ListEntry>` 標記也可以包含 `<EntrySelectedBy>` 包含一或多個標記的標記 `<TypeName>` 。</span><span class="sxs-lookup"><span data-stu-id="7d451-201">If the view selection is defined using a selection set, the `<ListControl>` and `<ListEntry>` tags can also contain an `<EntrySelectedBy>` tag that contains one or more `<TypeName>` tags.</span></span> <span data-ttu-id="7d451-202">這些 `<TypeName>` 標記 `<ListControl>` 會指定標記要顯示的物件類型。</span><span class="sxs-lookup"><span data-stu-id="7d451-202">These `<TypeName>` tags specify the object type that the `<ListControl>` tag is intended to display.</span></span>

### <a name="widecontrol-tag"></a><span data-ttu-id="7d451-203">WideControl 標記</span><span class="sxs-lookup"><span data-stu-id="7d451-203">WideControl tag</span></span>

<span data-ttu-id="7d451-204">`<WideControl>`標記通常會包含 `<WideEntries>` 標記。</span><span class="sxs-lookup"><span data-stu-id="7d451-204">The `<WideControl>` tag typically contains a `<WideEntries>` tag.</span></span> <span data-ttu-id="7d451-205">`<WideEntries>`標記包含一或多個 `<WideEntry>` 標記。</span><span class="sxs-lookup"><span data-stu-id="7d451-205">The `<WideEntries>` tag contains one or more `<WideEntry>` tags.</span></span> <span data-ttu-id="7d451-206">`<WideEntry>`標記通常包含一個 `<PropertyName>` 標記，可指定要在視圖中指定位置顯示的屬性。</span><span class="sxs-lookup"><span data-stu-id="7d451-206">A `<WideEntry>` tag typically contains a `<PropertyName>` tag that specifies the property to be displayed at the specified location in the view.</span></span> <span data-ttu-id="7d451-207">`<PropertyName>`標記可以包含 `<FormatString>` 指定如何顯示內容的標記。</span><span class="sxs-lookup"><span data-stu-id="7d451-207">The `<PropertyName>` tag can contain a `<FormatString>` tag that specifies how the property is to be displayed.</span></span>

### <a name="customcontrol-tag"></a><span data-ttu-id="7d451-208">CustomControl 標記</span><span class="sxs-lookup"><span data-stu-id="7d451-208">CustomControl tag</span></span>

<span data-ttu-id="7d451-209">`<CustomControl>`標記可讓您使用腳本區塊來定義格式。</span><span class="sxs-lookup"><span data-stu-id="7d451-209">The `<CustomControl>` tag lets you use a script block to define a format.</span></span> <span data-ttu-id="7d451-210">`<CustomControl>`標記通常包含一個 `<CustomEntries>` 包含多個標記的標記 `<CustomEntry>` 。</span><span class="sxs-lookup"><span data-stu-id="7d451-210">A `<CustomControl>` tag typically contains a `<CustomEntries>` tag that contains multiple `<CustomEntry>` tags.</span></span> <span data-ttu-id="7d451-211">每個 `<CustomEntry>` 標記都包含一個 `<CustomItem>` 標記，其中可包含各種標記，以指定在視圖中指定位置的內容和格式，包括 `<Text>` 、 `<Indentation>` 、 `<ExpressionBinding>` 和 `<NewLine>` 標記。</span><span class="sxs-lookup"><span data-stu-id="7d451-211">Each `<CustomEntry>` tag contains a `<CustomItem>` tag that can contain a variety of tags that specify contents and formatting of the specified location in the view, including `<Text>`, `<Indentation>`, `<ExpressionBinding>`, and `<NewLine>` tags.</span></span>

## <a name="default-displays-in-typesps1xml"></a><span data-ttu-id="7d451-212">Types.ps1xml 中顯示預設值</span><span class="sxs-lookup"><span data-stu-id="7d451-212">Default displays in Types.ps1xml</span></span>

<span data-ttu-id="7d451-213">某些基本物件類型的預設顯示會定義在目錄中的檔案中 `Types.ps1xml` `$PSHOME` 。</span><span class="sxs-lookup"><span data-stu-id="7d451-213">The default displays of some basic object types are defined in the `Types.ps1xml` file in the `$PSHOME` directory.</span></span> <span data-ttu-id="7d451-214">節點會命名為 **PsStandardMembers** ，而子節點會使用下列其中一個標記：</span><span class="sxs-lookup"><span data-stu-id="7d451-214">The nodes are named **PsStandardMembers** , and the subnodes use one of the following tags:</span></span>

- `<DefaultDisplayProperty>`
- `<DefaultDisplayPropertySet>`
- `<DefaultKeyPropertySet>`

<span data-ttu-id="7d451-215">如需詳細資訊，請參閱 [about_Types.ps1xml](about_Types.ps1xml.md)。</span><span class="sxs-lookup"><span data-stu-id="7d451-215">For more information, see [about_Types.ps1xml](about_Types.ps1xml.md).</span></span>

## <a name="tracing-formatps1xml-file-use"></a><span data-ttu-id="7d451-216">追蹤 Format.ps1xml 檔案使用</span><span class="sxs-lookup"><span data-stu-id="7d451-216">Tracing Format.ps1xml file use</span></span>

<span data-ttu-id="7d451-217">若要偵測檔案載入或應用程式中的錯誤 `Format.ps1xml` ，請使用 `Trace-Command` Cmdlet 搭配下列任何格式元件做為 **Name** 參數的值：</span><span class="sxs-lookup"><span data-stu-id="7d451-217">To detect errors in the loading or application of `Format.ps1xml` files, use the `Trace-Command` cmdlet with any of the following format components as the value of the **Name** parameter:</span></span>

- <span data-ttu-id="7d451-218">FormatFileLoading</span><span class="sxs-lookup"><span data-stu-id="7d451-218">FormatFileLoading</span></span>
- <span data-ttu-id="7d451-219">FormatViewBinding</span><span class="sxs-lookup"><span data-stu-id="7d451-219">FormatViewBinding</span></span>

<span data-ttu-id="7d451-220">如需詳細資訊，請參閱 [追蹤命令](xref:Microsoft.PowerShell.Utility.Trace-Command) 和 [TraceSource](xref:Microsoft.PowerShell.Utility.Get-TraceSource)。</span><span class="sxs-lookup"><span data-stu-id="7d451-220">For more information, see [Trace-Command](xref:Microsoft.PowerShell.Utility.Trace-Command) and [Get-TraceSource](xref:Microsoft.PowerShell.Utility.Get-TraceSource).</span></span>

## <a name="signing-a-formatps1xml-file"></a><span data-ttu-id="7d451-221">簽署 Format.ps1xml 檔案</span><span class="sxs-lookup"><span data-stu-id="7d451-221">Signing a Format.ps1xml file</span></span>

<span data-ttu-id="7d451-222">若要保護檔案的使用者 `Format.ps1xml` ，請使用數位簽章來簽署檔案。</span><span class="sxs-lookup"><span data-stu-id="7d451-222">To protect the users of your `Format.ps1xml` file, sign the file using a digital signature.</span></span> <span data-ttu-id="7d451-223">如需詳細資訊，請參閱 [about_Signing](about_Signing.md)。</span><span class="sxs-lookup"><span data-stu-id="7d451-223">For more information, see [about_Signing](about_Signing.md).</span></span>

## <a name="sample-xml-for-a-format-table-custom-view"></a><span data-ttu-id="7d451-224">Format-Table 自訂視圖的範例 XML</span><span class="sxs-lookup"><span data-stu-id="7d451-224">Sample XML for a Format-Table custom view</span></span>

<span data-ttu-id="7d451-225">下列範例會 `Format-Table` 為所建立的 **DirectoryInfo** 和 **FileInfo** 物件建立自訂的視圖 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="7d451-225">The following sample creates a `Format-Table` custom view for the **System.IO.DirectoryInfo** and **System.IO.FileInfo** objects created by `Get-ChildItem`.</span></span> <span data-ttu-id="7d451-226">自訂視圖會命名為 **mygciview** ，並將 **CreationTime** 資料行加入至資料表。</span><span class="sxs-lookup"><span data-stu-id="7d451-226">The custom view is named **mygciview** and adds the **CreationTime** column to the table.</span></span>

<span data-ttu-id="7d451-227">自訂視圖是從儲存于 PowerShell 5.1 的檔案編輯版本所建立 `FileSystem.Format.ps1xml` `$PSHOME` 。</span><span class="sxs-lookup"><span data-stu-id="7d451-227">The custom view is created from an edited version of the `FileSystem.Format.ps1xml` file that's stored in `$PSHOME` on PowerShell 5.1.</span></span>

<span data-ttu-id="7d451-228">儲存自訂檔案之後 `.ps1xml` ，請使用 `Update-FormatData` 將此視圖包含在 PowerShell 會話中。</span><span class="sxs-lookup"><span data-stu-id="7d451-228">After your custom `.ps1xml` file is saved, use `Update-FormatData` to include the view in a PowerShell session.</span></span> <span data-ttu-id="7d451-229">在此範例中，自訂視圖必須使用表格格式，否則 `Format-Table` 會失敗。</span><span class="sxs-lookup"><span data-stu-id="7d451-229">For this example, the custom view must use the table format, otherwise, `Format-Table` fails.</span></span>

<span data-ttu-id="7d451-230">使用 `Format-Table` **View** 參數來指定自訂視圖的名稱，並格式化資料表的輸出。</span><span class="sxs-lookup"><span data-stu-id="7d451-230">Use `Format-Table` with the **View** parameter to specify the custom view's name and format the table's output.</span></span> <span data-ttu-id="7d451-231">如需如何執行命令的範例，請參閱 [格式化資料表](xref:Microsoft.PowerShell.Utility.Format-Table)。</span><span class="sxs-lookup"><span data-stu-id="7d451-231">For an example of how the command is run, see [Format-Table](xref:Microsoft.PowerShell.Utility.Format-Table).</span></span>

```powershell
$Parms = @{
  Path = "$PSHOME\*Format.ps1xml"
  Pattern = "System.IO.DirectoryInfo"
}
Select-String @Parms
Copy-Item $PSHome\FileSystem.format.ps1xml .\MyFileSystem.Format.ps1xml
Update-FormatData -PrependPath $PSHOME\Format\MyFileSystem.Format.ps1xml
```

> [!NOTE]
> <span data-ttu-id="7d451-232">若要在行寬限制內容納 XML 範例，必須壓縮部分縮排，並在程式碼中使用分行符號。</span><span class="sxs-lookup"><span data-stu-id="7d451-232">To fit the XML sample within line width limitations, it was necessary to compress some indentation and use line breaks within the code.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Configuration>
    <SelectionSets>
        <SelectionSet>
            <Name>FileSystemTypes</Name>
            <Types>
                <TypeName>System.IO.DirectoryInfo</TypeName>
                <TypeName>System.IO.FileInfo</TypeName>
            </Types>
        </SelectionSet>
    </SelectionSets>
<Controls>
<Control>
<Name>FileSystemTypes-GroupingFormat</Name>
<CustomControl>
 <CustomEntries>
  <CustomEntry>
    <CustomItem>
    <Frame>
    <LeftIndent>4</LeftIndent>
    <CustomItem>
    <Text AssemblyName="System.Management.Automation"
    BaseName="FileSystemProviderStrings"
    ResourceId="DirectoryDisplayGrouping"/>
    <ExpressionBinding>
     <ScriptBlock>
      $_.PSParentPath.Replace("Microsoft.PowerShell.Core\FileSystem::", "")
     </ScriptBlock>
    </ExpressionBinding>
    <NewLine/>
    </CustomItem>
    </Frame>
    </CustomItem>
    </CustomEntry>
 </CustomEntries>
</CustomControl>
</Control>
</Controls>
<ViewDefinitions>
    <View>
    <Name>mygciview</Name>
    <ViewSelectedBy>
        <SelectionSetName>FileSystemTypes</SelectionSetName>
    </ViewSelectedBy>
    <GroupBy>
      <PropertyName>PSParentPath</PropertyName>
      <CustomControlName>FileSystemTypes-GroupingFormat</CustomControlName>
    </GroupBy>
        <TableControl>
            <TableHeaders>
                <TableColumnHeader>
                    <Label>Mode</Label>
                    <Width>7</Width>
                    <Alignment>left</Alignment>
                </TableColumnHeader>
                <TableColumnHeader>
                    <Label>LastWriteTime</Label>
                    <Width>25</Width>
                    <Alignment>right</Alignment>
                </TableColumnHeader>
                <TableColumnHeader>
                    <Label>CreationTime</Label>
                    <Width>25</Width>
                    <Alignment>right</Alignment>
                </TableColumnHeader>
                <TableColumnHeader>
                    <Label>Length</Label>
                    <Width>14</Width>
                    <Alignment>right</Alignment>
                </TableColumnHeader>
                <TableColumnHeader/>
            </TableHeaders>
            <TableRowEntries>
                <TableRowEntry>
                    <Wrap/>
                    <TableColumnItems>
                        <TableColumnItem>
                            <PropertyName>Mode</PropertyName>
                        </TableColumnItem>
                        <TableColumnItem>
                            <ScriptBlock>
                                [String]::Format("{0,10}  {1,8}",
                                    $_.LastWriteTime.ToString("d"),
                                    $_.LastWriteTime.ToString("t"))
                            </ScriptBlock>
                        </TableColumnItem>
                        <TableColumnItem>
                            <ScriptBlock>
                                [String]::Format("{0,10}  {1,8}",
                                    $_.CreationTime.ToString("d"),
                                    $_.LastWriteTime.ToString("t"))
                            </ScriptBlock>
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

## <a name="see-also"></a><span data-ttu-id="7d451-233">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d451-233">See also</span></span>

[<span data-ttu-id="7d451-234">Export-FormatData</span><span class="sxs-lookup"><span data-stu-id="7d451-234">Export-FormatData</span></span>](xref:Microsoft.PowerShell.Utility.Export-FormatData)

[<span data-ttu-id="7d451-235">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="7d451-235">Get-FormatData</span></span>](xref:Microsoft.PowerShell.Utility.Get-FormatData)

[<span data-ttu-id="7d451-236">Get-TraceSource</span><span class="sxs-lookup"><span data-stu-id="7d451-236">Get-TraceSource</span></span>](xref:Microsoft.PowerShell.Utility.Get-TraceSource)

[<span data-ttu-id="7d451-237">格式結構描述 XML 參考</span><span class="sxs-lookup"><span data-stu-id="7d451-237">Format Schema XML Reference</span></span>](/powershell/scripting/developer/format/format-schema-xml-reference)

[<span data-ttu-id="7d451-238">Trace-Command</span><span class="sxs-lookup"><span data-stu-id="7d451-238">Trace-Command</span></span>](xref:Microsoft.PowerShell.Utility.Trace-Command)

[<span data-ttu-id="7d451-239">Update-FormatData</span><span class="sxs-lookup"><span data-stu-id="7d451-239">Update-FormatData</span></span>](xref:Microsoft.PowerShell.Utility.Update-FormatData)

[<span data-ttu-id="7d451-240">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="7d451-240">Writing a PowerShell Formatting File</span></span>](/powershell/scripting/developer/format/writing-a-powershell-formatting-file)
