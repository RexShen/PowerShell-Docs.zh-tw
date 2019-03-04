---
title: ItemSelectionCondition ListControl （格式） 的 ListItem 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2668aea-37e9-4753-a4e9-7980ae5ec2eb
caps.latest.revision: 10
ms.openlocfilehash: 6bc0ccbcc5bd62429f63ed220da66dc66f44f7ca
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861864"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a>ListControl 之 ListItem 的 ItemSelectionCondition 元素 (格式)

定義要使用此清單項目必須存在的條件。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） ListControl 項目 （格式） ListEntries 項目 ListEntry ListControl （格式） ListItems 元素 ListEntries ListControl （格式） ListEntry 項目ListControl （格式） ItemSelectionCondition ListControl （格式） 的 ListItem 元素 ListItems ListControl （格式） ListItem 元素

## <a name="syntax"></a>語法

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`ItemSelectionCondition`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[PropertyName ItemSelectionCondition 如 ListControl （格式） 的項目](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|選擇性的項目。<br /><br /> 指定觸發條件的.NET 屬性。|
|[ItemSelectionCondition ListControl （格式） 的指令碼區塊項目](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|選擇性的項目。<br /><br /> 指定的指令碼，就會觸發條件。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ListItems ListControl （格式） 的 ListItem 項目](./listitem-element-for-listitems-for-listcontrol-format.md)|定義屬性或其值會顯示 [清單] 檢視的資料列中的指令碼。|

## <a name="remarks"></a>備註

您可以指定一個屬性名稱或用於這種狀況的指令碼，但不能同時指定。

## <a name="see-also"></a>另請參閱

[ListItems ListControl （格式） 的 ListItem 項目](./listitem-element-for-listitems-for-listcontrol-format.md)

[PropertyName ItemSelectionCondition 如 ListControl （格式） 的項目](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[ItemSelectionCondition ListControl （格式） 的指令碼區塊項目](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
