---
title: EntrySelectedBy CustomEntry 組態 （格式） 的控制項的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30abae8f-c7f7-479d-ad85-19e07ddef204
caps.latest.revision: 10
ms.openlocfilehash: 81eca4f66f0057074612f2d60482b45adc36357b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066289"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a>設定之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)

定義使用的通用控制項或條件必須存在於要使用這個控制項定義的.NET 類型。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

組態 （格式） 的組態 （格式） 的組態 （CustomControl 的 CustomEntries 項目控制項的組態 （格式） CustomControl 項目控制項的控制項項目的組態項目 （格式） 的控制項項目CustomControl CustomEntry 控制項組態 （格式） 的組態 （格式） EntrySelectedBy 元素的控制項的格式） CustomEntry 項目

## <a name="syntax"></a>語法

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`EntrySelectedBy`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[SelectionCondition EntrySelectedBy 組態 （格式） 的控制項的項目](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|選擇性的項目。<br /><br /> 定義必須存在通用控制項定義要使用的條件。|
|[SelectionSetName EntrySelectedBy 組態 （格式） 的控制項的項目](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|選擇性的項目。<br /><br /> 指定一組使用通用控制項的這個定義的.NET 型別。|
|[TypeName EntrySelectedBy 組態 （格式） 的控制項的項目](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|選擇性的項目。<br /><br /> 指定會使用通用控制項的這個定義的.NET 型別。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[CustomEntry CustomControl 組態 （格式） 的控制項的項目](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|提供通用控制項的定義。|

## <a name="remarks"></a>備註

最小值，每個定義必須至少一個.NET 類型、 選取項目集或指定的選取範圍條件。 沒有任何類型、 選取項目集或選擇條件，您可以指定數目的最大限制。

## <a name="see-also"></a>另請參閱

[SelectionCondition EntrySelectedBy 組態 （格式） 的控制項的項目](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[SelectionSetName EntrySelectedBy 組態 （格式） 的控制項的項目](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[CustomEntry CustomControl 組態 （格式） 的控制項的項目](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[TypeName EntrySelectedBy 組態 （格式） 的控制項的項目](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
