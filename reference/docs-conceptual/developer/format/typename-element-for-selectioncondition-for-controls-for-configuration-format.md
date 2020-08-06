---
title: 設定 (格式) 之控制項的 SelectionCondition 的 TypeName 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2db856d1b84dded315204d8c8574ae86acb63515
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780061"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-configuration-format"></a>設定之控制項的 SelectionCondition 的 TypeName 元素 (格式)

指定觸發條件的 .NET 類型。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

Configuration 元素 (格式) Controls 設定的控制項元素 (格式設定的控制項) 控制項專案 (格式) 設定 (格式的控制項的 CustomControl 的 CustomEntries 元素) CustomEntry 元素針對設定 (格式的控制項的 CustomControl) 之 entryselectedby 元素，用於 CustomEntry 的之 entryselectedby for CustomEntry for configuration (Format) TypeName 元素 For SelectionCondition for configuration (格式) )  (

## <a name="syntax"></a>語法

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `TypeName` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[適用于 CustomEntry 之之 entryselectedby 的 SelectionCondition 元素 (格式) ](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|定義必須存在的條件，才能使用控制項定義。|

## <a name="text-value"></a>文字值

指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo` 。

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[適用于 CustomEntry 之之 entryselectedby 的 SelectionCondition 元素 (格式) ](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
