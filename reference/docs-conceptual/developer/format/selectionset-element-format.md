---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSet 元素 (格式)
description: SelectionSet 元素 (格式)
ms.openlocfilehash: 944aa83569ad8ca789746a71f60e5da5c19fbf01
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647866"
---
# <a name="selectionset-element-format"></a>SelectionSet 元素 (格式)

定義一組可由集合名稱參考的 .NET 物件。

Configuration 元素 (格式) SelectionSets 元素 (格式) SelectionSet 元素 (格式) 

## <a name="syntax"></a>語法

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列章節說明屬性、子專案和元素的父元素 `SelectionSet` 。 每個選擇集都必須有名稱，而且必須指定集合的 .NET 物件。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[SelectionSet 的名稱元素 (格式)](./name-element-for-selectionset-format.md)|必要元素。<br /><br /> 指定用來參考選取集的名稱。|
|[類型元素 (格式) ](./types-element-for-selectionset-format.md)|必要元素。<br /><br /> 定義選取專案集中的 .NET 物件。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[SelectionSets 元素格式](./selectionsets-element-format.md)|定義可供格式化檔案的所有視圖使用的通用 .NET 物件集。|

## <a name="remarks"></a>備註

當您有一組要使用單一名稱來參考的相關物件時，例如一組透過繼承相關的物件，您可以使用選取集。 定義您的視圖時，您可以使用選取集的名稱來指定物件集合，而不是列出每個視圖內的所有物件。

在定義格式化檔案的視圖或視圖的定義時，會以名稱指定常用的選取集。 在這些情況下， `SelectionSetName` 和元素的子 `ViewSelectedBy` 元素 `EntrySelectedBy` 會指定要使用的集合。 如需選取集的詳細資訊，請參閱 [定義物件集](./defining-selection-sets.md)。

## <a name="example"></a>範例

下列範例顯示 `SelectionSet` 定義四個 .net 類型的元素。

```xml
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

[SelectionSet (格式的 Name 元素) ](./name-element-for-selectionset-format.md)

[SelectionSets 元素 (格式)](./selectionsets-element-format.md)

[類型元素 (格式) ](./types-element-for-selectionset-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
