---
title: WideControl (格式的 WideEntry 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 13dd1f6ad7ac1e9d8d0524f0a0f18fe80ffaf8e2
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780010"
---
# <a name="wideentry-element-for-widecontrol-format"></a>WideControl 的 WideEntry 元素 (格式)

提供寬視圖的定義。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) WideControl 元素 (格式) WideEntries 專案 (格式) WideEntry 專案 (格式) 

## <a name="syntax"></a>語法

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `WideEntry` 。 您必須指定單一 `WideItem` 子項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[WideEntry 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-wideentry-format.md)|選擇性項目。<br /><br /> 定義使用此寬專案定義的 .NET 類型，或必須存在才能使用此定義的條件。|
|[之 wideitem 元素 (格式) ](./wideitem-element-for-widecontrol-format.md)|必要元素。<br /><br /> 定義顯示其值的屬性或腳本。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[WideEntries 元素 (格式) ](./wideentries-element-for-widecontrol-format.md)|提供寬視圖的定義。|

## <a name="remarks"></a>備註

寬型視圖是一種清單格式，可顯示每個物件的單一屬性值或腳本值。 不同于其他類型的視圖，您只能為每個 view 定義指定一個 item 元素。 如需有關寬視圖之其他元件的詳細資訊，請參閱[建立寬視圖](./creating-a-wide-view.md)。

## <a name="example"></a>範例

下列範例顯示 `WideEntry` 定義單一專案的元素 `WideItem` 。 `WideItem`元素會定義屬性，其值會顯示在視圖中。

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

如需寬視圖的完整範例，請參閱[寬視圖 (基本) ](./wide-view-basic.md)。

## <a name="see-also"></a>另請參閱

[建立寬型檢視](./creating-a-wide-view.md)

[WideEntry (格式的 SelectionCondition 元素) ](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[WideEntry (格式的 SelectionSetName 元素) ](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[WideEntry (格式的 TypeName 元素) ](./typename-element-for-entryselectedby-for-wideentry-format.md)

[WideEntries 元素 (格式) ](./wideentries-element-for-widecontrol-format.md)

[之 wideitem 元素 (格式) ](./wideitem-element-for-widecontrol-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
