---
ms.date: 09/13/2016
ms.topic: reference
title: 設定之控制項的控制項 CustomControl 的 CustomEntry 元素 (格式)
description: 設定之控制項的控制項 CustomControl 的 CustomEntry 元素 (格式)
ms.openlocfilehash: 3967be86a1d6c12c7215ef19d50bac9fafd5ad6d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648283"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a>設定之控制項的控制項 CustomControl 的 CustomEntry 元素 (格式)

提供通用控制項的定義。 當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。

設定專案 (格式) 控制項的設定專案 (格式設定的控制項) 控制項專案 (格式) CustomEntries 專案的 CustomControl 設定 (格式) CustomEntry 元素，用於的設定 (格式)  (的控制項 CustomControl 的控制項

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
|[設定之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 定義 .NET 型別，這些型別會使用通用控制項的定義或必須存在才能使用此控制項的條件。|
|[適用于設定之控制項的 CustomEntry CustomItem 元素](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|必要元素。<br /><br /> 定義控制項顯示的資料以及其顯示方式。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[適用于 CustomControl 的 CustomEntries 元素，適用于 Configuration (格式) ](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|提供通用控制項的定義。|

## <a name="remarks"></a>備註

在大部分的情況下，每個通用自訂控制項都只需要一個定義，但如果您想要使用相同的控制項來顯示不同的 .NET 物件，則可以有多個定義。 在這些情況下，您可以為每個物件或一組物件提供個別的定義。

## <a name="see-also"></a>另請參閱

[適用于 CustomControl 的 CustomEntries 元素，適用于 Configuration (格式) ](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[適用于設定之控制項的 CustomEntry CustomItem 元素](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
