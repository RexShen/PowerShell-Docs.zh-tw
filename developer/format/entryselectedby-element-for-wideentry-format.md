---
title: EntrySelectedBy WideEntry （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0c98933-b7a5-4205-b811-06c0b0bf8988
caps.latest.revision: 9
ms.openlocfilehash: 54c7c261a23075721cd7bce75e530150dc0e0212
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066170"
---
# <a name="entryselectedby-element-for-wideentry-format"></a>WideEntry 的 EntrySelectedBy 元素 (格式)

定義使用此定義的寬型檢視或條件必須存在於要使用此定義的.NET 類型。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） WideControl 項目 （格式） WideEntries 項目 （格式） WideEntry 項目 （格式） EntrySelectedBy 項目 WideEntry （格式）

## <a name="syntax"></a>語法

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`EntrySelectedBy`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[WideEntry （格式） 的 EntrySelectedBy SelectionCondition 項目](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|選擇性的項目。<br /><br /> 定義要使用此寬型檢視定義必須存在的條件。|
|[WideEntry （格式） 的 EntrySelectedBy SelectionSetName 項目](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|選擇性的項目。<br /><br /> 指定一組使用此寬型檢視定義的.NET 型別。|
|[WideEntry （格式） 的 EntrySelectedBy TypeName 項目](./typename-element-for-entryselectedby-for-wideentry-format.md)|選擇性的項目。<br /><br /> 指定使用此寬型檢視定義的.NET 型別。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[WideEntry 項目 （格式）](./wideentry-element-for-widecontrol-format.md)|提供寬型檢視的定義。|

## <a name="remarks"></a>備註

您必須指定至少一個型別、 選取項目集或選擇條件的寬型檢視定義。 沒有任何子項目的，您可以使用數字的最大限制。

選擇條件用來定義要使用，例如當物件具有特定屬性的定義必須存在的條件，或特定的屬性值或指令碼的值評估為`true`。 如需有關選擇條件的詳細資訊，請參閱[定義的條件，顯示資料](./defining-conditions-for-displaying-data.md)。

寬型檢視的其他元件的相關資訊，請參閱[建立寬型檢視](./creating-a-wide-view.md)。

## <a name="see-also"></a>另請參閱

[WideEntry 項目 （格式）](./wideentry-element-for-widecontrol-format.md)

[WideEntry （格式） 的 EntrySelectedBy SelectionCondition 項目](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[WideEntry （格式） 的 EntrySelectedBy SelectionSetName 項目](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[WideEntry （格式） 的 EntrySelectedBy TypeName 項目](./typename-element-for-entryselectedby-for-wideentry-format.md)

[建立寬型檢視](./creating-a-wide-view.md)

[定義用於顯示資料的條件](./defining-conditions-for-displaying-data.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
