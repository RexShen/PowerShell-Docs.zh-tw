---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之控制項的控制項元素 (格式)
description: 檢視之控制項的控制項元素 (格式)
ms.openlocfilehash: c48b8b7ecaebfde5e6ed2123b837d92561551766
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668077"
---
# <a name="control-element-for-controls-for-view--format"></a>檢視之控制項的控制項元素 (格式)

定義可供視圖使用的控制項，以及用來參考控制項的名稱。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) Control 元素 (format) Control 控制項的控制項 (格式) 

## <a name="syntax"></a>語法

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列章節說明屬性、子專案和元素的父元素 `Control` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[View (Format 的控制項名稱元素) ](./name-element-for-control-for-controls-for-view-format.md)|必要元素。<br /><br /> 指定控制項的名稱。|
|[檢視之控制項的控制項 CustomControl 元素 (格式)](./customcontrol-element-for-control-for-controls-for-view-format.md)|必要元素。<br /><br /> 定義此視圖所使用的控制項。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[Controls 元素 (格式) ](./controls-element-for-view-format.md)|定義可供特定視圖使用的 view 控制項。|

## <a name="remarks"></a>備註

此控制項可以由下列元素指定：

- [檢視之控制項的 ExpressionBinding 的 CustomControlName 元素 (格式)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [檢視之 CustomControl 的 ExpressionBinding 的 CustomControlName 元素 (格式)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [GroupBy 之 ExpressionBinding 的 CustomControlName 元素 (格式)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [GroupBy 的 CustomControlName 元素 (格式)](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a>另請參閱

[檢視之控制項的控制項 CustomControl 元素 (格式)](./customcontrol-element-for-control-for-controls-for-view-format.md)

[檢視之控制項的 ExpressionBinding 的 CustomControlName 元素 (格式)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[檢視之 CustomControl 的 ExpressionBinding 的 CustomControlName 元素 (格式)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[GroupBy 之 ExpressionBinding 的 CustomControlName 元素 (格式)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[GroupBy 之 ExpressionBinding 的 CustomControlName 元素 (格式)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Controls 元素 (格式) ](./controls-element-for-view-format.md)

[檢視之控制項的控制項的名稱元素 (格式)](./name-element-for-control-for-controls-for-view-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
