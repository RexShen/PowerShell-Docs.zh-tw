---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSet 的名稱元素 (格式)
description: SelectionSet 的名稱元素 (格式)
ms.openlocfilehash: 98c13be6ea352055231fbdb3a60f0eb508f661b8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666448"
---
# <a name="name-element-for-selectionset-format"></a>SelectionSet 的名稱元素 (格式)

指定用來參考選取集的名稱。

設定元素 (格式) SelectionSets 元素 (格式) SelectionSet 元素 (格式) SelectionSet (格式) 名稱元素

## <a name="syntax"></a>語法

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述專案的屬性、子項目和父元素 `Name` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[SelectionSet 元素 (格式)](./selectionset-element-format.md)|定義可由集合名稱參考的一組 .NET 物件。|

## <a name="text-value"></a>文字值

指定參考選取集的名稱。 可以使用的字元沒有任何限制。

## <a name="remarks"></a>備註

此處指定的名稱用於 `SelectionSetName` 元素中。 可供視圖使用的選取範圍， (views 的 view 定義可以有多個定義) 或指定選取條件。 如需選取集的詳細資訊，請參閱 [定義物件集](./defining-selection-sets.md)。

## <a name="example"></a>範例

此範例顯示 `SelectionSet` 定義四個 .net 類型的元素。 選擇組的名稱為 "FileSystemTypes"。

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
