---
title: 項目類型 （格式） SelectionSet |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4606fec0-ff31-4d36-af68-227405335ec3
caps.latest.revision: 15
ms.openlocfilehash: 0427367efa2c8a7e352d718706d1341a0c8e3621
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862374"
---
# <a name="types-element-for-selectionset-format"></a>SelectionSet 的類型元素 (格式)

定義選取範圍中設定的.NET 物件。

組態項目 （格式） SelectionSets 項目 （格式） SelectionSet 項目 （格式） 型別項目 （格式）

## <a name="syntax"></a>語法

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`Types`項目。 必須有至少一個子元素，但沒有可加入的子項目數目沒有上限限制。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[TypeName 項目類型 （格式）](./typename-element-for-types-format.md)|必要項目。<br /><br /> 指定屬於選取項目集的.NET 物件。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[SelectionSet 項目 （格式）](./selectionset-element-format.md)|定義一組.NET 物件可以參考的集合的名稱。|

## <a name="remarks"></a>備註

這個項目所定義的物件會構成可以檢視的定義所使用的檢視中，選取項目集 （檢視可以有多個定義），或指定選取條件時。  如需選取項目集的詳細資訊，請參閱[定義設定的物件](./defining-selection-sets.md)。

## <a name="example"></a>範例

此範例示範`SelectionSet`項目，定義四個.NET 型別。

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

[SelectionSet 項目 （格式）](./selectionset-element-format.md)

[TypeName 項目類型 （格式）](./typename-element-for-types-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
