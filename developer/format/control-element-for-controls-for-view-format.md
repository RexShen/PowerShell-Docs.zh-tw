---
title: 控制控制項的項目，檢視 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fd53f55-698d-4df5-bb9a-fe28dc3193e1
caps.latest.revision: 11
ms.openlocfilehash: df568ccb36a2646b983622cdf95718dd5cac62c3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853724"
---
# <a name="control-element-for-controls-for-view--format"></a>檢視之控制項的控制項元素 (格式)

定義可供檢視和名稱，用來參考控制項的控制項。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） 的檢視 （格式） 控制項的 Controls 項目 （格式） 控制項項目

## <a name="syntax"></a>語法

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`Control`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[控制項的檢視 （格式） 的 name 元素](./name-element-for-control-for-controls-for-view-format.md)|必要項目。<br /><br /> 指定控制項的名稱。|
|[用於檢視 （格式） 的控制項的控制項 CustomControl 項目](./customcontrol-element-for-control-for-controls-for-view-format.md)|必要項目。<br /><br /> 定義這份檢視所使用的控制項。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[控制項項目 （格式）](./controls-element-for-view-format.md)|定義可供特定檢視的檢視控制項。|

## <a name="remarks"></a>備註

這個控制項可以指定下列項目：

- [用於檢視 （格式） 的控制項 ExpressionBinding CustomControlName 項目](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [CustomControlName CustomControl 檢視 （格式） 的 ExpressionBinding 的項目](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [CustomControlName ExpressionBinding 的 GroupBy （格式） 的項目](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [CustomControlName GroupBy （格式） 的項目](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a>另請參閱

[用於檢視 （格式） 的控制項的控制項 CustomControl 項目](./customcontrol-element-for-control-for-controls-for-view-format.md)

[用於檢視 （格式） 的控制項 ExpressionBinding CustomControlName 項目](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[CustomControlName CustomControl 檢視 （格式） 的 ExpressionBinding 的項目](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[CustomControlName ExpressionBinding 的 GroupBy （格式） 的項目](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[CustomControlName ExpressionBinding 的 GroupBy （格式） 的項目](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[控制項項目 （格式）](./controls-element-for-view-format.md)

[用於檢視 （格式） 的控制項的控制項的 name 元素](./name-element-for-control-for-controls-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
