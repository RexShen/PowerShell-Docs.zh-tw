---
title: 項目名稱 （格式） SelectionSet |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914917f7-0efc-4d1f-88bd-de714bedd98f
caps.latest.revision: 15
ms.openlocfilehash: 29dbdbd335511e4ca2706a625541554825838f23
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858164"
---
# <a name="name-element-for-selectionset-format"></a>SelectionSet 的名稱元素 (格式)

指定用來參考選取項目集的名稱。

組態項目 （格式） SelectionSets 項目 （格式） SelectionSet 項目 （格式） 名稱項目 SelectionSet （格式）

## <a name="syntax"></a>語法

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`Name`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[SelectionSet 項目 （格式）](./selectionset-element-format.md)|定義一組.NET 物件，可以參考集的名稱。|

## <a name="text-value"></a>文字值

指定要參考的選取項目集的名稱。 有可以使用哪些字元沒有限制。

## <a name="remarks"></a>備註

在這裡指定的名稱會在`SelectionSetName`項目。 可以檢視的定義所使用的檢視中，選取項目集 （檢視可以有多個定義），或指定選取條件時。 如需選取項目集的詳細資訊，請參閱[定義設定的物件](./defining-selection-sets.md)。

## <a name="example"></a>範例

此範例示範`SelectionSet`項目，定義四個.NET 型別。 選取項目集的名稱是"FileSystemTypes 」。

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

[SelectionSet 項目 （格式）](./selectionset-element-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
