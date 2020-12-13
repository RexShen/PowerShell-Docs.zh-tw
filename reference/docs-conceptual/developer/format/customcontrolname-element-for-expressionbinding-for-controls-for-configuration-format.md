---
ms.date: 09/13/2016
ms.topic: reference
title: 設定之控制項的 ExpressionBinding 的 CustomControlName 元素 (格式)
description: 設定之控制項的 ExpressionBinding 的 CustomControlName 元素 (格式)
ms.openlocfilehash: 3815956f59f19c0215aaf26b94dede656b9453cb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648319"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format"></a>設定之控制項的 ExpressionBinding 的 CustomControlName 元素 (格式)

指定通用控制項的名稱。 當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。

設定元素 (格式) 控制項的設定元素 (格式) 控制項的設定 (格式) CustomControl 元素，用於 CustomControl 的設定 (格式) CustomEntry 元素針對 configuration (格式的控制項的 CustomControl 格式) CustomItem 元素，用於 CustomEntry 的控制項，以設定 (格式的控制項之 CustomItem 的 CustomControlName 專案) ExpressionBinding 元素)  (

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
|[設定之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|定義控制項所顯示的資料。|

## <a name="text-value"></a>文字值

指定控制項的名稱。

## <a name="remarks"></a>備註

您可以建立可供格式化檔案的所有視圖使用的通用控制項，也可以建立可供特定視圖使用的 view 控制項。 下列元素會指定這些控制項的名稱：

- [設定之控制項的控制項的名稱元素 (格式)](./name-element-for-control-for-controls-for-configuration-format.md)

- [檢視之控制項的控制項的名稱元素 (格式)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>另請參閱

[設定之控制項的控制項的名稱元素 (格式)](./name-element-for-control-for-controls-for-configuration-format.md)

[檢視之控制項的控制項的名稱元素 (格式)](./name-element-for-control-for-controls-for-view-format.md)

[設定之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
