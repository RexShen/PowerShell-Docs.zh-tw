---
title: WideControl 的 WideEntry 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 014763cb-7716-4931-899c-8375b5d7a3dd
caps.latest.revision: 15
ms.openlocfilehash: d1d13b5c3436871053353814293d9163ea13c7fb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367897"
---
# <a name="wideentry-element-for-widecontrol-format"></a>WideControl 的 WideEntry 元素 (格式)

提供寬視圖的定義。

Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（格式） WideControl 元素（格式） WideEntries 元素（格式） WideEntry 元素（格式）

## <a name="syntax"></a>語法

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `WideEntry` 專案的父元素。 您必須指定單一 `WideItem` 子項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[WideEntry 的之 entryselectedby 元素（格式）](./entryselectedby-element-for-wideentry-format.md)|選擇性項目。<br /><br /> 定義使用此寬專案定義的 .NET 類型，或必須存在才能使用此定義的條件。|
|[之 wideitem 元素（格式）](./wideitem-element-for-widecontrol-format.md)|必要項目。<br /><br /> 定義顯示其值的屬性或腳本。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[WideEntries 元素（格式）](./wideentries-element-for-widecontrol-format.md)|提供寬視圖的定義。|

## <a name="remarks"></a>備註

寬型視圖是一種清單格式，可顯示每個物件的單一屬性值或腳本值。 不同于其他類型的視圖，您只能為每個 view 定義指定一個 item 元素。 如需有關寬視圖之其他元件的詳細資訊，請參閱[建立寬視圖](./creating-a-wide-view.md)。

## <a name="example"></a>範例

下列範例顯示定義單一 `WideItem` 元素的 `WideEntry` 專案。 `WideItem` 元素會定義屬性，其值會顯示在視圖中。

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

如需寬視圖的完整範例，請參閱[寬視圖（基本）](./wide-view-basic.md)。

## <a name="see-also"></a>另請參閱

[建立寬型視圖](./creating-a-wide-view.md)

[WideEntry 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[WideEntry 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[WideEntry 的 TypeName 元素（格式）](./typename-element-for-entryselectedby-for-wideentry-format.md)

[WideEntries 元素（格式）](./wideentries-element-for-widecontrol-format.md)

[之 wideitem 元素（格式）](./wideitem-element-for-widecontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
