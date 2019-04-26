---
title: 類型名稱的項目類型 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0595b99e-b438-4240-b47b-555cf0316f33
caps.latest.revision: 15
ms.openlocfilehash: bd5baa03c2050b2c3bbe1d7697c253d923175d39
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083785"
---
# <a name="typename-element-for-types-format"></a>類型的 TypeName 元素 (格式)

指定屬於選取項目集之物件的.NET 類型。

組態項目 （格式） SelectionSets 項目 （格式） SelectionSet 項目 （格式） 類型的類型 （格式） 的項目 （格式） 類型名稱項目

## <a name="syntax"></a>語法

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`TypeName`項目。 至少一個`TypeName`元素必須包含在選取項目集。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[類型項目 （格式）](./types-element-for-selectionset-format.md)|定義選取範圍中設定的.NET 物件。|

## <a name="text-value"></a>文字值

指定的.NET 類型的完整的名稱。

## <a name="remarks"></a>備註

當您有一組您想要使用單一的名稱，例如一組透過繼承相關聯的物件參考的相關物件時，您可以使用選取項目集。 在定義您的檢視時，您可以指定一組物件使用的設定而非列出每個檢視中的所有物件的選取範圍的名稱。

常見的選取項目集指定其名稱所定義的格式化檔案的檢視時。 在這些情況下，`SelectionSetName`子項目`ViewSelectedBy`檢視的項目會指定集合。 不過，不同的項目 檢視也可以指定套用至該檢視的項目選取項目集。 如需選取項目集的詳細資訊，請參閱[定義設定的物件](./defining-selection-sets.md)。

## <a name="example"></a>範例

下列範例所示`SelectionSet`項目，定義四個.NET 型別。

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

[定義選取範圍](./defining-selection-sets.md)

[SelectionSet 項目 （格式）](./selectionset-element-format.md)

[SelectionSets 項目 （格式）](./selectionsets-element-format.md)

[類型項目 （格式）](./types-element-for-selectionset-format.md)

[撰寫 Windows PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
