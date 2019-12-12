---
title: WideEntry 的之 entryselectedby 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0c98933-b7a5-4205-b811-06c0b0bf8988
caps.latest.revision: 9
ms.openlocfilehash: 54c7c261a23075721cd7bce75e530150dc0e0212
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363327"
---
# <a name="entryselectedby-element-for-wideentry-format"></a>WideEntry 的 EntrySelectedBy 元素 (格式)

定義使用此寬視圖定義的 .NET 類型，或必須存在才能使用此定義的條件。

Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） WideControl 元素（格式） WideEntries 元素（格式） WideEntry 元素（格式）之 entryselectedby 元素（格式）

## <a name="syntax"></a>語法

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `EntrySelectedBy` 專案的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[WideEntry 之之 entryselectedby 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|選擇性項目。<br /><br /> 定義必須存在的條件，才能使用此寬視圖定義。|
|[WideEntry 之之 entryselectedby 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|選擇性項目。<br /><br /> 指定一組使用此寬視圖定義的 .NET 類型。|
|[WideEntry 之之 entryselectedby 的 TypeName 元素（格式）](./typename-element-for-entryselectedby-for-wideentry-format.md)|選擇性項目。<br /><br /> 指定使用此寬視圖定義的 .NET 類型。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[WideEntry 元素（格式）](./wideentry-element-for-widecontrol-format.md)|提供寬視圖的定義。|

## <a name="remarks"></a>備註

您必須為寬視圖定義指定至少一個類型、選取範圍或選取條件。 您可以使用的子項目數目沒有上限。

選取條件是用來定義要使用的定義必須存在的條件，例如，當物件具有特定屬性，或特定屬性值或腳本值評估為 `true`時。 如需選取條件的詳細資訊，請參閱[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。

如需有關寬視圖之其他元件的詳細資訊，請參閱[建立寬視圖](./creating-a-wide-view.md)。

## <a name="see-also"></a>另請參閱

[WideEntry 元素（格式）](./wideentry-element-for-widecontrol-format.md)

[WideEntry 之之 entryselectedby 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[WideEntry 之之 entryselectedby 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[WideEntry 之之 entryselectedby 的 TypeName 元素（格式）](./typename-element-for-entryselectedby-for-wideentry-format.md)

[建立寬型視圖](./creating-a-wide-view.md)

[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
