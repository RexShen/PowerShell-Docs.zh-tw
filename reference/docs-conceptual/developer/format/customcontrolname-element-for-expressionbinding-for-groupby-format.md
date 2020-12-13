---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy 之 ExpressionBinding 的 CustomControlName 元素 (格式)
description: GroupBy 之 ExpressionBinding 的 CustomControlName 元素 (格式)
ms.openlocfilehash: bb7dbd449137628da1794628c5a7d7e10158dd46
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655435"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a>GroupBy 之 ExpressionBinding 的 CustomControlName 元素 (格式)

指定通用控制項或 view 控制項的名稱。 定義如何顯示新的物件群組時，會使用這個元素。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy 專案的視圖 (格式) CustomEntries 元素用於 GroupBy (格式) 元素用於 CustomEntry 的 groupby (格式) CustomControl 專案用於 CustomItem 的 groupby (格式) CustomEntry 專案的 ExpressionBinding 的 groupby (格式) CustomItem 元素

## <a name="syntax"></a>語法

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `CustomControlName` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[GroupBy 之 CustomItem 的 ExpressionBinding 元素 (格式)](./expressionbinding-element-for-customitem-for-groupby-format.md)|定義控制項所顯示的資料。|

## <a name="text-value"></a>文字值

指定控制項的名稱。

## <a name="remarks"></a>備註

您可以建立可供格式化檔案的所有視圖使用的通用控制項，也可以建立可供特定視圖使用的 view 控制項。 下列元素會指定這些控制項的名稱：

- [設定之控制項的控制項的名稱元素 (格式)](./name-element-for-control-for-controls-for-configuration-format.md)

- [檢視之控制項的控制項的名稱元素 (格式)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>另請參閱

[設定之控制項的控制項的名稱元素 (格式)](./name-element-for-control-for-controls-for-configuration-format.md)

[檢視之控制項的控制項的名稱元素 (格式)](./name-element-for-control-for-controls-for-view-format.md)

[GroupBy 之 CustomItem 的 ExpressionBinding 元素 (格式)](./expressionbinding-element-for-customitem-for-groupby-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
