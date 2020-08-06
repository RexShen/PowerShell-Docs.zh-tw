---
title: SelectionSets 元素 (格式) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 718b08e02220f285ef215fdca727492fd4407466
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785195"
---
# <a name="selectionsets-element-format"></a>SelectionSets 元素 (格式)

定義一組通用的 .NET 物件，可供格式化檔案的所有視圖使用。 格式設定檔案的視圖和控制項只能使用選取範圍的名稱來參考一組完整的物件。

Configuration 元素 SelectionSets 元素格式

## <a name="syntax"></a>語法

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述元素的屬性、子專案和父項目 `SelectionSets` 。 每個子專案都會定義一組可由集合名稱參考的物件。 子項目的順序並不重要。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[SelectionSet 元素 (格式)](./selectionset-element-format.md)|必要元素。<br /><br /> 定義一組可由集合名稱參考的 .NET 物件。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[組態元素](./configuration-element-format.md)|代表格式化檔案的最上層元素。|

## <a name="remarks"></a>備註

當您有一組想要使用單一名稱來參考的相關物件（例如透過繼承相關的一組物件）時，您可以使用 [選擇集]。 定義您的視圖時，您可以使用選取範圍的名稱來指定物件集合，而不會列出每個視圖內的所有物件。

定義格式檔案的觀點或 views 定義時，會以名稱指定一般選取範圍。 在這些情況下， `SelectionSetName` 和元素的子 `ViewSelectedBy` 專案 `EntrySelectedBy` 會指定要使用的集合。 如需選取集的詳細資訊，請參閱[定義物件的集合](./defining-selection-sets.md)。

## <a name="see-also"></a>另請參閱

[組態元素](./configuration-element-format.md)

[定義選取範圍集合](./defining-selection-sets.md)

[SelectionSet 元素 (格式)](./selectionset-element-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
