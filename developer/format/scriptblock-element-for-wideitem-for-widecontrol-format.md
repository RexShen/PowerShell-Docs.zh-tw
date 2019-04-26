---
title: WideItem WideControl （格式） 的指令碼區塊項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e00e8f36-76f2-49a0-9b02-3a2a7fceb2dd
caps.latest.revision: 8
ms.openlocfilehash: 6534e9dbfbe0dedf60dadd6467cff9ad9b447ba4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064198"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a>WideControl 之 WideItem 的 ScriptBlock 元素 (格式)

指定其值會顯示在寬型檢視的指令碼。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） WideControl 項目 （格式） WideEntries 項目 （格式） WideEntry 項目 （格式） WideItem 項目 （格式） 指令碼區塊項目 WideItem （格式）

## <a name="syntax"></a>語法

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`ScriptBlock`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[WideItem 項目 （格式）](./wideitem-element-for-widecontrol-format.md)|定義在寬型檢視中顯示其值的屬性或指令碼區塊。|

## <a name="text-value"></a>文字值

指定其值會顯示指令碼。

## <a name="remarks"></a>備註

如需詳細的寬型檢視元件的相關資訊，請參閱[建立寬型檢視](./creating-a-wide-view.md)。

## <a name="example"></a>範例

此範例示範`WideItem`項目，定義其值會顯示在檢視指令碼。

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a>另請參閱

[WideItem 項目 （格式）](./wideitem-element-for-widecontrol-format.md)

[建立寬型檢視](./creating-a-wide-view.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
