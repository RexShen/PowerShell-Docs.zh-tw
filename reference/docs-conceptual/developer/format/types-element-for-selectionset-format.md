---
title: SelectionSet (格式) 的 Types 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 9978daefb3e97ab131774ca4dff633dde6b4dfbf
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772513"
---
# <a name="types-element-for-selectionset-format"></a>SelectionSet 的類型元素 (格式)

定義選取集中的 .NET 物件。

Configuration 元素 (格式) SelectionSets 元素 (格式) SelectionSet 元素 (格式) 類型元素 (格式) 

## <a name="syntax"></a>語法

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `Types` 。 必須至少有一個子專案，但可以加入的子專案數目沒有上限。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[類型的 TypeName 元素 (格式) ](./typename-element-for-types-format.md)|必要元素。<br /><br /> 指定屬於選取集的 .NET 物件。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[SelectionSet 元素 (格式)](./selectionset-element-format.md)|定義一組可由集合名稱參考的 .NET 物件。|

## <a name="remarks"></a>備註

這個專案所定義的物件組成一個可供視圖使用的選擇集，而 view 的定義 (views 可以) 多個定義，或指定選取條件。  如需選取集的詳細資訊，請參閱[定義物件的集合](./defining-selection-sets.md)。

## <a name="example"></a>範例

這個範例會顯示 `SelectionSet` 定義四個 .net 類型的元素。

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

[定義物件的集合](./defining-selection-sets.md)

[SelectionSet 元素 (格式)](./selectionset-element-format.md)

[類型的 TypeName 元素 (格式) ](./typename-element-for-types-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
