---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSets 元素 (格式)
description: SelectionSets 元素 (格式)
ms.openlocfilehash: e5c928dfb82bc6963b4a87aef9ec06d34cacfdcb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654931"
---
# <a name="selectionsets-element-format"></a>SelectionSets 元素 (格式)

定義可供格式化檔案的所有視圖使用的通用 .NET 物件集。 格式設定檔案的視圖和控制項可以使用選取範圍的名稱，參考一組完整的物件。

Configuration 元素 SelectionSets 元素格式

## <a name="syntax"></a>語法

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述專案的屬性、子項目和父元素 `SelectionSets` 。 每個子專案都會定義一組可由集合名稱參考的物件。 子項目的順序並不重要。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[SelectionSet 元素 (格式)](./selectionset-element-format.md)|必要元素。<br /><br /> 定義可由集合名稱參考的一組 .NET 物件。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[組態元素](./configuration-element-format.md)|代表格式化檔案的最上層元素。|

## <a name="remarks"></a>備註

當您有一組要使用單一名稱來參考的相關物件時，例如一組透過繼承相關的物件，您可以使用選取集。 定義您的視圖時，您可以使用選取集的名稱來指定物件集合，而不是列出每個視圖內的所有物件。

在定義格式化檔案的視圖或視圖的定義時，會以名稱指定常用的選取集。 在這些情況下， `SelectionSetName` 和元素的子 `ViewSelectedBy` 元素 `EntrySelectedBy` 會指定要使用的集合。 如需選取集的詳細資訊，請參閱 [定義物件集](./defining-selection-sets.md)。

## <a name="see-also"></a>另請參閱

[組態元素](./configuration-element-format.md)

[定義選取範圍集合](./defining-selection-sets.md)

[SelectionSet 元素 (格式)](./selectionset-element-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
