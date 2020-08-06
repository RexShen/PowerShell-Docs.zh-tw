---
title: View (Format) 的控制項之之 entryselectedby 的 SelectionSetName 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5c762a626fff746266919d1f7fcb991a8cdbcdf2
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787541"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-view-format"></a>檢視之控制項的 EntrySelectedBy 的 SelectionSetName 元素 (格式)

指定一組使用此控制項定義的 .NET 類型。 定義可供視圖使用的控制項時，會使用這個元素。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) 控制項專案 (格式控制項的) 控制項專案 (格式) CustomControl 專案控制項的控制項 () 格式的 CustomEntries 元素 CustomControl for View (Format) CustomEntry 元素 for CustomEntries for view (Format) 之 entryselectedby 元素 for CustomEntry for view (format) SelectionSetName 元素 for view (Format) 的控制項

## <a name="syntax"></a>語法

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `SelectionSetName` 。

### <a name="attributes"></a>屬性

無

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[檢視之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|定義使用此控制項定義的 .NET 類型，或必須存在才能使用此定義的條件。|

## <a name="text-value"></a>文字值

指定選取範圍的名稱。

## <a name="remarks"></a>備註

每個控制項定義都必須定義至少一個型別名稱、選擇集或選取條件。

當您想要定義多個視圖中使用的一組物件時，通常會使用選取範圍集。 如需定義選取集的詳細資訊，請參閱[定義選取範圍集合](./defining-selection-sets.md)。

## <a name="see-also"></a>另請參閱

[檢視之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
