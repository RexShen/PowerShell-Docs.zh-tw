---
title: PropertyName ItemSelectionCondition 如 ListControl （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5e707ae-3c84-4ceb-ba31-56b3ffde6d6c
caps.latest.revision: 7
ms.openlocfilehash: b15e26e18126f69eee7c3a857f9a461d4bdf5848
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064742"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a>ListControl 之 ItemSelectionCondition 的 PropertyName 元素 (格式)

指定觸發條件的.NET 屬性。 當這個屬性是存在，或當其評估結果為`true`、 符合條件，和在所用的檢視。 定義清單檢視時，會使用這個項目。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） ListControl 項目 （格式） ListEntries 項目 （格式） ListEntry 項目如 ListControl （格式） 的 ListItem ListEntry ListControl （格式） ListItems 項目ListControl （格式） ItemSelectionCondition ListControls PropertyName 元素 ItemSelectionCondition ListControl （格式） 的 ListItem 元素 ListItems 的項目

## <a name="syntax"></a>語法

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目，以及的父項目`PropertyName`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[ItemSelectionCondition ListControl （格式） 的 ListItem 元素](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a>文字值

指定其值會顯示屬性的名稱。

## <a name="remarks"></a>備註

如果會使用這個項目，您無法指定[ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)時定義的選取項目條件的項目。

## <a name="see-also"></a>另請參閱

[ItemSelectionCondition ListIControl （格式） 的指令碼區塊項目](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[ItemSelectionCondition ListControl （格式） 的 ListItem 元素](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
