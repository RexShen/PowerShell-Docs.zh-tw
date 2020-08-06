---
title: 之 entryselectedby 之控制項的 SelectionSetName 元素，用於設定 (格式) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 72072d8d13e6ca22afdb9bca2e0237d29ba0594f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787558"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format"></a>設定之控制項的 EntrySelectedBy 的 SelectionSetName 元素 (格式)

指定一組使用此控制項定義的 .NET 類型。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

Configuration 專案 (格式) Controls 設定的控制項元素 (格式設定的控制項) 控制項專案 (格式) 設定 (格式的 CustomControl 的 CustomEntries 專案設定) 格式 (CustomControl 元素適用于設定) 格式 (之 entryselectedby 專案的 CustomEntry 的控制項的設定) 格式 (SelectionSetName 專案) 

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
|[設定之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|定義使用此控制項定義的 .NET 類型，或必須存在才能使用此定義的條件。|

## <a name="text-value"></a>文字值

指定選取範圍的名稱。

## <a name="remarks"></a>備註

每個控制項定義都必須定義至少一個型別名稱、選擇集或選取條件。

當您想要定義多個視圖中使用的一組物件時，通常會使用選取範圍集。 如需定義選取集的詳細資訊，請參閱[定義選取範圍集合](./defining-selection-sets.md)。

## <a name="see-also"></a>另請參閱

[設定之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
