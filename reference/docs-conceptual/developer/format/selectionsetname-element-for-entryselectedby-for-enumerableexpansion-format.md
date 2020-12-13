---
ms.date: 09/13/2016
ms.topic: reference
title: EnumerableExpansion 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)
description: EnumerableExpansion 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)
ms.openlocfilehash: 074f810f5a3cbad61ee8be69408967758f0591df
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651883"
---
# <a name="selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format"></a>EnumerableExpansion 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)

指定由這個定義擴充的 .NET 類型集合。

設定元素 (格式) DefaultSettings 元素 (格式) EnumerableExpansions 專案 (格式) EnumerableExpansion 元素 (格式) 之 entryselectedby 專案的 EnumerableExpansion (格式) SelectionSetName 專案之 entryselectedby 的 EnumerableExpansion (格式) 

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
|[EnumerableExpansion 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-enumerableexpansion-format.md)|定義由這個定義擴充的 .NET 集合物件。|

## <a name="text-value"></a>文字值

指定選項群組的名稱。

## <a name="remarks"></a>備註

每個定義都必須指定一個或多個類型名稱、選取集或選取條件。

當您想要定義多個視圖中使用的一組物件時，通常會使用選取集。 例如，您可能會想要為相同的物件集建立資料表視圖和清單視圖。 如需定義選擇集的詳細資訊，請參閱 [定義視圖的物件集](./defining-selection-sets.md)。

## <a name="see-also"></a>另請參閱

[定義選取範圍集合](./defining-selection-sets.md)

[EnumerableExpansion 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-enumerableexpansion-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
