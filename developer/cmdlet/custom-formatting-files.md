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
# <a name="custom-formatting-files"></a>自訂格式設定檔案

Cmdlet、 函數和指令碼所傳回的物件的顯示格式會定義使用格式檔案 （format.ps1xml 檔案）。 這些檔案的數個會提供定義 Windows PowerShell cmdlet 所傳回的物件的預設顯示格式的 Windows PowerShell。 不過，您也可以建立您自己自訂的格式化檔案，覆寫預設顯示格式，或定義您自己的命令所傳回的物件的顯示。

Windows PowerShell 會使用這些格式的檔案中的資料，來決定所顯示的內容，以及如何格式化資料。 顯示的資料可以包含物件的屬性或值的指令碼區塊。  如果您想要顯示某些值不可以直接從物件的屬性，則會使用指令碼區塊。 例如，您可能要新增的兩個物件的屬性值，並顯示為個別的一種資料的總和。 當您撰寫自己的格式化檔案時，您必須定義*檢視*您想要顯示的物件。 您可以定義每個物件的單一檢視，您可以定義多個物件的單一檢視，或您可以定義多個檢視，針對相同的物件。 沒有任何限制，您可以定義的檢視數目。

> [!IMPORTANT]
> 格式化檔案並判斷會傳回至管線的物件項目。 當物件傳回至管線時，該物件的所有成員都都可用。

## <a name="format-views"></a>格式檢視

格式化檢視可以顯示的物件中以資料表格式、 以清單格式、 寬的格式和自訂的格式。 大部分的情況下，每個格式定義一組描述檢視的 XML 標記所描述。 每個檢視包含的檢視名稱使用檢視和檢視，例如表格檢視的資料行和資料列資訊的元件的物件。

提供下列檢視。

資料表檢視會列出物件或一或多個資料行中的指令碼區塊值的屬性。 每個資料行表示的物件或指令碼區塊值的屬性。 您可以定義顯示的物件，物件或屬性和值的組合指令碼區塊的屬性子集的所有屬性的資料表檢視。 資料表的每個資料列都代表傳回的物件。 如需有關此檢視的詳細資訊，請參閱[資料表檢視](../format/creating-a-table-view.md)。

清單檢視會列出物件或單一資料行中的指令碼區塊值的屬性。 選擇性的標籤或屬性名稱後面的屬性或指令碼區塊的值，則會顯示清單的每個資料列。 如需有關此檢視的詳細資訊，請參閱[清單檢視](../format/creating-a-list-view.md)。

寬型檢視會列出物件或指令碼區塊中的值一或多個資料行的單一屬性。 沒有任何標籤或標頭，此檢視。 如需有關此檢視的詳細資訊，請參閱[寬型檢視](../format/creating-a-wide-view.md)。

自訂檢視會顯示物件屬性的指令碼區塊值不會遵守固定的結構的資料表檢視、 清單檢視或寬幅檢視的自訂檢視。 您可以定義獨立自訂檢視，或您可以定義自訂的檢視，可由另一個檢視，例如以資料表或清單檢視。 如需有關此檢視的詳細資訊，請參閱[的自訂檢視](../format/creating-custom-controls.md)。

## <a name="view-xml-elements"></a>檢視 XML 項目

下列範例示範用來定義包含兩個資料行的資料表檢視的 XML 標記。 [ViewDefinitions](../format/viewdefinitions-element-format.md)項目是在格式檔案中定義的所有檢視的容器項目。 [檢視](../format/view-element-format.md)項目會定義特定資料表、 清單、 寬，或自訂的檢視。 在每個檢視中，[名稱](../format/name-element-for-view-format.md)項目指定的檢視名稱[ViewSelectedBy](../format/viewselectedby-element-format.md)項目會定義檢視和不同的控制項項目所使用的物件 (例如`TableControl`項目） 定義的檢視格式。

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

[資料表檢視](../format/creating-a-table-view.md)

[清單檢視](../format/creating-a-list-view.md)

[寬型檢視](../format/creating-a-wide-view.md)

[自訂檢視](../format/creating-custom-controls.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
