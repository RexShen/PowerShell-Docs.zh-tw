---
title: ListControl (格式之專案的 ItemSelectionCondition 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: f5c388928668e03b96923130fb5849f637548f12
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783614"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a>ListControl 之 ListItem 的 ItemSelectionCondition 元素 (格式)

定義必須存在才能使用此清單專案的條件。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ListControl 專案 (格式) ListControl (格式) ListEntry 元素，ListEntries for ListControl (format) ListItems 元素用於 ListEntry 的 ListControl (format) ListItems 元素的 ListControl (format) 

## <a name="syntax"></a>語法

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `ItemSelectionCondition` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[ListControl 之 ItemSelectionCondition 的 PropertyName 元素 (格式)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|選擇性項目。<br /><br /> 指定觸發條件的 .NET 屬性。|
|[ListControl 之 ItemSelectionCondition 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|選擇性項目。<br /><br /> 指定觸發條件的腳本。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[ListControl 之 ListItems 的 ListItem 元素 (格式)](./listitem-element-for-listitems-for-listcontrol-format.md)|定義屬性或腳本，其值會顯示在清單視圖的資料列中。|

## <a name="remarks"></a>備註

您可以為此條件指定一個屬性名稱或腳本，但不能同時指定這兩者。

## <a name="see-also"></a>另請參閱

[ListControl 之 ListItems 的 ListItem 元素 (格式)](./listitem-element-for-listitems-for-listcontrol-format.md)

[ListControl 之 ItemSelectionCondition 的 PropertyName 元素 (格式)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[ListControl 之 ItemSelectionCondition 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
