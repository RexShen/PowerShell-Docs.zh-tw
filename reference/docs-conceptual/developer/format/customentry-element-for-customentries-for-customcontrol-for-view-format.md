---
title: CustomControl for View (格式) 的 CustomEntries 的 CustomEntry 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a13e83ec941bed80eaab02e40131054432fcce00
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785875"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a>檢視之 CustomControl 的 CustomEntries 的 CustomEntry 元素 (格式)

提供自訂控制項視圖的定義。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (Format) CustomControl 元素 (format) CustomEntries 元素 for CustomControl for view (format) CustomEntry 元素 for View (Format) 

## <a name="syntax"></a>語法

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `CustomEntry` 。 您必須指定定義所顯示的專案。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[CustomEntry for View (格式的之 entryselectedby 元素) ](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 定義使用自訂控制項視圖定義的 .NET 類型，或必須存在才能使用此定義的條件。|
|[CustomEntry for View (格式的 CustomItem 元素) ](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|定義自訂控制項定義的控制項。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[檢視之 CustomControl 的 CustomEntries 元素 (格式)](./customentries-element-for-customcontrol-for-view-format.md)|提供自訂控制項視圖的定義。 自訂控制項視圖必須指定一或多個定義。|

## <a name="remarks"></a>備註

在大部分的情況下，每個自訂控制項視圖都只需要一個定義，但是如果您想要使用相同的視圖來顯示不同的 .NET 物件，則可能會有多個定義。 在這些情況下，您可以為每個物件或一組物件提供個別的定義。

## <a name="see-also"></a>另請參閱

[檢視的 CustomControl 元素 (格式)](./customcontrol-element-for-view-format.md)

[CustomEntry for View (格式的 CustomItem 元素) ](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[CustomEntry for View (格式的之 entryselectedby 元素) ](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
