---
title: ScriptBlock ListControl （格式） 的 ListItem 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74e30938-00ef-46fd-84e5-f0a83706a50e
caps.latest.revision: 11
ms.openlocfilehash: 76b600256af3f957f7fe0578f9fef810262aa5d5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855554"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a>ListControl 之 ListItem 的 ScriptBlock 元素 (格式)

指定資料列中顯示其值的指令碼。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） ListControl 項目 （格式） ListEntries 項目 ListEntry ListControl （格式） ListItems 元素 ListEntries ListControl （格式） ListEntry 項目ListControl （格式） ScriptBlock ListControl （格式） 的 ListItem 元素 ListItems ListControl （格式） ListItem 元素

## <a name="syntax"></a>語法

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`ScriptBlock`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ListItem 項目 （格式）](./listitem-element-for-listitems-for-listcontrol-format.md)|定義屬性或其值會顯示 [清單] 檢視的資料列中的指令碼。|

## <a name="text-value"></a>文字值

指定資料列中顯示其值的指令碼。

## <a name="remarks"></a>備註

當指定這個項目時，您無法指定[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)項目。

如需指定清單檢視中的指令碼的詳細資訊，請參閱[清單檢視](./creating-a-list-view.md)。

## <a name="example"></a>範例

下列範例示範如何指定其值會顯示其屬性。

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a>另請參閱

[PropertyName ListControl （格式） 的 ListItem 元素](./propertyname-element-for-listitem-for-listcontrol-format.md)

[建立清單檢視](./creating-a-list-view.md)

[ListItems ListControl （格式） 的 ListItem 項目](./listitem-element-for-listitems-for-listcontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
