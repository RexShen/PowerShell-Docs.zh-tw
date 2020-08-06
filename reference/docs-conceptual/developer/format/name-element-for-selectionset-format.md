---
title: SelectionSet (格式) 的 Name 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1fc33eeb87a6912ed6793629ab1969cd65b5f0c5
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773295"
---
# <a name="name-element-for-selectionset-format"></a>SelectionSet 的名稱元素 (格式)

指定用來參考選取集的名稱。

Configuration 元素 (格式) SelectionSets 元素 (格式) SelectionSet 元素 (格式) SelectionSet 的 Name 元素 (格式) 

## <a name="syntax"></a>語法

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述元素的屬性、子專案和父項目 `Name` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[SelectionSet 元素 (格式)](./selectionset-element-format.md)|定義一組可由集合名稱參考的 .NET 物件。|

## <a name="text-value"></a>文字值

指定要參考選取集的名稱。 對於可使用的字元沒有任何限制。

## <a name="remarks"></a>備註

此處指定的名稱用於 `SelectionSetName` 元素中。 View 所能使用的選取範圍 (views 的定義可以) 多個定義，或指定選取條件時。 如需選取集的詳細資訊，請參閱[定義物件的集合](./defining-selection-sets.md)。

## <a name="example"></a>範例

這個範例會顯示 `SelectionSet` 定義四個 .net 類型的元素。 選取集的名稱是 "FileSystemTypes"。

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

[SelectionSet 元素 (格式)](./selectionset-element-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
