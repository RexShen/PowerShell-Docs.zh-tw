---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)
description: 檢視之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)
ms.openlocfilehash: 29b0574a95d81962fb3f72a526f89273baeea647
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660255"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a>檢視之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)

定義使用此控制項定義的 .NET 型別，或必須存在才能使用此定義的條件。 當定義可供視圖使用的控制項時，會使用這個元素。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) Control 元素 (format) format (format 控制項控制項的控制項) CustomEntries (格式控制項的控制項) 專案 (格式) 專案 (格式) 專案 (格式) 專案格式控制項的

## <a name="syntax"></a>語法

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述專案的屬性、子項目和父元素 `EntrySelectedBy` 。 您必須為定義指定至少一個類型、選取集或選取條件。 您可以使用的子項目數目沒有最大限制。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[檢視之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 定義必須存在的條件，才能使用這個定義。|
|[檢視之控制項的 EntrySelectedBy 的 SelectionSetName 元素 (格式)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 指定一組使用此控制項定義的 .NET 類型。|
|[檢視之控制項的 EntrySelectedBy 的 TypeName 元素 (格式)](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 指定使用此控制項定義的 .NET 類型。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[檢視之控制項的 CustomEntries 的 CustomEntry 元素 (格式)](./customentry-element-for-customentries-for-controls-for-view-format.md)|提供控制項的定義。|

## <a name="remarks"></a>備註

選取條件是用來定義必須存在才能使用定義的條件，例如當物件有特定屬性，或當特定屬性值或腳本評估為時 `true` 。 如需選取條件的詳細資訊，請參閱 [定義使用視圖專案或專案的條件](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另請參閱

[檢視之控制項的 CustomEntries 的 CustomEntry 元素 (格式)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
