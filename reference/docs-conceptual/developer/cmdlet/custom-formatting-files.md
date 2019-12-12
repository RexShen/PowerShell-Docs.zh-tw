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
# <a name="custom-formatting-files"></a>自訂格式設定檔案

Cmdlet、函式和腳本所傳回物件的顯示格式是使用格式檔案（types.ps1xml 檔案）所定義。 Windows PowerShell 會提供這些檔案中的幾個，以定義 Windows PowerShell Cmdlet 所傳回之物件的預設顯示格式。 不過，您也可以建立自己的自訂格式檔案，以覆寫預設的顯示格式，或定義您自己的命令所傳回的物件顯示。

Windows PowerShell 會使用這些格式檔案中的資料來判斷要顯示的內容，以及資料的格式化方式。 顯示的資料可以包含物件的屬性或腳本區塊的值。  如果您想要顯示無法直接從物件的屬性取得的某個值，則會使用腳本區塊。 例如，您可能會想要新增物件的兩個屬性值，並將總和顯示為個別的資料片段。 當您撰寫自己的格式化檔案時，您必須定義要顯示之物件的*視圖*。 您可以為每個物件定義單一視圖，您可以為多個物件定義單一視圖，也可以為相同的物件定義多個視圖。 您可以定義的視圖數目沒有限制。

> [!IMPORTANT]
> 格式化檔案不會判斷傳回給管線之物件的元素。 當物件傳回至管線時，可以使用該物件的所有成員。

## <a name="format-views"></a>格式化視圖

格式化視圖可以使用表格格式、清單格式、寬格式，以及自訂格式來顯示物件。 在大部分的情況下，每個格式定義都是由一組描述視圖的 XML 標記所描述。 每個視圖都會包含視圖的名稱、使用此視圖的物件，以及視圖的元素，例如資料表視圖的資料行和資料列資訊。

下列為可用的視圖。

資料表視圖會列出一個或多個資料行中物件或腳本區塊值的屬性。 每個資料行都代表物件或腳本區塊值的屬性。 您可以定義資料表視圖，以顯示物件的所有屬性、物件屬性的子集，或是屬性和腳本區塊值的組合。 資料表的每個資料列都代表一個傳回的物件。 如需此視圖的詳細資訊，請參閱[資料表視圖](../format/creating-a-table-view.md)。

清單視圖會列出物件的屬性或單一資料行中的腳本區塊值。 清單的每個資料列都會顯示選擇性標籤或屬性名稱，後面接著屬性或腳本區塊的值。 如需此視圖的詳細資訊，請參閱[清單視圖](../format/creating-a-list-view.md)。

寬型視圖會列出一個或多個資料行中物件或腳本區塊值的單一屬性。 沒有此視圖的標籤或標頭。 如需此視圖的詳細資訊，請參閱[Wide view](../format/creating-a-wide-view.md)。

[自訂視圖] 會顯示物件屬性或腳本區塊值的可自訂視圖，而不會遵守資料表視圖、清單視圖或寬視圖的嚴格結構。 您可以定義獨立的自訂視圖，也可以定義另一個視圖所使用的自訂視圖，例如資料表視圖或清單視圖。 如需此視圖的詳細資訊，請參閱[自訂視圖](../format/creating-custom-controls.md)。

## <a name="view-xml-elements"></a>View XML 元素

下列範例顯示用來定義包含兩個數據行之資料表視圖的 XML 標記。 [ViewDefinitions](../format/viewdefinitions-element-format.md)元素是格式檔案中定義之所有視圖的容器元素。 [View](../format/view-element-format.md)元素會定義特定的資料表、清單、寬型或自訂視圖。 在每個視圖中， [name](../format/name-element-for-view-format.md)元素會指定視圖的名稱， [ViewSelectedBy](../format/viewselectedby-element-format.md)元素會定義使用此視圖的物件，而不同的控制項專案（例如 `TableControl` 專案）會定義視圖的格式。

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

## <a name="see-also"></a>另請參閱

[資料表視圖](../format/creating-a-table-view.md)

[清單檢視](../format/creating-a-list-view.md)

[寬視圖](../format/creating-a-wide-view.md)

[自訂視圖](../format/creating-custom-controls.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
