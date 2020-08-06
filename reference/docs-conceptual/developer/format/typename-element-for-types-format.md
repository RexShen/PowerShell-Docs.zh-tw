---
title: 類型的 TypeName 元素 (格式) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 40fad73c66124d6c3b0d969b4268713a492c963a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772530"
---
# <a name="typename-element-for-types-format"></a>類型的 TypeName 元素 (格式)

指定屬於選取集之物件的 .NET 類型。

Configuration 元素 (格式) SelectionSets 元素 (格式) SelectionSet 專案 (格式) 類型元素 (格式) 格式的類型名稱元素 (

## <a name="syntax"></a>語法

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `TypeName` 。 `TypeName`選取範圍中至少必須包含一個元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[Types 元素 (格式) ](./types-element-for-selectionset-format.md)|定義選取集中的 .NET 物件。|

## <a name="text-value"></a>文字值

指定 .NET 類型的完整名稱。

## <a name="remarks"></a>備註

當您有一組想要使用單一名稱來參考的相關物件（例如透過繼承相關的一組物件）時，您可以使用 [選擇集]。 定義您的視圖時，您可以使用選取範圍的名稱來指定物件集合，而不會列出每個視圖內的所有物件。

定義格式設定檔案的視圖時，會以名稱指定一般選取範圍。 在這些情況下， `SelectionSetName` view 元素的子項目會 `ViewSelectedBy` 指定集合。 不過，不同的視圖專案也可以指定僅適用于該視圖專案的選擇集。 如需選取集的詳細資訊，請參閱[定義物件的集合](./defining-selection-sets.md)。

## <a name="example"></a>範例

下列範例顯示 `SelectionSet` 定義四個 .net 類型的元素。

```
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

## <a name="see-also"></a>另請參閱

[定義選取範圍集合](./defining-selection-sets.md)

[SelectionSet 元素 (格式)](./selectionset-element-format.md)

[SelectionSets 元素 (格式)](./selectionsets-element-format.md)

[Types 元素 (格式) ](./types-element-for-selectionset-format.md)

[撰寫 Windows PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
