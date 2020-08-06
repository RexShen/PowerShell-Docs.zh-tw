---
title: SelectionCondition for 之 entryselectedby for WideControl (Format 的 TypeName 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5021f665b994581f9ff982e13af922d7940ebf2b
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783308"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a>WideControl 之 EntrySelectedBy 的 SelectionCondition 的 TypeName 元素 (格式)

指定觸發條件的 .NET 類型。 當此型別存在時，就會使用定義。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) WideControl 專案 (格式) WideEntries 專案 (格式) WideEntry 專案 (格式) 之 entryselectedby 元素（WideEntry 的 SelectionCondition 的之 entryselectedby (格式) WideEntry for SelectionCondition 的之 entryselectedby (格式) 

## <a name="syntax"></a>語法

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `TypeName` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[WideEntry (格式的之 entryselectedby 的 SelectionCondition 元素) ](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|定義必須存在才能使用此寬專案的條件。|

## <a name="text-value"></a>文字值

指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo` 。

## <a name="remarks"></a>備註

選取條件可以指定 .NET 類型或選擇集，但不能同時指定兩者。 如需如何使用選取條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。

如需有關寬視圖之其他元件的詳細資訊，請參閱[建立寬視圖](./creating-a-wide-view.md)。

## <a name="see-also"></a>另請參閱

[建立寬型檢視](./creating-a-wide-view.md)

[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)

[WideEntry (格式的之 entryselectedby 的 SelectionCondition 元素) ](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[WideEntry 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
