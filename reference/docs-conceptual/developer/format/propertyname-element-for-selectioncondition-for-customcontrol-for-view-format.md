---
title: SelectionCondition for CustomControl for View (格式的 PropertyName 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: aa3955b84b8de9901f394e8108f31440fcb6c942
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780792"
---
# <a name="propertyname-element-for-selectioncondition-for-customcontrol-for-view-format"></a>檢視之 CustomControl 的 SelectionCondition 的 PropertyName 元素 (格式)

指定觸發條件的 .NET 屬性。 當這個屬性存在或評估為時 `true` ，就會符合條件，並使用定義。 定義自訂控制項視圖時，會使用這個元素。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) CustomControl for View 的 CustomEntries 專案 (格式) CustomEntry 專案的 CustomEntries for CustomControl for View (CustomItem 元素針對 CustomControl for view (格式的 CustomEntry，) 之 entryselectedby 元素用於 CustomEntry for CustomControl for view (Format) SelectionCondition for 之 entryselectedby for view (格式) PropertyName 元素，CustomControl for SelectionCondition for View (格式) 

## <a name="syntax"></a>語法

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `PropertyName` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[CustomControl for View (格式) 的之 entryselectedby 的 SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|定義必須存在的條件，才能使用控制項定義。|

## <a name="text-value"></a>文字值

指定 .NET 屬性名稱。

## <a name="remarks"></a>備註

選取條件必須指定至少一個屬性名稱或腳本，但不能同時指定兩者。 如需如何使用選取條件的詳細資訊，請參閱[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另請參閱

[CustomControl for View (格式) 的之 entryselectedby 的 SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
