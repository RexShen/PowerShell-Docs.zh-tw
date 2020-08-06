---
title: ItemSelectionCondition for ListControl (格式的 PropertyName 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 8bdbb05326f7ff5ccffa46215631a5c954080dc1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780860"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a>ListControl 之 ItemSelectionCondition 的 PropertyName 元素 (格式)

指定觸發條件的 .NET 屬性。 當這個屬性存在或評估為時 `true` ，就會符合條件，並使用此視圖。 定義清單視圖時，會使用這個元素。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ListControl 專案 (格式) ListEntries 專案 (格式) ListControl (格式) ListItems 專案（ListEntry 的 ListControl 的 ListItems 專案 (格式) ListControl 元素，ItemSelectionCondition 的 ListControls 的 PropertyName 元素 (格式 ItemSelectionCondition) 

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

如果使用這個元素，則在定義選取條件時，不能指定[ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)元素。

## <a name="see-also"></a>另請參閱

[ItemSelectionCondition for ListIControl (格式的 ScriptBlock 元素) ](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[ListControl 之 ListItem 的 ItemSelectionCondition 元素 (格式)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
