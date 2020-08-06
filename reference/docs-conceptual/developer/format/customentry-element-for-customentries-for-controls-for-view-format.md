---
title: View (Format) 的控制項之 CustomEntries 的 CustomEntry 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4fc960ab803580f684ce0f224b1db4d7d4af1720
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785892"
---
# <a name="customentry-element-for-customentries-for-controls-for-view-format"></a>檢視之控制項的 CustomEntries 的 CustomEntry 元素 (格式)

提供控制項的定義。 定義可供視圖使用的控制項時，會使用這個元素。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) 控制項專案 (格式控制項的) 控制項專案 CustomControl 格式 (格式的控制項的 CustomEntries 專案) 格式 (CustomEntry 元素用於 view) 格式的控制項 (CustomEntries 專案

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
|[檢視之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 定義使用此控制項定義的 .NET 類型，或必須存在才能使用此定義的條件。|
|[檢視之控制項的 CustomEntry 的 CustomItem 元素 (格式)](./customitem-element-for-customentry-for-controls-for-view-format.md)|必要元素。<br /><br /> 定義控制項顯示資料的方式。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[檢視之 CustomControl 的 CustomEntries 元素 (格式)](./customentries-element-for-customcontrol-for-view-format.md)|提供控制項的定義。|

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[檢視之 CustomControl 的 CustomEntries 元素 (格式)](./customentries-element-for-customcontrol-for-view-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
