---
ms.date: 09/13/2016
ms.topic: reference
title: 格式設定檔案概觀
description: 格式設定檔案概觀
ms.openlocfilehash: b86119c304c895ec08ac67de693b3a052bc7a2a0
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667822"
---
# <a name="formatting-file-overview"></a>格式設定檔案概觀

命令所傳回之物件的顯示格式 (Cmdlet、函式和腳本) 是使用 ( # B0 xml 檔案) 的格式檔案來定義。 PowerShell 會提供這些檔案中的數個，以定義由 PowerShell 所提供命令所傳回之物件的顯示格式，例如 Cmdlet 所傳回的[system.object （Process](/dotnet/api/System.Diagnostics.Process) ）物件。 `Get-Process` 不過，您也可以建立自己的自訂格式檔案來覆寫預設顯示格式，也可以撰寫自訂格式檔案來定義您自己的命令所傳回的物件顯示。

> [!IMPORTANT]
> 格式化檔案不會決定傳回至管線的物件元素。 當物件傳回至管線時，該物件的所有成員即使沒有顯示，也可以使用。

PowerShell 會使用這些格式設定檔案中的資料來判斷所顯示的內容，以及如何格式化顯示的資料。 顯示的資料可以包含物件的屬性或腳本的值。 如果您想要顯示一些無法直接從物件的屬性中使用的值，例如加入物件的兩個屬性值，然後將總和顯示為數據片段，則會使用腳本。 您可以藉由定義要顯示之物件的視圖，來格式化顯示的資料。 您可以為每個物件定義單一視圖，您可以為多個物件定義單一視圖，也可以為相同的物件定義多個視圖。 您可以定義的視圖數目沒有任何限制。

## <a name="common-features-of-formatting-files"></a>格式化檔案的一般功能

每個格式化檔案都可以定義下列元件，這些元件可以跨檔案定義的所有視圖共用：

- 預設設定，例如，如果資料的長度超過資料行的寬度，則資料列中顯示的資料是否會顯示在下一行。 如需這些設定的詳細資訊，請參閱 [定義一般設定](./defining-common-configuration-features.md)。

- 物件的集合，可由格式化檔案的任何視圖顯示。 如需這些集合的詳細資訊 (稱為 *選取範圍*) ，請參閱 [定義物件集](./defining-selection-sets.md)。

- 格式化檔案的所有視圖都可使用的通用控制項。 控制項可讓您更精確地控制資料的顯示方式。 如需控制項的詳細資訊，請參閱 [定義自訂控制項](./creating-custom-controls.md)。

## <a name="formatting-views"></a>格式化視圖

格式化視圖可以用表格格式、清單格式、寬格式和自訂格式來顯示物件。 在大部分的情況下，每個格式化定義都是由一組描述視圖的 XML 標記所描述。 每個視圖都包含視圖的名稱、使用視圖的物件以及視圖的元素，例如資料表視圖的資料行和資料列資訊。

資料表視圖會列出一或多個資料行中物件或腳本區塊值的屬性。 每個資料行都代表物件或腳本值的單一屬性。 您可以定義資料表視圖，以顯示物件的所有屬性、物件的屬性子集，或屬性和腳本值的組合。 資料表的每個資料列都代表一個傳回的物件。 建立資料表視圖非常類似于當您使用管線將物件傳送至 `Format-Table` Cmdlet。 如需此視圖的詳細資訊，請參閱 [表格視圖](./creating-a-table-view.md)。

清單視圖會列出物件的屬性，或是單一資料行中的腳本值。 清單中的每個資料列都會顯示選用的標籤，或屬性名稱後面接著屬性或腳本的值。 建立清單視圖非常類似于使用管線將物件傳送至 `Format-List` Cmdlet。 如需此視圖的詳細資訊，請參閱 [清單視圖](./creating-a-list-view.md)。

寬型視圖會列出一個或多個資料行中物件或腳本值的單一屬性。 此視圖沒有標籤或標頭。 建立廣泛的視圖非常類似于將物件輸送至 `Format-Wide` Cmdlet。 如需此視圖的詳細資訊，請參閱 [Wide view](./creating-a-wide-view.md)。

自訂視圖會顯示物件屬性或腳本值的可自訂視圖，這些值不會遵守資料表視圖、清單視圖或寬視圖的固定結構。 您可以定義獨立的自訂視圖，也可以定義另一個視圖所使用的自訂視圖，例如資料表視圖或清單視圖。 建立自訂的視圖非常類似于使用管線將物件傳送至 `Format-Custom` Cmdlet。 如需此視圖的詳細資訊，請參閱 [自訂視圖](./creating-custom-controls.md)。

## <a name="components-of-a-view"></a>視圖的元件

下列 XML 範例顯示視圖的基本 XML 元件。 個別的 XML 元素會根據您想要建立的視圖而有所不同，但視圖的基本元件全都相同。

首先，每個視圖都有一個專案 `Name` ，可指定用來參考視圖的使用者易記名稱。 專案， `ViewSelectedBy` 定義要由視圖顯示的 .net 物件，以及定義此視圖的 *控制項* 元素。

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

在控制項專案中，您可以定義一個或多個 *entry 專案* 。 如果您使用多個定義，您必須指定要使用每個定義的 .NET 物件。 每個控制項通常都只需要一個專案，只有一個定義。

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

在視圖的每個專案專案內，您可以指定 *專案專案* ，以定義該視圖所顯示的 .net 屬性或腳本。

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

如先前的範例所示，格式化檔案可以包含多個視圖、一個 view 可以包含多個定義，而且每個定義都可以包含多個專案。

## <a name="example-of-a-table-view"></a>資料表視圖的範例

下列範例顯示用來定義資料表視圖的 XML 標記，其中包含兩個數據行。 [ViewDefinitions](./viewdefinitions-element-format.md)元素是格式化檔案中定義之所有視圖的容器元素。 [View](./view-element-format.md)元素會定義特定的資料表、清單、寬或自訂視圖。 在每個 [view](./view-element-format.md) 專案中， [Name](./name-element-for-view-format.md) 元素會指定視圖的名稱、 [ViewSelectedBy](./viewselectedby-element-format.md) 元素會定義使用 view 的物件，而不同的控制項元素 (例如 `TableControl` 下列範例中所示的元素) 定義視圖的型別。

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

## <a name="see-also"></a>另請參閱

[建立清單檢視](./creating-a-list-view.md)

[建立表格檢視](./creating-a-table-view.md)

[建立寬型檢視](./creating-a-wide-view.md)

[建立自訂控制項](./creating-custom-controls.md)

[撰寫 PowerShell 格式化和類型檔案](./writing-a-powershell-formatting-file.md)
