---
title: WideControl (格式) 的之 entryselectedby 的 SelectionSetName 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 546225b0619ebec83d04a7e27bbc298ffef0a14d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785246"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a>WideControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)

為定義指定一組 .NET 物件。 每當顯示這些物件的其中一個時，就會使用定義。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) WideControl 專案 (格式) WideEntries 專案 (格式) WideEntry 專案 (格式) 之 entryselectedby 元素用於 WideEntry (格式) SelectionSetName 元素 (

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
|[WideEntry 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-wideentry-format.md)|定義使用此寬專案的 .NET 類型，或必須存在才能使用此專案的條件。|

## <a name="text-value"></a>文字值

指定選取範圍的名稱。

## <a name="remarks"></a>備註

每個定義都必須指定一個型別名稱、選擇集或選取條件。

當您想要定義多個視圖中使用的一組物件時，通常會使用選取範圍集。 例如，您可能會想要建立一組相同物件的資料表視圖和清單視圖。 如需定義選取集的詳細資訊，請參閱[定義視圖的物件集合](./defining-selection-sets.md)。

如需有關寬視圖之其他元件的詳細資訊，請參閱[建立寬視圖](./creating-a-wide-view.md)。

## <a name="see-also"></a>另請參閱

[建立寬型檢視](./creating-a-wide-view.md)

[定義選取範圍集合](./defining-selection-sets.md)

[WideEntry 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-wideentry-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
