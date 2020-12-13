---
ms.date: 09/13/2016
ms.topic: reference
title: 類型的 TypeName 元素 (格式)
description: 類型的 TypeName 元素 (格式)
ms.openlocfilehash: c656b8e7e5877b72ff2164e5b417857273cada61
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664612"
---
# <a name="typename-element-for-types-format"></a>類型的 TypeName 元素 (格式)

指定屬於選取集之物件的 .NET 類型。

Configuration 元素 (格式) SelectionSets 元素 (格式) SelectionSet 專案 (格式) 類型專案 (格式) 格式 (類型) 格式

## <a name="syntax"></a>語法

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列章節說明屬性、子專案和元素的父元素 `TypeName` 。 `TypeName`選取專案集中必須包含至少一個元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[類型元素 (格式) ](./types-element-for-selectionset-format.md)|定義選取專案集中的 .NET 物件。|

## <a name="text-value"></a>文字值

指定 .NET 類型的完整名稱。

## <a name="remarks"></a>備註

當您有一組要使用單一名稱來參考的相關物件時，例如一組透過繼承相關的物件，您可以使用選取集。 定義您的視圖時，您可以使用選取集的名稱來指定物件集合，而不是列出每個視圖內的所有物件。

定義格式化檔案的視圖時，會依名稱來指定常用的選取集。 在這些情況下， `SelectionSetName` view 專案的子項目會 `ViewSelectedBy` 指定集合。 不過，view 的不同專案也可以指定僅套用至該專案的選項組。 如需選取集的詳細資訊，請參閱 [定義物件集](./defining-selection-sets.md)。

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

[類型元素 (格式) ](./types-element-for-selectionset-format.md)

[撰寫 Windows PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
