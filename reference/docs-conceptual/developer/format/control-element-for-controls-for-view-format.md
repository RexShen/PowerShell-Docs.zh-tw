---
title: View 控制項的控制項元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fd53f55-698d-4df5-bb9a-fe28dc3193e1
caps.latest.revision: 11
ms.openlocfilehash: df568ccb36a2646b983622cdf95718dd5cac62c3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363467"
---
# <a name="control-element-for-controls-for-view--format"></a>檢視之控制項的控制項元素 (格式)

定義可供視圖使用的控制項，以及用來參考控制項的名稱。

設定專案（格式） ViewDefinitions 元素（格式） View 元素（格式）控制項的元素（格式）控制項專案（格式）

## <a name="syntax"></a>語法

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `Control` 專案的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[View 控制項的 Name 元素（格式）](./name-element-for-control-for-controls-for-view-format.md)|必要項目。<br /><br /> 指定控制項的名稱。|
|[View 控制項的 CustomControl 元素（格式）](./customcontrol-element-for-control-for-controls-for-view-format.md)|必要項目。<br /><br /> 定義此視圖所使用的控制項。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[Controls 元素（格式）](./controls-element-for-view-format.md)|定義可供特定視圖使用的 view 控制項。|

## <a name="remarks"></a>備註

這個控制項可以由下列元素指定：

- [View 之控制項的 ExpressionBinding 的 CustomControlName 元素（格式）](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [CustomControl for View 的 ExpressionBinding 的 CustomControlName 元素（格式）](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [GroupBy 之 ExpressionBinding 的 CustomControlName 元素（格式）](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [GroupBy 的 CustomControlName 元素（格式）](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a>另請參閱

[View 控制項的 CustomControl 元素（格式）](./customcontrol-element-for-control-for-controls-for-view-format.md)

[View 之控制項的 ExpressionBinding 的 CustomControlName 元素（格式）](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[CustomControl for View 的 ExpressionBinding 的 CustomControlName 元素（格式）](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[GroupBy 之 ExpressionBinding 的 CustomControlName 元素（格式）](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[GroupBy 之 ExpressionBinding 的 CustomControlName 元素（格式）](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Controls 元素（格式）](./controls-element-for-view-format.md)

[View 控制項控制項的 Name 元素（格式）](./name-element-for-control-for-controls-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
