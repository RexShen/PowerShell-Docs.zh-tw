---
title: EnumerableExpansion (格式) 的之 entryselectedby 的 SelectionSetName 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 8745ef9e6f326c3e8a5dbf185a595bbe93e92414
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785314"
---
# <a name="selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format"></a>EnumerableExpansion 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)

指定由這個定義擴充的 .NET 類型集合。

Configuration 元素 (格式) DefaultSettings 元素 (格式) EnumerableExpansions 元素 (格式) EnumerableExpansion 專案 (格式) EnumerableExpansion (格式) SelectionSetName 元素之 entryselectedby (格式) 

## <a name="syntax"></a>語法

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `SelectionSetName` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[EnumerableExpansion 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-enumerableexpansion-format.md)|定義由這個定義展開的 .NET 集合物件。|

## <a name="text-value"></a>文字值

指定選取範圍的名稱。

## <a name="remarks"></a>備註

每個定義都必須指定一或多個類型名稱、選取範圍或選取條件。

當您想要定義多個視圖中使用的一組物件時，通常會使用選取範圍集。 例如，您可能會想要建立一組相同物件的資料表視圖和清單視圖。 如需定義選取集的詳細資訊，請參閱[定義視圖的物件集合](./defining-selection-sets.md)。

## <a name="see-also"></a>另請參閱

[定義選取範圍集合](./defining-selection-sets.md)

[EnumerableExpansion 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-enumerableexpansion-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
