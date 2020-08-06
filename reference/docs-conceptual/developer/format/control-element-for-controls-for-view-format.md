---
title: View (格式) 控制項的控制項元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 13ea2f09aec7fea8e5460197f133b5f5219cd369
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783801"
---
# <a name="control-element-for-controls-for-view--format"></a>檢視之控制項的控制項元素 (格式)

定義可供視圖使用的控制項，以及用來參考控制項的名稱。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) Controls 元素 (格式控制項的) 控制項專案 (格式) 

## <a name="syntax"></a>語法

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `Control` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[View (格式之控制項的 Name 元素) ](./name-element-for-control-for-controls-for-view-format.md)|必要元素。<br /><br /> 指定控制項的名稱。|
|[檢視之控制項的控制項 CustomControl 元素 (格式)](./customcontrol-element-for-control-for-controls-for-view-format.md)|必要元素。<br /><br /> 定義此視圖所使用的控制項。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[Controls 元素 (格式) ](./controls-element-for-view-format.md)|定義可供特定視圖使用的 view 控制項。|

## <a name="remarks"></a>備註

這個控制項可以由下列元素指定：

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
