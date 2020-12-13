---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之控制項的 CustomEntries 的 CustomEntry 元素 (格式)
description: 檢視之控制項的 CustomEntries 的 CustomEntry 元素 (格式)
ms.openlocfilehash: a525b198c8f595e04dc0804d36b5533b94f43c6b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646086"
---
# <a name="customentry-element-for-customentries-for-controls-for-view-format"></a>檢視之控制項的 CustomEntries 的 CustomEntry 元素 (格式)

提供控制項的定義。 當定義可供視圖使用的控制項時，會使用這個元素。

設定元素 (格式) ViewDefinitions 元素 (格式) View 專案 (格式) 控制項專案 (格式) 控制項專案 (格式) CustomEntries 專案 (格式) 專案 (格式)  (格式控制項的控制項) 格式元素格式 CustomEntry 專案的控制項格式

## <a name="syntax"></a>語法

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `CustomEntry` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[檢視之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 定義使用此控制項定義的 .NET 型別，或必須存在才能使用此定義的條件。|
|[檢視之控制項的 CustomEntry 的 CustomItem 元素 (格式)](./customitem-element-for-customentry-for-controls-for-view-format.md)|必要元素。<br /><br /> 定義控制項顯示資料的方式。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[檢視之 CustomControl 的 CustomEntries 元素 (格式)](./customentries-element-for-customcontrol-for-view-format.md)|提供控制項的定義。|

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[檢視之 CustomControl 的 CustomEntries 元素 (格式)](./customentries-element-for-customcontrol-for-view-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
