---
title: 建立資料表檢視 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1f405afb-70b5-4fe0-9986-bc07401d93fd
caps.latest.revision: 23
ms.openlocfilehash: 862f942facafff6cea66c4f8f1040772c6a62ec3
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057360"
---
# <a name="creating-a-table-view"></a>建立表格檢視

資料表檢視中一或多個資料行中顯示資料。 在資料表中的每個資料列代表.NET 物件，而資料表的每個資料行表示的物件或指令碼值的屬性。 您可以定義會顯示物件的所有屬性或物件的屬性子集的資料表檢視。

## <a name="a-table-view-display"></a>資料表檢視顯示

下列範例會示範 Windows PowerShell 的會顯示[System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)所傳回的物件[Get-service](/powershell/module/microsoft.powershell.management/get-service) cmdlet。 此物件中，Windows PowerShell 已定義顯示的資料表檢視`Status`屬性，`Name`屬性 (此屬性是別名屬性`ServiceName`屬性)，和`DisplayName`屬性。 在資料表中的每個資料列代表 cmdlet 傳回的物件。

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a>定義資料表檢視

下列 XML 顯示的資料表檢視結構描述顯示[System.Serviceprocess.Servicecontroller 嗎？Displayproperty = Fullname>](/dotnet/api/System.ServiceProcess.ServiceController)物件。 您必須指定您想要在資料表檢視中顯示每個屬性。

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

下列 XML 元素用來定義清單檢視：

- [檢視](./view-element-format.md)項目是 [資料表] 檢視的父項目。 （這是針對清單中，，和自訂的控制項檢視相同的父項目）。

- [名稱](./name-element-for-view-format.md)項目會指定檢視的名稱。 所有檢視需要此項目。

- [ViewSelectedBy](./viewselectedby-element-format.md)項目會定義使用檢視的物件。 需要此項目。

- [GroupBy](./groupby-element-for-view-format.md) （未顯示在此範例中） 的項目會定義當物件的新群組就會顯示。 每次特定的屬性或指令碼的值變更時，會啟動新的群組。 這是選擇性元素。

- [控制項](./controls-element-for-view-format.md)（未顯示在此範例中） 的項目會定義由 [資料表] 檢視所定義的自訂控制項。 控制項可讓您進一步指定 顯示資料的方式。 這是選擇性元素。 檢視可以定義自己的自訂控制項，或可以使用通用控制項，可供任何檢視中的格式化檔案。 如需有關自訂控制項的詳細資訊，請參閱 <<c0> [ 建立自訂控制項](./creating-custom-controls.md)。

- [HideTableHeaders](./hidetableheaders-element-format.md)項目 （不在此範例中顯示） 可讓您指定的資料表不會顯示在資料表頂端的任何標籤。 這是選擇性元素。

- [TableControl](./tablecontrol-element-format.md)項目，定義的標頭和資料列資訊的資料表。 類似於其他所有的檢視，[資料表] 檢視可以顯示指令碼所產生的值或物件屬性的值。

## <a name="defining-column-headers"></a>定義資料行標頭

1. [TableHeaders](./tableheaders-element-format.md)項目和其子項目會定義在資料表頂端顯示的內容。

2. [TableColumnHeader](./tablecolumnheader-element-format.md)項目會定義在資料表資料行的頂端顯示的內容。 您想要顯示的標頭的順序指定這些項目。

   您可以使用，這些項目數目，但數目沒有限制[TableColumnHeader](./tablecolumnheader-element-format.md)在資料表檢視中的項目必須等於數目[TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)您所使用的項目。

3. [標籤](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)項目會指定所顯示的文字。 這是選擇性元素。

4. [寬度](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)項目會指定資料行的寬度 （以字元為單位）。 這是選擇性元素。

5. [對齊](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)項目可讓您指定標籤的顯示方式。 標籤可以是靠左、 右邊，對齊或置中對齊。 這是選擇性元素。

## <a name="defining-the-table-rows"></a>定義資料表的資料列

資料表檢視可以提供一或多個指定哪些資料時，會顯示在資料表的資料列上，使用的子元素的定義[TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md)項目。 請注意，您可以指定多個定義的資料列的資料表，但標頭資料列維持不變，不論使用何種資料列定義。 一般而言，資料表必須只有一個定義。

在下列範例中，此檢視會提供顯示的數個屬性的值的單一定義[System.Diagnostics.Process 嗎？Displayproperty = Fullname>](/dotnet/api/System.Diagnostics.Process)物件。 資料表檢視，可以顯示屬性的值或指令碼 （未顯示在範例中） 的值，其資料列中。

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

下列的 XML 項目可以用來提供資料列的定義中：

- [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md)元素和其子項目會定義資料表的資料列中顯示的內容。

- [TableRowEntry](./listentry-element-for-listcontrol-format.md)項目提供的資料列的定義。 至少一個[TableRowEntry](./listentry-element-for-listcontrol-format.md)是必要項; 不過，還有您可以新增的項目數沒有上限限制。 在大部分情況下，檢視必須只有一個定義。

- [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)項目會指定特定的定義所顯示的物件。 這個項目是選擇性的只有在您定義多個時，才需要[TableRowEntry](./listentry-element-for-listcontrol-format.md)顯示不同的物件項目。

- [包裝](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)項目會指定超過欄寬度的文字會顯示在下一行。 根據預設，系統會截斷超過欄寬度的文字。

- [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)項目定義的屬性或其值會顯示資料列中的指令碼。

- [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)項目定義之屬性或其值會顯示在資料列的資料行的指令碼。 A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) ，則需要每個資料行的資料列元素。 第一個項目會顯示在第一個資料行，第二個項目，在第二個資料行，依此類推。

- [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)項目會指定資料列中顯示其值的屬性。 您必須指定屬性或指令碼，但您無法同時指定。

- [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)項目會指定其值會顯示資料列中的指令碼。 您必須指定指令碼或屬性，但您無法同時指定。

- [FormatString](./label-element-for-listitem-for-listcontrol-format.md)項目會指定定義的屬性或指令碼的值的顯示方式的格式模式。 這是選擇性元素。

- [對齊](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)項目可讓您指定的指令碼的屬性值的顯示方式。 值可以靠左，向右對齊或置中對齊。 這是選擇性元素。

## <a name="defining-the-objects-that-use-the-table-view"></a>定義使用 [資料表] 檢視的物件

有兩種方式可定義的.NET 物件會使用 [資料表] 檢視。 您可以使用[ViewSelectedBy](./viewselectedby-element-format.md)項目來定義可顯示的檢視，或您的所有定義的物件可以使用[EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md)項目來定義會顯示哪些物件特定檢視的定義。 在大部分情況下，檢視有只有一個定義，因此物件通常會定義所[ViewSelectedBy](./viewselectedby-element-format.md)項目。

下列範例示範如何定義會顯示資料表 檢視使用的物件[ViewSelectedBy](./viewselectedby-element-format.md)並[TypeName](./typename-element-for-viewselectedby-format.md)項目。 沒有任何限制的數目[TypeName](./typename-element-for-viewselectedby-format.md) ，您可以指定，且其順序並不重要的項目。

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

下列的 XML 項目可以用來指定物件所使用的資料表檢視中：

- [ViewSelectedBy](./viewselectedby-element-format.md)項目會定義 [清單] 檢視會顯示哪些物件。

- [TypeName](./typename-element-for-viewselectedby-format.md)項目會指定檢視所顯示的.NET 物件。 需要完整的.NET 型別名稱。 您必須指定至少一個型別或設定檢視中，選取項目，但可以指定的項目沒有最大數目。

下列範例會使用[ViewSelectedBy](./viewselectedby-element-format.md)並[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)項目。 使用選取項目集都有一組相關的物件，會顯示使用多個檢視，例如當您定義清單檢視和資料表檢視表相同的物件的位置。 如需如何建立選取項目集的詳細資訊，請參閱[定義的選取項目集](./defining-selection-sets.md)。

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

下列的 XML 項目可以用來指定物件所使用的清單檢視中：

- [ViewSelectedBy](./viewselectedby-element-format.md)項目會定義 [清單] 檢視會顯示哪些物件。

- [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)項目會指定一組可以檢視所顯示的物件。 您必須指定至少一個選取項目集或類型檢視中，但您可以指定的項目沒有最大數目。

下列範例示範如何定義顯示由特定的資料表檢視使用定義的物件[EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)項目。 您可以使用這個項目，來指定物件、 選取項目集的物件或選取條件，指定當使用定義的.NET 型別名稱。 如需如何建立選取項目條件的詳細資訊，請參閱[定義的條件，顯示資料](./defining-conditions-for-displaying-data.md)。

> [!NOTE]
> 建立多個資料表的檢視定義時，您無法指定不同的資料行標頭。 您可以指定只顯示之內容的資料表，例如哪些物件會顯示資料列。

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

下列的 XML 項目可以用來指定物件所使用的特定檢視的定義清單中：

- [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)項目會定義哪些物件會定義所顯示。

- [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md)項目會指定定義所顯示的.NET 物件。 使用這個項目，完整的.NET 型別名稱時需要。 您必須指定至少一個型別、 選取項目集或選擇條件的定義，但您可以指定的項目沒有最大數目。

- [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) （未顯示） 的項目會指定一組可顯示的這個定義的物件。 您必須指定至少一個型別、 選取項目集或選擇條件的定義，但您可以指定的項目沒有最大數目。

- [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) （未顯示） 的項目會指定要使用此定義必須存在的條件。 您必須指定至少一個型別、 選取項目集或選擇條件的定義，但您可以指定的項目沒有最大數目。 如需定義選擇條件的詳細資訊，請參閱 <<c0> [ 定義的條件，顯示資料](./defining-conditions-for-displaying-data.md)。

## <a name="using-format-strings"></a>使用格式字串

格式字串可以加入檢視，以進一步定義資料的顯示方式。 下列範例示範如何定義的格式化字串的值，`StartTime`屬性。

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

下列的 XML 項目可以用來指定之格式模式中：

- [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)項目定義之屬性或其值會顯示在資料列的資料行的指令碼。 A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) ，則需要每個資料行的資料列元素。 第一個項目會顯示在第一個資料行，第二個項目，在第二個資料行，依此類推。

- [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)項目會指定資料列中顯示其值的屬性。 您必須指定屬性或指令碼，但您無法同時指定。

- [FormatString](./label-element-for-listitem-for-listcontrol-format.md)項目會指定定義的屬性或指令碼的值的顯示方式的格式模式。

在下列範例中，`ToString`來格式化值的指令碼會呼叫方法。 指令碼可以呼叫任何方法的物件。 因此，如果物件有一個方法，例如`ToString`具有格式設定的參數，指令碼可以呼叫該方法，來設定指令碼的輸出值的格式。

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

下列的 XML 項目可以用來呼叫`ToString`方法：

- [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)項目定義之屬性或其值會顯示在資料列的資料行的指令碼。 A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) ，則需要每個資料行的資料列元素。 第一個項目會顯示在第一個資料行，第二個項目，在第二個資料行，依此類推。

- [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)項目會指定其值會顯示資料列中的指令碼。 您必須指定指令碼或屬性，但您無法同時指定。

## <a name="see-also"></a>另請參閱

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
