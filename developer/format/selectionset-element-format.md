---
title: SelectionSet 項目 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 848e7acd-d578-4fd1-a575-c0c3b9b5e68a
caps.latest.revision: 17
ms.openlocfilehash: c809aa6c3a40d16cfd2fd99065a846d265ec0f61
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861154"
---
# <a name="selectionset-element-format"></a>SelectionSet 元素 (格式)

定義一組.NET 物件可以參考的集合的名稱。

組態項目 （格式） SelectionSets 項目 （格式） SelectionSet 項目 （格式）

## <a name="syntax"></a>語法

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`SelectionSet`項目。 每個選取項目集必須具有名稱，而且必須指定.NET 物件的集合。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[SelectionSet （格式） 的 name 元素](./name-element-for-selectionset-format.md)|必要項目。<br /><br /> 指定用來參考選取項目集的名稱。|
|[類型項目 （格式）](./types-element-for-selectionset-format.md)|必要項目。<br /><br /> 定義選取範圍中設定的.NET 物件。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[SelectionSets 項目格式](./selectionsets-element-format.md)|定義通用的集合，可供所有檢視的格式化檔案的.NET 物件。|

## <a name="remarks"></a>備註

當您有一組您想要使用單一的名稱，例如一組透過繼承相關聯的物件參考的相關物件時，您可以使用選取項目集。 在定義您的檢視時，您可以指定一組物件使用的設定而非列出每個檢視中的所有物件的選取範圍的名稱。

定義格式化檔案的檢視或檢視的定義時常見的選取項目集指定的名稱。 在這些情況下，`SelectionSetName`子元素`ViewSelectedBy`和`EntrySelectedBy`元素指定要使用的集合。 如需選取項目集的詳細資訊，請參閱[定義設定的物件](./defining-selection-sets.md)。

## <a name="example"></a>範例

下列範例所示`SelectionSet`項目，定義四個.NET 型別。

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

[定義選取範圍](./defining-selection-sets.md)

[Name 元素 SelectionSet （格式）](./name-element-for-selectionset-format.md)

[SelectionSets 項目 （格式）](./selectionsets-element-format.md)

[類型項目 （格式）](./types-element-for-selectionset-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
