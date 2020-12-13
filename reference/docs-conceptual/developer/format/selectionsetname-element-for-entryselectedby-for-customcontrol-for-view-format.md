---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之 CustomControl 的 EntrySelectedBy 的 SelectionSetName 元素 (格式)
description: 檢視之 CustomControl 的 EntrySelectedBy 的 SelectionSetName 元素 (格式)
ms.openlocfilehash: a158c5476fb3a168a146ce67565c0ed6f7859519
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651921"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a>檢視之 CustomControl 的 EntrySelectedBy 的 SelectionSetName 元素 (格式)

指定清單專案的一組 .NET 物件。 可以針對專案指定的選取範圍數目沒有任何限制。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) CustomControl 專案 (格式) CustomEntries 專案 (格式) 專案 (格式) CustomEntry 專案 (格式) CustomEntries 專案之 entryselectedby for CustomEntry 的 SelectionSetName (格式) 

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
|[適用于 CustomEntry 的之 entryselectedby 元素 (格式) ](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|定義使用此自訂專案的 .NET 型別，或必須存在才能使用此專案的條件。|

## <a name="text-value"></a>文字值

指定選項群組的名稱。

## <a name="remarks"></a>備註

每個自訂控制項專案都必須定義至少一個類型名稱、選取集或選取條件。

當您想要定義多個視圖中使用的一組物件時，通常會使用選取集。 例如，您可能會想要為相同的物件集建立資料表視圖和清單視圖。 如需定義選取範圍的詳細資訊，請參閱 [定義選取集合](./defining-selection-sets.md)。

如需自訂控制項視圖元件的詳細資訊，請參閱 [建立自訂控制項](./creating-custom-controls.md)。

## <a name="see-also"></a>另請參閱

[適用于 CustomEntry 的之 entryselectedby 元素 (格式) ](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[自訂控制項視圖](./creating-custom-controls.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
