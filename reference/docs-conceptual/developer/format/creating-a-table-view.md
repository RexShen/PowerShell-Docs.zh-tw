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
# <a name="creating-a-table-view"></a>建立表格檢視

資料表視圖會顯示一個或多個資料行中的資料。 資料表中的每個資料列都代表一個 .NET 物件，而資料表的每個資料行都代表物件或腳本值的屬性。 您可以定義資料表視圖，以顯示物件的所有屬性或物件的屬性子集。

## <a name="a-table-view-display"></a>資料表視圖顯示

下列範例顯示 Windows PowerShell 如何顯示由[get-help](/powershell/module/microsoft.powershell.management/get-service) Cmdlet 所傳回的[system.serviceprocess.dll Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)物件。 對於此物件，Windows PowerShell 已定義顯示內容的資料表視圖 `Status` 、 `Name` 屬性 (這個屬性是屬性) 的別名屬性 `ServiceName` 和 `DisplayName` 屬性。 資料表中的每個資料列都代表 Cmdlet 所傳回的物件。

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a>定義資料表視圖

下列 XML 會顯示用來顯示 System.serviceprocess.dll. Servicecontroller 的表格視圖架構 [？Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) 物件。 您必須指定要顯示在資料表視圖中的每個屬性。

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

下列 XML 元素用來定義清單視圖：

- [View](./view-element-format.md)元素是資料表視圖的父元素。  (這是清單、寬和自訂控制項視圖的相同父元素。 ) 

- [Name](./name-element-for-view-format.md)元素會指定視圖的名稱。 所有視圖都需要這個元素。

- [ViewSelectedBy](./viewselectedby-element-format.md)元素會定義使用 view 的物件。 這個元素是必要的。

- 這個範例中未顯示的 [GroupBy](./groupby-element-for-view-format.md) 元素 () 會定義何時會顯示新的物件群組。 每當特定屬性或腳本的值變更時，就會啟動新的群組。 這是選擇性的項目。

-  (不會在此範例中顯示 [Controls](./controls-element-for-view-format.md) 元素) 定義資料表視圖所定義的自訂控制項。 控制項可讓您進一步指定顯示資料的方式。 這是選擇性的項目。 View 可以定義自己的自訂控制項，也可以使用格式檔案中任何視圖都可使用的通用控制項。 如需自訂控制項的詳細資訊，請參閱 [建立自訂控制項](./creating-custom-controls.md)。

- [HideTableHeaders](./hidetableheaders-element-format.md)元素 (不會顯示在此範例中) 指定資料表不會在資料表頂端顯示任何標籤。 這是選擇性的項目。

- [TableControl](./tablecontrol-element-format.md)元素，定義資料表的標頭和資料列資訊。 資料表視圖類似于所有其他的視圖，可顯示物件屬性的值或腳本所產生的值。

## <a name="defining-column-headers"></a>定義欄標題

1. [TableHeaders](./tableheaders-element-format.md)元素和其子項目會定義在資料表頂端顯示的專案。

2. [之 tablecolumnheader](./tablecolumnheader-element-format.md)元素會定義在資料表資料行頂端顯示的內容。 依您想要顯示標頭的順序指定這些元素。

   您可以使用的元素數目沒有限制，但資料表視圖中的 [之 tablecolumnheader](./tablecolumnheader-element-format.md) 元素數目必須等於您所使用的 [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) 元素數目。

3. [Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)元素會指定所顯示的文字。 這是選擇性的項目。

4. [Width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)元素會指定資料行的寬度 (字元) 。 這是選擇性的項目。

5. [對齊](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)元素會指定標籤的顯示方式。 標籤可以靠左、靠右或置中對齊。 這是選擇性的項目。

## <a name="defining-the-table-rows"></a>定義資料表資料列

資料表視圖可以提供一或多個定義，以使用 [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) 元素的子項目來指定要在資料表的資料列中顯示哪些資料。 請注意，您可以為資料表的資料列指定多個定義，但是資料列的標頭會維持不變，不論使用哪一種資料列定義。 通常，資料表只會有一個定義。

在下列範例中，視圖會提供單一定義，以顯示 [...] 的數個屬性值 [？Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process) 物件。 資料表視圖可以顯示內容的值或腳本的值 (不會顯示在其資料列中的範例) 。

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

下列 XML 元素可以用來提供資料列的定義：

- [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md)元素和其子項目會定義資料表的資料列中所顯示的內容。

- [TableRowEntry](./listentry-element-for-listcontrol-format.md)元素提供資料列的定義。 至少需要一個 [TableRowEntry](./listentry-element-for-listcontrol-format.md) ;不過，您可以新增的元素數目沒有最大限制。 在大部分的情況下，view 只會有一個定義。

- [之 entryselectedby](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)元素會指定特定定義所顯示的物件。 這個元素是選擇性的，只有當您定義多個顯示不同物件的 [TableRowEntry](./listentry-element-for-listcontrol-format.md) 專案時，才需要此專案。

- [Wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)元素會指定超出資料行寬度的文字會顯示在下一行。 根據預設，系統會截斷超過欄寬度的文字。

- [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)元素會定義其值會顯示在資料列中的屬性或腳本。

- [之 tablecolumnitem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)元素會定義其值會顯示在資料列的資料行中的屬性或腳本。 資料列的每個資料行都需要 [之 tablecolumnitem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) 元素。 第一個專案會顯示在第一個資料行中，第二個數據行中的第二個專案，依此類推。

- [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)元素會指定屬性，其值會顯示在資料列中。 您必須指定屬性或腳本，但不能同時指定這兩種方法。

- [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)元素會指定其值會顯示在資料列中的腳本。 您必須指定腳本或屬性，但不能同時指定兩者。

- 格式 [值元素會](./label-element-for-listitem-for-listcontrol-format.md) 指定定義屬性或腳本值顯示方式的格式模式。 這是選擇性的項目。

- [對齊](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)元素會指定屬性或腳本的值的顯示方式。 值可以靠左、靠右或置中對齊。 這是選擇性的項目。

## <a name="defining-the-objects-that-use-the-table-view"></a>定義使用資料表視圖的物件

有兩種方式可以定義要使用資料表視圖的 .NET 物件。 您可以使用 [ViewSelectedBy](./viewselectedby-element-format.md) 專案來定義可由視圖的所有定義顯示的物件，或者，您可以使用 [之 entryselectedby](./entryselectedby-element-for-listentry-for-listcontrol-format.md) 元素來定義由視圖的特定定義所顯示的物件。 在大部分的情況下，視圖只有一個定義，因此物件通常是由 [ViewSelectedBy](./viewselectedby-element-format.md) 元素定義。

下列範例示範如何使用 [ViewSelectedBy](./viewselectedby-element-format.md) 和 [TypeName](./typename-element-for-viewselectedby-format.md) 元素，定義資料表視圖所顯示的物件。 您可以指定的 [TypeName](./typename-element-for-viewselectedby-format.md) 元素數目沒有任何限制，而且其順序並不重要。

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

下列 XML 元素可以用來指定資料表視圖所使用的物件：

- [ViewSelectedBy](./viewselectedby-element-format.md)元素會定義清單視圖要顯示的物件。

- [TypeName](./typename-element-for-viewselectedby-format.md)元素會指定視圖所顯示的 .net 物件。 需要完整的 .NET 型別名稱。 您必須為此視圖指定至少一個類型或選取範圍，但無法指定的元素數目上限。

下列範例會使用 [ViewSelectedBy](./viewselectedby-element-format.md) 和 [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) 元素。 如果您有一組相關的物件會使用多個視圖顯示，例如當您針對相同物件定義清單視圖和資料表視圖時，請使用選取集。 如需有關如何建立選取範圍的詳細資訊，請參閱 [定義選取集合](./defining-selection-sets.md)。

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

下列 XML 元素可以用來指定清單視圖所使用的物件：

- [ViewSelectedBy](./viewselectedby-element-format.md)元素會定義清單視圖要顯示的物件。

- [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素會指定可供視圖顯示的一組物件。 您必須為此視圖指定至少一個選擇集或類型，但無法指定的元素數目上限。

下列範例示範如何使用 [之 entryselectedby](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) 元素定義資料表視圖的特定定義所顯示的物件。 您可以使用這個專案，指定物件的 .NET 類型名稱、一組選取的物件，或指定使用定義時指定的選取條件。 如需如何建立選取條件的詳細資訊，請參閱 [定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。

> [!NOTE]
> 當您建立資料表視圖的多個定義時，不能指定不同的資料行標題。 您只能指定顯示在資料表資料列中的內容，例如要顯示的物件。

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

下列 XML 專案可以用來指定清單視圖的特定定義所使用的物件：

- [之 entryselectedby](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)元素會定義定義所顯示的物件。

- [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md)元素會指定定義所顯示的 .net 物件。 使用這個專案時，需要完整的 .NET 型別名稱。 您必須為定義指定至少一個類型、選取集或選取條件，但無法指定的元素數目上限。

- [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)元素 (未顯示) 指定可由此定義顯示的一組物件。 您必須為定義指定至少一個類型、選取集或選取條件，但無法指定的元素數目上限。

- [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)元素 (未顯示) 指定必須存在才能使用此定義的條件。 您必須為定義指定至少一個類型、選取集或選取條件，但無法指定的元素數目上限。 如需定義選取條件的詳細資訊，請參閱 [定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。

## <a name="using-format-strings"></a>使用格式字串

您可以將字串格式設定加入至視圖，以進一步定義資料的顯示方式。 下列範例顯示如何定義屬性值的格式化字串 `StartTime` 。

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

下列 XML 元素可以用來指定格式模式：

- [之 tablecolumnitem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)元素會定義其值會顯示在資料列的資料行中的屬性或腳本。 資料列的每個資料行都需要 [之 tablecolumnitem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) 元素。 第一個專案會顯示在第一個資料行中，第二個數據行中的第二個專案，依此類推。

- [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)元素會指定屬性，其值會顯示在資料列中。 您必須指定屬性或腳本，但不能同時指定這兩種方法。

- 格式 [值元素會](./label-element-for-listitem-for-listcontrol-format.md) 指定定義屬性或腳本值顯示方式的格式模式。

在下列範例中， `ToString` 會呼叫方法來格式化腳本的值。 腳本可以呼叫物件的任何方法。 因此，如果物件具有具有格式化參數的方法（例如 `ToString` ），則腳本可以呼叫該方法來格式化腳本的輸出值。

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

下列 XML 元素可以用來呼叫 `ToString` 方法：

- [之 tablecolumnitem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)元素會定義其值會顯示在資料列的資料行中的屬性或腳本。 資料列的每個資料行都需要 [之 tablecolumnitem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) 元素。 第一個專案會顯示在第一個資料行中，第二個數據行中的第二個專案，依此類推。

- [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)元素會指定其值會顯示在資料列中的腳本。 您必須指定腳本或屬性，但不能同時指定兩者。

## <a name="see-also"></a>另請參閱

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
