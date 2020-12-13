---
ms.date: 09/13/2016
ms.topic: reference
title: 設定之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)
description: 設定之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)
ms.openlocfilehash: fadcdb69ac71269ba2f2f80baf139bb363d4acba
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666666"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a>設定之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)

定義 .NET 型別，這些型別會使用通用控制項的定義或必須存在才能使用此控制項的條件。 當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。

設定專案 (格式) 控制項的設定專案 (格式設定的控制項) 控制項專案 (格式) CustomEntries 專案的 CustomControl 設定 (格式) 的格式 (格式) CustomControl 專案設定 (格式)  (格式的控制項) 格式

## <a name="syntax"></a>語法

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `EntrySelectedBy` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[設定之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 定義要使用的通用控制項定義必須存在的條件。|
|[設定之控制項的 EntrySelectedBy 的 SelectionSetName 元素 (格式)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 指定一組使用此通用控制項定義的 .NET 類型。|
|[設定之控制項的 EntrySelectedBy 的 TypeName 元素 (格式)](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 指定使用此通用控制項定義的 .NET 類型。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[設定之控制項的控制項 CustomControl 的 CustomEntry 元素 (格式)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|提供通用控制項的定義。|

## <a name="remarks"></a>備註

每個定義至少必須指定一個 .NET 類型、選取集或選取條件。 您可以指定的類型、選取集或選取條件數目沒有最大限制。

## <a name="see-also"></a>另請參閱

[設定之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[設定之控制項的 EntrySelectedBy 的 SelectionSetName 元素 (格式)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[設定之控制項的控制項 CustomControl 的 CustomEntry 元素 (格式)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[設定之控制項的 EntrySelectedBy 的 TypeName 元素 (格式)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
