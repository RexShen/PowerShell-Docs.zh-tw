---
title: SelectionSet 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 848e7acd-d578-4fd1-a575-c0c3b9b5e68a
caps.latest.revision: 17
ms.openlocfilehash: c809aa6c3a40d16cfd2fd99065a846d265ec0f61
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368377"
---
# <a name="selectionset-element-format"></a>SelectionSet 元素 (格式)

定義一組可由集合名稱參考的 .NET 物件。

Configuration 元素（格式） SelectionSets 元素（格式） SelectionSet 元素（格式）

## <a name="syntax"></a>語法

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `SelectionSet` 專案的父元素。 每個選取範圍都必須要有名稱，而且必須指定集合的 .NET 物件。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|項目|說明|
|-------------|-----------------|
|[SelectionSet 的名稱元素（格式）](./name-element-for-selectionset-format.md)|必要元素。<br /><br /> 指定用來參考選取集的名稱。|
|[Types 元素（格式）](./types-element-for-selectionset-format.md)|必要元素。<br /><br /> 定義選取集中的 .NET 物件。|

### <a name="parent-elements"></a>父元素

|項目|說明|
|-------------|-----------------|
|[SelectionSets 元素格式](./selectionsets-element-format.md)|定義一組通用的 .NET 物件，可供格式化檔案的所有視圖使用。|

## <a name="remarks"></a>備註

當您有一組想要使用單一名稱來參考的相關物件（例如透過繼承相關的一組物件）時，您可以使用 [選擇集]。 定義您的視圖時，您可以使用選取範圍的名稱來指定物件集合，而不會列出每個視圖內的所有物件。

定義格式檔案的觀點或 views 定義時，會以名稱指定一般選取範圍。 在這些情況下，`ViewSelectedBy` 和 `EntrySelectedBy` 元素的 `SelectionSetName` 子項目會指定要使用的集合。 如需選取集的詳細資訊，請參閱[定義物件的集合](./defining-selection-sets.md)。

## <a name="example"></a>範例

下列範例會顯示定義四個 .NET 類型的 `SelectionSet` 元素。

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

[SelectionSet 的 Name 元素（格式）](./name-element-for-selectionset-format.md)

[SelectionSets 元素（格式）](./selectionsets-element-format.md)

[Types 元素（格式）](./types-element-for-selectionset-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
