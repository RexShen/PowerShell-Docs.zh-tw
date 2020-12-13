---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl 之 ListItem 的 ItemSelectionCondition 元素 (格式)
description: ListControl 之 ListItem 的 ItemSelectionCondition 元素 (格式)
ms.openlocfilehash: 13d925da10c2386123983d52b109c03a0c3c63ab
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667805"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a>ListControl 之 ListItem 的 ItemSelectionCondition 元素 (格式)

定義必須存在才能使用此清單專案的條件。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) ListControl 元素 (format) ListEntries 元素 for ListControl (Format) ListEntry for ListEntries for ListControl (ListItems 專案 ListEntry) 格式 (ListControl 元素適用于 ListItems 的 ListControl) 格式 (

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

您可以為此條件指定一個屬性名稱或腳本，但不能同時指定兩者。

## <a name="see-also"></a>另請參閱

[ListControl 之 ListItems 的 ListItem 元素 (格式)](./listitem-element-for-listitems-for-listcontrol-format.md)

[ListControl 之 ItemSelectionCondition 的 PropertyName 元素 (格式)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[ListControl 之 ItemSelectionCondition 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
