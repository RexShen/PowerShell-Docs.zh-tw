---
title: SelectionSet 的名稱元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914917f7-0efc-4d1f-88bd-de714bedd98f
caps.latest.revision: 15
ms.openlocfilehash: 29dbdbd335511e4ca2706a625541554825838f23
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362667"
---
# <a name="name-element-for-selectionset-format"></a>SelectionSet 的名稱元素 (格式)

指定用來參考選取集的名稱。

Configuration 元素（格式） SelectionSets 元素（格式） SelectionSet 元素（格式） SelectionSet 的名稱元素（格式）

## <a name="syntax"></a>語法

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明 `Name` 元素的屬性、子專案和父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[SelectionSet 元素（格式）](./selectionset-element-format.md)|定義一組可由集合名稱參考的 .NET 物件。|

## <a name="text-value"></a>文字值

指定要參考選取集的名稱。 對於可使用的字元沒有任何限制。

## <a name="remarks"></a>備註

此處指定的名稱用於 `SelectionSetName` 元素中。 可供視圖使用的選取範圍，由視圖的定義（views 可以有多個定義）或指定選取條件。 如需選取集的詳細資訊，請參閱[定義物件的集合](./defining-selection-sets.md)。

## <a name="example"></a>範例

這個範例會顯示定義四個 .NET 類型的 @no__t 0 元素。 選取集的名稱是 "FileSystemTypes"。

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

[SelectionSet 元素（格式）](./selectionset-element-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
