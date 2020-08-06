---
title: 適用于 CustomControl 之 GroupBy (格式的 CustomEntry 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4df8e5b96868b3814c6d84fa329950bb5345ef6e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785909"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a>GroupBy 之 CustomControl 的 CustomEntry 元素 (格式)

提供控制項的定義。 此元素是在定義新物件群組的顯示方式時使用。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy 元素（groupby (格式）) CustomEntries 元素（適用于 groupby (格式的 CustomEntry) CustomControl 元素） (

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
|[GroupBy 之 CustomEntry 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-customentry-for-groupby-format.md)|選擇性項目。<br /><br /> 定義使用此控制項定義的 .NET 類型，或必須存在才能使用此定義的條件。|
|[GroupBy 之 CustomEntry 的 CustomItem 元素 (格式)](./customitem-element-for-customentry-for-groupby-format.md)|必要元素。<br /><br /> 定義控制項顯示資料的方式。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[GroupBy 之 CustomControl 的 CustomEntries 元素 (格式)](./customentries-element-for-customcontrol-for-groupby-format.md)|提供控制項的定義。|

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[GroupBy 之 CustomEntry 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-customentry-for-groupby-format.md)

[GroupBy 之 CustomEntry 的 CustomItem 元素 (格式)](./customitem-element-for-customentry-for-groupby-format.md)

[GroupBy 之 CustomControl 的 CustomEntries 元素 (格式)](./customentries-element-for-customcontrol-for-groupby-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
