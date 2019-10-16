---
title: ListControl 之 ItemSelectionCondition 的 ScriptBlock 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c929a6df-d050-416a-9de0-e913dd5a035c
caps.latest.revision: 8
ms.openlocfilehash: a0768a9c1ac66cd9dcf1848c4b031ccbc722b4c2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362097"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a>ListControl 之 ItemSelectionCondition 的 ScriptBlock 元素 (格式)

指定觸發條件的腳本。 當此腳本評估為 `true` 時，即符合條件，且會使用清單專案。 定義清單視圖時，會使用這個元素。

Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） ListControl 元素（format） ListEntries 元素（適用于 ListEntry 的 ListEntries for ListControl （Format） ListItems 元素） ListControl （Format） ListEntry 元素適用于 ListItems 的 ListControl （Format） [清單控制項（格式）] 元素，用於 ItemSelectionCondition for ListControl 的 ListControl （Format） ScriptBlock 元素（格式）

## <a name="syntax"></a>語法

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `ScriptBlock` 元素的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ListControl 之專案的 ItemSelectionCondition 元素（格式）](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|定義必須存在才能使用此清單專案的條件。|

## <a name="text-value"></a>文字值

指定要評估的腳本。

## <a name="remarks"></a>備註

如果使用這個元素，則在定義選取條件時，不能指定 `PropertyName` 元素。

## <a name="see-also"></a>另請參閱

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
