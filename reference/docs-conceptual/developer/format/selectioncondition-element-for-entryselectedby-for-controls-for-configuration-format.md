---
title: 之 entryselectedby 之控制項的 SelectionCondition 元素，用於設定 (格式) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 748aa1aa0ba603a44334d9401e9e2c0e68f14e03
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783410"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a>設定之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)

定義必須存在的條件，才能使用通用控制項定義。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

Configuration 專案 (格式) 控制設定的控制項元素 (格式設定的控制項) 控制項專案 (格式) 設定 (格式的控制項的 CustomControl 的 CustomEntries 元素) 設定 (格式) CustomControl 元素適用于之 entryselectedby for CustomEntry for SelectionCondition for configuration (之 entryselectedby 專案的 CustomEntry 元素) 設定的專案

## <a name="syntax"></a>語法

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `SelectionCondition` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[設定之控制項的 SelectionCondition 的 PropertyName 元素 (格式)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 指定觸發條件的 .NET 屬性。|
|[設定之控制項的 SelectionCondition 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 指定觸發條件的腳本。|
|[設定之控制項的 SelectionCondition 的 SelectionSetName 元素 (格式)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 指定觸發條件的 .NET 類型集合。|
|[設定之控制項的 SelectionCondition 的 TypeName 元素 (格式)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 指定觸發條件的 .NET 類型。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[設定之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|定義使用此通用控制項定義之專案的 .NET 類型。|

## <a name="remarks"></a>備註

定義選取條件時，必須遵循下列指導方針：

- 選取條件必須指定至少一個屬性名稱或腳本區塊，但不能同時指定兩者。

- 選取條件可以指定任意數目的 .NET 類型或選擇集，但無法同時指定兩者。

如需如何使用選取條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另請參閱

[設定之控制項的 SelectionCondition 的 PropertyName 元素 (格式)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[設定之控制項的 SelectionCondition 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[設定之控制項的 SelectionCondition 的 SelectionSetName 元素 (格式)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[設定之控制項的 SelectionCondition 的 TypeName 元素 (格式)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[設定之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[撰寫 Windows PowerShell 格式化和類型檔案](./writing-a-powershell-formatting-file.md)
