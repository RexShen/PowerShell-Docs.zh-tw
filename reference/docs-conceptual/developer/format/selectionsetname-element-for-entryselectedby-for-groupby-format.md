---
title: 適用于之 entryselectedby 之 GroupBy (格式的 SelectionSetName 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 362f7844c09a52494387a62e329adfb309767427
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785280"
---
# <a name="selectionsetname-element-for-entryselectedby-for-groupby-format"></a>GroupBy 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)

為清單專案指定一組 .NET 物件。 可以為專案指定的選擇集數目沒有限制。 此元素是在定義新物件群組的顯示方式時使用。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy 元素（GroupBy (格式）) CustomEntries 專案（適用于 CustomEntry 的 groupby (格式) CustomControl 專案 (之 entryselectedby 元素（適用于 groupby) 格式的 CustomEntry） (SelectionSetName 元素

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
|[GroupBy 之 CustomEntry 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-customentry-for-groupby-format.md)|定義使用此自訂專案的 .NET 類型，或必須存在才能使用此專案的條件。|

## <a name="text-value"></a>文字值

指定選取範圍的名稱。

## <a name="remarks"></a>備註

每個自訂控制項定義都必須定義至少一個型別名稱、選擇集或選取條件。

當您想要定義多個視圖中使用的一組物件時，通常會使用選取範圍集。 例如，您可能會想要建立一組相同物件的資料表視圖和清單視圖。 如需定義選取集的詳細資訊，請參閱[定義選取範圍集合](./defining-selection-sets.md)。

如需自訂控制項視圖之元件的詳細資訊，請參閱[建立自訂控制項](./creating-custom-controls.md)。

## <a name="see-also"></a>另請參閱

[GroupBy 之 CustomEntry 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-customentry-for-groupby-format.md)

[建立自訂控制項](./creating-custom-controls.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
