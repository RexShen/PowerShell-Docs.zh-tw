---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl 之 ItemSelectionCondition 的 ScriptBlock 元素 (格式)
description: ListControl 之 ItemSelectionCondition 的 ScriptBlock 元素 (格式)
ms.openlocfilehash: 1e518f898e0e1e62ca64f9897b1323cc6dd89ae9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665061"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a>ListControl 之 ItemSelectionCondition 的 ScriptBlock 元素 (格式)

指定觸發條件的腳本。 當此腳本評估為時 `true` ，就會符合條件，並且會使用清單專案。 定義清單視圖時，會使用這個元素。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) ListControl 元素 (format) ListEntries 元素 for ListControl (Format) ListEntry 專案 for ListEntries for ListControl (format) ListItems for ListEntry for ListControl 的 ListItems 專案 (格式) ItemSelectionCondition 的 ListControl 專案 (格式) ItemSelectionCondition 專案的 ListControl (格式) 元素 (

## <a name="syntax"></a>語法

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `ScriptBlock` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[ListControl 之 ListItem 的 ItemSelectionCondition 元素 (格式)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|定義必須存在才能使用此清單專案的條件。|

## <a name="text-value"></a>文字值

指定要評估的腳本。

## <a name="remarks"></a>備註

如果使用此元素，則在 `PropertyName` 定義選取條件時，不能指定元素。

## <a name="see-also"></a>另請參閱

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
