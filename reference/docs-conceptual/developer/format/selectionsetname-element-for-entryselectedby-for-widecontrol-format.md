---
ms.date: 09/13/2016
ms.topic: reference
title: WideControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)
description: WideControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)
ms.openlocfilehash: bf6a44bb733421f36a9140d0ec10e61aedfbda6a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651692"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a>WideControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)

指定定義的一組 .NET 物件。 每當顯示這些物件的其中一個時，就會使用定義。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) WideControl 元素 (格式) WideEntries 元素 (格式) WideEntry 專案 (格式) 之 entryselectedby 專案 (格式) WideEntry 專案 SelectionSetName 的之 entryselectedby (格式) 

## <a name="syntax"></a>語法

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a>屬性和項目

下列章節說明屬性、子專案和元素的父元素 `SelectionSetName` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[WideEntry 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-wideentry-format.md)|定義使用此寬專案的 .NET 型別，或必須存在才能使用此專案的條件。|

## <a name="text-value"></a>文字值

指定選項群組的名稱。

## <a name="remarks"></a>備註

每個定義都必須指定一個類型名稱、選取集或選取條件。

當您想要定義多個視圖中使用的一組物件時，通常會使用選取集。 例如，您可能會想要為相同的物件集建立資料表視圖和清單視圖。 如需定義選擇集的詳細資訊，請參閱 [定義視圖的物件集](./defining-selection-sets.md)。

如需更多有關廣泛視圖的元件的詳細資訊，請參閱 [建立廣泛的觀點](./creating-a-wide-view.md)。

## <a name="see-also"></a>另請參閱

[建立寬型檢視](./creating-a-wide-view.md)

[定義選取範圍集合](./defining-selection-sets.md)

[WideEntry 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-wideentry-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
