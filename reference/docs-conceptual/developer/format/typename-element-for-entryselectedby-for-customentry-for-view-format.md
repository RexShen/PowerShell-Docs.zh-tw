---
title: CustomEntry for View (格式的之 entryselectedby 的 TypeName 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: f8dc2c808e6eb3d6a7873cdbddc936b95d94c541
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785093"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a>檢視之 CustomEntry 的 EntrySelectedBy 的 TypeName 元素 (格式)

指定使用自訂控制項視圖之定義的 .NET 類型。 可以針對定義指定的類型數目沒有限制。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) CustomControl 專案 (格式) CustomControl for view (CustomEntry 元素，CustomEntries for view) format (之 entryselectedby 專案（CustomEntry for 之 entryselectedby for view) 格式 (CustomEntry 元素) 

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
|[CustomEntry for View (格式的之 entryselectedby 元素) ](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|定義使用此自訂控制項視圖定義的 .NET 類型，或必須存在才能使用此定義的條件。|

## <a name="text-value"></a>文字值

指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo` 。

## <a name="remarks"></a>備註

每個自訂控制項視圖定義都必須定義至少一個型別名稱、選擇集或選取條件。

如需自訂控制項視圖之元件的詳細資訊，請參閱[建立自訂控制項](./creating-custom-controls.md)。

## <a name="see-also"></a>另請參閱

[建立自訂控制項](./creating-custom-controls.md)

[CustomEntry for View (格式的之 entryselectedby 元素) ](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
