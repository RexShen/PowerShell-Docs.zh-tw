---
title: 格式化檔案總覽 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe888fee-1fe9-459f-9d62-35732c19a7f8
caps.latest.revision: 13
ms.openlocfilehash: d418cff70c1197aa3c331eed909f49198da139e9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363687"
---
# <a name="formatting-file-overview"></a>格式設定檔案概觀

命令（Cmdlet、函式和腳本）所傳回之物件的顯示格式是使用格式檔案（types.ps1xml 檔案）所定義。 PowerShell 會提供這些檔案中的幾個，以定義 PowerShell 提供的命令所傳回之物件的顯示格式，例如 `Get-Process` Cmdlet 所傳回的[system.object](/dotnet/api/System.Diagnostics.Process)物件。 不過，您也可以建立自己的自訂格式檔案來覆寫預設的顯示格式，或者您也可以撰寫自訂格式檔案，以定義您自己的命令所傳回的物件顯示。

> [!IMPORTANT]
> 格式化檔案不會判斷傳回給管線之物件的元素。 當物件傳回至管線時，即使部分不會顯示，該物件的所有成員都可供使用。

PowerShell 會使用這些格式檔案中的資料來決定要顯示的內容，以及如何格式化顯示的資料。 顯示的資料可以包含物件的屬性或腳本的值。 如果您想要顯示無法直接從物件的屬性取得的某個值，例如加入物件的兩個屬性值，然後將總和顯示為數據片段，則會使用腳本。 藉由定義要顯示之物件的視圖，即可完成所顯示資料的格式設定。 您可以為每個物件定義單一視圖，您可以為多個物件定義單一視圖，也可以為相同的物件定義多個視圖。 您可以定義的視圖數目沒有限制。

## <a name="common-features-of-formatting-files"></a>格式化檔案的一般功能

每個格式化檔案都可以定義下列元件，這些元件可以在檔案所定義的所有視圖之間共用：

- 預設設定，例如，資料表資料列中所顯示的資料是否會顯示在下一行（如果資料長度超過資料行的寬度）。 如需這些設定的詳細資訊，請參閱[定義一般設定](./defining-common-configuration-features.md)。

- 一組物件，可由格式化檔案的任何一種視圖顯示。 如需這些集合（稱為*選擇集*）的詳細資訊，請參閱[定義物件集合](./defining-selection-sets.md)。

- 可供格式檔案的所有視圖使用的通用控制項。 控制項可讓您更精確地控制資料的顯示方式。 如需控制項的詳細資訊，請參閱[定義自訂控制項](./creating-custom-controls.md)。

## <a name="formatting-views"></a>格式化視圖

格式化視圖可以使用表格格式、清單格式、寬格式和自訂格式來顯示物件。 在大部分的情況下，每個格式定義都是由一組描述此視圖的 XML 標記所描述。 每個視圖都會包含視圖的名稱、使用此視圖的物件，以及視圖的元素，例如資料表視圖的資料行和資料列資訊。

資料表視圖會列出一個或多個資料行中物件或腳本區塊值的屬性。 每個資料行都代表物件的單一屬性或腳本值。 您可以定義資料表視圖，以顯示物件的所有屬性、物件屬性的子集，或是屬性和腳本值的組合。 資料表的每個資料列都代表一個傳回的物件。 當您使用管線將物件傳送至 `Format-Table` Cmdlet 時，建立資料表視圖非常類似。 如需此視圖的詳細資訊，請參閱[資料表視圖](./creating-a-table-view.md)。

清單視圖會列出物件的屬性或單一資料行中的腳本值。 清單的每個資料列都會顯示選擇性標籤或屬性名稱，後面接著屬性或腳本的值。 建立清單視圖非常類似于使用管線將物件傳送至 `Format-List` Cmdlet。 如需此視圖的詳細資訊，請參閱[清單視圖](./creating-a-list-view.md)。

寬型視圖會列出物件的單一屬性或一或多個資料行中的腳本值。 沒有此視圖的標籤或標頭。 建立寬視圖非常類似于使用管線將物件傳送至 `Format-Wide` Cmdlet。 如需此視圖的詳細資訊，請參閱[Wide view](./creating-a-wide-view.md)。

[自訂視圖] 會顯示物件屬性或腳本值的可自訂視圖，而不會遵守資料表視圖、清單視圖或寬視圖的嚴格結構。 您可以定義獨立的自訂視圖，也可以定義另一個視圖所使用的自訂視圖，例如資料表視圖或清單視圖。 建立自訂視圖非常類似于使用管線將物件傳送至 `Format-Custom` Cmdlet。 如需此視圖的詳細資訊，請參閱[自訂視圖](./creating-custom-controls.md)。

## <a name="components-of-a-view"></a>視圖的元件

下列 XML 範例顯示視圖的基本 XML 元件。 個別的 XML 元素會根據您要建立的視圖而有所不同，但 views 的基本元件全都相同。

一開始，每個 view 都有一個 `Name` 元素，可指定用來參考此視圖的使用者易記名稱。 `ViewSelectedBy` 元素，定義要由視圖顯示的 .NET 物件，以及定義視圖的*控制項*元素。

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

在 control 元素內，您可以定義一個或多個*entry*元素。 如果您使用多個定義，則必須指定要使用每個定義的 .NET 物件。 每個控制項通常只需要一個只有一個定義的專案。

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

在 view 的每個 entry 元素內，您可以指定*專案*元素，以定義該視圖所顯示的 .net 屬性或腳本。

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

如先前範例所示，格式檔案可以包含多個視圖、一個 view 可以包含多個定義，而且每個定義都可以包含多個專案。

## <a name="example-of-a-table-view"></a>資料表視圖的範例

下列範例顯示用來定義包含兩個數據行之資料表視圖的 XML 標記。 [ViewDefinitions](./viewdefinitions-element-format.md)元素是格式檔案中定義之所有視圖的容器元素。 [View](./view-element-format.md)元素會定義特定的資料表、清單、寬型或自訂視圖。 在每個[view](./view-element-format.md)元素內， [name](./name-element-for-view-format.md)元素會指定視圖的名稱， [ViewSelectedBy](./viewselectedby-element-format.md)元素會定義使用 view 的物件，以及不同的控制項專案（例如下列專案中顯示的 `TableControl` 元素）。範例）定義視圖的類型。

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

[建立清單視圖](./creating-a-list-view.md)

[建立資料表視圖](./creating-a-table-view.md)

[建立寬型視圖](./creating-a-wide-view.md)

[建立自訂控制項](./creating-custom-controls.md)

[撰寫 PowerShell 格式化和類型檔案](./writing-a-powershell-formatting-file.md)
