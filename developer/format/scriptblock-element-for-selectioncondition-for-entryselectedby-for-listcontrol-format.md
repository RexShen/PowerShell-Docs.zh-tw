---
title: 針對 ListControl （格式） 的 EntrySelectedBy SelectionCondition 的指令碼區塊項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a1adad7-e864-4892-9d26-a6476a9698d2
caps.latest.revision: 7
ms.openlocfilehash: b65d953169f6daf15fb617ce4d0303cf4cb584ee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064345"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a>ListControl 之 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素 (格式)

指定的指令碼，就會觸發條件。 此指令碼會評估為`true`、 符合條件，和使用清單項目。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） ListControl 項目 （格式） ListEntries 項目 （格式） ListEntry 項目 （格式） EntrySelectedBy 項目用於 ListEntry （格式） SelectionCondition 元素EntrySelectedBy ListEntry （格式） 的 EntrySelectedBy 的 SelectionCondition ListEntry （格式） ScriptBlock 元素

## <a name="syntax"></a>語法

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
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
|[ListEntry （格式） 的 EntrySelectedBy SelectionCondition 項目](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|定義要使用此清單項目必須存在的條件。|

## <a name="text-value"></a>文字值

指定評估指令碼。

## <a name="remarks"></a>備註

選取條件必須指定至少一個指令碼或屬性名稱來評估，但不能同時指定。 (如需如何使用選擇條件的詳細資訊，請參閱[定義條件時檢視項目或項目用](./defining-conditions-for-displaying-data.md)。)

清單檢視的其他元件的相關資訊，請參閱[清單檢視](./creating-a-list-view.md)。

## <a name="see-also"></a>另請參閱

[ListEntry 項目 （格式）](./listentry-element-for-listcontrol-format.md)

[PropertyName ListEntry （格式） 的 EntrySelectedBy 的 SelectionCondition 的項目](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[ListEntry （格式） 的 EntrySelectedBy SelectionCondition 項目](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[清單檢視](./creating-a-list-view.md)

[使用 檢視項目或項目時定義的條件](./defining-conditions-for-displaying-data.md)

[撰寫 Windows PowerShell 格式和類型的檔案](./writing-a-powershell-formatting-file.md)
