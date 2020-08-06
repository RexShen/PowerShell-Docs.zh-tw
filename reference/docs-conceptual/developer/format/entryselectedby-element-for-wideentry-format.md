---
title: WideEntry (格式的之 entryselectedby 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: ba0a776839c39d753d12859335388c5326639fd4
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774077"
---
# <a name="entryselectedby-element-for-wideentry-format"></a>WideEntry 的 EntrySelectedBy 元素 (格式)

定義使用此寬視圖定義的 .NET 類型，或必須存在才能使用此定義的條件。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) WideControl 元素 (格式) WideEntries 專案 (格式) WideEntry 專案 (格式) 之 entryselectedby 元素用於 WideEntry (格式) 

## <a name="syntax"></a>語法

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `EntrySelectedBy` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[WideEntry (格式的之 entryselectedby 的 SelectionCondition 元素) ](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|選擇性項目。<br /><br /> 定義必須存在的條件，才能使用此寬視圖定義。|
|[WideEntry (格式的之 entryselectedby 的 SelectionSetName 元素) ](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|選擇性項目。<br /><br /> 指定一組使用此寬視圖定義的 .NET 類型。|
|[WideEntry 之 EntrySelectedBy 的 TypeName 元素 (格式)](./typename-element-for-entryselectedby-for-wideentry-format.md)|選擇性項目。<br /><br /> 指定使用此寬視圖定義的 .NET 類型。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[WideEntry 元素 (格式) ](./wideentry-element-for-widecontrol-format.md)|提供寬視圖的定義。|

## <a name="remarks"></a>備註

您必須為寬視圖定義指定至少一個類型、選取範圍或選取條件。 您可以使用的子項目數目沒有上限。

選取條件是用來定義要使用的定義必須存在的條件，例如，當物件具有特定屬性或特定屬性值或腳本值評估為時 `true` 。 如需選取條件的詳細資訊，請參閱[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。

如需有關寬視圖之其他元件的詳細資訊，請參閱[建立寬視圖](./creating-a-wide-view.md)。

## <a name="see-also"></a>另請參閱

[WideEntry 元素 (格式) ](./wideentry-element-for-widecontrol-format.md)

[WideEntry (格式的之 entryselectedby 的 SelectionCondition 元素) ](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[WideEntry (格式的之 entryselectedby 的 SelectionSetName 元素) ](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[WideEntry 之 EntrySelectedBy 的 TypeName 元素 (格式)](./typename-element-for-entryselectedby-for-wideentry-format.md)

[建立寬型檢視](./creating-a-wide-view.md)

[定義用於顯示資料的條件](./defining-conditions-for-displaying-data.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
