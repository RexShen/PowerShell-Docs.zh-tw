---
title: ListControl 之專案的 ItemSelectionCondition 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2668aea-37e9-4753-a4e9-7980ae5ec2eb
caps.latest.revision: 10
ms.openlocfilehash: 6bc0ccbcc5bd62429f63ed220da66dc66f44f7ca
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365187"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a>ListControl 之 ListItem 的 ItemSelectionCondition 元素 (格式)

定義必須存在才能使用此清單專案的條件。

Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） ListControl 元素（format） ListEntries 元素（適用于 ListEntry 的 ListEntries for ListControl （Format） ListItems 元素） ListControl （Format） ListEntry 元素適用于 ListItems 之 ListControl （Format） ItemSelectionCondition 元素的 ListControl （格式）專案專案，適用于 ListControl 的專案（格式）

## <a name="syntax"></a>語法

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `ItemSelectionCondition` 元素的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[ListControl 之 ItemSelectionCondition 的 PropertyName 元素（格式）](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|選擇性元素。<br /><br /> 指定觸發條件的 .NET 屬性。|
|[ListControl 之 ItemSelectionCondition 的 ScriptBlock 元素（格式）](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|選擇性元素。<br /><br /> 指定觸發條件的腳本。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[適用于 ListControl 之 ListItems 的專案專案元素（格式）](./listitem-element-for-listitems-for-listcontrol-format.md)|定義屬性或腳本，其值會顯示在清單視圖的資料列中。|

## <a name="remarks"></a>備註

您可以為此條件指定一個屬性名稱或腳本，但不能同時指定這兩者。

## <a name="see-also"></a>另請參閱

[適用于 ListControl 之 ListItems 的專案專案元素（格式）](./listitem-element-for-listitems-for-listcontrol-format.md)

[ListControl 之 ItemSelectionCondition 的 PropertyName 元素（格式）](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[ListControl 之 ItemSelectionCondition 的 ScriptBlock 元素（格式）](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
