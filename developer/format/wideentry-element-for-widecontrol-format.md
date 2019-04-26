---
title: WideEntry WideControl （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 014763cb-7716-4931-899c-8375b5d7a3dd
caps.latest.revision: 15
ms.openlocfilehash: d1d13b5c3436871053353814293d9163ea13c7fb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083666"
---
# <a name="wideentry-element-for-widecontrol-format"></a>WideControl 的 WideEntry 元素 (格式)

提供寬型檢視的定義。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） WideControl 項目 （格式） WideEntries 項目 （格式） WideEntry 項目 （格式）

## <a name="syntax"></a>語法

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`WideEntry`項目。 您必須指定單一`WideItem`子項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[EntrySelectedBy WideEntry （格式） 的項目](./entryselectedby-element-for-wideentry-format.md)|選擇性的項目。<br /><br /> 定義使用此寬的項目定義或必須存在於要使用此定義條件的.NET 類型。|
|[WideItem 項目 （格式）](./wideitem-element-for-widecontrol-format.md)|必要項目。<br /><br /> 定義屬性或其值會顯示指令碼。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[WideEntries 項目 （格式）](./wideentries-element-for-widecontrol-format.md)|提供的寬型檢視的定義。|

## <a name="remarks"></a>備註

寬型檢視是顯示單一屬性值或每個物件的指令碼值以清單格式。 不同於其他類型的檢視中，您可以指定只有一個項目元素的每個檢視定義。 寬型檢視的其他元件的相關資訊，請參閱[建立寬型檢視](./creating-a-wide-view.md)。

## <a name="example"></a>範例

下列範例所示`WideEntry`項目，定義單一`WideItem`項目。 `WideItem`項目會定義在檢視中顯示其值的屬性。

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

寬型檢視的完整範例，請參閱[（基本） 的寬型檢視](./wide-view-basic.md)。

## <a name="see-also"></a>另請參閱

[建立寬型檢視](./creating-a-wide-view.md)

[SelectionCondition WideEntry （格式） 的項目](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[SelectionSetName WideEntry （格式） 的項目](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[TypeName WideEntry （格式） 的項目](./typename-element-for-entryselectedby-for-wideentry-format.md)

[WideEntries 項目 （格式）](./wideentries-element-for-widecontrol-format.md)

[WideItem 項目 （格式）](./wideitem-element-for-widecontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
