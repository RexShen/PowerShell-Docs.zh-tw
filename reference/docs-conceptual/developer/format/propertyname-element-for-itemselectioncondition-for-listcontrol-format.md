---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl 之 ItemSelectionCondition 的 PropertyName 元素 (格式)
description: ListControl 之 ItemSelectionCondition 的 PropertyName 元素 (格式)
ms.openlocfilehash: c515efe70afdb1c1186c0a07fe1f52dc49ad57b9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665986"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a>ListControl 之 ItemSelectionCondition 的 PropertyName 元素 (格式)

指定觸發條件的 .NET 屬性。 當這個屬性存在或評估為時， `true` 就會符合條件，並使用 view。 定義清單視圖時，會使用這個元素。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) ListControl 元素 (format) ListEntries 專案 (format) ListEntry (格式) ListControl 專案的 ListItems (格式) ListEntry 專案的 ListControl (格式) ListItems 專案 ListControl 的 ItemSelectionCondition 屬性 (格式) 

## <a name="syntax"></a>語法

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `PropertyName` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[ListControl 之 ListItem 的 ItemSelectionCondition 元素 (格式)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a>文字值

指定顯示其值的屬性名稱。

## <a name="remarks"></a>備註

如果使用此元素，則在定義選取條件時，不能指定 [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) 元素。

## <a name="see-also"></a>另請參閱

[適用于 ListIControl 的 ItemSelectionCondition 的 ScriptBlock 元素 (格式) ](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[ListControl 之 ListItem 的 ItemSelectionCondition 元素 (格式)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
