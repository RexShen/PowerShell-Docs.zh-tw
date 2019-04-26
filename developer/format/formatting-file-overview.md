---
title: 格式檔案概觀 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe888fee-1fe9-459f-9d62-35732c19a7f8
caps.latest.revision: 13
ms.openlocfilehash: d418cff70c1197aa3c331eed909f49198da139e9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065728"
---
# <a name="formatting-file-overview"></a>格式設定檔案概觀

使用格式化檔案 （format.ps1xml 檔案中） 所定義的命令 （cmdlet、 函數和指令碼） 所傳回的物件的顯示格式。 這些檔案的數個所提供的 PowerShell，來定義所提供 PowerShell 命令，例如傳回這些物件的顯示格式[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)所傳回的物件`Get-Process`cmdlet。 不過，您也可以建立您自己自訂的格式化檔案，以覆寫預設顯示格式，或者您可以撰寫自訂的格式檔案，以定義您自己的命令所傳回的物件的顯示。

> [!IMPORTANT]
> 格式化檔案並判斷會傳回至管線的物件項目。 當物件傳回至管線時，該物件的所有成員都是可用，即使有些無法顯示。

PowerShell 會使用這些格式的檔案中的資料，來決定所顯示的內容，以及如何格式化顯示的資料。 顯示的資料可以包含物件的屬性或指令碼的值。 如果您想要顯示某些值不可以直接從物件，例如新增的兩個物件的屬性值，並顯示總和為某份資料的屬性，則會使用指令碼。 顯示資料的格式是由定義您想要顯示物件的檢視。 您可以定義每個物件的單一檢視，您可以定義多個物件的單一檢視，或您可以定義多個檢視，針對相同的物件。 沒有任何限制，您可以定義的檢視數目。

## <a name="common-features-of-formatting-files"></a>格式化檔案的通用功能

每個格式檔案可以定義可由檔案所定義的所有檢視之間共用的下列元件：

- 預設的組態設定，例如是否只要資料長度超過資料行的寬度，資料表的資料列中顯示的資料就會顯示在下一行。 如需有關這些設定的詳細資訊，請參閱 <<c0> [ 定義通用的組態設定](./defining-common-configuration-features.md)。

- 可以由任何格式化檔案的檢視所顯示的物件集。 如需有關這些集合 (稱為*選取項目集*)，請參閱[定義設定的物件](./defining-selection-sets.md)。

- 可用的格式化檔案的所有檢視通用控制項。 控制項可讓您更細微的控制，在資料顯示方式。 如需控制項的詳細資訊，請參閱[定義的自訂控制項](./creating-custom-controls.md)。

## <a name="formatting-views"></a>格式化檢視

格式化檢視可以表格格式，清單格式、 寬的格式和自訂格式中顯示的物件。 大部分的情況下，每個格式定義一組描述檢視的 XML 標記所描述。 每個檢視包含的檢視名稱使用檢視和檢視，例如表格檢視的資料行和資料列資訊的元件的物件。

資料表檢視清單物件或一或多個資料行中的指令碼區塊值的屬性。 每個資料行表示的物件或指令碼值的單一屬性。 您可以定義顯示的物件，物件或屬性和指令碼值的組合的屬性子集的所有屬性的資料表檢視。 資料表的每個資料列都代表傳回的物件。 建立資料表檢視，是非常類似於當您使用管線傳送物件`Format-Table`cmdlet。 如需有關此檢視的詳細資訊，請參閱[資料表檢視](./creating-a-table-view.md)。

清單檢視會列出物件或單一資料行中的指令碼值的屬性。 選擇性的標籤或屬性名稱後面的屬性或指令碼的值，則會顯示清單的每個資料列。 建立清單檢視是非常類似於使用管線傳送物件`Format-List`cmdlet。 如需有關此檢視的詳細資訊，請參閱[清單檢視](./creating-a-list-view.md)。

寬型檢視會列出物件或指令碼中的值一或多個資料行的單一屬性。 沒有任何標籤或標頭，此檢視。 建立寬型檢視是非常類似於使用管線傳送物件`Format-Wide`cmdlet。 如需有關此檢視的詳細資訊，請參閱[寬型檢視](./creating-a-wide-view.md)。

自訂檢視會顯示物件屬性的指令碼的值不會遵守固定的結構的資料表檢視、 清單檢視或寬幅檢視的自訂檢視。 您可以定義獨立的自訂檢視，或您可以定義自訂的檢視，可由另一個檢視，例如以資料表或清單檢視。 建立自訂檢視是非常類似於使用管線傳送物件`Format-Custom`cmdlet。 如需有關此檢視的詳細資訊，請參閱[的自訂檢視](./creating-custom-controls.md)。

## <a name="components-of-a-view"></a>檢視元件

在下列 XML 中，示範了檢視表的基本 XML 元件。 個別的 XML 項目而異的檢視根據您想要建立，但基本的檢視元件全都相同。

若要開始，每個檢視有`Name`項目，指定用來參考檢視的使用者易記名稱。 `ViewSelectedBy`定義的.NET 物件的檢視，所顯示的項目和*控制*定義檢視的項目。

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

在控制項項目，您可以定義一或多個*項目*項目。 如果您使用多個定義，您必須指定哪個.NET 物件會使用每個定義。 通常只有一個項目，只有一個定義，使用所需的每個控制項。

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

您在檢視的每個輸入元素，指定*項目*定義該檢視所顯示的指令碼的.NET 屬性的項目。

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

上述範例所示，此格式的檔案可以包含多個檢視、 檢視表可以包含多個定義，和每個定義可以包含多個項目。

## <a name="example-of-a-table-view"></a>資料表檢視的範例

下列範例示範用來定義包含兩個資料行的資料表檢視的 XML 標記。 [ViewDefinitions](./viewdefinitions-element-format.md)項目是在格式檔案中定義的所有檢視的容器項目。 [檢視](./view-element-format.md)項目會定義特定資料表、 清單、 寬，或自訂的檢視。 在每個[檢視](./view-element-format.md)項目[名稱](./name-element-for-view-format.md)項目指定的檢視名稱[ViewSelectedBy](./viewselectedby-element-format.md)項目會定義使用檢視和不同的物件控制項目 (例如`TableControl`下列範例所示的項目) 定義檢視的類型。

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

[建立資料表檢視](./creating-a-table-view.md)

[建立寬型檢視](./creating-a-wide-view.md)

[建立自訂控制項](./creating-custom-controls.md)

[撰寫 PowerShell 格式和類型的檔案](./writing-a-powershell-formatting-file.md)
