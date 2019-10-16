---
title: ListControl 之 ItemSelectionCondition 的 PropertyName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5e707ae-3c84-4ceb-ba31-56b3ffde6d6c
caps.latest.revision: 7
ms.openlocfilehash: b15e26e18126f69eee7c3a857f9a461d4bdf5848
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362387"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a>ListControl 之 ItemSelectionCondition 的 PropertyName 元素 (格式)

指定觸發條件的 .NET 屬性。 當這個屬性存在或評估為 `true` 時，就會符合條件，並使用此視圖。 定義清單視圖時，會使用這個元素。

Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） ListControl 專案（格式） ListEntries 元素（格式） ListEntry 元素（用於 ListControl 的 ListItems （格式） ListEntry 元素）ListItems for ListControl （Format） ItemSelectionCondition 元素的元素，適用于 ItemSelectionCondition for ListControl 的 ListControls PropertyName 元素（格式）

## <a name="syntax"></a>語法

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `PropertyName` 元素的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ListControl 之專案的 ItemSelectionCondition 元素（格式）](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a>文字值

指定顯示其值的屬性名稱。

## <a name="remarks"></a>備註

如果使用這個元素，則在定義選取條件時，不能指定[ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)元素。

## <a name="see-also"></a>另請參閱

[ListIControl 之 ItemSelectionCondition 的 ScriptBlock 元素（格式）](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[ListControl 之專案的 ItemSelectionCondition 元素（格式）](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
