---
title: WideItem WideControl （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862624"
---
# <a name="wideitem-element-for-widecontrol-format"></a>WideControl 的 WideItem 元素 (格式)

定義屬性或其值會顯示指令碼。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） WideControl 項目 （格式） WideEntries 項目 （格式） WideEntry 項目 （格式） WideItem 項目 （格式）

## <a name="syntax"></a>語法

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`WideItem`項目。 `FormatString` 元素為選擇性。 不過，您必須指定`PropertyName`或`ScriptBlock`項目，但是您無法同時指定兩者。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[WideControl （格式） 的 WideItem 的 FormatString 元素](./formatstring-element-for-wideitem-for-widecontrol-format.md)|選擇性的項目。<br /><br /> 指定之格式模式所定義的屬性或指令碼的值在檢視中的顯示方式。|
|[PropertyName WideItem （格式） 的項目](./propertyname-element-for-wideitem-for-widecontrol-format.md)|指定其值會顯示在寬型檢視物件的屬性。|
|[ScriptBlock WideItem （格式） 的項目](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|指定其值會顯示在寬型檢視的指令碼。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[WideEntry 項目 （格式）](./wideentry-element-for-widecontrol-format.md)|提供寬型檢視的定義。|

## <a name="remarks"></a>備註

如需詳細的寬型檢視元件的相關資訊，請參閱[寬型檢視](./creating-a-wide-view.md)。

## <a name="example"></a>範例

下列範例所示`WideEntry`項目，定義單一`WideItem`項目。 `WideItem`項目定義之屬性或其值會顯示在檢視中的指令碼。

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

寬型檢視的完整範例，請參閱[（基本） 的寬型檢視](./wide-view-basic.md)。

## <a name="see-also"></a>另請參閱

[WideControl （格式） 的 WideItem 的 FormatString 元素](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[PropertyName WideItem （格式） 的項目](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[ScriptBlock WideItem （格式） 的項目](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[WideEntry 項目 （格式）](./wideentry-element-for-widecontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
