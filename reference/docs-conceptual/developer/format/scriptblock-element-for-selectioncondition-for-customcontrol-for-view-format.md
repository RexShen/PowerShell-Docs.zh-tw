---
title: SelectionCondition for CustomControl for View (Format) 的 ScriptBlock 元素Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d3506188d32ce85ad6345dc0d0866dd789a1f293
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785399"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a>檢視之 CustomControl 的 SelectionCondition 的 ScriptBlock 元素 (格式)

指定觸發條件的腳本。 當此腳本評估為時 `true` ，會符合條件，並使用定義。 定義自訂控制項視圖時，會使用這個元素。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (Format) CustomControl for view (格式的 CustomEntries 專案) 格式 (CustomEntry for CustomEntries for view) CustomControl 元素的 CustomItem for CustomEntry for view (format) CustomControl 元素 for SelectionCondition for view (格式) 之 entryselectedby 元素（CustomControl for SelectionCondition for view (format) ScriptBlock 元素） (

## <a name="syntax"></a>語法

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `ScriptBlock` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[CustomControl for View (格式) 的之 entryselectedby 的 SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|定義必須存在的條件，才能使用控制項定義。|

## <a name="text-value"></a>文字值

指定要評估的腳本。

## <a name="remarks"></a>備註

選取條件必須指定至少一個要評估的腳本或屬性名稱，但不能同時指定兩者。 如需如何使用選取條件的詳細資訊，請參閱[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另請參閱

[CustomControl for View (格式) 的之 entryselectedby 的 SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
