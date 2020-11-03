---
description: 從 PowerShell 6 開始，會在 PowerShell 原始程式碼中定義物件的預設視圖。  您可以建立自己的檔案 `Format.ps1xml` 來變更物件的顯示方式，或針對您在 PowerShell 中建立的新物件類型定義預設顯示。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_format.ps1xml?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Format.ps1xml
ms.openlocfilehash: bbe7c9d2d36673ff6240be89f9ceb439ab0d0dfa
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207103"
---
# <a name="about-formatps1xml"></a>關於 Format.ps1xml

## <a name="short-description"></a>簡短描述

從 PowerShell 6 開始，會在 PowerShell 原始程式碼中定義物件的預設視圖。

您可以建立自己的檔案 `Format.ps1xml` 來變更物件的顯示方式，或針對您在 PowerShell 中建立的新物件類型定義預設顯示。

## <a name="long-description"></a>完整描述

從 PowerShell 6 開始，預設的視圖會定義于 PowerShell 原始程式碼中。 Powershell `Format.ps1xml` 5.1 與較舊版本中的檔案不存在於 powershell 6 和更新版本中。

PowerShell 原始程式碼會定義 PowerShell 主控台中物件的預設顯示。 您可以建立自己的檔案 `Format.ps1xml` 來變更物件的顯示方式，或針對您在 PowerShell 中建立的新物件類型定義預設顯示。

當 PowerShell 顯示物件時，它會使用結構化格式設定檔案中的資料來判斷物件的預設顯示。 格式檔案中的資料會決定物件是轉譯在資料表或清單中，而且會決定預設會顯示哪些屬性。

格式只會影響顯示。 它不會影響在管線或傳遞的物件屬性。 `Format.ps1xml` 檔案不能用來自訂雜湊表的輸出格式。

`.ps1xml`格式化檔案可以為每個物件定義四個不同的視圖：

- Table
- 清單
- 寬
- Custom

例如，將命令的輸出 `Get-ChildItem` 輸送至 `Format-List` 命令時，會使用在 `Format-List` 原始程式碼中定義的清單視圖，以決定如何將檔案和資料夾物件顯示為清單。

當格式化檔案包含一個以上的物件檢視時，PowerShell 會套用它所找到的第一個視圖。

在自訂檔案中 `Format.ps1xml` ，view 是由一組 XML 標記所定義，這些標籤會描述視圖的名稱、可套用它的物件類型、資料行標頭，以及顯示在視圖主體中的屬性。 檔案中的格式 `Format.ps1xml` 會在將資料呈現給使用者之前套用。

## <a name="creating-new-formatps1xml-files"></a>建立新的 Format.ps1xml 檔案

若要變更現有物件檢視的顯示格式，或加入新物件的視圖，請建立您自己的檔案 `Format.ps1xml` ，然後將它們新增至您的 PowerShell 會話。

若要建立檔案 `Format.ps1xml` 來定義自訂視圖，請使用 [FormatData](xref:Microsoft.PowerShell.Utility.Get-FormatData) 和 [Export-FormatData](xref:Microsoft.PowerShell.Utility.Export-FormatData) Cmdlet。 使用文字編輯器來編輯檔案。 檔案可以儲存至 PowerShell 可存取的任何目錄，例如的子目錄 `$HOME` 。

若要變更目前視圖的格式，請在格式化檔案中找出視圖，然後使用這些標記來變更視圖。 若要建立新物件類型的視圖，請建立新的視圖，或使用現有的 view 做為模型。 下一節將說明這些標記。 然後，您可以刪除檔案中的所有其他視圖，讓任何人都能清楚變更檢查檔案的方式。

儲存變更之後，請使用 [FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData) 將新檔案新增至您的 PowerShell 會話。 如果您想要讓您的視圖優先于內建檔案中所定義的視圖，請使用 **PrependPath** 參數。 `Update-FormatData` 只會影響目前的會話。 若要對所有未來的會話進行變更，請將 `Update-FormatData` 命令新增至您的 PowerShell 設定檔。

### <a name="example-add-calendar-data-to-culture-objects"></a>範例：將行事歷數據加入至文化特性物件

此範例示範如何在目前的 PowerShell 會話中，變更 Cmdlet 所產生之文化特性物件的格式 **。** `Get-Culture` 範例中的命令會將行事 **曆** 屬性新增至文化特性物件的預設資料表視圖顯示。

首先，從原始程式碼檔取得格式資料，然後建立 `Format.ps1xml` 包含文化特性物件目前觀點的檔案。

```powershell
Get-FormatData -TypeName System.Globalization.CultureInfo |
  Export-FormatData -Path $HOME\Format\CultureInfo.Format.ps1xml
```

`CultureInfo.Format.ps1xml`在任何 XML 或文字編輯器中開啟檔案，例如 Visual Studio Code。 下列 XML 會定義 **CultureInfo** 物件的視圖。

檔案 `CultureInfo.Format.ps1xml` 看起來應該如下列範例所示：

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

藉由新增一組新的標記，為行事 **曆** 屬性建立新的資料行 `<TableColumnHeader>` 。 行事 **曆** 屬性的值可能很長，因此請將45個字元的值指定為 `<Width>` 。

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

使用和標記，在資料表資料列中加入行事 **曆** 的新資料行專案 `<TableColumnItem>` `<PropertyName` ：

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

儲存並關閉檔案。 使用將 `Update-FormatData` 新的格式檔案新增至目前的 PowerShell 會話。

這個範例會使用 **PrependPath** 參數，將新的檔案以比原始檔案更高的優先順序來放置。 如需詳細資訊，請參閱 [FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData)。

```powershell
Update-FormatData -PrependPath $HOME\Format\CultureInfo.Format.ps1xml
```

若要測試變更，請輸入 `Get-Culture` 並檢查包含行事 **曆** 屬性的輸出。

```powershell
Get-Culture
```

```Output
LCID  Name   Calendar                                DisplayName
----  ----   --------                                -----------
1033  en-US  System.Globalization.GregorianCalendar  English (United States)
```

## <a name="the-xml-in-formatps1xml-files"></a>Format.ps1xml 檔案中的 XML

您可以在 GitHub 上的 PowerShell 原始程式碼存放庫中，以 [.Xsd 格式](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Format.xsd) 找到完整的架構定義。

每個檔案的 **ViewDefinitions** 區段 `Format.ps1xml` 包含 `<View>` 定義每個視圖的標記。 典型的 `<View>` 標記包含下列標記：

- `<Name>` 識別視圖的名稱。
- `<ViewSelectedBy>` 指定要套用視圖的物件類型或類型。
- `<GroupBy>` 指定如何將視圖中的專案結合在群組中。
- `<TableControl>`、 `<ListControl>` 、 `<WideControl>` 和 `<CustomControl>` 包含指定每個專案的顯示方式的標記。

### <a name="viewselectedby-tag"></a>ViewSelectedBy 標記

`<ViewSelectedBy>`標記可包含 `<TypeName>` 適用于此視圖之每個物件類型的標記。 或者，它可以包含一個 `<SelectionSetName>` 標記，參考使用標記在其他地方定義的選取集合 `<SelectionSet>` 。

### <a name="groupby-tag"></a>GroupBy 標記

`<GroupBy>`標記包含一個 `<PropertyName>` 標記，可指定要用來分組專案的物件屬性。 它也包含一個 `<Label>` 標記，可指定要當做每個群組的標籤使用的字串，或 `<CustomControlName>` 參考使用標記在其他位置定義的自訂控制項的標記 `<Control>` 。 `<Control>`標記包含 `<Name>` 標記和 `<CustomControl>` 標記。

### <a name="tablecontroltag"></a>TableControlTag

`<TableControl>`標記通常包含 `<TableHeaders>` `<TableRowEntries>` 定義資料表標頭和資料列之格式的和標記。 `<TableHeaders>`標記通常會包含 `<TableColumnHeader>` 包含 `<Label>` 、 `<Width>` 和標記的標記 `<Alignment>` 。 `<TableRowEntries>`標記包含 `<TableRowEntry>` 資料表中每個資料列的標記。 `<TableRowEntry>`標記包含一個 `<TableColumnItems>` 標記，其中包含資料 `<TableColumnItem>` 列中每個資料行的標記。 通常， `<TableColumnItem>` 標記包含的標記會 `<PropertyName>` 識別要顯示在定義位置中的物件屬性，或是包含 `<ScriptBlock>` 腳本的標記，此標記會計算要顯示在位置中的結果。

> [!NOTE]
> 您也可以在其他地方，將腳本區塊用於計算結果可能很有用的位置。

`<TableColumnItem>`標記也可以包含 `<FormatString>` 指定如何顯示內容或計算結果的標記。

### <a name="listcontrol-tag"></a>ListControl 標記

`<ListControl>`標記通常會包含 `<ListEntries>` 標記。 `<ListEntries>`標記包含 `<ListEntry>` 標記。 `<ListEntry>`標記包含 `<ListItems>` 標記。 `<ListItems>`標記包含 `<ListItem>` 包含標記的標記 `<PropertyName>` 。 `<PropertyName>`標記會指定要顯示在清單中指定位置的物件屬性。 如果使用選取集來定義視圖選取範圍， `<ListControl>` 和 `<ListEntry>` 標記也可以包含 `<EntrySelectedBy>` 包含一或多個標記的標記 `<TypeName>` 。 這些 `<TypeName>` 標記 `<ListControl>` 會指定標記要顯示的物件類型。

### <a name="widecontrol-tag"></a>WideControl 標記

`<WideControl>`標記通常會包含 `<WideEntries>` 標記。 `<WideEntries>`標記包含一或多個 `<WideEntry>` 標記。 `<WideEntry>`標記通常包含一個 `<PropertyName>` 標記，可指定要在視圖中指定位置顯示的屬性。 `<PropertyName>`標記可以包含 `<FormatString>` 指定如何顯示內容的標記。

### <a name="customcontrol-tag"></a>CustomControl 標記

`<CustomControl>`標記可讓您使用腳本區塊來定義格式。 `<CustomControl>`標記通常包含一個 `<CustomEntries>` 包含多個標記的標記 `<CustomEntry>` 。 每個 `<CustomEntry>` 標記都包含一個 `<CustomItem>` 標記，其中可包含各種標記，以指定在視圖中指定位置的內容和格式，包括 `<Text>` 、 `<Indentation>` 、 `<ExpressionBinding>` 和 `<NewLine>` 標記。

## <a name="tracing-formatps1xml-file-use"></a>追蹤 Format.ps1xml 檔案使用

若要偵測檔案載入或應用程式中的錯誤 `Format.ps1xml` ，請使用 `Trace-Command` Cmdlet 搭配下列任何格式元件做為 **Name** 參數的值：

- FormatFileLoading
- FormatViewBinding

如需詳細資訊，請參閱 [追蹤命令](xref:Microsoft.PowerShell.Utility.Trace-Command) 和 [TraceSource](xref:Microsoft.PowerShell.Utility.Get-TraceSource)。

## <a name="signing-a-formatps1xml-file"></a>簽署 Format.ps1xml 檔案

若要保護檔案的使用者 `Format.ps1xml` ，請使用數位簽章來簽署檔案。 如需詳細資訊，請參閱 [about_Signing](about_Signing.md)。

## <a name="sample-xml-for-a-format-table-custom-view"></a>Format-Table 自訂視圖的範例 XML

下列 XML 範例會 `Format-Table` 為所建立的 **DirectoryInfo** 和 **FileInfo** 物件建立自訂的視圖 `Get-ChildItem` 。 自訂視圖會命名為 **mygciview** ，並將 **CreationTime** 資料行加入至資料表。

若要建立自訂視圖，請使用 `Get-FormatData` 和 `Export-FormatData` Cmdlet 來產生檔案 `.ps1xml` 。 然後，編輯您的檔案， `.ps1xml` 以建立自訂視圖的程式碼。 檔案 `.ps1xml` 可以儲存在任何 PowerShell 可以存取的目錄中。 例如，的子目錄 `$HOME` 。

建立檔案之後 `.ps1xml` ，請使用 Cmdlet 將 `Update-FormatData` 視圖包含在目前的 PowerShell 會話中。 或者，如果您需要所有 PowerShell 會話都有可用的 view，請將 update 命令新增至您的 PowerShell 設定檔。

在此範例中，自訂視圖必須使用表格格式，否則 `Format-Table` 會失敗。

使用 `Format-Table` **View** 參數可指定自訂視圖的名稱、 **Mygciview** ，以及使用 **CreationTime** 資料行來格式化資料表的輸出。 如需如何執行命令的範例，請參閱 [格式化資料表](xref:Microsoft.PowerShell.Utility.Format-Table)。

> [!NOTE]
> 雖然您可以從原始程式碼取得格式化 XML 來建立自訂視圖，但可能需要進行更多的開發以取得所需的結果。

在下列 `Get-FormatData` 命令中，有一個 **PowerShellVersion** 參數的替代方法，以確保傳回所有的本機格式化資訊。 使用 `-PowerShellVersion $PSVersionTable.PSVersion` 而不是特定的 PowerShell 版本。

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

## <a name="see-also"></a>另請參閱

[Export-FormatData](xref:Microsoft.PowerShell.Utility.Export-FormatData)

[Get-FormatData](xref:Microsoft.PowerShell.Utility.Get-FormatData)

[Get-TraceSource](xref:Microsoft.PowerShell.Utility.Get-TraceSource)

[格式結構描述 XML 參考](/powershell/scripting/developer/format/format-schema-xml-reference)

[Trace-Command](xref:Microsoft.PowerShell.Utility.Trace-Command)

[Update-FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData)

[撰寫 PowerShell 格式設定檔案](/powershell/scripting/developer/format/writing-a-powershell-formatting-file)
