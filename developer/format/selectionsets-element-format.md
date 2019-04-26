---
title: SelectionSets 項目 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebbac73a-1c99-4388-9f47-703cd024dc6d
caps.latest.revision: 18
ms.openlocfilehash: a9356635d60d5f8c5d4dec4ec8b7d0aea2b037dd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063761"
---
# <a name="selectionsets-element-format"></a>SelectionSets 元素 (格式)

定義通用的集合，可供所有檢視的格式化檔案的.NET 物件。 使用選取項目集的名稱，以檢視和控制項的格式化檔案可以參考一組完整的物件。

組態項目 SelectionSets 元素格式

## <a name="syntax"></a>語法

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`SelectionSets`項目。 每個子項目會定義一組可以集的名稱所參考的物件。 子元素的順序並不重要。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[SelectionSet 項目 （格式）](./selectionset-element-format.md)|必要項目。<br /><br /> 定義一組.NET 物件，可以參考集的名稱。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[組態項目](./configuration-element-format.md)|表示格式化檔案的最上層項目。|

## <a name="remarks"></a>備註

當您有一組您想要使用單一的名稱，例如一組透過繼承相關聯的物件參考的相關物件時，您可以使用選取項目集。 在定義您的檢視時，您可以指定一組物件使用的設定而非列出每個檢視中的所有物件的選取範圍的名稱。

定義格式化檔案的檢視或檢視的定義時常見的選取項目集指定的名稱。 在這些情況下，`SelectionSetName`子元素`ViewSelectedBy`和`EntrySelectedBy`元素指定要使用的集合。 如需選取項目集的詳細資訊，請參閱[定義設定的物件](./defining-selection-sets.md)。

## <a name="see-also"></a>另請參閱

[組態項目](./configuration-element-format.md)

[定義選取範圍](./defining-selection-sets.md)

[SelectionSet 項目 （格式）](./selectionset-element-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
